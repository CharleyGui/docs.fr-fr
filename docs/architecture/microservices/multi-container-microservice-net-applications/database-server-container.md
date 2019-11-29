---
title: Utilisation d’un serveur de base de données s’exécutant en tant que conteneur
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Utilisation d’un serveur de base de données s’exécutant en tant que conteneur ? Uniquement pour le développement ! Comprendre pourquoi.
ms.date: 10/02/2018
ms.openlocfilehash: 371d622dc39681edb0b52e723faccbf611b7797c
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568432"
---
# <a name="using-a-database-server-running-as-a-container"></a><span data-ttu-id="8e5b3-104">Utilisation d’un serveur de base de données s’exécutant en tant que conteneur</span><span class="sxs-lookup"><span data-stu-id="8e5b3-104">Using a database server running as a container</span></span>

<span data-ttu-id="8e5b3-105">Vos bases de données (SQL Server, PostgreSQL, MySQL, etc.) peuvent être stockées sur des serveurs autonomes ordinaires, dans des clusters locaux ou sur des services PaaS dans le cloud comme Azure SQL DB.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="8e5b3-106">Toutefois, pour les environnements de développement et de test, il est pratique de pouvoir exécuter des bases de données en tant que conteneurs. En effet, vous n’avez aucune dépendance externe, et la simple exécution de la commande `docker-compose up` démarre l’ensemble de l’application.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-106">However, for development and test environments, having your databases running as containers is convenient, because you do not have any external dependency and simply running the `docker-compose up` command starts the whole application.</span></span> <span data-ttu-id="8e5b3-107">Le fait de disposer de ces bases de données en tant que conteneurs est également idéal pour les tests d’intégration, car la base de données démarre dans le conteneur et contient toujours les mêmes exemples de données. Les tests sont donc plus prévisibles.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="8e5b3-108">Exécution de SQL Server en tant que conteneur avec une base de données liée à un microservice</span><span class="sxs-lookup"><span data-stu-id="8e5b3-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="8e5b3-109">Dans eShopOnContainers, un conteneur nommé sql.data est défini dans le fichier [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) et exécute SQL Server pour Linux avec toutes les bases de données SQL Server nécessaires aux microservices.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-109">In eShopOnContainers, there is a container named sql.data defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file that runs SQL Server for Linux with all the SQL Server databases needed for the microservices.</span></span> <span data-ttu-id="8e5b3-110">(Vous pouvez également avoir un conteneur SQL Server pour chaque base de données, mais cela nécessiterait plus de mémoire allouée à l’ancrage.) Le point important dans les microservices est que chaque microservice possède ses données associées, par conséquent la base de données SQL associée dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-110">(You could also have one SQL Server container for each database, but that would require more memory assigned to Docker.) The important point in microservices is that each microservice owns its related data, therefore its related SQL database in this case.</span></span> <span data-ttu-id="8e5b3-111">Mais les bases de données peuvent se trouver n’importe où.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-111">But the databases can be anywhere.</span></span>

