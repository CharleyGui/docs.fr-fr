---
title: Tester des applications ASP.NET Core MVC
description: Architecturer des applications web modernes avec ASP.NET Core et Azure | Tester des applications ASP.NET Core MVC
author: ardalis
ms.author: wiwagn
ms.date: 12/01/2020
ms.openlocfilehash: b253cfb90487cc462b0f3b8a7564c97ad403aa06
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851397"
---
# <a name="test-aspnet-core-mvc-apps"></a>Tester des applications ASP.NET Core MVC

> *« Si vous n’avez pas envie d’effectuer des tests unitaires sur votre produit, il est fort probable que vos clients n’auront pas non plus envie de l’essayer. »*
 > \_ - Anonyme -

Tous les logiciels, quel que soit leur niveau de complexité, peuvent un jour échouer de façon inattendue en réponse à des modifications. C’est pourquoi vous devez obligatoirement tester toutes vos applications, y compris les plus triviales ou les moins stratégiques, après y avoir apporté des modifications. Tester un logiciel manuellement est la méthode de test la plus lente, la moins fiable et la plus coûteuse. Malheureusement, c’est parfois la seule méthode envisageable pour des applications qui n’ont pas été conçues dans l’optique d’être testées. Les applications écrites pour suivre les principes architecturaux énoncés au [Chapitre 4](architectural-principles.md) doivent être testables unitaires. Les applications ASP.NET Core prennent en charge l’intégration et les tests fonctionnels automatisés.

## <a name="kinds-of-automated-tests"></a>Types de tests automatisés

Il existe de nombreuses sortes de tests automatisés pour les applications logicielles. Le test de base, le plus simple, est le test unitaire. À un niveau légèrement supérieur, il existe des tests d’intégration et des tests fonctionnels. D’autres types de tests, tels que les tests de l’interface utilisateur, les tests de charge, les tests de stress et les tests de fumée, n’entrent pas dans le cadre de ce document.

### <a name="unit-tests"></a>Tests unitaires

Un test unitaire teste une seule partie (unité) de la logique de votre application. Pour mieux le décrire, on peut lister ce qu’il fait et ce qu’il ne fait pas. Un test unitaire ne teste pas la manière dont votre code fonctionne avec les dépendances ou l’infrastructure (cet aspect est vérifié par les tests d’intégration). Un test unitaire ne teste pas le framework sur lequel votre code est écrit. Vous partez du principe qu’il fonctionne correctement. Sinon, entrez un bogue et codez une solution de contournement. Un test unitaire s’exécute entièrement en mémoire et dans le processus. Il ne communique pas avec le système de fichiers, le réseau ou des bases de données. Les tests unitaires doivent uniquement tester votre code.

Les tests unitaires, en raison du fait qu’ils testent une seule unité de votre code, sans dépendances externes, doivent s’exécuter extrêmement rapidement. Vous devez donc pouvoir exécuter des suites de centaines de tests unitaires en quelques secondes. Lancez fréquemment ces tests, idéalement avant chaque envoi de données dans un référentiel de contrôle de code source partagé et bien sûr, avec chaque build automatisée sur votre serveur de builds.

### <a name="integration-tests"></a>Tests d’intégration

Même si vous avez la bonne idée d’encapsuler votre code qui interagit avec une infrastructure comme les bases de données et les systèmes de fichiers, il reste toujours une partie de ce code à tester. En outre, vous devez vérifier que les différentes couches de votre code interagissent comme prévu quand les dépendances de votre application sont entièrement résolues. Cette fonctionnalité est la responsabilité des tests d’intégration. Les tests d’intégration sont généralement plus lents et plus difficiles à configurer que les tests unitaires, car ils dépendent souvent d’une infrastructure et de dépendances externes. Par conséquent, évitez d’utiliser des tests d’intégration pour tester des éléments qui peuvent l’être à l’aide de tests unitaires. Si vous pouvez tester un scénario donné avec un test unitaire, choisissez cette méthode. Si cela n’est pas possible, utilisez un test d’intégration.

Les procédures de configuration et de désactivation (teardown) des tests d’intégration sont souvent plus complexes que pour les tests unitaires. Par exemple, un test d’intégration exécuté sur une base de données réelle doit avoir un moyen de rétablir la base de données à un état connu avant chaque nouveau test. À mesure que de nouveaux tests sont ajoutés et que le schéma de la base de données de production évolue, la taille et la complexité des scripts de test augmentent. Sur la plupart des grands systèmes, il est quasiment impossible d’exécuter des suites entières de tests d’intégration sur les stations de travail de développement avant d’enregistrer les modifications apportées dans le contrôle de code source partagé. Dans ces cas de figure, les tests d’intégration peuvent être exécutés sur un serveur de builds.

