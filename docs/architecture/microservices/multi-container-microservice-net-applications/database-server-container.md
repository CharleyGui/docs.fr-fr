---
title: Utiliser un serveur de base de données s’exécutant en tant que conteneur
description: Comprendre l’importance de l’utilisation d’un serveur de base de données qui s’exécute en tant que conteneur uniquement pour le développement. Jamais pour la production.
ms.date: 01/30/2020
ms.openlocfilehash: 816ac196636f78a368a9f20e8eedcc6a22567fa7
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77502292"
---
# <a name="use-a-database-server-running-as-a-container"></a><span data-ttu-id="75f99-104">Utiliser un serveur de base de données s’exécutant en tant que conteneur</span><span class="sxs-lookup"><span data-stu-id="75f99-104">Use a database server running as a container</span></span>

<span data-ttu-id="75f99-105">Vos bases de données (SQL Server, PostgreSQL, MySQL, etc.) peuvent être stockées sur des serveurs autonomes ordinaires, dans des clusters locaux ou sur des services PaaS dans le cloud comme Azure SQL DB.</span><span class="sxs-lookup"><span data-stu-id="75f99-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="75f99-106">Toutefois, pour les environnements de développement et de test, l’exécution de vos bases de données en tant que conteneurs est pratique, car vous n’avez pas de dépendance externe et en exécutant simplement la commande `docker-compose up` démarre l’application entière.</span><span class="sxs-lookup"><span data-stu-id="75f99-106">However, for development and test environments, having your databases running as containers is convenient, because you don't have any external dependency and simply running the `docker-compose up` command starts the whole application.</span></span> <span data-ttu-id="75f99-107">Le fait de disposer de ces bases de données en tant que conteneurs est également idéal pour les tests d’intégration, car la base de données démarre dans le conteneur et contient toujours les mêmes exemples de données. Les tests sont donc plus prévisibles.</span><span class="sxs-lookup"><span data-stu-id="75f99-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

## <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="75f99-108">Exécution de SQL Server en tant que conteneur avec une base de données liée à un microservice</span><span class="sxs-lookup"><span data-stu-id="75f99-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="75f99-109">Dans eShopOnContainers, il existe un conteneur nommé `sqldata`, tel que défini dans le fichier [docker-compose. yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) , qui exécute une SQL Server pour une instance Linux avec les bases de données SQL pour tous les microservices qui en ont besoin.</span><span class="sxs-lookup"><span data-stu-id="75f99-109">In eShopOnContainers, there's a container named `sqldata`, as defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file, that runs a SQL Server for Linux instance with the SQL databases for all microservices that need one.</span></span>

<span data-ttu-id="75f99-110">Un point clé dans les microservices est que chaque microservice possède ses données associées. il doit donc posséder sa propre base de données.</span><span class="sxs-lookup"><span data-stu-id="75f99-110">A key point in microservices is that each microservice owns its related data, so it should have its own database.</span></span> <span data-ttu-id="75f99-111">Toutefois, les bases de données peuvent se trouver n’importe où.</span><span class="sxs-lookup"><span data-stu-id="75f99-111">However, the databases can be anywhere.</span></span> <span data-ttu-id="75f99-112">Dans ce cas, ils se trouvent tous dans le même conteneur pour que les besoins en mémoire de l’ancrage soient aussi bas que possible.</span><span class="sxs-lookup"><span data-stu-id="75f99-112">In this case, they are all in the same container to keep Docker memory requirements as low as possible.</span></span> <span data-ttu-id="75f99-113">Gardez à l’esprit qu’il s’agit d’une solution suffisamment bonne pour le développement et, éventuellement, de tests, mais pas pour la production.</span><span class="sxs-lookup"><span data-stu-id="75f99-113">Keep in mind that this is a good-enough solution for development and, perhaps, testing but not for production.</span></span>

