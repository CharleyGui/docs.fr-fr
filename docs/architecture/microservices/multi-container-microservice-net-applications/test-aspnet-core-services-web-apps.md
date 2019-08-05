---
title: Test d’applications web et de services ASP.NET Core
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Explorer une architecture pour le test d’applications web et de services ASP.NET Core dans des conteneurs.
ms.date: 10/02/2018
ms.openlocfilehash: 0a741fca84f456d635e1790d6be1c72e70345a24
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68675836"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a><span data-ttu-id="1c2a5-103">Test d’applications web et de services ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1c2a5-103">Testing ASP.NET Core services and web apps</span></span>

<span data-ttu-id="1c2a5-104">Les contrôleurs constituent l’élément central des services d’API ASP.NET Core et des applications web ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-104">Controllers are a central part of any ASP.NET Core API service and ASP.NET MVC Web application.</span></span> <span data-ttu-id="1c2a5-105">Par conséquent, vous devez être sûr qu’ils vont se comporter comme prévu avec votre application.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-105">As such, you should have confidence they behave as intended for your application.</span></span> <span data-ttu-id="1c2a5-106">Les tests automatisés peuvent vous donner cette confiance et détecter des erreurs avant la mise en production.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-106">Automated tests can provide you with this confidence and can detect errors before they reach production.</span></span>

<span data-ttu-id="1c2a5-107">Vous devez tester le comportement du contrôleur avec les entrées valides et non valides, ainsi que les réponses du contrôleur en fonction du résultat de l’opération qu’il effectue.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-107">You need to test how the controller behaves based on valid or invalid inputs, and test controller responses based on the result of the business operation it performs.</span></span> <span data-ttu-id="1c2a5-108">Toutefois, vous devez avoir ces types de test pour vos microservices :</span><span class="sxs-lookup"><span data-stu-id="1c2a5-108">However, you should have these types of tests for your microservices:</span></span>

- <span data-ttu-id="1c2a5-109">Tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-109">Unit tests.</span></span> <span data-ttu-id="1c2a5-110">Ces tests permettent de vérifier que les composants de l’application fonctionnent comme prévu.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-110">These ensure that individual components of the application work as expected.</span></span> <span data-ttu-id="1c2a5-111">Les assertions testent l’API des composants.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-111">Assertions test the component API.</span></span>

- <span data-ttu-id="1c2a5-112">Tests d’intégration.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-112">Integration tests.</span></span> <span data-ttu-id="1c2a5-113">Ces tests permettent de vérifier que les interactions entre composants fonctionnent comme prévu, en se basant sur des artefacts externes comme les bases de données.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-113">These ensure that component interactions work as expected against external artifacts like databases.</span></span> <span data-ttu-id="1c2a5-114">Les assertions peuvent tester l’API des composants, l’interface utilisateur ou les effets secondaires des actions telles que les E/S de base de données, la journalisation, etc.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-114">Assertions can test component API, UI, or the side effects of actions like database I/O, logging, etc.</span></span>

- <span data-ttu-id="1c2a5-115">Tests fonctionnels pour chaque microservice.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-115">Functional tests for each microservice.</span></span> <span data-ttu-id="1c2a5-116">Ces tests permettent de vérifier que l’application fonctionne comme prévu du point de vue de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-116">These ensure that the application works as expected from the user’s perspective.</span></span>

- <span data-ttu-id="1c2a5-117">Tests de service.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-117">Service tests.</span></span> <span data-ttu-id="1c2a5-118">Ces tests permettent de garantir que les cas d’usage de service de bout en bout (y compris l’exécution simultanée de plusieurs services) sont testés.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-118">These ensure that end-to-end service use cases, including testing multiple services at the same time, are tested.</span></span> <span data-ttu-id="1c2a5-119">Pour ce type de test, vous devez d’abord préparer l’environnement.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-119">For this type of testing, you need to prepare the environment first.</span></span> <span data-ttu-id="1c2a5-120">Dans ce cas, cela signifie démarrer les services (à l’aide de docker-compose up, par exemple).</span><span class="sxs-lookup"><span data-stu-id="1c2a5-120">In this case, it means starting the services (for example, by using docker-compose up).</span></span>

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a><span data-ttu-id="1c2a5-121">Implémentation des tests unitaires pour les API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1c2a5-121">Implementing unit tests for ASP.NET Core Web APIs</span></span>