### <a name="functional-tests"></a>Tests fonctionnels

Les tests d’intégration sont écrits du point de vue du développeur, pour vérifier que certains composants du système fonctionnent correctement ensemble. Les tests fonctionnels sont écrits du point de vue de l’utilisateur final, pour vérifier que le système répond aux exigences. L’extrait suivant se sert d’une analogie intéressante pour expliquer la différence entre des tests fonctionnels et des tests unitaires :

> « Par de nombreux aspects, le développement d’un système logiciel s’apparente à la construction d’une maison. Cette analogie n’est pas tout à fait exacte, mais nous pouvons l’extrapoler pour mieux comprendre la différence entre les tests unitaires et les tests fonctionnels. Les tests unitaires peuvent être comparés aux visites du maître d’œuvre sur le chantier de construction de la maison. Le maître d’œuvre examine les divers systèmes internes de la maison, les fondations, la charpente, l’installation électrique, la plomberie, etc. Il garantit (et vérifie) que les différentes parties de la maison sont conformes aux exigences fonctionnelles et de sécurité, qui constituent le code de construction. Dans ce scénario, les tests fonctionnels s’apparentent aux visites du propriétaire de la maison sur le même chantier de construction. Le propriétaire part du principe que les systèmes internes fonctionnent de manière appropriée et que le maître d’œuvre fait correctement son travail. Sa préoccupation principale est d’imaginer sa vie dans sa nouvelle maison. Ce qui intéresse le propriétaire est de vérifier l’aspect de sa maison, si les différentes pièces sont suffisamment grandes, si la maison répond aux besoins de sa famille, si les fenêtres sont bien orientées pour profiter du soleil le matin, etc. En quelque sorte, le propriétaire effectue des tests fonctionnels sur la maison. Il se trouve dans la même perspective que l’utilisateur d’un logiciel. Le maître d’œuvre réalise des tests unitaires sur la maison. Il se trouve dans la même perspective que le développeur d’un logiciel. »

Source : [Test unitaires et tests fonctionnels](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)

J’aime bien dire que « nous, les développeurs, nous pouvons échouer de deux manières : en concevant mal quelque chose ou en concevant quelque chose d’inadapté. » Les tests unitaires permettent de vous assurer que vous concevez une chose de manière correcte, alors que les tests fonctionnels garantissent que vous concevez la chose attendue.

Étant donné que les tests fonctionnels s’exécutent au niveau du système, ils peuvent nécessitent un certain degré d’automatisation de l’interface utilisateur. Comme les tests d’intégration, les tests fonctionnels interagissent aussi généralement avec l’infrastructure de test. Cette activité les rend plus lents et plus fragiles que les tests d’unité et d’intégration. Vous ne devez pas prévoir plus de tests fonctionnels que le nombre nécessaire pour garantir que le système se comporte comme les utilisateurs l’attendent.

### <a name="testing-pyramid"></a>Pyramide des tests

La figure 9-1 ci-dessous montre un exemple de la pyramide des tests de Martin Fowler.

![Pyramide des tests](./media/image9-1.png)

**Figure 9-1**. Pyramide des tests

Les différentes couches de la pyramide, et leurs tailles respectives, représentent plusieurs sortes de tests et la part de chaque sorte de tests à prévoir pour votre application. Comme vous pouvez le voir, la recommandation est de prévoir une large couche de base de tests unitaires, puis une couche plus petite de tests d’intégration et enfin, une couche encore plus petite de tests fonctionnels. Dans l’idéal, chaque couche doit contenir uniquement des tests qui ne peuvent pas être effectués correctement dans une couche inférieure. Gardez en tête cette pyramide des tests quand vous essayez de déterminer la sorte de tests dont vous avez besoin pour un scénario particulier.

### <a name="what-to-test"></a>Éléments à tester

