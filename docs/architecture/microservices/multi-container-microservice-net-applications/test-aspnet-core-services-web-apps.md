---
title: Test d’applications web et de services ASP.NET Core
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Explorer une architecture pour le test d’applications web et de services ASP.NET Core dans des conteneurs.
ms.date: 01/30/2020
ms.openlocfilehash: f66d6184d913405c9372904f8072dda1dbfbe6ac
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988230"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a>Test d’applications web et de services ASP.NET Core

Les contrôleurs constituent l’élément central des services d’API ASP.NET Core et des applications web ASP.NET MVC. Par conséquent, vous devez être sûr qu’ils vont se comporter comme prévu avec votre application. Les tests automatisés peuvent vous donner cette confiance et détecter des erreurs avant la mise en production.

Vous devez tester le comportement du contrôleur avec les entrées valides et non valides, ainsi que les réponses du contrôleur en fonction du résultat de l’opération qu’il effectue. Toutefois, vous devez avoir ces types de test pour vos microservices :

- Tests unitaires. Ces tests permettent de vérifier que les composants de l’application fonctionnent comme prévu. Les assertions testent l’API des composants.

- Tests d’intégration. Ces tests permettent de vérifier que les interactions entre composants fonctionnent comme prévu, en se basant sur des artefacts externes comme les bases de données. Les assertions peuvent tester l’API des composants, l’interface utilisateur ou les effets secondaires des actions telles que les E/S de base de données, la journalisation, etc.

- Tests fonctionnels pour chaque microservice. Ceux-ci garantissent que l’application fonctionne comme prévu du point de vue de l’utilisateur.

- Tests de service. Ces tests permettent de garantir que les cas d’usage de service de bout en bout (y compris l’exécution simultanée de plusieurs services) sont testés. Pour ce type de test, vous devez d’abord préparer l’environnement. Dans ce cas, cela signifie démarrer les services (à l’aide de docker-compose up, par exemple).

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a>Implémentation des tests unitaires pour les API web ASP.NET Core

Les tests unitaires impliquent le test d’une partie d’une application de façon isolée, par rapport à son infrastructure et à ses dépendances. Lors du test de la logique d’un contrôleur, seul le contenu d’une action ou d’une méthode est testé, et non pas le comportement de ses dépendances ou du framework lui-même. Les tests unitaires ne détectent pas les problèmes d’interaction entre les composants, qui sont l’objet des tests d’intégration.

Quand vous procédez à des tests unitaires pour les actions de votre contrôleur, concentrez-vous uniquement sur leur comportement. Les tests unitaires d’un contrôleur évitent les éléments tels que les filtres, le routage ou la liaison de données (le mappage de données de requête à un ViewModel ou à un objet DTO). Comme ils ne s’occupent que d’un seul objet à la fois, les tests unitaires sont généralement simples à écrire et rapides à exécuter. Un ensemble de tests unitaires bien écrits peut être exécuté fréquemment sans engendrer une surcharge importante.

Les tests unitaires sont implémentés selon les frameworks de tests comme xUnit.net, MSTest, Moq ou NUnit. Pour l’exemple d’application eShopOnContainers, nous utilisons xUnit.

Lorsque vous écrivez un test unitaire pour un contrôleur d’API web, vous instanciez la classe de contrôleur directement à l’aide du mot clé new dans du code C\#, pour que le test s’exécute aussi rapidement que possible. L’exemple suivant montre comment effectuer cette opération en utilisant [xUnit](https://xunit.github.io/) comme framework de tests.

```csharp
[Fact]
public async Task Get_order_detail_success()
{
    //Arrange
    var fakeOrderId = "12";
    var fakeOrder = GetFakeOrder();

    //...

    //Act
    var orderController = new OrderController(
        _orderServiceMock.Object,
        _basketServiceMock.Object,
        _identityParserMock.Object);

    orderController.ControllerContext.HttpContext = _contextMock.Object;
    var actionResult = await orderController.Detail(fakeOrderId);

    //Assert
    var viewResult = Assert.IsType<ViewResult>(actionResult);
    Assert.IsAssignableFrom<Order>(viewResult.ViewData.Model);
}
```

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a>Implémentation de tests d’intégration et de tests fonctionnels pour chaque microservice