<span data-ttu-id="75f99-114">Le conteneur SQL Server de l’exemple d’application est configuré avec le code YAML suivant dans le fichier docker-compose.yml. Celui-ci s’exécute quand vous exécutez `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="75f99-114">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run `docker-compose up`.</span></span> <span data-ttu-id="75f99-115">Notez que le code YAML a regroupé les informations de configuration du fichier docker-compose.yml générique et du fichier docker-compose.override.yml.</span><span class="sxs-lookup"><span data-stu-id="75f99-115">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="75f99-116">(En règle générale, vous devez séparer les paramètres d’environnement des informations de base ou statiques liées à l’image SQL Server.)</span><span class="sxs-lookup"><span data-stu-id="75f99-116">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

<span data-ttu-id="75f99-117">De même, au lieu d’utiliser `docker-compose`, la commande `docker run` suivante peut exécuter ce conteneur :</span><span class="sxs-lookup"><span data-stu-id="75f99-117">In a similar way, instead of using `docker-compose`, the following `docker run` command can run that container:</span></span>

```powershell
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

<span data-ttu-id="75f99-118">Toutefois, si vous déployez une application à plusieurs conteneurs comme eShopOnContainers, il est plus pratique d’utiliser la commande `docker-compose up` afin de déployer tous les conteneurs nécessaires pour l’application.</span><span class="sxs-lookup"><span data-stu-id="75f99-118">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the `docker-compose up` command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="75f99-119">Quand vous démarrez ce conteneur SQL Server pour la première fois, il initialise SQL Server à l’aide du mot de passe que vous indiquez.</span><span class="sxs-lookup"><span data-stu-id="75f99-119">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="75f99-120">Une fois que SQL Server est en cours d’exécution en tant que conteneur, vous pouvez mettre à jour la base de données en vous connectant via une connexion SQL normale, par exemple SQL Server Management Studio, Visual Studio ou du code C\#.</span><span class="sxs-lookup"><span data-stu-id="75f99-120">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="75f99-121">L’application eShopOnContainers initialise chaque base de données de microservice à l’aide d’exemples de données en les alimentant avec des données au démarrage, comme l’explique la section suivante.</span><span class="sxs-lookup"><span data-stu-id="75f99-121">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="75f99-122">L’exécution de SQL Server en tant que conteneur n’est pas seulement utile à une version de démonstration pour laquelle vous n’avez peut-être pas accès à une instance de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="75f99-122">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="75f99-123">Comme indiqué précédemment, elle est également idéale pour les environnements de développement et de test. Ainsi, vous pouvez facilement exécuter des tests d’intégration à partir d’une image SQL Server propre et de données connues en fournissant de nouveaux exemples de données.</span><span class="sxs-lookup"><span data-stu-id="75f99-123">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="75f99-124">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="75f99-124">Additional resources</span></span>

- <span data-ttu-id="75f99-125">**Exécuter l’image SQL Server Docker sur Linux, Mac ou Windows** </span><span class="sxs-lookup"><span data-stu-id="75f99-125">**Run the SQL Server Docker image on Linux, Mac, or Windows** </span></span>\
    <https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker>

- <span data-ttu-id="75f99-126">**Se connecter à SQL Server et y effectuer des requêtes sur Linux avec sqlcmd** </span><span class="sxs-lookup"><span data-stu-id="75f99-126">**Connect and query SQL Server on Linux with sqlcmd** </span></span>\
    <https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd>

## <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="75f99-127">Alimentation à l’aide de données de test au démarrage de l’application web</span><span class="sxs-lookup"><span data-stu-id="75f99-127">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="75f99-128">Pour ajouter des données à la base de données au démarrage de l’application, vous pouvez ajouter le code suivant à la méthode `Main` de la classe `Program` du projet d’API Web :</span><span class="sxs-lookup"><span data-stu-id="75f99-128">To add data to the database when the application starts up, you can add code like the following to the `Main` method in the `Program` class of the Web API project:</span></span>

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