Les développeurs novices dans l’écriture de tests automatisés ont souvent des difficultés à déterminer quels éléments tester. Un bon point de départ est de tester la logique conditionnelle. Partout où vous disposez d’une méthode dont le comportement change en fonction d’une instruction conditionnelle (if-else, Switch, etc.), vous devez être en mesure de rencontrer au moins quelques tests qui confirment le comportement correct pour certaines conditions. Si votre code inclut des conditions d’erreur, il est judicieux d’écrire au moins un test pour le « bon chemin » (sans erreur) à travers le code et au moins un test pour le « mauvais chemin » (avec des erreurs ou des résultats atypiques) pour confirmer que votre application se comporte comme prévu en cas d’erreurs. Enfin, mettez davantage l’accent sur le test d’éléments qui peuvent échouer que sur le test de métriques telles que la couverture du code. En général, mieux vaut avoir une plus grande couverture du code que pas assez. Toutefois, l’écriture d’un certain nombre de tests d’une méthode complexe et critique est généralement une meilleure utilisation du temps que l’écriture de tests pour les propriétés automatiques uniquement pour améliorer les mesures de couverture du code de test.

## <a name="organizing-test-projects"></a>Organisation des projets de test

Vous pouvez organiser vos projets de test de la façon qui vous convient le mieux. Il est conseillé de séparer les tests par type (test unitaire, test d’intégration) et par élément testé (projet, espace de noms). Vous pouvez choisir d’implémenter cette séparation en utilisant plusieurs dossiers au sein d’un seul projet de test, ou plusieurs projets de test distincts. L’utilisation d’un projet unique est plus simple, mais si vous avez des projets volumineux avec beaucoup de tests ou si vous voulez exécuter plus facilement différentes séries de tests, il peut être préférable de créer différents projets de test. Les équipes de développement organisent souvent les projets de test en fonction du projet testé. Pour les applications avec de nombreux projets, cette pratique peut entraîner une multiplication des projets de test, en particulier si vous continuez à organiser ces projets selon la sorte de tests qu’ils contiennent. Une solution de compromis consiste à avoir un projet par sorte de tests et par application, avec des dossiers dans chaque projet de test pour indiquer quel projet (et quelle classe) est testé.

Une approche courante consiste à organiser les projets d’application sous un dossier « src », ainsi que les projets de test de l’application dans un dossier « tests » parallèle. Vous pouvez créer des dossiers de solution correspondants dans Visual Studio, si vous trouvez cette organisation utile.

![Organisation de test dans votre solution](./media/image9-2.png)

**Figure 9-2**. Organisation de test dans votre solution

Vous pouvez choisir le framework de test que vous préférez. Le framework xUnit est performant et c’est celui qui est utilisé pour tous les tests ASP.NET Core et EF Core. Vous pouvez ajouter un projet de test xUnit dans Visual Studio à l’aide du modèle illustré à la figure 9-3, ou à partir de l’interface CLI à l’aide de `dotnet new xunit` .

![Ajouter un projet de test xUnit dans Visual Studio](./media/image9-3.png)

**Figure 9-3**. Ajouter un projet de test xUnit dans Visual Studio

### <a name="test-naming"></a>Nommage des tests

Nommez vos tests de manière cohérente, avec des noms qui indiquent ce que fait chaque test. Une approche que j’ai expérimentée et qui a fait ses preuves est de nommer les classes de test en fonction de la classe et de la méthode qu’elles testent. Cette approche se traduit par de nombreuses petites classes de test, mais elle permet de clarifier la responsabilité de chaque test. Une fois le nom de la classe de test configuré, pour identifier la classe et la méthode à tester, le nom de la méthode de test peut être utilisé pour spécifier le comportement testé. Ce nom doit inclure le comportement attendu et toutes les entrées ou hypothèses qui doivent donner ce comportement. Voici quelques exemples de noms de test :

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

Une variante de cette approche termine chaque nom de classe de test par « Should » et modifie légèrement la conjugaison du verbe :

- `CatalogControllerGetImage`**Doit** `.` **Appeler**`ImageServiceWithId`

- `CatalogControllerGetImage`**Doit** `.` **Journal**`WarningGivenImageMissingException`

Certaines équipes de développement trouvent la deuxième approche de nommage plus claire, bien que légèrement plus détaillée. Dans tous les cas, essayez de choisir une convention de nommage suffisamment explicite pour comprendre le comportement de test. Ainsi, si un ou plusieurs tests échouent, vous pourrez facilement déterminer ce qui a échoué d’après les noms des tests. Évitez de nommer vos tests vaguement, par exemple ControllerTests. test1, car ces noms n’offrent aucune valeur quand vous les voyez dans les résultats des tests.

Si vous choisissez une convention de nommage comme celle décrite ci-dessus, qui génère beaucoup de petites classes de test, il est préférable de plutôt organiser vos tests à l’aide de dossiers et d’espaces de noms. La figure 9-4 montre un exemple d’organisation des tests par dossier au sein de plusieurs projets de test.

