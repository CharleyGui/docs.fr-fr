---
title: analyse du fonctionnement ;
description: Explorez un moyen d’implémenter la supervision de l’intégrité.
ms.date: 03/02/2020
ms.openlocfilehash: 3b8ba57149061e629bee441672718eba8a79da63
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78241154"
---
# <a name="health-monitoring"></a><span data-ttu-id="61039-103">analyse du fonctionnement ;</span><span class="sxs-lookup"><span data-stu-id="61039-103">Health monitoring</span></span>

<span data-ttu-id="61039-104">La surveillance de l’intégrité fournit des informations quasiment en temps réel sur l’état de vos conteneurs et microservices.</span><span class="sxs-lookup"><span data-stu-id="61039-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="61039-105">La surveillance de l’intégrité est primordiale pour de multiples aspects du fonctionnement des microservices. Elle est particulièrement importante quand des orchestrateurs effectuent des mises à niveau d’application partielles par étapes, comme nous l’expliquerons plus tard.</span><span class="sxs-lookup"><span data-stu-id="61039-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="61039-106">Les applications basées sur des microservices utilisent souvent des pulsations ou des vérifications d’intégrité pour permettre à leurs analyseurs de performances, planificateurs et orchestrateurs d’assurer le suivi des divers services.</span><span class="sxs-lookup"><span data-stu-id="61039-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="61039-107">Si les services n’ont pas le moyen d’envoyer un signal de type « Je suis actif », à la demande ou selon une planification établie, votre application risque de connaître des problèmes quand vous déployez des mises à jour, ou elle risque simplement de détecter les défaillances trop tard et de ne pas être en mesure d’arrêter les défaillances en cascade, susceptibles au final d’entraîner des pannes majeures.</span><span class="sxs-lookup"><span data-stu-id="61039-107">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might just detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="61039-108">Dans le modèle standard, les services envoient des rapports sur leur état, et ces informations sont agrégées pour fournir une vue d’ensemble de l’état d’intégrité de votre application.</span><span class="sxs-lookup"><span data-stu-id="61039-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="61039-109">Si vous utilisez un orchestrateur, vous pouvez envoyer des informations d’intégrité au cluster de l’orchestrateur, afin que le cluster sache quelles actions exécuter.</span><span class="sxs-lookup"><span data-stu-id="61039-109">If you're using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="61039-110">Si vous optez pour des rapports d’intégrité complets et personnalisés pour votre application, vous pouvez détecter et résoudre les problèmes de votre application en cours d’exécution beaucoup plus facilement.</span><span class="sxs-lookup"><span data-stu-id="61039-110">If you invest in high-quality health reporting that's customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implement-health-checks-in-aspnet-core-services"></a><span data-ttu-id="61039-111">Implémenter des vérifications d’intégrité dans les services ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="61039-111">Implement health checks in ASP.NET Core services</span></span>

<span data-ttu-id="61039-112">Lorsque vous développez un microservice ou une application Web ASP.NET Core, vous pouvez utiliser la fonctionnalité de contrôles d’intégrité intégrée publiée dans ASP .NET Core 2,2 ([Microsoft. extensions. Diagnostics. HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)).</span><span class="sxs-lookup"><span data-stu-id="61039-112">When developing an ASP.NET Core microservice or web application, you can use the built-in health checks feature that was released in ASP .NET Core 2.2 ([Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)).</span></span> <span data-ttu-id="61039-113">Comme nombre de fonctionnalités ASP.NET Core, la fonctionnalité de vérification de l’intégrité est accompagnée d’un ensemble de services et d’un middleware (intergiciel).</span><span class="sxs-lookup"><span data-stu-id="61039-113">Like many ASP.NET Core features, health checks come with a set of services and a middleware.</span></span>

