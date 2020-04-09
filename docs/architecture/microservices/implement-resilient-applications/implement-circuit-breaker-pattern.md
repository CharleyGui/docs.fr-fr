---
title: Implémentation du modèle Disjoncteur
description: Découvrez comment implémenter le modèle Disjoncteur en tant que système complémentaire aux nouvelles tentatives Http.
ms.date: 03/03/2020
ms.openlocfilehash: bebe0b4a622db928175f78f8d3e303d3d7adf170
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988883"
---
# <a name="implement-the-circuit-breaker-pattern"></a>Implémenter le modèle Disjoncteur

Comme indiqué précédemment, vous devez gérer des erreurs dont le temps de récupération peut être variable, comme ça peut être le cas quand vous essayez de vous connecter à une ressource ou à un service distant. La gestion de ce type d’erreur peut améliorer la stabilité et la résilience d’une application.

Dans un environnement distribué, les appels à des ressources et services distants peuvent échouer en raison d’erreurs temporaires, telles que des connexions réseau lentes, l’expiration de délais d’attente, ou si des ressources ont un temps de réponse trop long ou sont temporairement indisponibles. En général, ces erreurs se corrigent d’elles-mêmes après un bref laps de temps, et une application cloud fiable doit être prête à les gérer à l’aide d’une stratégie comme le « modèle Nouvelle tentative ».

Toutefois, dans certaines situations, les erreurs sont dues à des événements imprévus dont la correction peut prendre beaucoup plus de temps. Ces erreurs peuvent aller d’une perte partielle de connectivité à la défaillance complète d’un service. Dans ces cas de figure, il peut être inutile qu’une application effectue de nouvelles tentatives dont la réussite sera peu probable.

L’application doit plutôt être codée pour reconnaître que l’opération a échoué et gérer l’échec en conséquence.

L’utilisation désinvolte des nouvelles tentatives Http peut entraîner la création d’une attaque par déni de service ([DoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)) au sein de votre propre logiciel. Lorsqu’un microservice échoue ou s’exécute lentement, plusieurs clients peuvent répéter à plusieurs reprises les demandes ayant échoué. Ceci crée un risque dangereux d’augmentation exponentielle du trafic ciblé vers le service défaillant.

Par conséquent, vous avez besoin d’une sorte de barrière de défense afin d’empêcher de nouvelles tentatives inutiles après un nombre excessif de requêtes. Cette barrière de défense est précisément le disjoncteur.

L’objectif du modèle Disjoncteur est différent de celui du « modèle Nouvelle tentative ». Le « modèle Nouvelle tentative » permet à une application de retenter une opération en partant du principe qu’elle finira par réussir. Le modèle Disjoncteur empêche une application d’effectuer une opération qui échouera probablement. Une application peut combiner ces deux modèles. Toutefois, la logique de nouvelle tentative doit être sensible aux exceptions retournées par le disjoncteur et doit abandonner les nouvelles tentatives si le disjoncteur indique qu’une erreur n’est pas temporaire.

## <a name="implement-circuit-breaker-pattern-with-ihttpclientfactory-and-polly"></a>Implémenter le `IHttpClientFactory` modèle de disjoncteur avec et Polly

Comme lors de la mise en œuvre des retries, l’approche recommandée pour les `IHttpClientFactory`disjoncteurs est de profiter de bibliothèques .NET prouvées comme Polly et son intégration indigène avec .

L’ajout d’une `IHttpClientFactory` politique de disjoncteur dans votre pipeline de middleware sortant `IHttpClientFactory`est aussi simple que l’ajout d’un seul morceau de code incrémental à ce que vous avez déjà lors de l’utilisation .

Ici, le seul ajout au code utilisé pour les nouvelles tentatives d’appel HTTP est le code où vous ajoutez la stratégie Disjoncteur à la liste des stratégies à utiliser, comme indiqué dans le code incrémentiel suivant, inscrit dans la méthode ConfigureServices().

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Sample. Default lifetime is 2 minutes
        .AddHttpMessageHandler<HttpClientAuthorizationDelegatingHandler>()
        .AddPolicyHandler(GetRetryPolicy())
        .AddPolicyHandler(GetCircuitBreakerPolicy());
