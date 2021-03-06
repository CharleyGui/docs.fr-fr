---
title: Implémentation de passerelles d’API avec Ocelot
description: Découvrez comment implémenter des passerelles d’API avec Ocelot et comment utiliser Ocelot dans un environnement basé sur un conteneur.
ms.date: 03/02/2020
ms.openlocfilehash: 5da8533eff394b587d123970742727484a7236ad
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678119"
---
# <a name="implement-api-gateways-with-ocelot"></a>Implémenter des passerelles API avec Ocelot

> [!IMPORTANT]
> L’application de microservice de référence [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) utilise actuellement les fonctionnalités fournies par [Envoy](https://www.envoyproxy.io/) pour implémenter la passerelle d’API au lieu des [Ocelot](https://github.com/ThreeMammals/Ocelot)référencés précédemment.
> Nous avons fait ce choix de conception en raison de la prise en charge intégrée du protocole WebSocket par Envoy, requise par les nouvelles communications gRPC entre les services implémentées dans eShopOnContainers.
> Toutefois, nous avons conservé cette section dans le guide pour vous permettre de considérer Ocelot comme une passerelle d’API simple, efficace et légère, adaptée aux scénarios de production.
> En outre, la dernière version de Ocelot contient une modification avec rupture sur son schéma JSON. Envisagez d’utiliser Ocelot < v 16.0.0 ou les itinéraires clés au lieu de rediriger.

## <a name="architect-and-design-your-api-gateways"></a>Structurer et concevoir les passerelles d’API

Le diagramme d’architecture suivant montre comment les passerelles d’API ont été implémentées avec Ocelot dans eShopOnContainers.

![Diagramme montrant l’architecture eShopOnContainers.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture.png)

**Figure 6-28.** Architecture d’eShopOnContainers avec passerelles d’API

Ce diagramme montre comment l’application entière est déployée sur un hôte ou un PC de développement unique, avec « Docker pour Windows » ou « docker pour Mac ». Toutefois, le déploiement dans n’importe quel orchestrateur est similaire, mais tout conteneur du diagramme peut être mis à l’échelle dans l’orchestrateur.

De plus, les ressources de l’infrastructure telles que les bases de données, le cache et les répartiteurs de messages doivent être déchargées à partir de l’orchestrateur et déployées dans des systèmes hautement disponibles pour l’infrastructure, tels qu’Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus ou toute solution de clustering à haute disponibilité en local.

Comme vous pouvez le constater dans le diagramme, l’utilisation de plusieurs passerelles d’API permet à plusieurs équipes de développement d’être autonomes (dans ce cas, les fonctionnalités de marketing et les fonctionnalités d’achat) lors du développement et du déploiement de leurs microservices, ainsi que de leurs passerelles d’API associées.

Si vous aviez une passerelle d’API monolithique unique, cela signifierait qu’un point unique serait mis à jour par plusieurs équipes de développement, ce qui associerait tous les microservices à une seule partie de l’application.

En allant beaucoup plus loin dans la conception, parfois, une passerelle d’API de granularité fine peut également être limitée à un seul microservice métier selon l’architecture choisie. Le fait que les limites de la passerelle d’API soient dictées par l’entreprise ou le domaine vous aidera à obtenir une meilleure conception.

Par exemple, une granularité fine au niveau de la passerelle d’API peut être particulièrement utile pour les applications d’interface utilisateur composites plus avancées qui sont basées sur des microservices, car le concept d’une passerelle d’API à granularité fine est similaire à un service de composition d’interface utilisateur.

Nous approfondissons davantage dans la section précédente, [Création d’une interface utilisateur composite basée sur des microservices](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).

En guise de point de vue clé, pour de nombreuses applications de taille moyenne ou grande, l’utilisation d’un produit de passerelle d’API personnalisée est généralement une bonne approche, mais pas en tant qu’agrégateur monolithique unique ou passerelle d’API personnalisée centrale unique, sauf si cette passerelle d’API autorise plusieurs zones de configuration indépendantes pour les différentes équipes de développement créant des microservices autonomes.

### <a name="sample-microservicescontainers-to-reroute-through-the-api-gateways"></a>Exemples de microservices/conteneurs à réacheminer via les passerelles d’API

Par exemple, eShopOnContainers a environ six types de microservices internes qui doivent être publiés par le biais des passerelles API, comme illustré à la figure suivante.

![Capture d’écran du dossier services montrant ses sous-dossiers.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-microservice-folders.png)

**Figure 6-29.** Dossiers de microservices dans une solution eShopOnContainers dans Visual Studio

En ce qui concerne le service Identity, dans sa conception, il est tenu à l’écart du routage de passerelle API, car il est le seul problème transversal du système, même si Ocelot permet également de l’inclure dans le cadre des listes de reroutages.

Tous ces services sont actuellement implémentés en tant que services d’API web ASP.NET Core, comme vous pouvez le voir dans le code. Nous allons nous concentrer sur l’un des microservices, comme le code de microservice de catalogue.

![Capture d’écran de Explorateur de solutions montrant le contenu du projet Catalog. API.](./media/implement-api-gateways-with-ocelot/catalog-api-microservice-folders.png)

**Figure 6-30.** Exemple de microservice d’API web (microservice Catalog)

Vous pouvez voir que le microservice Catalog est un projet d’API web ASP.NET Core standard avec plusieurs contrôleurs et méthodes, comme dans le code suivant.

```csharp
[HttpGet]
[Route("items/{id:int}")]
[ProducesResponseType((int)HttpStatusCode.BadRequest)]
[ProducesResponseType((int)HttpStatusCode.NotFound)]
[ProducesResponseType(typeof(CatalogItem),(int)HttpStatusCode.OK)]
public async Task<IActionResult> GetItemById(int id)
{
    if (id <= 0)
    {
        return BadRequest();
    }
    var item = await _catalogContext.CatalogItems.
                                          SingleOrDefaultAsync(ci => ci.Id == id);
    //…

    if (item != null)
    {
        return Ok(item);
    }
    return NotFound();
}
```

La requête HTTP finit par exécuter ce type de code C# qui accède à la base de données du microservice ainsi que toute autre action supplémentaire nécessaire.

En ce qui concerne l’URL du microservice, lorsque les conteneurs sont déployés sur votre PC de développement local (hôte de l’ancrage local), chaque conteneur de microservice possède toujours un port interne (généralement le port 80) spécifié dans son fichier dockerfile, comme dans l’fichier dockerfile suivant :

```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
```

Le port 80 indiqué dans le code est interne à l’hôte Docker et n’est donc pas accessible par les applications clientes.

Les applications clientes peuvent uniquement accéder aux ports externes (le cas échéant) publiés lors du déploiement avec `docker-compose`.

Ces ports externes ne doivent pas être publiés lors du déploiement dans un environnement de production. Pour cette raison spécifique, pourquoi vous souhaitez utiliser la passerelle d’API pour éviter la communication directe entre les applications clientes et les microservices.

Toutefois, lors du développement, vous souhaitez accéder directement au microservice/conteneur et l’exécuter via Swagger. C’est pourquoi, dans eShopOnContainers, les ports externes sont toujours spécifiés même s’ils ne sont pas utilisés par la passerelle d’API ou les applications clientes.

Voici un exemple de `docker-compose.override.yml` fichier pour le microservice de catalogue :

```yml
catalog-api:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:80
    - ConnectionString=YOUR_VALUE
    - ... Other Environment Variables
  ports:
    - "5101:80"   # Important: In a production environment you should remove the external port (5101) kept here for microservice debugging purposes.
                  # The API Gateway redirects and access through the internal port (80).
```

Vous pouvez voir dans la configuration docker-compose.override.yml que le port interne pour le conteneur Catalog est le port 80, mais que le port 5101 est utilisé pour l’accès externe. Mais ce port ne doit pas être utilisé par l’application lors de l’utilisation d’une passerelle d’API, mais uniquement pour déboguer, exécuter et tester uniquement le microservice de catalogue.

Normalement, vous ne devez pas déployer avec l’amarrage-compose dans un environnement de production, car l’environnement de déploiement de production approprié pour les microservices est un orchestrateur comme Kubernetes ou Service Fabric. Lors du déploiement sur ces environnements, vous utilisez des fichiers de configuration différents dans lesquels vous ne publiez pas directement de port externe pour les microservices, mais vous utilisez toujours le proxy inverse de la passerelle d’API.

Exécutez le microservice de catalogue dans votre hôte d’ancrage local. Exécutez la solution eShopOnContainers complète à partir de Visual Studio (elle exécute tous les services dans les fichiers dockr-compose) ou démarrez le microservice de catalogue avec la commande dockr-compose suivante dans CMD ou PowerShell positionnée au niveau du dossier où les `docker-compose.yml` et `docker-compose.override.yml` sont placés.

```console
docker-compose run --service-ports catalog-api
```

Cette commande exécute uniquement le conteneur de service Catalog-API, ainsi que les dépendances spécifiées dans docker-compose. yml. Dans ce cas, le conteneur SQL Server et le conteneur RabbitMQ.

Ensuite, vous pouvez accéder directement au microservice de catalogue et voir ses méthodes par le biais de l’interface utilisateur Swagger qui accède directement à ce port « externe », dans ce cas `http://localhost:5101/swagger` :

![Capture d’écran de l’interface utilisateur Swagger montrant l’API REST Catalog. API.](./media/implement-api-gateways-with-ocelot/test-catalog-microservice.png)

**Figure 6-31.** Test du microservice Catalog avec son interface utilisateur Swagger

À ce stade, vous pouvez définir un point d’arrêt dans le code C# dans Visual Studio, tester le microservice avec les méthodes exposées dans l’interface utilisateur Swagger et enfin tout nettoyer avec la commande `docker-compose down`.

Toutefois, la communication à accès direct au microservice, dans le cas présent via le port externe 5101, est précisément ce que vous voulez éviter dans votre application. Et vous pouvez l’éviter en définissant le niveau supplémentaire d’indirection de la passerelle d’API (dans ce cas, Ocelot). De cette façon, l’application cliente n’accède pas directement au microservice.

## <a name="implementing-your-api-gateways-with-ocelot"></a>Implémentation des passerelles d’API avec Ocelot

Ocelot est essentiellement un ensemble de middlewares que vous pouvez appliquer dans un ordre spécifique.

Ocelot est conçu pour fonctionner uniquement avec ASP.NET Core. La dernière version du package cible `.NETCoreApp 3.1` et, par conséquent, n’est pas adaptée aux applications .NET Framework.

Installez Ocelot et ses dépendances dans votre projet ASP.NET Core avec le [package NuGet d’Ocelot](https://www.nuget.org/packages/Ocelot/), à partir de Visual Studio.

```powershell
Install-Package Ocelot
```

Dans eShopOnContainers, son implémentation de passerelle d’API est un simple projet WebHost ASP.NET Core, et l’intergiciel (middleware) de Ocelot gère toutes les fonctionnalités de la passerelle API, comme illustré dans l’image suivante :

![Capture d’écran de Explorateur de solutions montrant le projet de passerelle d’API ocelot.](./media/implement-api-gateways-with-ocelot/ocelotapigw-base-project.png)

**Figure 6-32.** Projet de base OcelotApiGw dans eShopOnContainers

Ce projet ASP.NET Core WebHost est généré avec deux fichiers simples :  `Program.cs` et `Startup.cs` .

Le fichier Program.cs doit simplement créer et configurer la fonction BuildWebHost ASP.NET Core standard.

```csharp
namespace OcelotApiGw
{
    public class Program
    {
        public static void Main(string[] args)
        {
            BuildWebHost(args).Run();
        }

        public static IWebHost BuildWebHost(string[] args)
        {
            var builder = WebHost.CreateDefaultBuilder(args);

            builder.ConfigureServices(s => s.AddSingleton(builder))
                    .ConfigureAppConfiguration(
                          ic => ic.AddJsonFile(Path.Combine("configuration",
                                                            "configuration.json")))
                    .UseStartup<Startup>();
            var host = builder.Build();
            return host;
        }
    }
}
```

Le point important ici pour Ocelot est le fichier `configuration.json` que vous devez fournir au générateur via la méthode `AddJsonFile()`. Ce fichier `configuration.json` vous permet de spécifier tous les réacheminements des passerelles d’API, ce qui signifie les points de terminaison externes avec des ports spécifiques et les points de terminaison internes corrélés, généralement à l’aide de ports différents.

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

La configuration comprend deux sections. Tableau de reroutements et d’un GlobalConfiguration. Les reroutages sont les objets qui indiquent à Ocelot comment traiter une requête amont. La configuration globale autorise les remplacements de paramètres spécifiques de reroutage. Cela est utile si vous ne souhaitez pas gérer un grand nombre de paramètres spécifiques de reroutage.

Voici un exemple simplifié de [Rerouter le fichier de configuration](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) à partir de l’une des passerelles d’API à partir de eShopOnContainers.

```json
{
  "ReRoutes": [
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "catalog-api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/c/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ]
    },
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }

  ],
    "GlobalConfiguration": {
      "RequestIdKey": "OcRequestId",
      "AdministrationPath": "/administration"
    }
  }
```

La fonctionnalité principale d’une passerelle d’API Ocelot consiste à prendre les requêtes HTTP entrantes et à les transférer vers un service en aval, actuellement sous la forme d’une autre requête HTTP. Ocelot décrit le routage d’une demande vers une autre en tant que reroutage.

Par exemple, nous allons nous concentrer sur l’un des reroutages dans le configuration.jsà partir de ci-dessus, la configuration pour le microservice de panier.

```json
{
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
}
```

Les éléments DownstreamPathTemplate, Scheme et DownstreamHostAndPorts composent l’URL de microservice interne vers laquelle cette demande sera transmise.

Le port est le port interne utilisé par le service. Lorsque vous utilisez des conteneurs, le port spécifié dans son fichier Dockerfile.

L’élément `Host` est un nom de service qui dépend de la résolution de noms de service que vous utilisez. Lors de l’utilisation de docker-compose, les noms des services sont fournis par l’hôte Docker, lequel utilise les noms de service fournis dans les fichiers docker-compose. Si vous utilisez un orchestrateur comme Kubernetes ou Service Fabric, ce nom doit être résolu par la résolution de noms ou DNS fournie par chaque orchestrateur.

DownstreamHostAndPorts est un tableau qui contient l’hôte et le port de tous les services en aval vers lesquels vous souhaitez transférer des demandes. En règle générale, cette configuration ne contient qu’une seule entrée, mais vous pouvez parfois souhaiter équilibrer la charge des demandes vers vos services en aval et Ocelot vous permet d’ajouter plusieurs entrées, puis de sélectionner un équilibreur de charge. Toutefois, si vous utilisez Azure et un orchestrateur quelconque, il est probablement plus judicieux d’équilibrer la charge avec l’infrastructure d’orchestrateur et le cloud.

UpstreamPathTemplate est l’URL dont Ocelot se servira pour identifier l’URL DownstreamPathTemplate à utiliser pour une demande donnée à partir du client. Enfin, la méthode UpstreamHttpMethod est utilisée pour qu’Ocelot puisse faire la distinction entre les différentes demandes (GET, POST, PUT) sur la même URL.

À ce stade, vous pourriez avoir une seule passerelle d’API Ocelot (WebHost ASP.NET Core) utilisant un ou [plusieurs fichiers configuration.json fusionnés](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) ou vous pouvez également stocker la [configuration dans un magasin Consul KV](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).

Toutefois, comme indiqué dans la section d’architecture et de conception, si vous voulez vraiment avoir des microservices autonomes, il peut être préférable de diviser cette passerelle d’API monolithique en plusieurs passerelles d’API et/ou BFF (backend for frontend). À cet effet, voyons comment implémenter cette approche avec les conteneurs de l’ancrage.

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a>Utilisation d’une image de conteneur Docker individuelle pour exécuter différents types de conteneur de passerelles d’API/BFF

Dans eShopOnContainers, nous utilisons une seule image de conteneur d’ancrage avec la passerelle d’API Ocelot, mais, au moment de l’exécution, nous créons différents services/conteneurs pour chaque type d’API-passerelle/BFF en fournissant une configuration.jsdifférente sur le fichier, en utilisant un volume de station d’accueil pour accéder à un dossier PC différent pour chaque service.

![Diagramme d’une image de station d’accueil de passerelle Ocelot unique pour toutes les passerelles d’API.](./media/implement-api-gateways-with-ocelot/reusing-single-ocelot-docker-image.png)

**Figure 6-33.** Réutilisation d’une image Docker d’Ocelot unique sur plusieurs types de passerelle d’API

Dans eShopOnContainers, l' « image de la passerelle d’API Ocelot générique » est créée avec le projet nommé « OcelotApiGw » et le nom d’image « eShop/OcelotApiGw » spécifié dans le fichier docker-compose. yml. Ensuite, lors du déploiement sur Docker, quatre conteneurs de passerelle d’API sont créés à partir de cette même image Docker, comme indiqué dans l’extrait suivant du fichier docker-compose.yml.

```yml
  mobileshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  mobilemarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webmarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile
```

De plus, comme vous pouvez le voir dans le fichier docker-compose.override.yml suivant, la seule différence entre ces conteneurs de passerelle API est le fichier de configuration Ocelot, qui est différent pour chaque conteneur de service et qui est spécifié au moment de l’exécution par le biais d’un volume Docker.

```yml
mobileshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5200:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Shopping/apigw:/app/configuration

mobilemarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5201:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Marketing/apigw:/app/configuration

webshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5202:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Shopping/apigw:/app/configuration

webmarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5203:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Marketing/apigw:/app/configuration
```

En raison de ce code précédent et comme l’indique l’Explorateur Visual Studio ci-dessous, le seul fichier nécessaire pour définir chaque passerelle d’API d’entreprise/BFF spécifique est un fichier configuration.json, étant donné que les quatre passerelles d’API reposent sur la même image Docker.

![Capture d’écran montrant toutes les passerelles d’API avec configuration.jssur les fichiers.](./media/implement-api-gateways-with-ocelot/ocelot-configuration-files.png)

**Figure 6-34.** Le seul fichier nécessaire pour définir chaque passerelle d’API / BFF avec Ocelot est un fichier de configuration

En divisant la passerelle d’API en plusieurs passerelles d’API, différentes équipes de développement portant sur différents sous-ensembles de microservices peuvent gérer leurs propres passerelles d’API à l’aide de fichiers de configuration Ocelot indépendants. De plus, en même temps, elles peuvent réutiliser la même image Docker d’Ocelot.

Maintenant, si vous exécutez eShopOnContainers avec les passerelles d’API (incluses par défaut dans Visual Studio lors de l’ouverture de la solution eShopOnContainers-ServicesAndWebApps. sln ou si vous exécutez « docker-compose up »), les exemples d’itinéraires suivants seront exécutés.

Par exemple, lors de la visite de l’URL en amont `http://localhost:5202/api/v1/c/catalog/items/2/` prise en charge par la passerelle API webshoppingapigw, vous obtenez le même résultat à partir de l’URL interne en aval `http://catalog-api/api/v1/2` dans l’hôte Docker, comme dans le navigateur suivant.

![Capture d’écran d’un navigateur montrant une réponse passant par la passerelle d’API.](./media/implement-api-gateways-with-ocelot/access-microservice-through-url.png)

**Figure 6-35.** Accès à un microservice via une URL fournie par la passerelle d’API

En raison de raisons de test ou de débogage, si vous souhaitez accéder directement au conteneur de l’ancrage du catalogue (uniquement dans l’environnement de développement) sans passer par la passerelle d’API, dans la mesure où « Catalog-API » est une résolution DNS interne à l’hôte de l’ordinateur de la station d’accueil (la détection du service est gérée par les noms de service de l’ancrage-compose), le seul moyen d’accéder directement au conteneur est d’utiliser le port externe publié dans docker-compose. override. yml, qui est fourni uniquement pour les tests de développement, comme `http://localhost:5101/api/v1/Catalog/items/1` dans le

![Capture d’écran d’un navigateur montrant une réponse directe à l’API Catalog.](./media/implement-api-gateways-with-ocelot/direct-access-microservice-testing.png)

**Figure 6-36.** Accès direct à un microservice à des fins de test

Toutefois, l’application est configurée pour accéder à tous les microservices via les passerelles d’API, et non par le biais des « raccourcis » du port direct.

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a>Modèle d’agrégation de passerelle dans eShopOnContainers

Comme expliqué précédemment, une manière souple d’implémenter l’agrégation des demandes est d’utiliser les services personnalisés, par code. Vous pouvez également implémenter l’agrégation des demandes avec la [fonctionnalité d’agrégation des demandes dans Ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), mais elle peut ne pas être aussi flexible que nécessaire. Par conséquent, la méthode sélectionnée pour implémenter l’agrégation dans eShopOnContainers consiste à utiliser un service d’API Web ASP.NET Core explicite pour chaque agrégateur.

Selon cette approche, le diagramme de composition de passerelle API est en réalité un peu plus étendu quand les services d’agrégation qui ne figurent pas dans le diagramme d’architecture globale simplifiée illustrée précédemment sont pris en compte.

Dans le diagramme suivant, vous pouvez également voir les services d’agrégation fonctionner avec leurs passerelles d’API associées.

![Diagramme de l’architecture eShopOnContainers montrant les services d’agrégation.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture-aggregator-services.png)

**Figure 6-37.** Architecture eShopOnContainers avec services d’agrégation

En effectuant un zoom avant, dans le cadre de l’entreprise « shopping » de l’image suivante, vous pouvez voir que échanges excessifs entre les applications clientes et les microservices est réduit lors de l’utilisation des services d’agrégation dans les passerelles d’API.

![Diagramme montrant l’architecture eShopOnContainers zoom avant.](./media/implement-api-gateways-with-ocelot/zoom-in-vision-aggregator-services.png)

**Figure 6-38.** Vision agrandie des services d’agrégation

Vous pouvez remarquer le moment où le diagramme montre les demandes possibles provenant des passerelles d’API qu’il peut devenir complexes. En revanche, lorsque vous utilisez le modèle d’agrégation, vous pouvez voir comment les flèches en bleu simplifient la communication du point de vue d’une application cliente. Ce modèle permet non seulement de réduire la échanges excessifs et la latence dans la communication, mais également d’améliorer l’expérience utilisateur de manière significative pour les applications distantes (applications mobiles et SPA).

Dans le cas de la zone d’entreprise et des microservices « marketing », il s’agit d’un cas d’usage simple. il n’était donc pas nécessaire d’utiliser des agrégations, mais cela peut également être possible, si nécessaire.

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a>Authentification et autorisation dans les passerelles d’API Ocelot

Dans une passerelle d’API Ocelot, vous pouvez placer le service d’authentification, tel qu’un service API web ASP.NET Core avec [IdentityServer](https://identityserver.io/) pour fournir le jeton d’authentification, à l’extérieur ou à l’intérieur de la passerelle d’API.

Comme eShopOnContainers utilise plusieurs passerelles d’API avec des limites basées sur des secteurs d’activité et BFF, le service d’identité ou d’authentification est tenu à l’écart des passerelles d’API, tel qu’indiqué en jaune dans le diagramme suivant.

![Diagramme montrant le microservice d’identité sous la passerelle d’API.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-identity-service-position.png)

**Figure 6-39.** Position du service d’identité dans eShopOnContainers

Toutefois, Ocelot prend également en charge le placement du microservice d’identité/d’authentification dans les limites de la passerelle API, comme dans cet autre diagramme.

![Diagramme montrant l’authentification dans une passerelle d’API ocelot.](./media/implement-api-gateways-with-ocelot/ocelot-authentication.png)

**Figure 6-40.** Authentification dans Ocelot

Comme le montre le diagramme précédent, lorsque le microservice d’identité se trouve sous la passerelle d’API (AG) : 1) AG demande un jeton d’authentification à l’identité microservice, 2) le microservice d’identité retourne le jeton aux demandes GA, 3-4) AG des microservices à l’aide du jeton d’authentification. Étant donné que l’application eShopOnContainers a divisé la passerelle d’API en plusieurs BFF (backend pour frontend) et des passerelles d’API de secteurs d’activité, une autre option aurait été de créer une passerelle d’API supplémentaire pour les problèmes transversaux. Ce choix serait juste dans une architecture basée sur des microservices plus complexes avec plusieurs microservices de problèmes transversaux. Étant donné qu’il n’y a qu’un seul problème transversal dans eShopOnContainers, il a été décidé de gérer simplement le service de sécurité en dehors du domaine de la passerelle API, pour des raisons de simplicité.