<span data-ttu-id="61039-114">Le middleware et les services de vérification de l’intégrité sont simples d’emploi. Leurs fonctionnalités vous permettent de vérifier si chaque ressource externe nécessaire pour votre application (par exemple, une base de données SQL Server ou une API distante) fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="61039-114">Health check services and middleware are easy to use and provide capabilities that let you validate if any external resource needed for your application (like a SQL Server database or a remote API) is working properly.</span></span> <span data-ttu-id="61039-115">Avec cette fonctionnalité, vous pouvez également déterminer à quel moment une ressource est considérée comme saine, comme nous l’expliquerons plus tard.</span><span class="sxs-lookup"><span data-stu-id="61039-115">When you use this feature, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="61039-116">Pour utiliser cette fonctionnalité efficacement, vous devez d’abord configurer les services dans vos microservices.</span><span class="sxs-lookup"><span data-stu-id="61039-116">To use this feature effectively, you need to first configure services in your microservices.</span></span> <span data-ttu-id="61039-117">Ensuite, vous avez besoin d’une application frontale qui demande des rapports d’intégrité.</span><span class="sxs-lookup"><span data-stu-id="61039-117">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="61039-118">Cette application front-end peut être une application de création de rapports personnalisée, ou un orchestrateur qui adapte ses actions en fonction des états d’intégrité retournés.</span><span class="sxs-lookup"><span data-stu-id="61039-118">That front-end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="61039-119">Utiliser la fonctionnalité HealthChecks dans vos microservices ASP.NET back-end</span><span class="sxs-lookup"><span data-stu-id="61039-119">Use the HealthChecks feature in your back-end ASP.NET microservices</span></span>

<span data-ttu-id="61039-120">Dans cette section, vous allez apprendre à implémenter la fonctionnalité HealthChecks dans un ASP.NET Core exemple d’application API Web 3,1 lors de l’utilisation du package [Microsoft. extensions. Diagnostics. HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks) .</span><span class="sxs-lookup"><span data-stu-id="61039-120">In this section, you'll learn how to implement the HealthChecks feature in a sample ASP.NET Core 3.1 Web API application when using the [Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks) package.</span></span> <span data-ttu-id="61039-121">L’implémentation de cette fonctionnalité dans des microservices à grande échelle comme eShopOnContainers est expliquée dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="61039-121">The Implementation of this feature in a large-scale microservices like the eShopOnContainers is explained in the next section.</span></span>

<span data-ttu-id="61039-122">Pour commencer, vous devez définir ce qui constitue un état intègre pour chaque microservice.</span><span class="sxs-lookup"><span data-stu-id="61039-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="61039-123">Dans l’exemple d’application, nous définissons que le microservice est sain si son API est accessible via HTTP et que la base de données SQL Server associée est également disponible.</span><span class="sxs-lookup"><span data-stu-id="61039-123">In the sample application, we define the microservice is healthy if its API is accessible via HTTP and its related SQL Server database is also available.</span></span>

<span data-ttu-id="61039-124">Dans .NET Core 3,1, avec les API intégrées, vous pouvez configurer les services, ajouter un contrôle d’intégrité pour le microservice et sa base de données de SQL Server dépendante de cette façon :</span><span class="sxs-lookup"><span data-stu-id="61039-124">In .NET Core 3.1, with the built-in APIs, you can configure the services, add a Health Check for the microservice and its dependent SQL Server database in this way:</span></span>

```csharp
// Startup.cs from .NET Core 3.1 Web API sample
//
public void ConfigureServices(IServiceCollection services)
{
    //...
    // Registers required services for health checks
    services.AddHealthChecks()
        // Add a health check for a SQL Server database
        .AddCheck(
            "OrderingDB-check", 
            new SqlConnectionHealthCheck(Configuration["ConnectionString"]), 
            HealthStatus.Unhealthy, 
            new string[] { "orderingdb" });
}
```

<span data-ttu-id="61039-125">Dans le code précédent, la méthode `services.AddHealthChecks()` configure une vérification HTTP de base qui retourne un code d’état **200** (intègre).</span><span class="sxs-lookup"><span data-stu-id="61039-125">In the previous code, the `services.AddHealthChecks()` method configures a basic HTTP check that returns a status code **200** with “Healthy”.</span></span>  <span data-ttu-id="61039-126">En outre, la méthode d’extension `AddCheck()` configure un `SqlConnectionHealthCheck` personnalisé qui vérifie l’intégrité de la base de données SQL associée.</span><span class="sxs-lookup"><span data-stu-id="61039-126">Further, the `AddCheck()` extension method configures a custom `SqlConnectionHealthCheck` that checks the related SQL Database’s health.</span></span>

