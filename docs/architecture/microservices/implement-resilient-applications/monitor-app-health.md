---
title: Surveillance de l’intégrité
description: Explorez un moyen d’implémenter la supervision de l’intégrité.
ms.date: 03/02/2020
ms.openlocfilehash: d3d2bc72cf29b3d1ac93191e7ff2bd827c9ee68d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401710"
---
# <a name="health-monitoring"></a>Surveillance de l’intégrité

La surveillance de l’intégrité fournit des informations quasiment en temps réel sur l’état de vos conteneurs et microservices. La surveillance de l’intégrité est primordiale pour de multiples aspects du fonctionnement des microservices. Elle est particulièrement importante quand des orchestrateurs effectuent des mises à niveau d’application partielles par étapes, comme nous l’expliquerons plus tard.

Les applications basées sur des microservices utilisent souvent des pulsations ou des vérifications d’intégrité pour permettre à leurs analyseurs de performances, planificateurs et orchestrateurs d’assurer le suivi des divers services. Si les services n’ont pas le moyen d’envoyer un signal de type « Je suis actif », à la demande ou selon une planification établie, votre application risque de connaître des problèmes quand vous déployez des mises à jour, ou elle risque simplement de détecter les défaillances trop tard et de ne pas être en mesure d’arrêter les défaillances en cascade, susceptibles au final d’entraîner des pannes majeures.

Dans le modèle standard, les services envoient des rapports sur leur état, et ces informations sont agrégées pour fournir une vue d’ensemble de l’état d’intégrité de votre application. Si vous utilisez un orchestrateur, vous pouvez envoyer des informations d’intégrité au cluster de l’orchestrateur, afin que le cluster sache quelles actions exécuter. Si vous optez pour des rapports d’intégrité complets et personnalisés pour votre application, vous pouvez détecter et résoudre les problèmes de votre application en cours d’exécution beaucoup plus facilement.

## <a name="implement-health-checks-in-aspnet-core-services"></a>Implémenter des vérifications d’intégrité dans les services ASP.NET Core

Lors du développement d’un microservice ASP.NET Core ou d’une application web, vous pouvez utiliser la fonction de contrôle de santé intégré qui a été publié dans ASP .NET Core 2.2 ([Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)). Comme nombre de fonctionnalités ASP.NET Core, la fonctionnalité de vérification de l’intégrité est accompagnée d’un ensemble de services et d’un middleware (intergiciel).

Le middleware et les services de vérification de l’intégrité sont simples d’emploi. Leurs fonctionnalités vous permettent de vérifier si chaque ressource externe nécessaire pour votre application (par exemple, une base de données SQL Server ou une API distante) fonctionne correctement. Avec cette fonctionnalité, vous pouvez également déterminer à quel moment une ressource est considérée comme saine, comme nous l’expliquerons plus tard.

Pour utiliser cette fonctionnalité efficacement, vous devez d’abord configurer les services dans vos microservices. Ensuite, vous avez besoin d’une application frontale qui demande des rapports d’intégrité. Cette application front-end peut être une application de création de rapports personnalisée, ou un orchestrateur qui adapte ses actions en fonction des états d’intégrité retournés.

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a>Utiliser la fonctionnalité HealthChecks dans vos microservices ASP.NET back-end

Dans cette section, vous apprendrez à implémenter la fonctionnalité HealthChecks dans un échantillon ASP.NET’application aPI Web Core 3.1 lors de l’utilisation du package [Microsoft.Extensions.Diagnostics.HealthChecks.](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks) La mise en œuvre de cette fonctionnalité dans un microservices à grande échelle comme l’eShopOnContainers est expliquée dans la section suivante.

Pour commencer, vous devez définir ce qui constitue un état intègre pour chaque microservice. Dans l’application de l’échantillon, nous définissons le microservice est sain si son API est accessible via HTTP et sa base de données SQL Server connexe est également disponible.

Dans .NET Core 3.1, avec les API intégrées, vous pouvez configurer les services, ajouter un bilan de santé pour le microservice et sa base de données SQL Server dépendante de cette façon:

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

Dans le code précédent, la méthode `services.AddHealthChecks()` configure une vérification HTTP de base qui retourne un code d’état **200** (intègre).  En outre, la méthode d’extension `AddCheck()` configure un `SqlConnectionHealthCheck` personnalisé qui vérifie l’intégrité de la base de données SQL associée.

La méthode `AddCheck()` ajoute une nouvelle vérification d’intégrité avec un nom spécifié et l’implémentation de type `IHealthCheck`. Vous pouvez ajouter plusieurs vérifications d’intégrité à l’aide de la méthode AddCheck ; ainsi, un microservice indique un état « sain » uniquement quand toutes ses vérifications aboutissent à cet état.