![Organisation des classes de test par dossier en fonction de la classe en cours de test](./media/image9-4.png)

**Figure 9-4.** Organisation des classes de test par dossier en fonction de la classe testée.

Si de nombreuses méthodes sont testées pour une classe d’application particulière (et donc de nombreuses classes de test), il peut être judicieux de placer ces classes dans un dossier correspondant à la classe d’application. Cette organisation est semblable à la façon dont vous pouvez organiser les fichiers dans des dossiers ailleurs. Quand vous avez plus de trois ou quatre fichiers associés dans un dossier contenant beaucoup d’autres fichiers, il est souvent plus pratique de les déplacer dans leur propre sous-dossier.

## <a name="unit-testing-aspnet-core-apps"></a>Tests unitaires dans les applications ASP.NET Core

Dans une application ASP.NET Core bien conçue, la majeure partie de la complexité et de la logique métier est encapsulée dans les entités métier et divers services. L’application ASP.NET Core MVC elle-même, avec ses contrôleurs, filtres, ViewModels et vues, doit nécessiter quelques tests unitaires. La fonctionnalité d’une action donnée est en grande partie exposée en dehors de la méthode d’action proprement dite. Le fait de tester si le routage ou la gestion des erreurs globales fonctionne correctement ne peut pas être effectué efficacement avec un test unitaire. De même, tous les filtres, y compris la validation de modèle, les filtres d’authentification et d’autorisation, ne peuvent pas être testés par unité avec un test ciblant la méthode d’action d’un contrôleur. En dehors de ces sources de comportement, la plupart des méthodes d’action doivent être très petites, la plus grosse part de leur travail étant déléguée à des services qui peuvent être testés indépendamment du contrôleur qui les utilise.

Vous devrez parfois refactoriser votre code pour pouvoir le tester au moyen de tests unitaires. Cette activité implique souvent l’identification d’abstractions et l’utilisation de l’injection de dépendances pour accéder à l’abstraction dans le code que vous souhaitez tester, plutôt que de coder directement en fonction de l’infrastructure. Par exemple, considérez cette méthode d’action facile pour afficher des images :

```csharp
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    var contentRoot = _env.ContentRootPath + "//Pics";
    var path = Path.Combine(contentRoot, id + ".png");
    Byte[] b = System.IO.File.ReadAllBytes(path);
    return File(b, "image/png");
}
```

Il est difficile d’utiliser des tests unitaires pour tester cette méthode à cause de sa dépendance directe vis-à-vis de `System.IO.File`, qu’elle utilise pour lire les données du système de fichiers. Vous pouvez tester ce comportement pour vous assurer qu’il fonctionne comme prévu, mais vous devez utiliser un test d’intégration sur les fichiers réels. Il est à noter que vous ne pouvez pas effectuer de test unitaire sur l’itinéraire de cette méthode &mdash; . vous verrez comment effectuer ce test avec un test fonctionnel peu de chance.

Si vous ne pouvez pas utiliser de tests unitaires pour tester directement le comportement du système de fichiers, et que vous ne pouvez pas tester l’itinéraire, que reste-t-il à tester ? En fait, après avoir refactorisé le code pour rendre les tests unitaires possibles, vous risquez de découvrir des cas de test et un comportement manquant, comme la gestion des erreurs. Que fait la méthode quand il manque un fichier ? Que doit-elle faire ? Dans cet exemple, la méthode refactorisée ressemble à ceci :

```csharp
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    byte[] imageBytes;
    try
    {
        imageBytes = _imageService.GetImageBytesById(id);
    }
    catch (CatalogImageMissingException ex)
    {
        _logger.LogWarning($"No image found for id: {id}");
        return NotFound();
    }
    return File(imageBytes, "image/png");
}
```

`_logger` et `_imageService` sont tous deux injectés en tant que dépendances. Vous pouvez maintenant tester que le même ID qui est passé à la méthode d’action est passé à `_imageService` , et que les octets obtenus sont retournés dans le cadre du FileResult. Vous pouvez également vérifier que la journalisation des erreurs se produit comme prévu, et qu’un `NotFound` résultat est retourné si l’image est manquante, en supposant que ce comportement est un comportement d’application important (autrement dit, pas simplement du code temporaire que le développeur a ajouté pour diagnostiquer un problème). La logique du fichier réel a été déplacée dans un service d’implémentation distinct et a été augmentée pour retourner une exception d’application liée au fichier manquant. Vous pouvez tester cette implémentation indépendamment, à l’aide d’un test d’intégration.