<span data-ttu-id="61039-127">La méthode `AddCheck()` ajoute une nouvelle vérification d’intégrité avec un nom spécifié et l’implémentation de type `IHealthCheck`.</span><span class="sxs-lookup"><span data-stu-id="61039-127">The `AddCheck()` method adds a new health check with a specified name and the implementation of type `IHealthCheck`.</span></span> <span data-ttu-id="61039-128">Vous pouvez ajouter plusieurs vérifications d’intégrité à l’aide de la méthode AddCheck ; ainsi, un microservice indique un état « sain » uniquement quand toutes ses vérifications aboutissent à cet état.</span><span class="sxs-lookup"><span data-stu-id="61039-128">You can add multiple Health Checks using AddCheck method, so a microservice won't provide a “healthy” status until all its checks are healthy.</span></span>

<span data-ttu-id="61039-129">`SqlConnectionHealthCheck` est une classe personnalisée qui implémente `IHealthCheck`, qui prend une chaîne de connexion comme paramètre de constructeur et exécute une requête simple pour vérifier si la connexion à la base de données SQL est établie.</span><span class="sxs-lookup"><span data-stu-id="61039-129">`SqlConnectionHealthCheck` is a custom class that implements `IHealthCheck`, which takes a connection string as a constructor parameter and executes a simple query to check if the connection to the SQL database is successful.</span></span> <span data-ttu-id="61039-130">Elle retourne `HealthCheckResult.Healthy()` si la requête a été exécutée avec succès et un `FailureStatus` avec l’exception réelle en cas d’échec.</span><span class="sxs-lookup"><span data-stu-id="61039-130">It returns `HealthCheckResult.Healthy()` if the query was executed successfully and a `FailureStatus` with the actual exception when it fails.</span></span>

```csharp
// Sample SQL Connection Health Check
public class SqlConnectionHealthCheck : IHealthCheck
{
    private static readonly string DefaultTestQuery = "Select 1";

    public string ConnectionString { get; }

    public string TestQuery { get; }

    public SqlConnectionHealthCheck(string connectionString)
        : this(connectionString, testQuery: DefaultTestQuery)
    {
    }

    public SqlConnectionHealthCheck(string connectionString, string testQuery)
    {
        ConnectionString = connectionString ?? throw new ArgumentNullException(nameof(connectionString));
        TestQuery = testQuery;
    }

    public async Task<HealthCheckResult> CheckHealthAsync(HealthCheckContext context, CancellationToken cancellationToken = default(CancellationToken))
    {
        using (var connection = new SqlConnection(ConnectionString))
        {
            try
            {
                await connection.OpenAsync(cancellationToken);

                if (TestQuery != null)
                {
                    var command = connection.CreateCommand();
                    command.CommandText = TestQuery;

                    await command.ExecuteNonQueryAsync(cancellationToken);
                }
            }
            catch (DbException ex)
            {
                return new HealthCheckResult(status: context.Registration.FailureStatus, exception: ex);
            }
        }

        return HealthCheckResult.Healthy();
    }
}
```

<span data-ttu-id="61039-131">Notez que dans le code précédent, `Select 1` est la requête utilisée pour vérifier l’intégrité de la base de données.</span><span class="sxs-lookup"><span data-stu-id="61039-131">Note that in the previous code, `Select 1` is the query used to check the Health of the database.</span></span> <span data-ttu-id="61039-132">Pour surveiller la disponibilité de vos microservices, les orchestrateurs comme Kubernetes effectuent périodiquement des contrôles d’intégrité en envoyant des demandes pour tester les microservices.</span><span class="sxs-lookup"><span data-stu-id="61039-132">To monitor the availability of your microservices, orchestrators like Kubernetes periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="61039-133">Il est important que vos requêtes de base de données soient systématiquement efficaces afin que ces opérations soient rapides et n’entraînent pas une utilisation accrue des ressources.</span><span class="sxs-lookup"><span data-stu-id="61039-133">It's important to keep your database queries efficient so that these operations are quick and don’t result in a higher utilization of resources.</span></span>