Comme mentionné précédemment, les tests d’intégration et les tests fonctionnels ont des objectifs différents. Toutefois, leur implémentation est similaire lorsque vous testez les contrôleurs ASP.NET Core. Cette section se concentre donc sur les tests d’intégration.

Les tests d’intégration permettent de vérifier que les composants d’une application fonctionnent correctement une fois assemblés. ASP.NET Core prend en charge les tests d’intégration à l’aide des frameworks de tests unitaires et d’un hôte web de test intégré qui peut être utilisé pour gérer les requêtes, sans surcharger le réseau.

Contrairement aux tests unitaires, les tests d’intégration rencontrent souvent des problèmes d’infrastructure d’application, liés par exemple, aux bases de données, aux systèmes de fichiers, aux ressources réseau ou aux requêtes et réponses web. Les tests unitaires utilisent des fakes ou objets fictifs pour éviter de tels problèmes. Toutefois, l’objectif des tests d’intégration est de vérifier que le système fonctionne comme prévu avec ces systèmes. Par conséquent, pour les tests d’intégration, vous ne devez pas utiliser de fakes ou d’objets fictifs. Vous devez inclure l’infrastructure, comme l’accès de base de données ou l’appel de service, des autres services.

Étant donné que les tests d’intégration utilisent de plus grands segments de code que les tests unitaires, et comme les tests d’intégration reposent sur des éléments d’infrastructure, ils ont tendance à être beaucoup plus lents que les tests unitaires. Par conséquent, il est conseillé de limiter le nombre de tests d’intégration que vous écrivez et exécutez.

ASP.NET Core comprend un hébergeur de test intégré qui peut être utilisé pour traiter les demandes HTTP sans frais généraux réseau, ce qui signifie que vous pouvez exécuter ces tests plus rapidement que lors de l’utilisation d’un véritable hébergeur. L’hôte web de test (TestServer) est disponible dans un composant NuGet, sous le nom de Microsoft.AspNetCore.TestHost. Il peut être ajouté aux projets de test d’intégration et utilisé pour héberger les applications ASP.NET Core.

Comme vous pouvez le voir dans le code suivant, lorsque vous créez des tests d’intégration pour des contrôleurs ASP.NET Core, vous instanciez les contrôleurs via l’hôte de test. Ceci est comparable à une requête HTTP, avec toutefois, une exécution plus rapide.

```csharp
public class PrimeWebDefaultRequestShould
{
    private readonly TestServer _server;
    private readonly HttpClient _client;

    public PrimeWebDefaultRequestShould()
    {
        // Arrange
        _server = new TestServer(new WebHostBuilder()
           .UseStartup<Startup>());
           _client = _server.CreateClient();
    }

    [Fact]
    public async Task ReturnHelloWorld()
    {
        // Act
        var response = await _client.GetAsync("/");
        response.EnsureSuccessStatusCode();
        var responseString = await response.Content.ReadAsStringAsync();
        // Assert
        Assert.Equal("Hello World!", responseString);
    }
}
```

#### <a name="additional-resources"></a>Ressources supplémentaires