Dans tous les cas, si l’application est sécurisée au niveau des passerelles d’API, le module d’authentification de la passerelle d’API Ocelot est consulté dans un premier temps lorsque vous tentez d’utiliser un microservice sécurisé quelconque. Cela permet de rediriger la requête HTTP pour accéder au microservice d’identité ou d’authentification pour obtenir le jeton d’accès afin que vous puissiez visiter les services protégés avec le access_token.

La manière de sécuriser par authentification n’importe quel service au niveau de la passerelle d’API consiste à définir l’élément AuthenticationProviderKey dans ses paramètres associés, dans le fichier configuration.json.

```json
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }
```

Quand Ocelot s’exécute, il examine le reroutages AuthenticationOptions. AuthenticationProviderKey et vérifie qu’il existe un fournisseur d’authentification inscrit avec la clé donnée. S’il n’en existe pas, Ocelot ne démarre pas. S’il en existe, le réacheminement utilise ce fournisseur lorsqu’il s’exécute.

Étant donné que la méthode WebHost d’Ocelot est configurée avec `authenticationProviderKey = "IdentityApiKey"`, elle nécessite une authentification chaque fois que ce service a des demandes quelconques sans jeton d’authentification.

```csharp
namespace OcelotApiGw
{
    public class Startup
    {
        private readonly IConfiguration _cfg;

        public Startup(IConfiguration configuration) => _cfg = configuration;

        public void ConfigureServices(IServiceCollection services)
        {
            var identityUrl = _cfg.GetValue<string>("IdentityUrl");
            var authenticationProviderKey = "IdentityApiKey";
                         //…
            services.AddAuthentication()
                .AddJwtBearer(authenticationProviderKey, x =>
                {
                    x.Authority = identityUrl;
                    x.RequireHttpsMetadata = false;
                    x.TokenValidationParameters = new Microsoft.IdentityModel.Tokens.TokenValidationParameters()
                    {
                        ValidAudiences = new[] { "orders", "basket", "locations", "marketing", "mobileshoppingagg", "webshoppingagg" }
                    };
                });
            //...
        }
    }
}
```