<span data-ttu-id="61039-134">Enfin, ajoutez un intergiciel qui répond au chemin de l’URL `/hc`:</span><span class="sxs-lookup"><span data-stu-id="61039-134">Finally, add a middleware that responds to the url path `/hc`:</span></span>

```csharp
// Startup.cs from .NET Core 3.1 Web Api sample
//
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
        endpoints.MapHealthChecks("/hc");
        //...
    });
    //…
}
```

<span data-ttu-id="61039-135">Quand le point de terminaison `<yourmicroservice>/hc` est appelé, il exécute toutes les vérifications d’intégrité qui sont configurées dans la méthode `AddHealthChecks()` de la classe Startup et affiche le résultat.</span><span class="sxs-lookup"><span data-stu-id="61039-135">When the endpoint `<yourmicroservice>/hc` is invoked, it runs all the health checks that are configured in the `AddHealthChecks()` method in the Startup class and shows the result.</span></span>

### <a name="healthchecks-implementation-in-eshoponcontainers"></a><span data-ttu-id="61039-136">Implémentation de HealthChecks dans eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="61039-136">HealthChecks implementation in eShopOnContainers</span></span>

<span data-ttu-id="61039-137">Les microservices dans eShopOnContainers s’appuient sur plusieurs services pour effectuer leurs tâches.</span><span class="sxs-lookup"><span data-stu-id="61039-137">Microservices in eShopOnContainers rely on multiple services to perform its task.</span></span> <span data-ttu-id="61039-138">Par exemple, le microservice `Catalog.API` d’eShopOnContainers dépend de nombreux services, tels que Stockage Blob Azure, SQL Server et RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="61039-138">For example, the `Catalog.API` microservice from eShopOnContainers depends on many services, such as Azure Blob Storage, SQL Server, and RabbitMQ.</span></span> <span data-ttu-id="61039-139">Ainsi, plusieurs vérifications d’intégrité y sont ajoutées à l’aide de la méthode `AddCheck()`.</span><span class="sxs-lookup"><span data-stu-id="61039-139">Therefore, it has several health checks added using the `AddCheck()` method.</span></span> <span data-ttu-id="61039-140">Pour chaque service dépendant, une implémentation de `IHealthCheck` personnalisée qui définit son état d’intégrité respectif doit être ajoutée.</span><span class="sxs-lookup"><span data-stu-id="61039-140">For every dependent service, a custom `IHealthCheck` implementation that defines its respective health status would need to be added.</span></span>

<span data-ttu-id="61039-141">Le projet open source [AspNetCore. Diagnostics. HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) résout ce problème en fournissant des implémentations de contrôle d’intégrité personnalisées pour chacun de ces services d’entreprise, qui sont basées sur .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="61039-141">The open-source project [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) solves this problem by providing custom health check implementations for each of these enterprise services, that are built on top of .NET Core 3.1.</span></span> <span data-ttu-id="61039-142">Chaque vérification d’intégrité est disponible en tant que package NuGet individuel qui peut être facilement ajouté au projet.</span><span class="sxs-lookup"><span data-stu-id="61039-142">Each health check is available as an individual NuGet package that can be easily added to the project.</span></span> <span data-ttu-id="61039-143">eShopOnContainers les utilise largement dans tous ses microservices.</span><span class="sxs-lookup"><span data-stu-id="61039-143">eShopOnContainers uses them extensively in all its microservices.</span></span>

<span data-ttu-id="61039-144">Par exemple, dans le microservice `Catalog.API`, les packages NuGet suivants ont été ajoutés :</span><span class="sxs-lookup"><span data-stu-id="61039-144">For instance, in the `Catalog.API` microservice, the following NuGet packages were added:</span></span>