- **Steve Smith. Contrôleurs d’essai** (ASP.NET Core)
    [https://docs.microsoft.com/aspnet/core/mvc/controllers/testing](/aspnet/core/mvc/controllers/testing)

- **Steve Smith. Tests d’intégration** (ASP.NET Core)
    [https://docs.microsoft.com/aspnet/core/test/integration-tests](/aspnet/core/test/integration-tests)

- **Test unitaire dans .NET Core à l’aide du test dotnet** \
    [https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test](../../../core/testing/unit-testing-with-dotnet-test.md)

- **xUnit.net**. Site officiel. \
    <https://xunit.github.io/>

- **Bases de test unitaire.** \
    [https://docs.microsoft.com/visualstudio/test/unit-test-basics](/visualstudio/test/unit-test-basics)

- **Moq**. Dépôt GitHub. \
    <https://github.com/moq/moq>

- **NUnit**. Site officiel. \
    <https://www.nunit.org/>

### <a name="implementing-service-tests-on-a-multi-container-application"></a>Implémentation de tests de service dans une application à plusieurs conteneurs

Comme mentionné précédemment, lorsque vous testez des applications à plusieurs conteneurs, tous les microservices doivent être exécutés au sein de l’hôte Docker ou du cluster de conteneurs. Les tests de service de bout en bout qui incluent plusieurs opérations impliquant plusieurs microservices nécessitent le déploiement et le démarrage de l’application entière dans l’hôte Docker en exécutant docker-compose up (ou d’un mécanisme comparable si vous utilisez un orchestrateur). Une fois que l’application entière et tous ses services sont exécutés, vous pouvez exécuter des tests d’intégration et des tests fonctionnels de bout en bout.

Il existe pour cela plusieurs méthodes. Dans le fichier docker-compose.yml que vous utilisez pour déployer l’application au niveau de la solution, vous pouvez développer le point d’entrée pour utiliser la commande [dotnet test](../../../core/tools/dotnet-test.md). Vous pouvez également utiliser un autre fichier Compose pour exécuter vos tests dans l’image que vous ciblez. En utilisant un autre fichier Compose pour les tests d’intégration comprenant vos microservices et vos bases de données dans des conteneurs, vous pouvez être sûr que les données associées sont toujours réinitialisées à leur état d’origine avant d’exécuter les tests.

Une fois que l’application Compose est fonctionnelle, vous pouvez tirer parti des points d’arrêt et des exceptions si vous exécutez Visual Studio. Vous pouvez également exécuter les tests d’intégration automatiquement dans votre pipeline d’intégration continue dans Azure DevOps Services, ou dans un autre système d’intégration ou de livraison continue prenant en charge les conteneurs Docker.

## <a name="testing-in-eshoponcontainers"></a>Test dans eShopOnContainers

Les tests de l’application de référence (eShopOnContainers) ont été récemment restructurés et il existe maintenant quatre catégories :

1. **Tests unitaires** : simplement des anciens tests unitaires normaux, contenus dans les projets **{MicroserviceName}.UnitTests**

2. **Tests fonctionnels/d’intégration de microservices** : avec les cas de test impliquant l’infrastructure de chaque microservice, mais pris isolément des autres et contenus dans les projets **{NomMicroservice}.FunctionalTests**.

3. **Tests fonctionnels/d’intégration d’application,** qui mettent l’accent sur l’intégration des microservices, avec des cas de test qui exercent plusieurs microservices. Ces tests se trouvent dans le projet **Application.FunctionalTests**.

Les tests unitaires et les tests d’intégration par microservice se trouvent dans le dossier de test de chaque microservice, et les tests d’application et de charge sont contenus sous le dossier de test du dossier de solution, comme l’illustre la figure 6-25.

![Capture d’écran de VS soulignant certains des projets de test dans la solution.](./media/test-aspnet-core-services-web-apps/eshoponcontainers-test-folder-structure.png)

**Figure 6-25.** Tester la structure des dossiers dans eShopOnContainers

Les tests fonctionnels/d’intégration de microservices et d’applications sont exécutés à partir de Visual Studio, à l’aide de l’exécuteur de tests standard, mais vous devez d’abord démarrer les services d’infrastructure nécessaires au moyen d’un ensemble de fichiers docker-compose contenus dans le dossier de test de la solution :

**docker-compose-test.yml**

```yml
version: '3.4'

services:
  redis.data:
    image: redis:alpine
  rabbitmq:
    image: rabbitmq:3-management-alpine
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
  nosqldata:
    image: mongo
```

**docker-compose-test.override.yml**

```yml
version: '3.4'

services:
  redis.data:
    ports:
      - "6379:6379"
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"
  sqldata:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosqldata:
    ports:
      - "27017:27017"
```

Par conséquent, pour exécuter les tests fonctionnels/d’intégration, vous devez tout d’abord exécuter la commande suivante à partir du dossier de test de la solution :

```console
docker-compose -f docker-compose-test.yml -f docker-compose-test.override.yml up
```

Comme on peut le constater, ces fichiers Docker Compose lancent seulement les microservices Redis, RabbitMQ, SQL Server et MongoDB.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Fichier Lisez-moi relatif aux tests** dans le dépôt eShopOnContainers sur GitHub \
    <https://github.com/dotnet-architecture/eShopOnContainers/tree/dev/test>

- **Fichier Lisez-moi relatif aux tests de charge** dans le dépôt eShopOnContainers sur GitHub \
    <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/test/ServicesTests/LoadTest/>

> [!div class="step-by-step"]
> [Suivant précédent](subscribe-events.md)
> [Next](background-tasks-with-ihostedservice.md)