Dans la plupart des cas, vous souhaiterez utiliser des gestionnaires d’exceptions globaux dans vos contrôleurs, donc la quantité de logique qu’ils contiennent doit être minime et sans doute pas la peine de tester les unités. Effectuez la plupart de vos tests d’actions de contrôleur à l’aide de tests fonctionnels et de la `TestServer` classe décrite ci-dessous.

## <a name="integration-testing-aspnet-core-apps"></a>Tests d’intégration dans les applications ASP.NET Core

La plupart des tests d’intégration figurant dans vos applications ASP.NET Core doivent tester les services et les autres types d’implémentation définis dans votre projet Infrastructure. Par exemple, vous pouvez [tester qu’EF Core a été correctement mis à jour et a récupéré les données que vous attendez](/ef/core/miscellaneous/testing/) à partir de vos classes d’accès aux données résidant dans le projet Infrastructure. La meilleure façon de vérifier le bon comportement de votre projet ASP.NET Core MVC consiste à utiliser les tests fonctionnels qui s’exécutent par rapport à votre application en cours d’exécution dans un hôte de test.

## <a name="functional-testing-aspnet-core-apps"></a>Tests fonctionnels dans les applications ASP.NET Core

Pour les applications ASP.NET Core, la classe `TestServer` facilite grandement l’écriture de tests fonctionnels. Vous configurez un `TestServer` à l’aide d’un `WebHostBuilder` (ou `HostBuilder` ) directement (comme vous le feriez normalement pour votre application) ou avec le `WebApplicationFactory` type (disponible depuis la version 2,1). Essayez de faire correspondre votre hôte de test à votre hôte de production aussi fidèlement que possible, afin que vos tests exercent un comportement similaire à ce que l’application fera en production. La classe `WebApplicationFactory` s’avère utile pour configurer la clé ContentRoot de TestServer, dont se sert ASP.NET Core pour localiser les ressources statiques telles que les vues.

Vous pouvez créer des tests fonctionnels simples en créant une classe de test qui implémente `IClassFixture\<WebApplicationFactory\<TEntry>>` , où `TEntry` est la classe de votre application Web `Startup` . Une fois cette interface en place, votre contexte de test peut créer un client à l’aide de la méthode de la fabrique `CreateClient` :

```csharp
public class BasicWebTests : IClassFixture<WebApplicationFactory<Startup>>
{
    protected readonly HttpClient _client;

    public BasicWebTests(WebApplicationFactory<Startup> factory)
    {
        _client = factory.CreateClient();
    }

    // write tests that use _client
}
```

Souvent, vous devez effectuer une configuration supplémentaire de votre site avant chaque exécution de test, comme la configuration de l’application pour utiliser une banque de données en mémoire, puis l’amorçage de l’application avec des données de test. Pour obtenir cette fonctionnalité, créez votre propre sous-classe de `WebApplicationFactory\<TEntry>` et substituez sa `ConfigureWebHost` méthode. L’exemple ci-dessous est tiré du projet eShopOnWeb FunctionalTests et est utilisé dans le cadre des tests effectués sur l’application web principale.