![Capture d’écran des packages NuGet AspNetCore. Diagnostics. HealthChecks.](./media/monitor-app-health/aspnet-core-diagnostics-health-checks.png)

<span data-ttu-id="61039-146">**Figure 8-7**.</span><span class="sxs-lookup"><span data-stu-id="61039-146">**Figure 8-7**.</span></span> <span data-ttu-id="61039-147">Vérifications d’intégrité personnalisées implémentées dans Catalog.API à l’aide d’AspNetCore.Diagnostics.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="61039-147">Custom Health Checks implemented in Catalog.API using AspNetCore.Diagnostics.HealthChecks</span></span>

<span data-ttu-id="61039-148">Dans le code suivant, les implémentations de la vérification d’intégrité sont ajoutées pour chaque service dépendant, puis le middleware est configuré :</span><span class="sxs-lookup"><span data-stu-id="61039-148">In the following code, the health check implementations are added for each dependent service and then the middleware is configured:</span></span>

```csharp
// Startup.cs from Catalog.api microservice
//
public static IServiceCollection AddCustomHealthCheck(this IServiceCollection services, IConfiguration configuration)
{
    var accountName = configuration.GetValue<string>("AzureStorageAccountName");
    var accountKey = configuration.GetValue<string>("AzureStorageAccountKey");

    var hcBuilder = services.AddHealthChecks();

    hcBuilder
        .AddSqlServer(
            configuration["ConnectionString"],
            name: "CatalogDB-check",
            tags: new string[] { "catalogdb" });

    if (!string.IsNullOrEmpty(accountName) && !string.IsNullOrEmpty(accountKey))
    {
        hcBuilder
            .AddAzureBlobStorage(
                $"DefaultEndpointsProtocol=https;AccountName={accountName};AccountKey={accountKey};EndpointSuffix=core.windows.net",
                name: "catalog-storage-check",
                tags: new string[] { "catalogstorage" });
    }
    if (configuration.GetValue<bool>("AzureServiceBusEnabled"))
    {
        hcBuilder
            .AddAzureServiceBusTopic(
                configuration["EventBusConnection"],
                topicName: "eshop_event_bus",
                name: "catalog-servicebus-check",
                tags: new string[] { "servicebus" });
    }
    else
    {
        hcBuilder
            .AddRabbitMQ(
                $"amqp://{configuration["EventBusConnection"]}",
                name: "catalog-rabbitmqbus-check",
                tags: new string[] { "rabbitmqbus" });
    }

    return services;
}
```

<span data-ttu-id="61039-149">Enfin, ajoutez l’intergiciel (middleware) de vérification pour écouter le point de terminaison « /HC » :</span><span class="sxs-lookup"><span data-stu-id="61039-149">Finally, add the HealthCheck middleware to listen to “/hc” endpoint:</span></span>

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="61039-150">Interroger vos microservices pour connaître leur état d’intégrité</span><span class="sxs-lookup"><span data-stu-id="61039-150">Query your microservices to report about their health status</span></span>

<span data-ttu-id="61039-151">Quand vous avez configuré les vérifications d’intégrité décrites dans cet article et que le microservice est en cours d’exécution dans Docker, vous pouvez directement vérifier son intégrité à partir d’un navigateur.</span><span class="sxs-lookup"><span data-stu-id="61039-151">When you've configured health checks as described in this article and you have the microservice running in Docker, you can directly check from a browser if it's healthy.</span></span> <span data-ttu-id="61039-152">Vous devez publier le port du conteneur dans l’hôte Docker, afin de pouvoir accéder au conteneur par le biais de `localhost` ou de l’adresse IP d’hôte Docker externe, comme illustré par la Figure 8-8.</span><span class="sxs-lookup"><span data-stu-id="61039-152">You have to publish the container port in the Docker host, so you can access the container through the external Docker host IP or through `localhost`, as shown in figure 8-8.</span></span>

![Capture d’écran de la réponse JSON retournée par un contrôle d’intégrité.](./media/monitor-app-health/health-check-json-response.png)