`SqlConnectionHealthCheck` est une classe personnalisée qui implémente `IHealthCheck`, qui prend une chaîne de connexion comme paramètre de constructeur et exécute une requête simple pour vérifier si la connexion à la base de données SQL est établie. Elle retourne `HealthCheckResult.Healthy()` si la requête a été exécutée avec succès et un `FailureStatus` avec l’exception réelle en cas d’échec.

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

Notez que dans le code précédent, `Select 1` est la requête utilisée pour vérifier l’intégrité de la base de données. Pour surveiller la disponibilité de vos microservices, des orchestrateurs comme Kubernetes effectuent périodiquement des contrôles de santé en envoyant des demandes pour tester les microservices. Il est important que vos requêtes de base de données soient systématiquement efficaces afin que ces opérations soient rapides et n’entraînent pas une utilisation accrue des ressources.

Enfin, ajoutez un middleware qui répond `/hc`au chemin url :

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

Quand le point de terminaison `<yourmicroservice>/hc` est appelé, il exécute toutes les vérifications d’intégrité qui sont configurées dans la méthode `AddHealthChecks()` de la classe Startup et affiche le résultat.

### <a name="healthchecks-implementation-in-eshoponcontainers"></a>Implémentation de HealthChecks dans eShopOnContainers

Les microservices dans eShopOnContainers s’appuient sur plusieurs services pour effectuer leurs tâches. Par exemple, le microservice `Catalog.API` d’eShopOnContainers dépend de nombreux services, tels que Stockage Blob Azure, SQL Server et RabbitMQ. Ainsi, plusieurs vérifications d’intégrité y sont ajoutées à l’aide de la méthode `AddCheck()`. Pour chaque service à `IHealthCheck` charge, une implémentation personnalisée qui définit son état de santé respectif devrait être ajoutée.

Le projet open-source [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) résout ce problème en fournissant des implémentations personnalisées de bilan de santé pour chacun de ces services d’entreprise, qui sont construits au-dessus de .NET Core 3.1. Chaque vérification d’intégrité est disponible en tant que package NuGet individuel qui peut être facilement ajouté au projet. eShopOnContainers les utilise largement dans tous ses microservices.

Par exemple, dans le microservice `Catalog.API`, les packages NuGet suivants ont été ajoutés :

![Capture d’écran des forfaits AspNetCore.Diagnostics.HealthChecks NuGet.](./media/monitor-app-health/aspnet-core-diagnostics-health-checks.png)

**Figure 8-7**. Vérifications d’intégrité personnalisées implémentées dans Catalog.API à l’aide d’AspNetCore.Diagnostics.HealthChecks

Dans le code suivant, les implémentations de la vérification d’intégrité sont ajoutées pour chaque service dépendant, puis le middleware est configuré :

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

Enfin, ajoutez le middleware HealthCheck pour écouter le point de terminaison «/hc » :

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a>Interroger vos microservices pour connaître leur état d’intégrité

Quand vous avez configuré les vérifications d’intégrité décrites dans cet article et que le microservice est en cours d’exécution dans Docker, vous pouvez directement vérifier son intégrité à partir d’un navigateur. Vous devez publier le port du conteneur dans l’hôte Docker, afin de pouvoir accéder au conteneur par le biais de `localhost` ou de l’adresse IP d’hôte Docker externe, comme illustré par la Figure 8-8.

![Capture d’écran de la réponse JSON retourné par un bilan de santé.](./media/monitor-app-health/health-check-json-response.png)

**Figure 8-8**. Vérification de l’état d’intégrité d’un service à partir d’un navigateur

Dans ce test, vous pouvez voir que le microservice `Catalog.API` (exécuté sur le port 5101) est sain et qu’il retourne l’état HTTP 200 et les informations d’état au format JSON. Le service ayant également vérifié l’intégrité de sa dépendance à la base de données SQL Server et à RabbitMQ, la vérification d’intégrité l’a elle-même considéré comme sain.

## <a name="use-watchdogs"></a>Utiliser des pilotes de surveillance

Un pilote de surveillance est un service distinct qui peut surveiller l’intégrité et la charge parmi les services, et fournir des informations sur l’intégrité des microservices en interrogeant la bibliothèque `HealthChecks` présentée plus haut. Cela permet d’éviter des erreurs qui ne seraient pas détectées à partir de l’affichage d’un service unique. Les agents de surveillance sont également un bon moyen d’héberger du code capable d’effectuer des actions de correction dans des conditions connues, sans nécessiter l’intervention d’un utilisateur.

L’exemple eShopOnContainers contient une page web qui affiche des exemples de rapports de vérification d’intégrité, comme illustré à la Figure 8-9. Il s’agit du pilote de surveillance le plus simple que vous pouvez avoir, car il ne fait qu’afficher l’état des microservices et des applications web dans eShopOnContainers. En règle générale, un pilote de surveillance exécute aussi certaines actions quand il détecte des états non intègres.