<span data-ttu-id="1c2a5-122">Les tests unitaires impliquent le test d’une partie d’une application de façon isolée, par rapport à son infrastructure et à ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-122">Unit testing involves testing a part of an application in isolation from its infrastructure and dependencies.</span></span> <span data-ttu-id="1c2a5-123">Lors du test de la logique d’un contrôleur, seul le contenu d’une action ou d’une méthode est testé, et non pas le comportement de ses dépendances ou du framework lui-même.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-123">When you unit test controller logic, only the content of a single action or method is tested, not the behavior of its dependencies or of the framework itself.</span></span> <span data-ttu-id="1c2a5-124">Les tests unitaires ne détectent pas les problèmes d’interaction entre les composants, qui sont l’objet des tests d’intégration.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-124">Unit tests do not detect issues in the interaction between components—that is the purpose of integration testing.</span></span>

<span data-ttu-id="1c2a5-125">Quand vous procédez à des tests unitaires pour les actions de votre contrôleur, concentrez-vous uniquement sur leur comportement.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-125">As you unit test your controller actions, make sure you focus only on their behavior.</span></span> <span data-ttu-id="1c2a5-126">Les tests unitaires d’un contrôleur évitent les éléments tels que les filtres, le routage ou la liaison de données (le mappage de données de requête à un ViewModel ou à un objet DTO).</span><span class="sxs-lookup"><span data-stu-id="1c2a5-126">A controller unit test avoids things like filters, routing, or model binding (the mapping of request data to a ViewModel or DTO).</span></span> <span data-ttu-id="1c2a5-127">Comme ils ne s’occupent que d’un seul objet à la fois, les tests unitaires sont généralement simples à écrire et rapides à exécuter.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-127">Because they focus on testing just one thing, unit tests are generally simple to write and quick to run.</span></span> <span data-ttu-id="1c2a5-128">Un ensemble de tests unitaires bien écrits peut être exécuté fréquemment sans engendrer une surcharge importante.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-128">A well-written set of unit tests can be run frequently without much overhead.</span></span>

<span data-ttu-id="1c2a5-129">Les tests unitaires sont implémentés selon les frameworks de tests comme xUnit.net, MSTest, Moq ou NUnit.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-129">Unit tests are implemented based on test frameworks like xUnit.net, MSTest, Moq, or NUnit.</span></span> <span data-ttu-id="1c2a5-130">Pour l’exemple d’application eShopOnContainers, nous utilisons xUnit.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-130">For the eShopOnContainers sample application, we are using xUnit.</span></span>

<span data-ttu-id="1c2a5-131">Lorsque vous écrivez un test unitaire pour un contrôleur d’API web, vous instanciez la classe de contrôleur directement à l’aide du mot clé new dans du code C\#, pour que le test s’exécute aussi rapidement que possible.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-131">When you write a unit test for a Web API controller, you instantiate the controller class directly using the new keyword in C\#, so that the test will run as fast as possible.</span></span> <span data-ttu-id="1c2a5-132">L’exemple suivant montre comment effectuer cette opération en utilisant [xUnit](https://xunit.github.io/) comme framework de tests.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-132">The following example shows how to do this when using [xUnit](https://xunit.github.io/) as the Test framework.</span></span>

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a><span data-ttu-id="1c2a5-133">Implémentation de tests d’intégration et de tests fonctionnels pour chaque microservice</span><span class="sxs-lookup"><span data-stu-id="1c2a5-133">Implementing integration and functional tests for each microservice</span></span>

<span data-ttu-id="1c2a5-134">Comme mentionné précédemment, les tests d’intégration et les tests fonctionnels ont des objectifs différents.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-134">As noted, integration tests and functional tests have different purposes and goals.</span></span> <span data-ttu-id="1c2a5-135">Toutefois, leur implémentation est similaire lorsque vous testez les contrôleurs ASP.NET Core. Cette section se concentre donc sur les tests d’intégration.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-135">However, the way you implement both when testing ASP.NET Core controllers is similar, so in this section we concentrate on integration tests.</span></span>