```csharp
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Identity;
using Microsoft.AspNetCore.Mvc.Testing;
using Microsoft.EntityFrameworkCore;
using Microsoft.eShopWeb.Infrastructure.Data;
using Microsoft.eShopWeb.Infrastructure.Identity;
using Microsoft.eShopWeb.Web;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Logging;
using System;

namespace Microsoft.eShopWeb.FunctionalTests.Web
{
    public class WebTestFixture : WebApplicationFactory<Startup>
    {
        protected override void ConfigureWebHost(IWebHostBuilder builder)
        {
            builder.UseEnvironment("Testing");

            builder.ConfigureServices(services =>
            {
                 services.AddEntityFrameworkInMemoryDatabase();

                // Create a new service provider.
                var provider = services
                    .AddEntityFrameworkInMemoryDatabase()
                    .BuildServiceProvider();

                // Add a database context (ApplicationDbContext) using an in-memory
                // database for testing.
                services.AddDbContext<CatalogContext>(options =>
                {
                    options.UseInMemoryDatabase("InMemoryDbForTesting");
                    options.UseInternalServiceProvider(provider);
                });

                services.AddDbContext<AppIdentityDbContext>(options =>
                {
                    options.UseInMemoryDatabase("Identity");
                    options.UseInternalServiceProvider(provider);
                });

                // Build the service provider.
                var sp = services.BuildServiceProvider();

                // Create a scope to obtain a reference to the database
                // context (ApplicationDbContext).
                using (var scope = sp.CreateScope())
                {
                    var scopedServices = scope.ServiceProvider;
                    var db = scopedServices.GetRequiredService<CatalogContext>();
                    var loggerFactory = scopedServices.GetRequiredService<ILoggerFactory>();

                    var logger = scopedServices
                        .GetRequiredService<ILogger<WebTestFixture>>();

                    // Ensure the database is created.
                    db.Database.EnsureCreated();

                    try
                    {
                        // Seed the database with test data.
                        CatalogContextSeed.SeedAsync(db, loggerFactory).Wait();

                        // seed sample user data
                        var userManager = scopedServices.GetRequiredService<UserManager<ApplicationUser>>();
                        var roleManager = scopedServices.GetRequiredService<RoleManager<IdentityRole>>();
                        AppIdentityDbContextSeed.SeedAsync(userManager, roleManager).Wait();
                    }
                    catch (Exception ex)
                    {
                        logger.LogError(ex, $"An error occurred seeding the " +
                            "database with test messages. Error: {ex.Message}");
                    }
                }
            });
        }
    }
}
```

Les tests peuvent exploiter cette classe WebApplicationFactory personnalisée pour créer un client et adresser des requêtes à l’application en utilisant cette instance de client. Les données sont alors amorcées par l’application et peuvent être utilisées dans les assertions du test. Le test suivant vérifie que la page d’accueil de l’application eShopOnWeb se charge correctement et qu’elle présente une liste de produits qui a été ajoutée à l’application avec les données initiales.

```csharp
using Microsoft.eShopWeb.FunctionalTests.Web;
using System.Net.Http;
using System.Threading.Tasks;
using Xunit;

namespace Microsoft.eShopWeb.FunctionalTests.WebRazorPages
{
    [Collection("Sequential")]
    public class HomePageOnGet : IClassFixture<WebTestFixture>
    {
        public HomePageOnGet(WebTestFixture factory)
        {
            Client = factory.CreateClient();
        }

        public HttpClient Client { get; }

        [Fact]
        public async Task ReturnsHomePageWithProductListing()
        {
            // Arrange & Act
            var response = await Client.GetAsync("/");
            response.EnsureSuccessStatusCode();
            var stringResponse = await response.Content.ReadAsStringAsync();

            // Assert
            Assert.Contains(".NET Bot Black Sweatshirt", stringResponse);
        }
    }
}
```

Ce test fonctionnel exerce la pile d’applications ASP.NET Core MVC/Razor Pages complète, y compris tous les intergiciels (middleware), les filtres et les classeurs qui peuvent être en place. Il vérifie qu’un itinéraire donné (« / ») retourne le code d’état de réussite attendu et la sortie HTML. Il le fait sans configurer de serveur Web réel et évite une grande partie de la fragilité qui consiste à utiliser un serveur Web réel à des fins de test (par exemple, des problèmes avec les paramètres du pare-feu). Les tests fonctionnels exécutés sur le TestServer sont généralement plus lents que les tests d’intégration et les tests unitaires, mais ils sont beaucoup plus rapides que les tests exécutés sur un serveur web de test via le réseau. Utilisez les tests fonctionnels pour vous assurer que la pile frontale de votre application fonctionne comme prévu. Ces tests sont particulièrement utiles quand vous trouvez un doublon dans vos contrôleurs ou pages et que vous corrigez ce problème en ajoutant des filtres. Dans l’idéal, cette refactorisation ne modifie pas le comportement de l’application, et une suite de tests fonctionnels vérifie que c’est bien le cas.

> ### <a name="references--test-aspnet-core-mvc-apps"></a>Références – Tester des applications ASP.NET Core MVC
>
> - **Test dans ASP.NET Core** \
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - **Convention d’affectation de noms de tests unitaires** \
>   <https://ardalis.com/unit-test-naming-convention>
> - **Test EF Core** \
>   <https://docs.microsoft.com/ef/core/miscellaneous/testing/>
> - **Tests d’intégration dans ASP.NET Core** \
>   <https://docs.microsoft.com/aspnet/core/test/integration-tests>

>[!div class="step-by-step"]
>[Précédent](work-with-data-in-asp-net-core-apps.md) 
> [Suivant](development-process-for-azure.md)