```

La méthode `AddPolicyHandler()` ajoute des stratégies aux objets `HttpClient` que vous utiliserez. Dans ce cas, elle ajoute une stratégie Polly pour un disjoncteur.

Pour bénéficier d’une approche plus modulaire, la stratégie Disjoncteur est définie dans une méthode distincte nommée `GetCircuitBreakerPolicy()`, comme illustré dans le code suivant :

```csharp
static IAsyncPolicy<HttpResponseMessage> GetCircuitBreakerPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));
}
```

Dans l’exemple de code ci-dessus, la stratégie Disjoncteur est configurée de manière à rompre ou ouvrir le circuit après cinq erreurs consécutives lors des nouvelles tentatives de requêtes HTTP. Quand cela se produit, le circuit est rompu pendant 30 secondes : durant ce laps de temps, le disjoncteur met immédiatement les appels en échec au lieu de les transmettre.  La stratégie interprète automatiquement [les exceptions et les codes d’état HTTP correspondants](/aspnet/core/fundamentals/http-requests#handle-transient-faults) comme des erreurs.  

Les disjoncteurs doivent également être utilisés pour rediriger les requêtes vers une infrastructure de secours si vous rencontrez des problèmes dans une ressource particulière déployée dans un environnement autre que l’application cliente ou le service qui effectue l’appel HTTP. De cette façon, si le centre de données subit une panne qui a un impact uniquement sur vos microservices back-end, mais pas sur vos applications clientes, ces dernières peuvent effectuer une redirection vers les services de secours. Polly planifie une nouvelle stratégie pour automatiser ce scénario de [stratégie de basculement](https://github.com/App-vNext/Polly/wiki/Polly-Roadmap#failover-policy).

Toutes ces fonctionnalités sont appropriées pour les cas où vous gérez le basculement à partir du code .NET, au lieu qu’il soit géré automatiquement par Azure, avec la transparence des emplacements.

D’un point de vue d’utilisation, lors de l’utilisation de HttpClient, il `HttpClient` n’est pas nécessaire d’ajouter quelque chose de nouveau ici parce que le code est le même que lors de l’utilisation avec `IHttpClientFactory`, comme indiqué dans les sections précédentes.

## <a name="test-http-retries-and-circuit-breakers-in-eshoponcontainers"></a>Tester les disjoncteurs et les nouvelles tentatives Http dans eShopOnContainers

Chaque fois que vous démarrez la solution eShopOnContainers sur un hôte Docker, celle-ci doit démarrer plusieurs conteneurs. Certains des conteneurs sont plus lents à démarrer et à initialiser, comme le conteneur SQL Server. C’est particulièrement vrai la première fois que vous déployez l’application eShopOnContainers dans Docker, car elle doit configurer les images et la base de données. Le fait que certains conteneurs démarrent plus lentement que d’autres peut entraîner la levée d’exceptions HTTP par le reste des services, même si vous définissez des dépendances entre les conteneurs au niveau de Docker Compose, comme expliqué dans les sections précédentes. Ces dépendances Docker Compose entre les conteneurs sont uniquement au niveau processus. Le processus de point d’entrée du conteneur pourrait être lancé, mais SQL Server pourrait ne pas être prêt pour les requêtes. Cela peut avoir pour conséquence une cascade d’erreurs, et l’application peut recevoir une exception lors d’une tentative d’utilisation de ce conteneur particulier.

Vous pouvez également voir ce type d’erreur au démarrage pendant le déploiement de l’application dans le cloud. Dans ce cas, les orchestrateurs peuvent déplacer des conteneurs d’un nœud ou d’une VM à un autre (c’est-à-dire à commencer de nouveaux cas) lorsqu’ils équilibrent le nombre de conteneurs dans les nœuds du cluster.

La façon dont « eShopOnContainers » résout ces problèmes lors du démarrage de tous les conteneurs consiste à utiliser le modèle de nouvelle tentative illustré précédemment.

### <a name="test-the-circuit-breaker-in-eshoponcontainers"></a>Tester le disjoncteur dans eShopOnContainers

Il existe plusieurs façons de rompre/ouvrir le circuit et de le tester avec eShopOnContainers.

L’une des options consiste à réduire le nombre de tentatives autorisées à 1 dans la stratégie Disjoncteur et à redéployer l’ensemble de la solution dans Docker. Avec une seule nouvelle tentative, il y a de fortes chances qu’une requête HTTP échoue pendant le déploiement, que le disjoncteur s’ouvre et que vous obteniez une erreur.

Une autre option consiste à utiliser l’intergiciel (middleware) personnalisé qui est implémenté dans le microservice **Basket**. Quand ce middleware est activé, il intercepte toutes les requêtes HTTP et retourne le code d’état 500. Vous pouvez activer le middleware en effectuant une requête GET à l’URI qui a échoué, comme suit :

- `GET http://localhost:5103/failing`\
  Cette requête retourne l’état actuel du middleware. Si le middleware est activé, la requête retourne le code d’état 500. Si le middleware est désactivé, il n’y a pas de réponse.

