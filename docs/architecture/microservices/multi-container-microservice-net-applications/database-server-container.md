---
title: Utilisez un serveur de base de données fonctionnant comme conteneur
description: Comprendre l’importance d’utiliser un serveur de base de données fonctionnant comme un conteneur uniquement pour le développement. Jamais pour la production.
ms.date: 01/30/2020
ms.openlocfilehash: 0cbc933003aac10970814378c27e88b5cb0ddbe5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628525"
---
# <a name="use-a-database-server-running-as-a-container"></a>Utilisez un serveur de base de données fonctionnant comme conteneur

Vos bases de données (SQL Server, PostgreSQL, MySQL, etc.) peuvent être stockées sur des serveurs autonomes ordinaires, dans des clusters locaux ou sur des services PaaS dans le cloud comme Azure SQL DB. Cependant, pour les environnements de développement et de test, avoir vos bases de données `docker-compose up` en cours d’exécution comme conteneurs est pratique, parce que vous n’avez pas de dépendance externe et tout simplement l’exécution de la commande commence l’ensemble de l’application. Le fait de disposer de ces bases de données en tant que conteneurs est également idéal pour les tests d’intégration, car la base de données démarre dans le conteneur et contient toujours les mêmes exemples de données. Les tests sont donc plus prévisibles.

## <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>Exécution de SQL Server en tant que conteneur avec une base de données liée à un microservice

Dans eShopOnContainers, il ya `sqldata`un conteneur nommé , tel que défini dans le fichier [docker-compose.yml,](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) qui exécute un serveur SQL pour Linux par exemple avec les bases de données SQL pour tous les microservices qui en ont besoin.

Un point clé dans les microservices est que chaque microservice possède ses données connexes, de sorte qu’il devrait avoir sa propre base de données. Cependant, les bases de données peuvent être n’importe où. Dans ce cas, ils sont tous dans le même conteneur pour garder les exigences de mémoire Docker aussi bas que possible. Gardez à l’esprit qu’il s’agit d’une solution suffisante pour le développement et, peut-être, les tests, mais pas pour la production.

Le conteneur SQL Server de l’exemple d’application est configuré avec le code YAML suivant dans le fichier docker-compose.yml. Celui-ci s’exécute quand vous exécutez `docker-compose up`. Notez que le code YAML a regroupé les informations de configuration du fichier docker-compose.yml générique et du fichier docker-compose.override.yml. (En règle générale, vous devez séparer les paramètres d’environnement des informations de base ou statiques liées à l’image SQL Server.)

```yml
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

De même, au lieu d’utiliser `docker-compose`, la commande `docker run` suivante peut exécuter ce conteneur :

```powershell
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

Toutefois, si vous déployez une application à plusieurs conteneurs comme eShopOnContainers, il est plus pratique d’utiliser la commande `docker-compose up` afin de déployer tous les conteneurs nécessaires pour l’application.

Quand vous démarrez ce conteneur SQL Server pour la première fois, il initialise SQL Server à l’aide du mot de passe que vous indiquez. Une fois que SQL Server est en cours d’exécution en tant que conteneur, vous pouvez mettre à jour la base de données en vous connectant via une connexion SQL normale, par exemple SQL Server Management Studio, Visual Studio ou du code C\#.

L’application eShopOnContainers initialise chaque base de données de microservice à l’aide d’exemples de données en les alimentant avec des données au démarrage, comme l’explique la section suivante.

L’exécution de SQL Server en tant que conteneur n’est pas seulement utile à une version de démonstration pour laquelle vous n’avez peut-être pas accès à une instance de SQL Server. Comme indiqué précédemment, elle est également idéale pour les environnements de développement et de test. Ainsi, vous pouvez facilement exécuter des tests d’intégration à partir d’une image SQL Server propre et de données connues en fournissant de nouveaux exemples de données.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Exécutez l’image SQL Server Docker sur Linux, Mac ou Windows** \
  <https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker>

- **Connectez et interrogez SQL Server sur Linux avec sqlcmd** \
  <https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd>

## <a name="seeding-with-test-data-on-web-application-startup"></a>Alimentation à l’aide de données de test au démarrage de l’application web

Pour ajouter des données à la base de données lorsque l’application démarre, vous pouvez ajouter du code comme ce qui suit à la `Main` méthode dans la `Program` classe du projet Web API :