<span data-ttu-id="1c2a5-136">Les tests d’intégration permettent de vérifier que les composants d’une application fonctionnent correctement une fois assemblés.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-136">Integration testing ensures that an application's components function correctly when assembled.</span></span> <span data-ttu-id="1c2a5-137">ASP.NET Core prend en charge les tests d’intégration à l’aide des frameworks de tests unitaires et d’un hôte web de test intégré qui peut être utilisé pour gérer les requêtes, sans surcharger le réseau.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-137">ASP.NET Core supports integration testing using unit test frameworks and a built-in test web host that can be used to handle requests without network overhead.</span></span>

<span data-ttu-id="1c2a5-138">Contrairement aux tests unitaires, les tests d’intégration rencontrent souvent des problèmes d’infrastructure d’application, liés par exemple, aux bases de données, aux systèmes de fichiers, aux ressources réseau ou aux requêtes et réponses web.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-138">Unlike unit testing, integration tests frequently involve application infrastructure concerns, such as a database, file system, network resources, or web requests and responses.</span></span> <span data-ttu-id="1c2a5-139">Les tests unitaires utilisent des fakes ou objets fictifs pour éviter de tels problèmes.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-139">Unit tests use fakes or mock objects in place of these concerns.</span></span> <span data-ttu-id="1c2a5-140">Toutefois, l’objectif des tests d’intégration est de vérifier que le système fonctionne comme prévu avec ces systèmes. Par conséquent, pour les tests d’intégration, vous ne devez pas utiliser de fakes ou d’objets fictifs.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-140">But the purpose of integration tests is to confirm that the system works as expected with these systems, so for integration testing you do not use fakes or mock objects.</span></span> <span data-ttu-id="1c2a5-141">Vous devez inclure l’infrastructure, comme l’accès de base de données ou l’appel de service, des autres services.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-141">Instead, you include the infrastructure, like database access or service invocation from other services.</span></span>

<span data-ttu-id="1c2a5-142">Étant donné que les tests d’intégration utilisent de plus grands segments de code que les tests unitaires, et comme les tests d’intégration reposent sur des éléments d’infrastructure, ils ont tendance à être beaucoup plus lents que les tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-142">Because integration tests exercise larger segments of code than unit tests, and because integration tests rely on infrastructure elements, they tend to be orders of magnitude slower than unit tests.</span></span> <span data-ttu-id="1c2a5-143">Par conséquent, il est conseillé de limiter le nombre de tests d’intégration que vous écrivez et exécutez.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-143">Thus, it is a good idea to limit how many integration tests you write and run.</span></span>

<span data-ttu-id="1c2a5-144">ASP.NET Core inclut un web hôte de test intégré qui peut être utilisé pour gérer les requêtes HTTP sans surcharger le réseau. Vous pouvez donc exécuter ces tests plus rapidement lorsque vous utilisez un hôte web réel.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-144">ASP.NET Core includes a built-in test web host that can be used to handle HTTP requests without network overhead, meaning that you can run those tests faster when using a real web host.</span></span> <span data-ttu-id="1c2a5-145">L’hôte web de test (TestServer) est disponible dans un composant NuGet, sous le nom de Microsoft.AspNetCore.TestHost.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-145">The test web host (TestServer) is available in a NuGet component as Microsoft.AspNetCore.TestHost.</span></span> <span data-ttu-id="1c2a5-146">Il peut être ajouté aux projets de test d’intégration et utilisé pour héberger les applications ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-146">It can be added to integration test projects and used to host ASP.NET Core applications.</span></span>

<span data-ttu-id="1c2a5-147">Comme vous pouvez le voir dans le code suivant, lorsque vous créez des tests d’intégration pour des contrôleurs ASP.NET Core, vous instanciez les contrôleurs via l’hôte de test.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-147">As you can see in the following code, when you create integration tests for ASP.NET Core controllers, you instantiate the controllers through the test host.</span></span> <span data-ttu-id="1c2a5-148">Ceci est comparable à une requête HTTP, avec toutefois, une exécution plus rapide.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-148">This is comparable to an HTTP request, but it runs faster.</span></span>

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