Heureusement, [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) fournit également le package NuGet [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) qui peut être utilisé pour afficher les résultats de la vérification d’intégrité à partir des URI configurés.

![Capture d’écran de l’assurance-maladie health Checks eShopOnContainers états de santé.](./media/monitor-app-health/health-check-status-ui.png)

**Figure 8-9**. Exemple de rapport de vérification d’intégrité dans eShopOnContainers

En résumé, ce service de surveillance interroge le point de terminaison « /hc » de chaque microservice. Ce point de terminaison exécute toutes les vérifications d’intégrité définies et retourne un état d’intégrité général si toutes ces vérifications sont intègres. Pour utiliser HealthChecksUI, il suffit de définir quelques entrées de configuration et d’ajouter deux lignes de code au fichier Startup.cs du service de surveillance.

Exemple de fichier de configuration de l’interface utilisateur de la vérification d’intégrité :

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

Fichier Startup.cs qui ajoute HealthChecksUI :

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

## <a name="health-checks-when-using-orchestrators"></a>Vérifications d’intégrité avec des orchestrateurs

Pour superviser la disponibilité de vos microservices, les orchestrateurs tels que Kubernetes et Service Fabric effectuent régulièrement des vérifications d’intégrité en envoyant des requêtes pour tester les microservices. Quand un orchestrateur détermine qu’un service ou conteneur n’est pas intègre, il arrête le routage des requêtes vers cette instance. Généralement, il crée aussi une autre instance de ce conteneur.

Par exemple, la plupart des orchestrateurs peuvent utiliser des vérifications d’intégrité pour gérer les déploiements sans temps d’arrêt. L’orchestrateur démarre le routage du trafic vers les instances d’un service ou conteneur uniquement quand l’état du service ou conteneur est de nouveau intègre.

La surveillance de l’intégrité est particulièrement importante quand un orchestrateur effectue une mise à niveau d’application. Certains orchestrateurs (comme Azure Service Fabric) mettent à jour les services par étapes. Par exemple, ils peuvent mettre à jour un cinquième de la surface du cluster pour chaque mise à niveau d’application. L’ensemble de nœuds mis à niveau en même temps est appelé *domaine de mise à niveau*. Une fois que chaque domaine de mise à niveau a été mis à niveau et est disponible pour les utilisateurs, le domaine doit passer les vérifications d’intégrité avant que le déploiement continue dans le domaine de mise à niveau suivant.

L’intégrité du service inclut un autre aspect : le rapport de mesures à partir du service. Il s’agit d’une fonctionnalité avancée du modèle d’intégrité de certains orchestrateurs, comme Service Fabric. Les métriques sont importantes quand vous utilisez un orchestrateur, car elles aident à équilibrer l’utilisation des ressources. Les mesures peuvent aussi servir d’indicateur de l’intégrité du système. Par exemple, une application inclut de nombreux microservices et chaque instance fournit une métrique de demandes par seconde (RPS). Si un service utilise davantage de ressources (mémoire, processeur, etc.) qu’un autre service, l’orchestrateur peut déplacer des instances du service dans le cluster pour mieux équilibrer l’utilisation des ressources entre les services.

Notez qu’Azure Service Fabric fournit son propre [modèle de vérification d’intégrité](/azure/service-fabric/service-fabric-health-introduction), qui est plus performant que les vérifications d’intégrité simples.

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>Surveillance avancée : visualisation, analyse et alertes

La dernière partie de la surveillance consiste en la visualisation du flux d’événements, la création de rapports sur les performances de service et la génération d’alertes en cas de détection d’un problème. Vous pouvez utiliser différentes solutions pour cet aspect de la surveillance.

Vous pouvez utiliser des applications personnalisées simples qui affichent l’état de vos services. C’est le cas de la page personnalisée présentée dans la section sur [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks). Vous pouvez aussi utiliser des outils plus avancés comme [Azure Monitor](https://azure.microsoft.com/services/monitor/) pour déclencher des alertes en fonction du flux d’événements.

Pour finir, si vous stockez tous les flux d’événements, vous pouvez utiliser Microsoft Power BI ou d’autres solutions comme Kibana ou Splunk pour visualiser les données.

## <a name="additional-resources"></a>Ressources supplémentaires

- **HealthChecks et HealthChecks UI pour ASP.NET Core** \
  <https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks>

- **Introduction à la surveillance de la santé de tissu de service** \
  [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

- **Moniteur Azure** \
  <https://azure.microsoft.com/services/monitor/>

>[!div class="step-by-step"]
>[Suivant précédent](implement-circuit-breaker-pattern.md)
>[Next](../secure-net-microservices-web-applications/index.md)