```csharp
public static int Main(string[] args)
{
    var configuration = GetConfiguration();

    Log.Logger = CreateSerilogLogger(configuration);

    try
    {
        Log.Information("Configuring web host ({ApplicationContext})...", AppName);
        var host = CreateHostBuilder(configuration, args);

        Log.Information("Applying migrations ({ApplicationContext})...", AppName);
        host.MigrateDbContext<CatalogContext>((context, services) =>
        {
            var env = services.GetService<IWebHostEnvironment>();
            var settings = services.GetService<IOptions<CatalogSettings>>();
            var logger = services.GetService<ILogger<CatalogContextSeed>>();

            new CatalogContextSeed()
                .SeedAsync(context, env, settings, logger)
                .Wait();
        })
        .MigrateDbContext<IntegrationEventLogContext>((_, __) => { });

        Log.Information("Starting web host ({ApplicationContext})...", AppName);
        host.Run();

        return 0;
    }
    catch (Exception ex)
    {
        Log.Fatal(ex, "Program terminated unexpectedly ({ApplicationContext})!", AppName);
        return 1;
    }
    finally
    {
        Log.CloseAndFlush();
    }
}
```

Il y a une mise en garde importante lors de l’application des migrations et de l’ensemencement d’une base de données pendant le démarrage des conteneurs. Étant donné que le serveur de base de données peut ne pas être disponible pour une raison quelconque, vous devez gérer les retries en attendant que le serveur soit disponible. Cette logique de réahantation est gérée par la méthode d’extension, `MigrateDbContext()` comme le montre le code suivant :

```cs
public static IWebHost MigrateDbContext<TContext>(
    this IWebHost host,
    Action<TContext,
    IServiceProvider> seeder)
      where TContext : DbContext
{
    var underK8s = host.IsInKubernetes();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        var logger = services.GetRequiredService<ILogger<TContext>>();

        var context = services.GetService<TContext>();

        try
        {
            logger.LogInformation("Migrating database associated with context {DbContextName}", typeof(TContext).Name);

            if (underK8s)
            {
                InvokeSeeder(seeder, context, services);
            }
            else
            {
                var retry = Policy.Handle<SqlException>()
                    .WaitAndRetry(new TimeSpan[]
                    {
                    TimeSpan.FromSeconds(3),
                    TimeSpan.FromSeconds(5),
                    TimeSpan.FromSeconds(8),
                    });

                //if the sql server container is not created on run docker compose this
                //migration can't fail for network related exception. The retry options for DbContext only
                //apply to transient exceptions
                // Note that this is NOT applied when running some orchestrators (let the orchestrator to recreate the failing service)
                retry.Execute(() => InvokeSeeder(seeder, context, services));
            }

            logger.LogInformation("Migrated database associated with context {DbContextName}", typeof(TContext).Name);
        }
        catch (Exception ex)
        {
            logger.LogError(ex, "An error occurred while migrating the database used on context {DbContextName}", typeof(TContext).Name);
            if (underK8s)
            {
                throw;          // Rethrow under k8s because we rely on k8s to re-run the pod
            }
        }
    }

    return host;
}
```

Le code suivant de la classe personnalisée CatalogContextSeed remplit les données.

```csharp
public class CatalogContextSeed
{
    public static async Task SeedAsync(IApplicationBuilder applicationBuilder)
    {
        var context = (CatalogContext)applicationBuilder
            .ApplicationServices.GetService(typeof(CatalogContext));
        using (context)
        {
            context.Database.Migrate();
            if (!context.CatalogBrands.Any())
            {
                context.CatalogBrands.AddRange(
                    GetPreconfiguredCatalogBrands());
                await context.SaveChangesAsync();
            }
            if (!context.CatalogTypes.Any())
            {
                context.CatalogTypes.AddRange(
                    GetPreconfiguredCatalogTypes());
                await context.SaveChangesAsync();
            }
        }
    }

    static IEnumerable<CatalogBrand> GetPreconfiguredCatalogBrands()
    {
        return new List<CatalogBrand>()
       {
           new CatalogBrand() { Brand = "Azure"},
           new CatalogBrand() { Brand = ".NET" },
           new CatalogBrand() { Brand = "Visual Studio" },
           new CatalogBrand() { Brand = "SQL Server" }
       };
    }

    static IEnumerable<CatalogType> GetPreconfiguredCatalogTypes()
    {
        return new List<CatalogType>()
        {
            new CatalogType() { Type = "Mug"},
            new CatalogType() { Type = "T-Shirt" },
            new CatalogType() { Type = "Backpack" },
            new CatalogType() { Type = "USB Memory Stick" }
        };
    }
}
```

Quand vous exécutez des tests d’intégration, il est utile de pouvoir générer des données cohérentes avec ces derniers. Le fait de pouvoir tout créer entièrement, notamment une instance de SQL Server s’exécutant dans un conteneur, est un avantage indéniable pour les environnements de test.