Ensuite, vous devez également définir une autorisation avec l’attribut [Authorize] sur une ressource quelconque accessible comme les microservices, comme dans le contrôleur de microservice de panier d’achat (Basket) suivant.

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class BasketController : Controller
    {
      //...
    }
}
```

Le ValidAudiences, tel que « basket », est corrélé avec l’audience définie dans chaque microservice avec `AddJwtBearer()` au ConfigureServices () de la classe Startup, comme dans le code ci-dessous.

```csharp
// prevent from mapping "sub" claim to nameidentifier.
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();

var identityUrl = Configuration.GetValue<string>("IdentityUrl");

services.AddAuthentication(options =>
{
    options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
    options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;

}).AddJwtBearer(options =>
{
    options.Authority = identityUrl;
    options.RequireHttpsMetadata = false;
    options.Audience = "basket";
});
```

Si vous essayez d’accéder à un microservice sécurisé, comme le microservice du panier avec une URL de reroutage basée sur la passerelle d’API comme `http://localhost:5202/api/v1/b/basket/1` , vous obtiendrez un 401 non autorisé, sauf si vous fournissez un jeton valide. D’un autre côté, si une URL de reroutage est authentifiée, Ocelot appelle le schéma en aval qui lui est associé (URL du microservice interne).

**Autorisation sur le niveau de reroutage de ocelot.**  Ocelot prend en charge l’autorisation basée sur les revendications évaluée après l’authentification. Vous définissez l’autorisation au niveau d’une route en ajoutant les lignes suivantes à la configuration des reroutages (ReRoutes).

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