#### <a name="additional-resources"></a><span data-ttu-id="1c2a5-149">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="1c2a5-149">Additional resources</span></span>

- <span data-ttu-id="1c2a5-150">**Steve Smith. Test des contrôleurs** (ASP.NET Core) </span><span class="sxs-lookup"><span data-stu-id="1c2a5-150">**Steve Smith. Testing controllers** (ASP.NET Core) </span></span>\
    [https://docs.microsoft.com/aspnet/core/mvc/controllers/testing](/aspnet/core/mvc/controllers/testing)

- <span data-ttu-id="1c2a5-151">**Steve Smith. Tests d’intégration**  (ASP.NET Core) </span><span class="sxs-lookup"><span data-stu-id="1c2a5-151">**Steve Smith. Integration testing** (ASP.NET Core) </span></span>\
    [https://docs.microsoft.com/aspnet/core/test/integration-tests](/aspnet/core/test/integration-tests)

- <span data-ttu-id="1c2a5-152">**Effectuer des tests unitaires dans .NET Core à l’aide de dotnet test** </span><span class="sxs-lookup"><span data-stu-id="1c2a5-152">**Unit testing in .NET Core using dotnet test** </span></span>\
    [https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test](../../../core/testing/unit-testing-with-dotnet-test.md)

- <span data-ttu-id="1c2a5-153">**xUnit.net**.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-153">**xUnit.net**.</span></span> <span data-ttu-id="1c2a5-154">Site officiel.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-154">Official site.</span></span> \
    <https://xunit.github.io/>

- <span data-ttu-id="1c2a5-155">**Concepts de base des tests unitaires.**</span><span class="sxs-lookup"><span data-stu-id="1c2a5-155">**Unit Test Basics.**</span></span> \
    [https://docs.microsoft.com/visualstudio/test/unit-test-basics](/visualstudio/test/unit-test-basics)

- <span data-ttu-id="1c2a5-156">**Moq**.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-156">**Moq**.</span></span> <span data-ttu-id="1c2a5-157">Dépôt GitHub.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-157">GitHub repo.</span></span> \
    <https://github.com/moq/moq>

- <span data-ttu-id="1c2a5-158">**NUnit**.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-158">**NUnit**.</span></span> <span data-ttu-id="1c2a5-159">Site officiel.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-159">Official site.</span></span> \
    <https://www.nunit.org/>

### <a name="implementing-service-tests-on-a-multi-container-application"></a><span data-ttu-id="1c2a5-160">Implémentation de tests de service dans une application à plusieurs conteneurs</span><span class="sxs-lookup"><span data-stu-id="1c2a5-160">Implementing service tests on a multi-container application</span></span>

<span data-ttu-id="1c2a5-161">Comme mentionné précédemment, lorsque vous testez des applications à plusieurs conteneurs, tous les microservices doivent être exécutés au sein de l’hôte Docker ou du cluster de conteneurs.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-161">As noted earlier, when you test multi-container applications, all the microservices need to be running within the Docker host or container cluster.</span></span> <span data-ttu-id="1c2a5-162">Les tests de service de bout en bout qui incluent plusieurs opérations impliquant plusieurs microservices nécessitent le déploiement et le démarrage de l’application entière dans l’hôte Docker en exécutant docker-compose up (ou d’un mécanisme comparable si vous utilisez un orchestrateur).</span><span class="sxs-lookup"><span data-stu-id="1c2a5-162">End-to-end service tests that include multiple operations involving several microservices require you to deploy and start the whole application in the Docker host by running docker-compose up (or a comparable mechanism if you are using an orchestrator).</span></span> <span data-ttu-id="1c2a5-163">Une fois que l’application entière et tous ses services sont exécutés, vous pouvez exécuter des tests d’intégration et des tests fonctionnels de bout en bout.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-163">Once the whole application and all its services is running, you can execute end-to-end integration and functional tests.</span></span>

<span data-ttu-id="1c2a5-164">Il existe pour cela plusieurs méthodes.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-164">There are a few approaches you can use.</span></span> <span data-ttu-id="1c2a5-165">Dans le fichier docker-compose.yml que vous utilisez pour déployer l’application au niveau de la solution, vous pouvez développer le point d’entrée pour utiliser la commande [dotnet test](../../../core/tools/dotnet-test.md).</span><span class="sxs-lookup"><span data-stu-id="1c2a5-165">In the docker-compose.yml file that you use to deploy the application at the solution level you can expand the entry point to use [dotnet test](../../../core/tools/dotnet-test.md).</span></span> <span data-ttu-id="1c2a5-166">Vous pouvez également utiliser un autre fichier Compose pour exécuter vos tests dans l’image que vous ciblez.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-166">You can also use another compose file that would run your tests in the image you are targeting.</span></span> <span data-ttu-id="1c2a5-167">En utilisant un autre fichier Compose pour les tests d’intégration comprenant vos microservices et vos bases de données dans des conteneurs, vous pouvez être sûr que les données associées sont toujours réinitialisées à leur état d’origine avant d’exécuter les tests.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-167">By using another compose file for integration tests that includes your microservices and databases on containers, you can make sure that the related data is always reset to its original state before running the tests.</span></span>

<span data-ttu-id="1c2a5-168">Une fois que l’application Compose est fonctionnelle, vous pouvez tirer parti des points d’arrêt et des exceptions si vous exécutez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-168">Once the compose application is up and running, you can take advantage of breakpoints and exceptions if you are running Visual Studio.</span></span> <span data-ttu-id="1c2a5-169">Vous pouvez également exécuter les tests d’intégration automatiquement dans votre pipeline d’intégration continue dans Azure DevOps Services, ou dans un autre système d’intégration ou de livraison continue prenant en charge les conteneurs Docker.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-169">Or you can run the integration tests automatically in your CI pipeline in Azure DevOps Services or any other CI/CD system that supports Docker containers.</span></span>

## <a name="testing-in-eshoponcontainers"></a><span data-ttu-id="1c2a5-170">Test dans eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="1c2a5-170">Testing in eShopOnContainers</span></span>

<span data-ttu-id="1c2a5-171">Les tests de l’application de référence (eShopOnContainers) ont été récemment restructurés et il existe maintenant quatre catégories :</span><span class="sxs-lookup"><span data-stu-id="1c2a5-171">The reference application (eShopOnContainers) tests were recently restructured and now there are four categories:</span></span>

1. <span data-ttu-id="1c2a5-172">**Tests unitaires** : simplement des anciens tests unitaires normaux, contenus dans les projets **{MicroserviceName}.UnitTests**</span><span class="sxs-lookup"><span data-stu-id="1c2a5-172">**Unit** tests, just plain old regular unit tests, contained in the **{MicroserviceName}.UnitTests** projects</span></span>

2. <span data-ttu-id="1c2a5-173">**Tests fonctionnels/d’intégration de microservices** : avec les cas de test impliquant l’infrastructure de chaque microservice, mais pris isolément des autres et contenus dans les projets **{NomMicroservice}.FunctionalTests**.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-173">**Microservice functional/integration tests**, with test cases involving the infrastructure for each microservice but isolated from the others and are contained in the **{MicroserviceName}.FunctionalTests** projects.</span></span>

3. <span data-ttu-id="1c2a5-174">**Tests fonctionnels/d’intégration d’applications** : se concentrent sur l’intégration de microservices, avec des cas de test qui emploient plusieurs microservices.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-174">**Application functional/integration tests**, that focus on microservices integration, with test cases that exert several microservices.</span></span> <span data-ttu-id="1c2a5-175">Ces tests se trouvent dans le projet **Application.FunctionalTests**.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-175">These tests are located in project **Application.FunctionalTests**.</span></span>

4. <span data-ttu-id="1c2a5-176">**Tests de charge** : se concentrent sur les temps de réponse pour chaque microservice.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-176">**Load tests**, that focus on response times for each microservice.</span></span> <span data-ttu-id="1c2a5-177">Ces tests se trouvent dans le projet **LoadTest** et nécessite Visual Studio 2017 Enterprise Edition.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-177">These tests are located in project **LoadTest** and need Visual Studio 2017 Enterprise Edition.</span></span>

<span data-ttu-id="1c2a5-178">Les tests unitaires et les tests d’intégration par microservice se trouvent dans le dossier de test de chaque microservice, et les tests d’application et de charge sont contenus sous le dossier de test du dossier de solution, comme l’illustre la figure 6-25.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-178">Unit and integration test per microservice are contained in a test folder in each microservice and Application a Load tests are contained under the test folder in the solution folder, as shown in Figure 6-25.</span></span>

![Structure des tests dans eShopOnContainers : chaque service dispose d’un dossier « test » qui inclut des tests unitaires et fonctionnels.](./media/image42.png)

<span data-ttu-id="1c2a5-181">**Figure 6-25.**</span><span class="sxs-lookup"><span data-stu-id="1c2a5-181">**Figure 6-25**.</span></span> <span data-ttu-id="1c2a5-182">Tester la structure des dossiers dans eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="1c2a5-182">Test folder structure in eShopOnContainers</span></span>

<span data-ttu-id="1c2a5-183">Les tests fonctionnels/d’intégration de microservices et d’applications sont exécutés à partir de Visual Studio, à l’aide de l’exécuteur de tests standard, mais vous devez d’abord démarrer les services d’infrastructure nécessaires au moyen d’un ensemble de fichiers docker-compose contenus dans le dossier de test de la solution :</span><span class="sxs-lookup"><span data-stu-id="1c2a5-183">Microservice and Application functional/integration tests are run from Visual Studio, using the regular tests runner, but first you need to start the required infrastructure services, by means of a set of docker-compose files contained in the solution test folder:</span></span>

<span data-ttu-id="1c2a5-184">**docker-compose-test.yml**</span><span class="sxs-lookup"><span data-stu-id="1c2a5-184">**docker-compose-test.yml**</span></span>

```yml
version: '3.4'

services:
  redis.data:
    image: redis:alpine
  rabbitmq:
    image: rabbitmq:3-management-alpine
  sql.data:
    image: microsoft/mssql-server-linux:2017-latest
  nosql.data:
    image: mongo
```

<span data-ttu-id="1c2a5-185">**docker-compose-test.override.yml**</span><span class="sxs-lookup"><span data-stu-id="1c2a5-185">**docker-compose-test.override.yml**</span></span>

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
  sql.data:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosql.data:
    ports:
      - "27017:27017"
```

<span data-ttu-id="1c2a5-186">Par conséquent, pour exécuter les tests fonctionnels/d’intégration, vous devez tout d’abord exécuter la commande suivante à partir du dossier de test de la solution :</span><span class="sxs-lookup"><span data-stu-id="1c2a5-186">So, to run the functional/integration tests you must first run this command, from the solution test folder:</span></span>

``` console
docker-compose -f docker-compose-test.yml -f docker-compose-test.override.yml up
```

<span data-ttu-id="1c2a5-187">Comme on peut le constater, ces fichiers Docker Compose lancent seulement les microservices Redis, RabbitMQ, SQL Server et MongoDB.</span><span class="sxs-lookup"><span data-stu-id="1c2a5-187">As you can see, these docker-compose files only start the Redis, RabbitMQ, SQL Server and MongoDB microservices.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1c2a5-188">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="1c2a5-188">Additional resources</span></span>

- <span data-ttu-id="1c2a5-189">**Fichier Lisez-moi relatif aux tests** dans le dépôt eShopOnContainers sur GitHub </span><span class="sxs-lookup"><span data-stu-id="1c2a5-189">**Tests README file** on the eShopOnContainers repo on GitHub </span></span>\
    <https://github.com/dotnet-architecture/eShopOnContainers/tree/dev/test>

- <span data-ttu-id="1c2a5-190">**Fichier Lisez-moi relatif aux tests de charge** dans le dépôt eShopOnContainers sur GitHub </span><span class="sxs-lookup"><span data-stu-id="1c2a5-190">**Load tests README file** on the eShopOnContainers repo on GitHub </span></span>\
    <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/test/ServicesTests/LoadTest/>

> [!div class="step-by-step"]
> <span data-ttu-id="1c2a5-191">[Précédent](subscribe-events.md)
> [Suivant](background-tasks-with-ihostedservice.md)</span><span class="sxs-lookup"><span data-stu-id="1c2a5-191">[Previous](subscribe-events.md)
[Next](background-tasks-with-ihostedservice.md)</span></span>