<span data-ttu-id="61039-154">**Figure 8-8**.</span><span class="sxs-lookup"><span data-stu-id="61039-154">**Figure 8-8**.</span></span> <span data-ttu-id="61039-155">Vérification de l’état d’intégrité d’un service à partir d’un navigateur</span><span class="sxs-lookup"><span data-stu-id="61039-155">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="61039-156">Dans ce test, vous pouvez voir que le microservice `Catalog.API` (exécuté sur le port 5101) est sain et qu’il retourne l’état HTTP 200 et les informations d’état au format JSON.</span><span class="sxs-lookup"><span data-stu-id="61039-156">In that test, you can see that the `Catalog.API` microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="61039-157">Le service ayant également vérifié l’intégrité de sa dépendance à la base de données SQL Server et à RabbitMQ, la vérification d’intégrité l’a elle-même considéré comme sain.</span><span class="sxs-lookup"><span data-stu-id="61039-157">The service also checked the health of its SQL Server database dependency and RabbitMQ, so the health check reported itself as healthy.</span></span>

## <a name="use-watchdogs"></a><span data-ttu-id="61039-158">Utiliser des pilotes de surveillance</span><span class="sxs-lookup"><span data-stu-id="61039-158">Use watchdogs</span></span>

<span data-ttu-id="61039-159">Un pilote de surveillance est un service distinct qui peut surveiller l’intégrité et la charge parmi les services, et fournir des informations sur l’intégrité des microservices en interrogeant la bibliothèque `HealthChecks` présentée plus haut.</span><span class="sxs-lookup"><span data-stu-id="61039-159">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the `HealthChecks` library introduced earlier.</span></span> <span data-ttu-id="61039-160">Cela permet d’éviter des erreurs qui ne seraient pas détectées à partir de l’affichage d’un service unique.</span><span class="sxs-lookup"><span data-stu-id="61039-160">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="61039-161">Les agents de surveillance sont également un bon moyen d’héberger du code capable d’effectuer des actions de correction dans des conditions connues, sans nécessiter l’intervention d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="61039-161">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="61039-162">L’exemple eShopOnContainers contient une page web qui affiche des exemples de rapports de vérification d’intégrité, comme illustré à la Figure 8-9.</span><span class="sxs-lookup"><span data-stu-id="61039-162">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 8-9.</span></span> <span data-ttu-id="61039-163">Il s’agit du pilote de surveillance le plus simple que vous pouvez avoir, car il ne fait qu’afficher l’état des microservices et des applications web dans eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="61039-163">This is the simplest watchdog you could have since it only shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="61039-164">En règle générale, un pilote de surveillance exécute aussi certaines actions quand il détecte des états non intègres.</span><span class="sxs-lookup"><span data-stu-id="61039-164">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

