---
title: Modèles de résilience d’application
description: Architecture des applications .NET natives Cloud pour Azure | Modèles de résilience d’application
ms.date: 06/30/2019
ms.openlocfilehash: 6805603f349578655b2535c7346af368c5ce1841
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199688"
---
# <a name="application-resiliency-patterns"></a>Modèles de résilience d’application

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

La première ligne de défense est la résilience des applications à extension logicielle.

Bien que vous puissiez consacrer beaucoup de temps à écrire votre propre infrastructure de résilience, de tels produits existent déjà. Par exemple, [Polly](http://www.thepollyproject.org/) est une bibliothèque complète de résilience .net et de gestion des erreurs temporaires qui permet aux développeurs d’exprimer les stratégies de résilience de façon Fluent et thread-safe. Polly cible les applications générées à l’aide de la .NET Framework complète ou de .NET Core. La figure 6-2 montre les stratégies de résilience (c’est-à-dire les fonctionnalités) disponibles à partir de la bibliothèque Polly. Ces stratégies peuvent être appliquées individuellement ou combinées ensemble.

![Framework Polly](./media/polly-resiliency-framework.png)

**Figure 6-2**. Fonctionnalités de l’infrastructure de résilience Polly

Notez comment, dans la figure précédente, les stratégies de résilience s’appliquent aux messages de demande, qu’ils proviennent d’un client externe ou d’un autre service principal. L’objectif est de compenser la demande d’un service qui peut être momentanément indisponible. Ces interruptions courtes se manifestent généralement avec les codes d’état HTTP illustrés dans la figure 6-3.

![Codes d’état HTTP à réessayer](./media/http-status-codes.png)

**Figure 6-3**. Codes d’état HTTP à réessayer

Question : voulez-vous réessayer un code d’état HTTP 403-interdit ? Non. Ici, le système fonctionne correctement, mais informe l’appelant qu’il n’est pas autorisé à effectuer l’opération demandée. Vous devez veiller à ne réessayer que les opérations provoquées par des défaillances.

Comme nous l’avons recommandé dans le chapitre 1, les développeurs Microsoft qui créent des applications Cloud natives doivent cibler .NET Core. La version 2,1 a introduit la bibliothèque [HTTPClientFactory](https://www.stevejgordon.co.uk/introduction-to-httpclientfactory-aspnetcore) pour la création d’instances client http pour l’interaction avec les ressources basées sur une URL. En remplaçant la classe HTTPClient d’origine, la classe Factory prend en charge de nombreuses fonctionnalités améliorées, dont l’une est une [intégration étroite](../microservices/implement-resilient-applications/implement-http-call-retries-exponential-backoff-polly.md) avec la bibliothèque de résilience Polly. Avec elle, vous pouvez facilement définir des stratégies de résilience dans la classe de démarrage de l’application pour gérer les défaillances partielles et les problèmes de connectivité.

Nous allons ensuite développer les modèles de réessai et de disjoncteur.

### <a name="retry-pattern"></a>Modèle Nouvelle tentative

Dans un environnement Cloud natif distribué, les appels aux services et aux ressources de Cloud peuvent échouer en raison d’échecs temporaires (éphémères), qui se corrigent généralement après une courte période de temps. L’implémentation d’une stratégie de nouvelle tentative aide un service Cloud-native à gérer ces scénarios.

Le [modèle de nouvelle tentative](https://docs.microsoft.com/azure/architecture/patterns/retry) permet à un service de retenter une opération de demande ayant échoué (configurable) un nombre de fois avec un délai d’attente qui croît de manière exponentielle. La figure 6-4 montre une nouvelle tentative en action.

![Modèle de nouvelle tentative en action](./media/retry-pattern.png)

**Figure 6-4**. Modèle de nouvelle tentative en action

Dans la figure précédente, un modèle de nouvelle tentative a été implémenté pour une opération de demande. Elle est configurée pour autoriser jusqu’à quatre tentatives avant d’échouer avec un intervalle d’attente (temps d’attente) à partir de deux secondes, ce qui double de façon exponentielle pour chaque tentative suivante.

- La première invocation échoue et retourne le code d’état HTTP 500. L’application attend deux secondes et réessaie l’appel.
- Le deuxième appel échoue également et retourne le code d’état HTTP 500. L’application double maintenant l’intervalle d’interruption à quatre secondes et réessaie l’appel.
- Enfin, le troisième appel aboutisse.
- Dans ce scénario, l’opération de nouvelle tentative aurait tenté jusqu’à quatre tentatives tout en doublant la durée de l’interruption avant l’échec de l’appel.

Il est important d’augmenter la période d’interruption avant de retenter l’appel pour que le temps de service s’auto-correct. Il est recommandé d’implémenter une interruption exponentiellement plus longue (doublement de la période à chaque nouvelle tentative) pour permettre une correction appropriée.

## <a name="circuit-breaker-pattern"></a>Modèle disjoncteur

Alors que le modèle de nouvelle tentative peut aider à récupérer une requête qui a été intégrée dans une défaillance partielle, il existe des situations où les échecs peuvent être provoqués par des événements imprévus qui nécessitent des périodes plus longues à résoudre. Ces erreurs peuvent aller d’une perte partielle de connectivité à la défaillance complète d’un service. Dans ces situations, il est inutile pour une application de réessayer continuellement une opération qui risque de ne pas aboutir.

Pour compliquer les choses, l’exécution d’opérations de nouvelle tentative continues sur un service non réactif peut vous faire passer dans un scénario de déni de service auto-imposé où vous inondez votre service d’appels continus qui épuisent les ressources telles que la mémoire, les threads et les connexions de base de données.

Dans ces situations, il serait préférable que l’opération échoue immédiatement et tente uniquement d’appeler le service si elle est susceptible de réussir.

Le [modèle disjoncteur](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker) peut empêcher une application de tenter d’exécuter à plusieurs reprises une opération qui risque d’échouer. Il surveille également l’application avec un appel d’essai périodique pour déterminer si l’erreur a été résolue. La figure 6-5 illustre le modèle de disjoncteur en action.

![Modèle disjoncteur en action](./media/circuit-breaker-pattern.png)

**Figure 6-5.** Modèle disjoncteur en action

Dans la figure précédente, un modèle de disjoncteur a été ajouté au modèle de nouvelle tentative d’origine. Notez comment après 10 échecs de requêtes, les disjoncteurs s’ouvrent et n’autorisent plus les appels au service. La valeur CheckCircuit, définie à 30 secondes, spécifie la fréquence à laquelle la bibliothèque autorise une requête à passer au service. Si cet appel s’effectue correctement, le circuit se ferme et le service est à nouveau disponible pour le trafic.

Gardez à l’esprit que l’objectif du modèle de disjoncteur est *différent* de celui du modèle de nouvelle tentative. Le modèle de nouvelle tentative permet à une application de retenter une opération dans l’attente qu’elle aboutisse. Le modèle disjoncteur empêche une application d’effectuer une opération qui risque d’échouer. Souvent, une application *associe* ces deux modèles en utilisant le modèle nouvelle tentative pour appeler une opération par le biais d’un disjoncteur. Toutefois, la logique de nouvelle tentative doit être sensible aux exceptions retournées par le disjoncteur et abandonner les nouvelles tentatives si le disjoncteur indique qu’une erreur n’est pas temporaire.

La résilience des applications est nécessaire pour gérer les opérations demandées. Mais il ne s’agit que de la moitié de l’histoire. Nous aborderons ensuite les fonctionnalités de résilience disponibles dans le Cloud Azure.

>[!div class="step-by-step"]
>[Précédent](resiliency.md)
>[suivant](infrastructure-resiliency-azure.md)