Dans cet exemple, quand l’intergiciel d’autorisation est appelé, Ocelot détermine si l’utilisateur a le type de revendication « UserType » dans le jeton, et si la valeur de cette revendication est « employee ». Si ce n’est pas le cas, l’utilisateur ne sera pas autorisé et la réponse sera 403 interdit.

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a>Utilisation de l’entrée Kubernetes et des passerelles d’API Ocelot

Lorsque vous utilisez Kubernetes (comme dans un cluster de service Azure Kubernetes), vous unifiez généralement toutes les requêtes HTTP via le niveau d’entrée [Kubernetes](https://kubernetes.io/docs/concepts/services-networking/ingress/) basé sur *Nginx*.

Dans Kubernetes, si vous n’utilisez pas d’approche d’entrée, vos services et gousses ont uniquement des adresses IP routables par le réseau de clusters.

Toutefois, si vous utilisez une approche d’entrée, vous disposez d’un niveau intermédiaire entre Internet et vos services (y compris vos passerelles d’API), agissant comme un proxy inverse.

Par définition, une entrée est une collection de règles qui autorisent les connexions entrantes à atteindre les services de cluster. Une entrée est configurée pour fournir aux services des URL accessibles en externe, un trafic d’équilibrage de charge, un processus de terminaison SSL, etc. Les utilisateurs demandent une entrée en publiant la ressource d’entrée sur le serveur d’API.

Dans eShopOnContainers, lorsque vous effectuez un développement local et utilisez simplement votre machine de développement en tant qu’hôte Docker, vous n’utilisez pas d’entrée, mais uniquement les multiples passerelles d’API.

Toutefois, lorsque vous ciblez un environnement de « production » basé sur Kubernetes, eShopOnContainers utilise une entrée devant les passerelles d’API. De cette façon, les clients appellent toujours la même URL de base, mais les demandes sont acheminées vers plusieurs passerelles d’API ou BFF.

Les passerelles d’API sont des serveurs frontaux ou des façades qui reposent uniquement sur les services, mais pas sur les applications Web qui sont généralement hors de portée. De plus, les passerelles d’API peuvent masquer certains microservices internes.

Toutefois, l’entrée redirige simplement les requêtes HTTP et n’essaie pas de masquer de microservice ni d’application web.

Le fait d’avoir un niveau Nginx d’entrée dans Kubernetes en face des applications web, ainsi que plusieurs passerelles d’API/BFF Ocelot, constitue l’architecture idéale, telle qu’elle est illustrée dans le diagramme suivant.

![Diagramme montrant comment un niveau d’entrée s’adapte à l’environnement AKS.](./media/implement-api-gateways-with-ocelot/eshoponcontainer-ingress-tier.png)

**Figure 6-41.** Niveau d’entrée dans eShopOnContainers lors d’un déploiement dans Kubernetes

Une entrée Kubernetes agit comme un proxy inverse pour tout le trafic vers l’application, y compris les applications Web, qui sont en dehors de l’étendue de la passerelle API. Quand vous déployez eShopOnContainers dans Kubernetes, il expose simplement quelques services ou points de terminaison via _l’entrée_, en fait la liste suivante de suffixes sur les URL :

- `/` pour l’application web SPA cliente
- `/webmvc` pour l’application web MVC cliente
- `/webstatus` pour l’application web cliente affichant l’état/les vérifications d’intégrité
- `/webshoppingapigw` pour les processus métier d’achat et BFF web
- `/webmarketingapigw` pour les processus métier marketing et BFF web
- `/mobileshoppingapigw` pour les processus métier d’achat et BFF mobiles
- `/mobilemarketingapigw` pour les processus métier marketing et BFF mobiles

Lors du déploiement sur Kubernetes, chaque passerelle d’API Ocelot utilise un fichier « configuration.jssur » différent pour chaque _Pod_ exécutant les passerelles d’API. Ces fichiers « configuration.json » sont fournis par montage (à l’origine avec le script deploy.ps1) un volume créé sur la base d’une _carte de configuration_ Kubernetes nommée « ocelot ». Chaque conteneur monte son fichier de configuration associé dans le dossier du conteneur nommé `/app/configuration` .

Dans les fichiers de code source de eShopOnContainers, les fichiers d’origine « configuration.json » se trouvent dans le `k8s/ocelot/` dossier. Il y a un fichier pour chaque BFF/APIGateway.

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a>Fonctionnalités transversales supplémentaires dans une passerelle d’API Ocelot

D’autres fonctionnalités importantes peuvent être étudiées et utilisées lorsque vous utilisez une passerelle d’API Ocelot. Elles sont décrites dans les liens suivants.

- **Détection de service côté client intégration de Ocelot à la série consulaire ou Eureka** \
  <https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html>

- **Mise en cache au niveau de la passerelle API** \
  <https://ocelot.readthedocs.io/en/latest/features/caching.html>

- **Journalisation au niveau de la passerelle API** \
  <https://ocelot.readthedocs.io/en/latest/features/logging.html>

- **Qualité de service (nouvelles tentatives et disjoncteurs) au niveau de la passerelle d’API** \
  <https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html>

- **Limitation du débit** \
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> [Précédent](background-tasks-with-ihostedservice.md) 
>  [Suivant](../microservice-ddd-cqrs-patterns/index.md)