- `GET http://localhost:5103/failing?enable`\
  Cette requête active le middleware.

- `GET http://localhost:5103/failing?disable`\
  Cette requête désactive le middleware.

Par exemple, une fois que l’application est en cours d’exécution, vous pouvez activer le middleware en créant une requête à l’aide de l’URI suivant dans n’importe quel navigateur. Notez que le microservice de commandes utilise le port 5103.

`http://localhost:5103/failing?enable`

Vous pouvez alors vérifier l’état à l’aide de l’URI `http://localhost:5103/failing`, comme illustré à la Figure 8-5.

![Capture d’écran de la vérification de l’état de la simulation middleware défaillante.](./media/implement-circuit-breaker-pattern/failing-middleware-simulation.png)

**Figure 8-5**. Vérification de l’état de la "Failing" ASP.NET middleware - Dans ce cas, désactivé.

À ce stade, le microservice Basket répond avec le code d’état 500 chaque fois que vous l’appelez.

Une fois que le middleware est en cours d’exécution, vous pouvez essayer d’effectuer une commande à partir de l’application web MVC. Étant donné que les requêtes échouent, le circuit s’ouvre.

Dans l’exemple suivant, vous pouvez voir que l’application web MVC a un bloc catch dans la logique du processus consistant à passer une commande.  Si le code intercepte une exception de circuit ouvert, il affiche à l’utilisateur un message convivial l’invitant à patienter.

```csharp
public class CartController : Controller
{
    //…
    public async Task<IActionResult> Index()
    {
        try
        {
            var user = _appUserParser.Parse(HttpContext.User);
            //Http requests using the Typed Client (Service Agent)
            var vm = await _basketSvc.GetBasket(user);
            return View(vm);
        }
        catch (BrokenCircuitException)
        {
            // Catches error when Basket.api is in circuit-opened mode
            HandleBrokenCircuitException();
        }
        return View();
    }

    private void HandleBrokenCircuitException()
    {
        TempData["BasketInoperativeMsg"] = "Basket Service is inoperative, please try later on. (Business message due to Circuit-Breaker)";
    }
}
```

Voici un récapitulatif. La stratégie Nouvelle tentative tente plusieurs fois d’exécuter la requête HTTP et obtient des erreurs HTTP. Quand le nombre maximal de nouvelles tentatives pour la stratégie Disjoncteur est atteint (dans le cas présent, 5), l’application lève une exception BrokenCircuitException. Le résultat est un message convivial, comme illustré à la Figure 8-6.

![Capture d’écran de l’application web MVC avec erreur inopérante du service de panier.](./media/implement-circuit-breaker-pattern/basket-service-inoperative.png)

**Figure 8-6**. Disjoncteur retournant une erreur à l’interface utilisateur

Vous pouvez implémenter une logique différente pour déterminer quand ouvrir/rompre le circuit. Vous pouvez également essayer une requête HTTP sur un autre microservice back-end s’il existe un centre de données de secours ou un système back-end redondant.

Enfin, une autre solution pour la stratégie `CircuitBreakerPolicy` consiste à utiliser `Isolate` (qui force l’ouverture du circuit et le maintient ouvert) et `Reset` (qui le referme). Ces solutions peuvent être utilisées pour créer un point de terminaison HTTP d’utilitaire qui appelle Isolate et Reset directement sur la stratégie.  Un tel point de terminaison HTTP peut également être utilisé, correctement sécurisé, en production pour l’isolation temporaire d’un système en aval, par exemple quand vous voulez procéder à sa mise à niveau. Ou bien il peut déclencher le circuit manuellement pour protéger un système en aval que vous soupçonnez d’avoir provoqué l’erreur.

## <a name="additional-resources"></a>Ressources supplémentaires

- **Modèle de disjoncteur**\
  [https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker](/azure/architecture/patterns/circuit-breaker)

>[!div class="step-by-step"]
>[Suivant précédent](implement-http-call-retries-exponential-backoff-polly.md)
>[Next](monitor-app-health.md)