<span data-ttu-id="75f99-129">Il y a un inconvénient important lors de l’application des migrations et de l’amorçage d’une base de données lors du démarrage du conteneur.</span><span class="sxs-lookup"><span data-stu-id="75f99-129">There's an important caveat when applying migrations and seeding a database during container startup.</span></span> <span data-ttu-id="75f99-130">Étant donné que le serveur de base de données n’est peut-être pas disponible pour une raison quelconque, vous devez gérer les nouvelles tentatives en attendant que le serveur soit disponible.</span><span class="sxs-lookup"><span data-stu-id="75f99-130">Since the database server might not be available for whatever reason, you must handle retries while waiting for the server to be available.</span></span> <span data-ttu-id="75f99-131">Cette logique de nouvelle tentative est gérée par la méthode d’extension `MigrateDbContext()`, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="75f99-131">This retry logic is handled by the `MigrateDbContext()` extension method, as shown in the following code:</span></span>

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

<span data-ttu-id="75f99-132">Le code suivant de la classe personnalisée CatalogContextSeed remplit les données.</span><span class="sxs-lookup"><span data-stu-id="75f99-132">The following code in the custom CatalogContextSeed class populates the data.</span></span>

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

<span data-ttu-id="75f99-133">Quand vous exécutez des tests d’intégration, il est utile de pouvoir générer des données cohérentes avec ces derniers.</span><span class="sxs-lookup"><span data-stu-id="75f99-133">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="75f99-134">Le fait de pouvoir tout créer entièrement, notamment une instance de SQL Server s’exécutant dans un conteneur, est un avantage indéniable pour les environnements de test.</span><span class="sxs-lookup"><span data-stu-id="75f99-134">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

## <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="75f99-135">Comparaison entre une base de données InMemory EF Core et SQL Server s’exécutant en tant que conteneur</span><span class="sxs-lookup"><span data-stu-id="75f99-135">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="75f99-136">Il existe un autre choix intéressant pour exécuter des tests : l’utilisation du fournisseur de base de données InMemory dans Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="75f99-136">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="75f99-137">Vous pouvez spécifier cette configuration dans la méthode ConfigureServices de la classe Startup de votre projet d’API web :</span><span class="sxs-lookup"><span data-stu-id="75f99-137">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

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

<span data-ttu-id="75f99-138">Toutefois, gardez à l’esprit un point important.</span><span class="sxs-lookup"><span data-stu-id="75f99-138">There is an important catch, though.</span></span> <span data-ttu-id="75f99-139">La base de données en mémoire ne prend pas en charge les nombreuses contraintes spécifiques à une base de données particulière.</span><span class="sxs-lookup"><span data-stu-id="75f99-139">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="75f99-140">Par exemple, vous pouvez ajouter un index unique sur une colonne de votre modèle EF Core, et écrire un test relatif à votre base de données en mémoire pour vérifier qu’il est impossible d’ajouter une valeur dupliquée.</span><span class="sxs-lookup"><span data-stu-id="75f99-140">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="75f99-141">Toutefois, quand vous utilisez la base de données en mémoire, vous ne pouvez pas prendre en charge les index uniques d’une colonne.</span><span class="sxs-lookup"><span data-stu-id="75f99-141">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="75f99-142">La base de données en mémoire ne se comporte donc pas exactement comme une véritable base de données SQL Server, elle n’émule pas les contraintes spécifiques aux bases de données.</span><span class="sxs-lookup"><span data-stu-id="75f99-142">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="75f99-143">Même ainsi, une base de données en mémoire est toujours utile pour des tâches de test et de prototypage.</span><span class="sxs-lookup"><span data-stu-id="75f99-143">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="75f99-144">Toutefois, si vous souhaitez créer des tests d’intégration précis qui prennent en compte le comportement d’une implémentation de base de données spécifique, vous devez utiliser une base de données réelle, telle qu’une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="75f99-144">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="75f99-145">Dans ce but, l’exécution de SQL Server dans un conteneur est un excellent choix, qui offre une plus grande précision que le choix du fournisseur de base de données InMemory EF Core.</span><span class="sxs-lookup"><span data-stu-id="75f99-145">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