<span data-ttu-id="8e5b3-112">Le conteneur SQL Server de l’exemple d’application est configuré avec le code YAML suivant dans le fichier docker-compose.yml. Celui-ci s’exécute quand vous exécutez `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-112">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run `docker-compose up`.</span></span> <span data-ttu-id="8e5b3-113">Notez que le code YAML a regroupé les informations de configuration du fichier docker-compose.yml générique et du fichier docker-compose.override.yml.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-113">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="8e5b3-114">(En règle générale, vous devez séparer les paramètres d’environnement des informations de base ou statiques liées à l’image SQL Server.)</span><span class="sxs-lookup"><span data-stu-id="8e5b3-114">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
  sql.data:
    image: microsoft/mssql-server-linux:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

<span data-ttu-id="8e5b3-115">De même, au lieu d’utiliser `docker-compose`, la commande `docker run` suivante peut exécuter ce conteneur :</span><span class="sxs-lookup"><span data-stu-id="8e5b3-115">In a similar way, instead of using `docker-compose`, the following `docker run` command can run that container:</span></span>

```console
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d microsoft/mssql-server-linux:2017-latest
```

<span data-ttu-id="8e5b3-116">Toutefois, si vous déployez une application à plusieurs conteneurs comme eShopOnContainers, il est plus pratique d’utiliser la commande `docker-compose up` afin de déployer tous les conteneurs nécessaires pour l’application.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-116">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the `docker-compose up` command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="8e5b3-117">Quand vous démarrez ce conteneur SQL Server pour la première fois, il initialise SQL Server à l’aide du mot de passe que vous indiquez.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-117">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="8e5b3-118">Une fois que SQL Server est en cours d’exécution en tant que conteneur, vous pouvez mettre à jour la base de données en vous connectant via une connexion SQL normale, par exemple SQL Server Management Studio, Visual Studio ou du code C\#.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-118">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="8e5b3-119">L’application eShopOnContainers initialise chaque base de données de microservice à l’aide d’exemples de données en les alimentant avec des données au démarrage, comme l’explique la section suivante.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-119">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="8e5b3-120">L’exécution de SQL Server en tant que conteneur n’est pas seulement utile à une version de démonstration pour laquelle vous n’avez peut-être pas accès à une instance de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-120">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="8e5b3-121">Comme indiqué précédemment, elle est également idéale pour les environnements de développement et de test. Ainsi, vous pouvez facilement exécuter des tests d’intégration à partir d’une image SQL Server propre et de données connues en fournissant de nouveaux exemples de données.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-121">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="8e5b3-122">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="8e5b3-122">Additional resources</span></span>

- <span data-ttu-id="8e5b3-123">**Exécuter l’image SQL Server Docker sur Linux, Mac ou Windows** </span><span class="sxs-lookup"><span data-stu-id="8e5b3-123">**Run the SQL Server Docker image on Linux, Mac, or Windows** </span></span>\
    [https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker](/sql/linux/sql-server-linux-setup-docker)

- <span data-ttu-id="8e5b3-124">**Se connecter à SQL Server et y effectuer des requêtes sur Linux avec sqlcmd** </span><span class="sxs-lookup"><span data-stu-id="8e5b3-124">**Connect and query SQL Server on Linux with sqlcmd** </span></span>\
    [https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd](/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="8e5b3-125">Alimentation à l’aide de données de test au démarrage de l’application web</span><span class="sxs-lookup"><span data-stu-id="8e5b3-125">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="8e5b3-126">Pour ajouter des données à la base de données au démarrage de l’application, ajoutez du code semblable à ce qui suit à la méthode Configure de la classe Startup du projet d’API web :</span><span class="sxs-lookup"><span data-stu-id="8e5b3-126">To add data to the database when the application starts up, you can add code like the following to the Configure method in the Startup class of the Web API project:</span></span>

```csharp
public class Startup
{
    // Other Startup code...
    public void Configure(IApplicationBuilder app,
        IHostingEnvironment env,
        ILoggerFactory loggerFactory)
    {
        // Other Configure code...
        // Seed data through our custom class
        CatalogContextSeed.SeedAsync(app)
            .Wait();
        // Other Configure code...
    }
}
```

<span data-ttu-id="8e5b3-127">Le code suivant de la classe personnalisée CatalogContextSeed remplit les données.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-127">The following code in the custom CatalogContextSeed class populates the data.</span></span>

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

<span data-ttu-id="8e5b3-128">Quand vous exécutez des tests d’intégration, il est utile de pouvoir générer des données cohérentes avec ces derniers.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-128">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="8e5b3-129">Le fait de pouvoir tout créer entièrement, notamment une instance de SQL Server s’exécutant dans un conteneur, est un avantage indéniable pour les environnements de test.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-129">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="8e5b3-130">Comparaison entre une base de données InMemory EF Core et SQL Server s’exécutant en tant que conteneur</span><span class="sxs-lookup"><span data-stu-id="8e5b3-130">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="8e5b3-131">Il existe un autre choix intéressant pour exécuter des tests : l’utilisation du fournisseur de base de données InMemory dans Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-131">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="8e5b3-132">Vous pouvez spécifier cette configuration dans la méthode ConfigureServices de la classe Startup de votre projet d’API web :</span><span class="sxs-lookup"><span data-stu-id="8e5b3-132">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

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

<span data-ttu-id="8e5b3-133">Toutefois, gardez à l’esprit un point important.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-133">There is an important catch, though.</span></span> <span data-ttu-id="8e5b3-134">La base de données en mémoire ne prend pas en charge les nombreuses contraintes spécifiques à une base de données particulière.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-134">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="8e5b3-135">Par exemple, vous pouvez ajouter un index unique sur une colonne de votre modèle EF Core, et écrire un test relatif à votre base de données en mémoire pour vérifier qu’il est impossible d’ajouter une valeur dupliquée.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-135">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="8e5b3-136">Toutefois, quand vous utilisez la base de données en mémoire, vous ne pouvez pas prendre en charge les index uniques d’une colonne.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-136">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="8e5b3-137">La base de données en mémoire ne se comporte donc pas exactement comme une véritable base de données SQL Server, elle n’émule pas les contraintes spécifiques aux bases de données.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-137">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="8e5b3-138">Même ainsi, une base de données en mémoire est toujours utile pour des tâches de test et de prototypage.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-138">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="8e5b3-139">Toutefois, si vous souhaitez créer des tests d’intégration précis qui prennent en compte le comportement d’une implémentation de base de données spécifique, vous devez utiliser une base de données réelle, telle qu’une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-139">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="8e5b3-140">Dans ce but, l’exécution de SQL Server dans un conteneur est un excellent choix, qui offre une plus grande précision que le choix du fournisseur de base de données InMemory EF Core.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-140">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

### <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="8e5b3-141">Utilisation d’un Cache Service Redis s’exécutant dans un conteneur</span><span class="sxs-lookup"><span data-stu-id="8e5b3-141">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="8e5b3-142">Vous pouvez exécuter Redis sur un conteneur, en particulier pour les tâches de développement et de test, ainsi que pour les scénarios de preuve de concept.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-142">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="8e5b3-143">Cela s’avère pratique, car toutes vos dépendances peuvent s’exécuter sur des conteneurs, non seulement pour vos machines de développement locales, mais également pour vos environnements de test dans les pipelines d’intégration continue/de livraison continue.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-143">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="8e5b3-144">Toutefois, quand vous utilisez Redis en production, il est préférable de rechercher une solution à haute disponibilité telle que Redis Microsoft Azure, qui s’exécute en tant que service PaaS (Platform as a Service).</span><span class="sxs-lookup"><span data-stu-id="8e5b3-144">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="8e5b3-145">Dans votre code, il vous suffit de changer les chaînes de connexion.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-145">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="8e5b3-146">Redis fournit une image Docker.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-146">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="8e5b3-147">Cette image est accessible à partir de Docker Hub à l’URL suivante :</span><span class="sxs-lookup"><span data-stu-id="8e5b3-147">That image is available from Docker Hub at this URL:</span></span>

<https://hub.docker.com/_/redis/>

<span data-ttu-id="8e5b3-148">Vous pouvez exécuter directement un conteneur Docker Redis en utilisant la commande Docker CLI suivante à l’invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="8e5b3-148">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```console
docker run --name some-redis -d redis
```

<span data-ttu-id="8e5b3-149">L’image Redis inclut expose:6379 (le port utilisé par Redis). Ainsi, la liaison de conteneur standard la rend automatiquement accessible aux conteneurs liés.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-149">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="8e5b3-150">Dans eShopOnContainers, le microservice basket.api utilise un cache Redis qui s’exécute en tant que conteneur.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-150">In eShopOnContainers, the basket.api microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="8e5b3-151">Le conteneur basket.data est défini dans le cadre du fichier docker-compose.yml à plusieurs conteneurs, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="8e5b3-151">That basket.data container is defined as part of the multi-container docker-compose.yml file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="8e5b3-152">Ce code du fichier docker-compose.yml définit un conteneur nommé basket.data basé sur l’image redis et qui publie sur le port 6379 de manière interne. Cela signifie qu’il est accessible uniquement aux autres conteneurs qui s’exécutent dans l’hôte Docker.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-152">This code in the docker-compose.yml defines a container named basket.data based on the redis image and publishing the port 6379 internally, meaning that it will be accessible only from other containers running within the Docker host.</span></span>

<span data-ttu-id="8e5b3-153">Enfin, dans le fichier docker-compose.override.yml, le microservice basket.api de l’exemple eShopOnContainers définit la chaîne de connexion à utiliser pour le conteneur Redis :</span><span class="sxs-lookup"><span data-stu-id="8e5b3-153">Finally, in the docker-compose.override.yml file, the basket.api microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```

<span data-ttu-id="8e5b3-154">Comme mentionné précédemment, le nom de microservice « basket.data » est résolu par le DNS de réseau interne de Docker.</span><span class="sxs-lookup"><span data-stu-id="8e5b3-154">As mentioned before, the name of the microservice "basket.data" is resolved by docker's internal network DNS.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8e5b3-155">[Précédent](multi-container-applications-docker-compose.md)
>[Suivant](integration-event-based-microservice-communications.md)</span><span class="sxs-lookup"><span data-stu-id="8e5b3-155">[Previous](multi-container-applications-docker-compose.md)
[Next](integration-event-based-microservice-communications.md)</span></span>
