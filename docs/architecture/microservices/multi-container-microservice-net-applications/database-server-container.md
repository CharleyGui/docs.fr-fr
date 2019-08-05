---
title: Utilisation d’un serveur de base de données s’exécutant en tant que conteneur
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Utilisation d’un serveur de base de données s’exécutant en tant que conteneur ? Uniquement pour le développement ! Comprendre pourquoi.
ms.date: 10/02/2018
ms.openlocfilehash: 5fd92a28a09cab041225c4c817a10f5ecfedc038
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676196"
---
# <a name="using-a-database-server-running-as-a-container"></a>Utilisation d’un serveur de base de données s’exécutant en tant que conteneur

Vos bases de données (SQL Server, PostgreSQL, MySQL, etc.) peuvent être stockées sur des serveurs autonomes ordinaires, dans des clusters locaux ou sur des services PaaS dans le cloud comme Azure SQL DB. Toutefois, pour les environnements de développement et de test, il est pratique de pouvoir exécuter des bases de données en tant que conteneurs. En effet, vous n’avez aucune dépendance externe, et la simple exécution de la commande `docker-compose up` démarre l’ensemble de l’application. Le fait de disposer de ces bases de données en tant que conteneurs est également idéal pour les tests d’intégration, car la base de données démarre dans le conteneur et contient toujours les mêmes exemples de données. Les tests sont donc plus prévisibles.

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>Exécution de SQL Server en tant que conteneur avec une base de données liée à un microservice

Dans eShopOnContainers, un conteneur nommé sql.data est défini dans le fichier [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) et exécute SQL Server pour Linux avec toutes les bases de données SQL Server nécessaires aux microservices. (Vous pouvez également avoir un conteneur SQL Server pour chaque base de données, mais cela nécessite l’affectation d’une plus grande quantité de mémoire à Docker.) Le point important des microservices est que chacun d’eux a ses données connexes, et donc sa base de données SQL associée. Mais les bases de données peuvent se trouver n’importe où.

Le conteneur SQL Server de l’exemple d’application est configuré avec le code YAML suivant dans le fichier docker-compose.yml. Celui-ci s’exécute quand vous exécutez `docker-compose up`. Notez que le code YAML a regroupé les informations de configuration du fichier docker-compose.yml générique et du fichier docker-compose.override.yml. (En règle générale, vous devez séparer les paramètres d’environnement des informations de base ou statiques liées à l’image SQL Server.)

```yml
  sql.data:
    image: microsoft/mssql-server-linux:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

De même, au lieu d’utiliser `docker-compose`, la commande `docker run` suivante peut exécuter ce conteneur :

```
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d microsoft/mssql-server-linux:2017-latest
```

Toutefois, si vous déployez une application à plusieurs conteneurs comme eShopOnContainers, il est plus pratique d’utiliser la commande `docker-compose up` afin de déployer tous les conteneurs nécessaires pour l’application.

Quand vous démarrez ce conteneur SQL Server pour la première fois, il initialise SQL Server à l’aide du mot de passe que vous indiquez. Une fois que SQL Server est en cours d’exécution en tant que conteneur, vous pouvez mettre à jour la base de données en vous connectant via une connexion SQL normale, par exemple SQL Server Management Studio, Visual Studio ou du code C\#.

L’application eShopOnContainers initialise chaque base de données de microservice à l’aide d’exemples de données en les alimentant avec des données au démarrage, comme l’explique la section suivante.

L’exécution de SQL Server en tant que conteneur n’est pas seulement utile à une version de démonstration pour laquelle vous n’avez peut-être pas accès à une instance de SQL Server. Comme indiqué précédemment, elle est également idéale pour les environnements de développement et de test. Ainsi, vous pouvez facilement exécuter des tests d’intégration à partir d’une image SQL Server propre et de données connues en fournissant de nouveaux exemples de données.

#### <a name="additional-resources"></a>Ressources supplémentaires

- **Exécuter l’image SQL Server Docker sur Linux, Mac ou Windows** \
    [https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker](/sql/linux/sql-server-linux-setup-docker)

- **Se connecter à SQL Server et y effectuer des requêtes sur Linux avec sqlcmd** \
    [https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd](/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a>Alimentation à l’aide de données de test au démarrage de l’application web

Pour ajouter des données à la base de données au démarrage de l’application, ajoutez du code semblable à ce qui suit à la méthode Configure de la classe Startup du projet d’API web :

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

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>Comparaison entre une base de données InMemory EF Core et SQL Server s’exécutant en tant que conteneur

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

### <a name="using-a-redis-cache-service-running-in-a-container"></a>Utilisation d’un Cache Service Redis s’exécutant dans un conteneur

Vous pouvez exécuter Redis sur un conteneur, en particulier pour les tâches de développement et de test, ainsi que pour les scénarios de preuve de concept. Cela s’avère pratique, car toutes vos dépendances peuvent s’exécuter sur des conteneurs, non seulement pour vos machines de développement locales, mais également pour vos environnements de test dans les pipelines d’intégration continue/de livraison continue.

Toutefois, quand vous utilisez Redis en production, il est préférable de rechercher une solution à haute disponibilité telle que Redis Microsoft Azure, qui s’exécute en tant que service PaaS (Platform as a Service). Dans votre code, il vous suffit de changer les chaînes de connexion.

Redis fournit une image Docker. Cette image est accessible à partir de Docker Hub à l’URL suivante :

<https://hub.docker.com/\_/redis/>

Vous pouvez exécuter directement un conteneur Docker Redis en utilisant la commande Docker CLI suivante à l’invite de commandes :

```
  docker run --name some-redis -d redis
```

L’image Redis inclut expose:6379 (le port utilisé par Redis). Ainsi, la liaison de conteneur standard la rend automatiquement accessible aux conteneurs liés.

Dans eShopOnContainers, le microservice basket.api utilise un cache Redis qui s’exécute en tant que conteneur. Le conteneur basket.data est défini dans le cadre du fichier docker-compose.yml à plusieurs conteneurs, comme le montre l’exemple suivant :

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

Ce code du fichier docker-compose.yml définit un conteneur nommé basket.data basé sur l’image redis et qui publie sur le port 6379 de manière interne. Cela signifie qu’il est accessible uniquement aux autres conteneurs qui s’exécutent dans l’hôte Docker.

Enfin, dans le fichier docker-compose.override.yml, le microservice basket.api de l’exemple eShopOnContainers définit la chaîne de connexion à utiliser pour le conteneur Redis :

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```

Comme mentionné précédemment, le nom de microservice « basket.data » est résolu par le DNS de réseau interne de Docker.

>[!div class="step-by-step"]
>[Précédent](multi-container-applications-docker-compose.md)
>[Suivant](integration-event-based-microservice-communications.md)