## <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>Comparaison entre une base de données InMemory EF Core et SQL Server s’exécutant en tant que conteneur

Il existe un autre choix intéressant pour exécuter des tests : l’utilisation du fournisseur de base de données InMemory dans Entity Framework. Vous pouvez spécifier cette configuration dans la méthode ConfigureServices de la classe Startup de votre projet d’API web :

```csharp
public class Startup
{
    // Other Startup code ...
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddSingleton<IConfiguration>(Configuration);
        // DbContext using an InMemory database provider
        services.AddDbContext<CatalogContext>(opt => opt.UseInMemoryDatabase());
        //(Alternative: DbContext using a SQL Server provider
        //services.AddDbContext<CatalogContext>(c =>
        //{
            // c.UseSqlServer(Configuration["ConnectionString"]);
            //
        //});
    }

    // Other Startup code ...
}
```

Toutefois, gardez à l’esprit un point important. La base de données en mémoire ne prend pas en charge les nombreuses contraintes spécifiques à une base de données particulière. Par exemple, vous pouvez ajouter un index unique sur une colonne de votre modèle EF Core, et écrire un test relatif à votre base de données en mémoire pour vérifier qu’il est impossible d’ajouter une valeur dupliquée. Toutefois, quand vous utilisez la base de données en mémoire, vous ne pouvez pas prendre en charge les index uniques d’une colonne. La base de données en mémoire ne se comporte donc pas exactement comme une véritable base de données SQL Server, elle n’émule pas les contraintes spécifiques aux bases de données.

Même ainsi, une base de données en mémoire est toujours utile pour des tâches de test et de prototypage. Toutefois, si vous souhaitez créer des tests d’intégration précis qui prennent en compte le comportement d’une implémentation de base de données spécifique, vous devez utiliser une base de données réelle, telle qu’une base de données SQL Server. Dans ce but, l’exécution de SQL Server dans un conteneur est un excellent choix, qui offre une plus grande précision que le choix du fournisseur de base de données InMemory EF Core.

## <a name="using-a-redis-cache-service-running-in-a-container"></a>Utilisation d’un Cache Service Redis s’exécutant dans un conteneur

Vous pouvez exécuter Redis sur un conteneur, en particulier pour les tâches de développement et de test, ainsi que pour les scénarios de preuve de concept. Cela s’avère pratique, car toutes vos dépendances peuvent s’exécuter sur des conteneurs, non seulement pour vos machines de développement locales, mais également pour vos environnements de test dans les pipelines d’intégration continue/de livraison continue.

Toutefois, quand vous utilisez Redis en production, il est préférable de rechercher une solution à haute disponibilité telle que Redis Microsoft Azure, qui s’exécute en tant que service PaaS (Platform as a Service). Dans votre code, il vous suffit de changer les chaînes de connexion.

Redis fournit une image Docker. Cette image est accessible à partir de Docker Hub à l’URL suivante :

<https://hub.docker.com/_/redis/>

Vous pouvez exécuter directement un conteneur Docker Redis en utilisant la commande Docker CLI suivante à l’invite de commandes :

```console
docker run --name some-redis -d redis
```

L’image Redis inclut expose:6379 (le port utilisé par Redis). Ainsi, la liaison de conteneur standard la rend automatiquement accessible aux conteneurs liés.

Dans eShopOnContainers, `basket-api` le microservice utilise un cache Redis fonctionnant comme conteneur. Ce `basketdata` conteneur est défini comme faisant partie du fichier *docker-compose.yml* multi-conteneurs, comme le montre l’exemple suivant :

```yml
#docker-compose.yml file
#...
  basketdata:
    image: redis
    expose:
      - "6379"
```

Ce code dans le docker-compose.yml `basketdata` définit un conteneur nommé en fonction de l’image redis et la publication du port 6379 en interne. Cela signifie qu’il ne sera accessible qu’à partir d’autres conteneurs fonctionnant au sein de l’hôte Docker.

Enfin, dans le fichier *docker-compose.override.yml,* le `basket-api` microservice pour l’échantillon eShopOnContainers définit la chaîne de connexion à utiliser pour cela Conteneur Redis :

```yml
  basket-api:
    environment:
      # Other data ...
      - ConnectionString=basketdata
      - EventBusConnection=rabbitmq
```

Comme mentionné précédemment, le nom `basketdata` du microservice est résolu par le réseau interne de Docker DNS.

>[!div class="step-by-step"]
>[Suivant précédent](multi-container-applications-docker-compose.md)
>[Next](integration-event-based-microservice-communications.md)