<span data-ttu-id="61039-165">Heureusement, [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) fournit également le package NuGet [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) qui peut être utilisé pour afficher les résultats de la vérification d’intégrité à partir des URI configurés.</span><span class="sxs-lookup"><span data-stu-id="61039-165">Fortunately, [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) also provides [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet package that can be used to display the health check results from the configured URIs.</span></span>

![Capture d’écran des États d’intégrité eShopOnContainers de l’interface utilisateur des contrôles d’intégrité.](./media/monitor-app-health/health-check-status-ui.png)

<span data-ttu-id="61039-167">**Figure 8-9**.</span><span class="sxs-lookup"><span data-stu-id="61039-167">**Figure 8-9**.</span></span> <span data-ttu-id="61039-168">Exemple de rapport de vérification d’intégrité dans eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="61039-168">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="61039-169">En résumé, ce service de surveillance interroge le point de terminaison « /hc » de chaque microservice.</span><span class="sxs-lookup"><span data-stu-id="61039-169">In summary, this watchdog service queries each microservice’s "/hc" endpoint.</span></span> <span data-ttu-id="61039-170">Ce point de terminaison exécute toutes les vérifications d’intégrité définies et retourne un état d’intégrité général si toutes ces vérifications sont intègres.</span><span class="sxs-lookup"><span data-stu-id="61039-170">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span> <span data-ttu-id="61039-171">Pour utiliser HealthChecksUI, il suffit de définir quelques entrées de configuration et d’ajouter deux lignes de code au fichier Startup.cs du service de surveillance.</span><span class="sxs-lookup"><span data-stu-id="61039-171">The HealthChecksUI is easy to consume with a few configuration entries and two lines of code that needs to be added into the Startup.cs of the watchdog service.</span></span>

<span data-ttu-id="61039-172">Exemple de fichier de configuration de l’interface utilisateur de la vérification d’intégrité :</span><span class="sxs-lookup"><span data-stu-id="61039-172">Sample configuration file for health check UI:</span></span>

```json
// Configuration
{
  "HealthChecks-UI": {
    "HealthChecks": [
      {
        "Name": "Ordering HTTP Check",
        "Uri": "http://localhost:5102/hc"
      },
      {
        "Name": "Ordering HTTP Background Check",
        "Uri": "http://localhost:5111/hc"
      },
      //...
    ]}
}
```

<span data-ttu-id="61039-173">Fichier Startup.cs qui ajoute HealthChecksUI :</span><span class="sxs-lookup"><span data-stu-id="61039-173">Startup.cs file that adds HealthChecksUI:</span></span>

```csharp
// Startup.cs from WebStatus(Watch Dog) service
//
public void ConfigureServices(IServiceCollection services)
{
    //…
    // Registers required services for health checks
    services.AddHealthChecksUI();
}
//…
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseHealthChecksUI(config=> config.UIPath = “/hc-ui”);
    //…
}
```

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="61039-174">Vérifications d’intégrité avec des orchestrateurs</span><span class="sxs-lookup"><span data-stu-id="61039-174">Health checks when using orchestrators</span></span>

<span data-ttu-id="61039-175">Pour superviser la disponibilité de vos microservices, les orchestrateurs tels que Kubernetes et Service Fabric effectuent régulièrement des vérifications d’intégrité en envoyant des requêtes pour tester les microservices.</span><span class="sxs-lookup"><span data-stu-id="61039-175">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="61039-176">Quand un orchestrateur détermine qu’un service ou conteneur n’est pas intègre, il arrête le routage des requêtes vers cette instance.</span><span class="sxs-lookup"><span data-stu-id="61039-176">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="61039-177">Généralement, il crée aussi une autre instance de ce conteneur.</span><span class="sxs-lookup"><span data-stu-id="61039-177">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="61039-178">Par exemple, la plupart des orchestrateurs peuvent utiliser des vérifications d’intégrité pour gérer les déploiements sans temps d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="61039-178">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="61039-179">L’orchestrateur démarre le routage du trafic vers les instances d’un service ou conteneur uniquement quand l’état du service ou conteneur est de nouveau intègre.</span><span class="sxs-lookup"><span data-stu-id="61039-179">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="61039-180">La surveillance de l’intégrité est particulièrement importante quand un orchestrateur effectue une mise à niveau d’application.</span><span class="sxs-lookup"><span data-stu-id="61039-180">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="61039-181">Certains orchestrateurs (comme Azure Service Fabric) mettent à jour les services par étapes. Par exemple, ils peuvent mettre à jour un cinquième de la surface du cluster pour chaque mise à niveau d’application.</span><span class="sxs-lookup"><span data-stu-id="61039-181">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="61039-182">L’ensemble de nœuds mis à niveau en même temps est appelé *domaine de mise à niveau*.</span><span class="sxs-lookup"><span data-stu-id="61039-182">The set of nodes that's upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="61039-183">Une fois que chaque domaine de mise à niveau a été mis à niveau et est disponible pour les utilisateurs, le domaine doit passer les vérifications d’intégrité avant que le déploiement continue dans le domaine de mise à niveau suivant.</span><span class="sxs-lookup"><span data-stu-id="61039-183">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="61039-184">L’intégrité du service inclut un autre aspect : le rapport de mesures à partir du service.</span><span class="sxs-lookup"><span data-stu-id="61039-184">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="61039-185">Il s’agit d’une fonctionnalité avancée du modèle d’intégrité de certains orchestrateurs, comme Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="61039-185">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="61039-186">Les métriques sont importantes quand vous utilisez un orchestrateur, car elles aident à équilibrer l’utilisation des ressources.</span><span class="sxs-lookup"><span data-stu-id="61039-186">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="61039-187">Les mesures peuvent aussi servir d’indicateur de l’intégrité du système.</span><span class="sxs-lookup"><span data-stu-id="61039-187">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="61039-188">Par exemple, une application inclut de nombreux microservices et chaque instance fournit une métrique de demandes par seconde (RPS).</span><span class="sxs-lookup"><span data-stu-id="61039-188">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="61039-189">Si un service utilise davantage de ressources (mémoire, processeur, etc.) qu’un autre service, l’orchestrateur peut déplacer des instances du service dans le cluster pour mieux équilibrer l’utilisation des ressources entre les services.</span><span class="sxs-lookup"><span data-stu-id="61039-189">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="61039-190">Notez qu’Azure Service Fabric fournit son propre [modèle de vérification d’intégrité](/azure/service-fabric/service-fabric-health-introduction), qui est plus performant que les vérifications d’intégrité simples.</span><span class="sxs-lookup"><span data-stu-id="61039-190">Note that Azure Service Fabric provides its own [Health Monitoring model](/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="61039-191">Surveillance avancée : visualisation, analyse et alertes</span><span class="sxs-lookup"><span data-stu-id="61039-191">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="61039-192">La dernière partie de la surveillance consiste en la visualisation du flux d’événements, la création de rapports sur les performances de service et la génération d’alertes en cas de détection d’un problème.</span><span class="sxs-lookup"><span data-stu-id="61039-192">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="61039-193">Vous pouvez utiliser différentes solutions pour cet aspect de la surveillance.</span><span class="sxs-lookup"><span data-stu-id="61039-193">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="61039-194">Vous pouvez utiliser des applications personnalisées simples qui affichent l’état de vos services. C’est le cas de la page personnalisée présentée dans la section sur [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="61039-194">You can use simple custom applications showing the state of your services, like the custom page shown when explaining the [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks).</span></span> <span data-ttu-id="61039-195">Vous pouvez aussi utiliser des outils plus avancés comme [Azure Monitor](https://azure.microsoft.com/services/monitor/) pour déclencher des alertes en fonction du flux d’événements.</span><span class="sxs-lookup"><span data-stu-id="61039-195">Or you could use more advanced tools like [Azure Monitor](https://azure.microsoft.com/services/monitor/) to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="61039-196">Pour finir, si vous stockez tous les flux d’événements, vous pouvez utiliser Microsoft Power BI ou d’autres solutions comme Kibana ou Splunk pour visualiser les données.</span><span class="sxs-lookup"><span data-stu-id="61039-196">Finally, if you're storing all the event streams, you can use Microsoft Power BI or other solutions like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="61039-197">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="61039-197">Additional resources</span></span>

- <span data-ttu-id="61039-198">**HealthChecks et interface utilisateur de HealthChecks pour ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="61039-198">**HealthChecks and HealthChecks UI for ASP.NET Core** </span></span>\
  <https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks>

- <span data-ttu-id="61039-199">**Présentation de la supervision de l’intégrité de Service Fabric** </span><span class="sxs-lookup"><span data-stu-id="61039-199">**Introduction to Service Fabric health monitoring** </span></span>\
  [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

- <span data-ttu-id="61039-200">**Azure Monitor** </span><span class="sxs-lookup"><span data-stu-id="61039-200">**Azure Monitor** </span></span>\
  <https://azure.microsoft.com/services/monitor/>

>[!div class="step-by-step"]
><span data-ttu-id="61039-201">[Précédent](implement-circuit-breaker-pattern.md)
>[Suivant](../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="61039-201">[Previous](implement-circuit-breaker-pattern.md)
[Next](../secure-net-microservices-web-applications/index.md)</span></span>