## <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="75f99-146">Utilisation d’un Cache Service Redis s’exécutant dans un conteneur</span><span class="sxs-lookup"><span data-stu-id="75f99-146">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="75f99-147">Vous pouvez exécuter Redis sur un conteneur, en particulier pour les tâches de développement et de test, ainsi que pour les scénarios de preuve de concept.</span><span class="sxs-lookup"><span data-stu-id="75f99-147">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="75f99-148">Cela s’avère pratique, car toutes vos dépendances peuvent s’exécuter sur des conteneurs, non seulement pour vos machines de développement locales, mais également pour vos environnements de test dans les pipelines d’intégration continue/de livraison continue.</span><span class="sxs-lookup"><span data-stu-id="75f99-148">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="75f99-149">Toutefois, quand vous utilisez Redis en production, il est préférable de rechercher une solution à haute disponibilité telle que Redis Microsoft Azure, qui s’exécute en tant que service PaaS (Platform as a Service).</span><span class="sxs-lookup"><span data-stu-id="75f99-149">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="75f99-150">Dans votre code, il vous suffit de changer les chaînes de connexion.</span><span class="sxs-lookup"><span data-stu-id="75f99-150">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="75f99-151">Redis fournit une image Docker.</span><span class="sxs-lookup"><span data-stu-id="75f99-151">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="75f99-152">Cette image est accessible à partir de Docker Hub à l’URL suivante :</span><span class="sxs-lookup"><span data-stu-id="75f99-152">That image is available from Docker Hub at this URL:</span></span>

<https://hub.docker.com/_/redis/>

<span data-ttu-id="75f99-153">Vous pouvez exécuter directement un conteneur Docker Redis en utilisant la commande Docker CLI suivante à l’invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="75f99-153">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```console
docker run --name some-redis -d redis
```

<span data-ttu-id="75f99-154">L’image Redis inclut expose:6379 (le port utilisé par Redis). Ainsi, la liaison de conteneur standard la rend automatiquement accessible aux conteneurs liés.</span><span class="sxs-lookup"><span data-stu-id="75f99-154">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="75f99-155">Dans eShopOnContainers, le microservice `basket-api` utilise un cache Redims s’exécutant en tant que conteneur.</span><span class="sxs-lookup"><span data-stu-id="75f99-155">In eShopOnContainers, the `basket-api` microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="75f99-156">Ce conteneur de `basketdata` est défini dans le cadre du fichier *docker-compose. yml* à plusieurs conteneurs, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="75f99-156">That `basketdata` container is defined as part of the multi-container *docker-compose.yml* file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basketdata:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="75f99-157">Ce code dans docker-compose. yml définit un conteneur nommé `basketdata` basé sur l’image redims et publiant le port 6379 en interne.</span><span class="sxs-lookup"><span data-stu-id="75f99-157">This code in the docker-compose.yml defines a container named `basketdata` based on the redis image and publishing the port 6379 internally.</span></span> <span data-ttu-id="75f99-158">Cela signifie qu’elle sera uniquement accessible à partir d’autres conteneurs exécutés dans l’hôte de l’ordinateur de la station d’accueil.</span><span class="sxs-lookup"><span data-stu-id="75f99-158">This means that it will only be accessible from other containers running within the Docker host.</span></span>

<span data-ttu-id="75f99-159">Enfin, dans le fichier *docker-compose. override. yml* , le microservice `basket-api` de l’exemple eShopOnContainers définit la chaîne de connexion à utiliser pour ce conteneur ReDim :</span><span class="sxs-lookup"><span data-stu-id="75f99-159">Finally, in the *docker-compose.override.yml* file, the `basket-api` microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket-api:
    environment:
      # Other data ...
      - ConnectionString=basketdata
      - EventBusConnection=rabbitmq
```

<span data-ttu-id="75f99-160">Comme mentionné précédemment, le nom du `basketdata` de microservice est résolu par le DNS du réseau interne de l’ancrage.</span><span class="sxs-lookup"><span data-stu-id="75f99-160">As mentioned before, the name of the microservice `basketdata` is resolved by Docker's internal network DNS.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="75f99-161">[Précédent](multi-container-applications-docker-compose.md)
>[Suivant](integration-event-based-microservice-communications.md)</span><span class="sxs-lookup"><span data-stu-id="75f99-161">[Previous](multi-container-applications-docker-compose.md)
[Next](integration-event-based-microservice-communications.md)</span></span>
