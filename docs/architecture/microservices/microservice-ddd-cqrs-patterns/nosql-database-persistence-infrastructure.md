---
title: Utilisation de bases de données NoSQL comme infrastructure de persistance
description: Comprenez l’utilisation des bases de données NoSql en général et Azure Cosmos DB en particulier, en tant qu’option d’implémentation de la persistance.
ms.date: 01/13/2021
ms.openlocfilehash: 32f32a3fd247f49ac54deaf33605bcc2ac7b55dc
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188827"
---
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a>Utiliser des bases de données NoSQL comme infrastructure de persistance

Quand vous utilisez des bases de données NoSQL pour votre couche de données d’infrastructure, vous n’utilisez généralement pas un ORM comme Entity Framework Core. À la place, vous utilisez l’API fournie par le moteur NoSQL, comme Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB ou des tables Stockage Azure.

Toutefois, quand vous utilisez une base de données NoSQL, en particulier une base de données orientée document comme Azure Cosmos DB, CouchDB ou RavenDB, la façon dont vous concevez votre modèle avec des agrégats DDD est en partie semblable à la façon dont vous pouvez le faire dans EF Core, en ce qui concerne l’identification des racines d’agrégat, les classes d’entité enfants et les classes d’objets de valeur. Mais finalement, la sélection de la base de données aura un impact sur votre conception.

Quand vous utilisez une base de données orientée document, vous implémentez un agrégat sous la forme d’un document unique, sérialisé au format JSON ou dans un autre format. Toutefois, l’utilisation de la base de données est transparente du point de vue du code du modèle de domaine. Quand vous utilisez une base de données NoSQL, vous utilisez toujours des classes d’entité et des classes de racine d’agrégat, mais avec plus de souplesse que quand vous utilisez EF Core, car la persistance n’est pas relationnelle.

La différence réside dans la façon dont vous rendez ce modèle persistant. Si vous avez implémenté votre modèle de domaine basé sur des classes d’entité OCT, indépendant de la persistance de l’infrastructure, il pourrait sembler que vous pouvez passer à une autre infrastructure de persistance, même des bases de données relationnelles aux bases de données NoSQL. Ça ne doit toutefois pas être votre objectif. Il existe toujours des contraintes et des compromis dans les différentes technologies de base de données : c’est pourquoi vous ne pouvez pas avoir le même modèle pour les bases de données relationnelles et les bases de données NoSQL. Modifier les modèles de persistance n’est pas une tâche triviale, car les transactions et les opérations de persistance sont très différentes.

Par exemple, dans une base de données orientée document, une racine d’agrégat peut avoir plusieurs propriétés de collection enfant. Dans une base de données relationnelle, l’interrogation de plusieurs propriétés de collections enfants n’est pas facile à optimiser, car vous obtenez en retour d’EF une instruction SQL UNION ALL. Il n’est pas simple d’avoir le même modèle de domaine pour les bases de données relationnelles et les bases de données NoSQL, et il est recommandé de ne pas essayer. Vous devez réellement concevoir votre modèle en comprenant comment les données vont être utilisées dans chaque base de données particulière.

Utiliser des bases de données NoSQL présente, entre autre, l’avantage d’avoir des entités plus dénormalisées. De ce fait, vous n’avez pas à définir un mappage de table. Votre modèle de domaine peut être plus flexible que quand vous utilisez une base de données relationnelle.

Quand vous concevez votre modèle de domaine basé sur des agrégats, le passage à des bases de données NoSQL et orientées document peut être encore plus simple que d’utiliser une base de données relationnelle, car les agrégats que vous concevez sont semblables aux documents sérialisés dans une base de données orientée document. Vous pouvez ensuite inclure dans ces « sacs » toutes les informations dont vous pouvez avoir besoin pour cet agrégat.

Par exemple, le code JSON suivant est un exemple d’implémentation d’un agrégat de commandes lors de l’utilisation d’une base de données orientée document. Il est semblable à l’agrégat de commandes que nous avons implémenté dans l’exemple eShopOnContainers, mais sans utiliser EF Core au-dessous.

```json
{
    "id": "2017001",
    "orderDate": "2/25/2017",
    "buyerId": "1234567",
    "address": [
        {
        "street": "100 One Microsoft Way",
        "city": "Redmond",
        "state": "WA",
        "zip": "98052",
        "country": "U.S."
        }
    ],
    "orderItems": [
        {"id": 20170011, "productId": "123456", "productName": ".NET T-Shirt",
        "unitPrice": 25, "units": 2, "discount": 0},
        {"id": 20170012, "productId": "123457", "productName": ".NET Mug",
        "unitPrice": 15, "units": 1, "discount": 0}
    ]
}
```

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a>Introduction à Azure Cosmos DB et à l’API Cosmos DB native

[Azure Cosmos DB](/azure/cosmos-db/introduction) est le service de base de données de Microsoft distribué à l’échelle mondiale pour les applications stratégiques. Azure Cosmos DB fournit la [distribution mondiale clés en main](/azure/cosmos-db/distribute-data-globally), la [mise à l’échelle élastique du débit et du stockage](/azure/cosmos-db/partition-data), des latences de l’ordre de quelques millisecondes dans le monde entier dans plus de 99 pour cent des cas, [cinq niveaux de cohérence bien définis](/azure/cosmos-db/consistency-levels) et une garantie d’une haute disponibilité, le tout soutenu par nos [contrats SLA de pointe](https://azure.microsoft.com/support/legal/sla/cosmos-db/). Azure Cosmos DB [indexe automatiquement les données](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) sans avoir à s’occuper de la gestion des schémas et des index. Il est multi-modèle et prend en charge les modèles de données en colonnes, documents, graphes et clé-valeur.

![Diagramme montrant la distribution globale Azure Cosmos DB.](./media/nosql-database-persistence-infrastructure/azure-cosmos-db-global-distribution.png)

**Figure 7-19**. Distribution globale de Azure Cosmos DB

Quand vous utilisez un modèle C\# pour implémenter l’agrégat que l’API Azure Cosmos DB doit utiliser, l’agrégat peut être semblable aux classes OCT C\# utilisées avec EF Core. La différence réside dans la façon de les utiliser à partir des couches Application et d’infrastructure, comme dans le code suivant :

```csharp
// C# EXAMPLE OF AN ORDER AGGREGATE BEING PERSISTED WITH AZURE COSMOS DB API
// **_ Domain Model Code _*_
// Aggregate: Create an Order object with its child entities and/or value objects.
// Then, use AggregateRoot's methods to add the nested objects so invariants and
// logic is consistent across the nested properties (value objects and entities).

Order orderAggregate = new Order
{
    Id = "2017001",
    OrderDate = new DateTime(2005, 7, 1),
    BuyerId = "1234567",
    PurchaseOrderNumber = "PO18009186470"
}

Address address = new Address
{
    Street = "100 One Microsoft Way",
    City = "Redmond",
    State = "WA",
    Zip = "98052",
    Country = "U.S."
}

orderAggregate.UpdateAddress(address);

OrderItem orderItem1 = new OrderItem
{
    Id = 20170011,
    ProductId = "123456",
    ProductName = ".NET T-Shirt",
    UnitPrice = 25,
    Units = 2,
    Discount = 0;
};

//Using methods with domain logic within the entity. No anemic-domain model
orderAggregate.AddOrderItem(orderItem1);
// _*_ End of Domain Model Code _*_

// _*_ Infrastructure Code using Cosmos DB Client API _*_
Uri collectionUri = UriFactory.CreateDocumentCollectionUri(databaseName,
    collectionName);

await client.CreateDocumentAsync(collectionUri, orderAggregate);

// As your app evolves, let's say your object has a new schema. You can insert
// OrderV2 objects without any changes to the database tier.
Order2 newOrder = GetOrderV2Sample("IdForSalesOrder2");
await client.CreateDocumentAsync(collectionUri, newOrder);
```

Comme vous pouvez le voir, la façon dont vous utilisez votre modèle de domaine peut être semblable à la façon dont vous l’utilisez dans votre couche de modèle de domaine quand l’infrastructure est EF. Vous utilisez toujours les mêmes méthodes de racine d’agrégat pour garantir la cohérence, les invariants et les validations au sein de l’agrégat.

Toutefois, quand vous rendez votre modèle persistant dans la base de données NoSQL, le code et l’API changent considérablement par rapport au code EF Core ou à tout autre code associé à des bases de données relationnelles.

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a>Implémenter du code .NET ciblant MongoDB et Azure Cosmos DB

### <a name="use-azure-cosmos-db-from-net-containers"></a>Utiliser Azure Cosmos DB à partir de conteneurs .NET

Vous pouvez accéder aux bases de données Azure Cosmos DB à partir du code .NET en cours d’exécution dans des conteneurs, comme à partir de n’importe quelle autre application .NET. Par exemple, les microservices Locations.API et Marketing.API dans eShopOnContainers sont implémentés afin de pouvoir consommer des bases de données Azure Cosmos DB.

Toutefois, il existe une limitation dans Azure Cosmos DB du point de vue de l’environnement de développement Docker. Même s’il existe un [émulateur Azure Cosmos DB](/azure/cosmos-db/local-emulator) local qui peut s’exécuter sur un ordinateur de développement local, il prend uniquement en charge Windows. Linux et macOS ne sont pas pris en charge.

Il est également possible d’exécuter cet émulateur sur l’arrimeur, mais uniquement sur des conteneurs Windows, et non avec des conteneurs Linux. Il s’agit d’un handicap initial pour l’environnement de développement si votre application est déployée en tant que conteneurs Linux, puisque, actuellement, vous ne pouvez pas déployer des conteneurs Linux et Windows sur Docker pour Windows en même temps. Tous les conteneurs en cours de déploiement doivent être soit pour Linux, soit pour Windows.

Le déploiement idéal et plus direct pour une solution de développement/test est celui qui permet de déployer vos systèmes de base de données comme des conteneurs avec vos conteneurs personnalisés, afin que vos environnements de développement/test soient toujours cohérents.

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a>Utiliser l’API MongoDB pour les conteneurs Linux/Windows de développement/test local et Azure Cosmos DB

Les bases de données Cosmos DB prennent en charge l’API MongoDB pour .NET, ainsi que le protocole filaire MongoDB natif. Cela signifie qu’en utilisant des pilotes existants, votre application écrite pour MongoDB peut maintenant communiquer avec Cosmos DB et utiliser des bases de données Cosmos DB au lieu de bases de données MongoDB, comme illustré dans la figure 7-20.

![Diagramme montrant que Cosmos DB prend en charge le protocole Wire .NET et MongoDB.](./media/nosql-database-persistence-infrastructure/mongodb-api-wire-protocol.png)

_ * Figure 7-20 * *. Utilisation de l’API et du protocole MongoDB pour accéder à Azure Cosmos DB

C’est une approche très pratique pour les preuves de concept dans les environnements Docker avec des conteneurs Linux, car l’[image Docker MongoDB](https://hub.docker.com/r/_/mongo/) est une image multi-arch qui prend en charge les conteneurs Docker Linux et Docker Windows.

Comme le montre l’image suivante, en utilisant l’API MongoDB, eShopOnContainers prend en charge les conteneurs MongoDB Linux et Windows pour l’environnement de développement local, mais ensuite, vous pouvez passer à une solution cloud PaaS scalable, comme Azure Cosmos DB, simplement en [changeant la chaîne de connexion MongoDB pour pointer vers Azure Cosmos DB](/azure/cosmos-db/connect-mongodb-account).

![Diagramme montrant que le microservice d’emplacement dans eShopOnContainers peut utiliser Cosmos DB ou Mongo DB.](./media/nosql-database-persistence-infrastructure/eshoponcontainers-mongodb-containers.png)

**Figure 7-21**. eShopOnContainers utilisant des conteneurs MongoDB pour un environnement de développement ou Azure Cosmos DB pour la production

Le Azure Cosmos DB de production s’exécuterait dans le Cloud d’Azure en tant que service PaaS et évolutif.

Vos conteneurs .NET personnalisés peuvent s’exécuter sur un hôte de l’animateur de développement local (qui utilise Docker pour Windows sur un ordinateur Windows 10) ou être déployés dans un environnement de production, comme Kubernetes dans Azure AKS ou Azure Service Fabric. Dans ce deuxième environnement, vous devez déployer uniquement les conteneurs personnalisés .NET, mais pas le conteneur MongoDB, car vous utiliserez Azure Cosmos DB dans le Cloud pour gérer les données en production.

Le fait que votre solution puisse s’exécuter dans les deux moteurs de base de données, MongoDB ou Azure Cosmos DB, constitue un avantage indéniable de l’utilisation de l’API MongoDB, car les migrations vers d’autres environnements devraient être faciles. Toutefois, il est parfois utile d’utiliser une API native (c’est-à-dire l’API Cosmos DB native) pour tirer pleinement parti des fonctionnalités d’un moteur de base de données spécifique.

Pour obtenir une comparaison supplémentaire entre utiliser simplement MongoDB et utiliser Cosmos DB dans le cloud, consultez les [avantages de l’utilisation d’Azure Cosmos DB dans cette page](/azure/cosmos-db/mongodb-introduction).

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a>Analyser votre approche pour les applications de production : API MongoDB et API Cosmos DB

Dans eShopOnContainers, nous utilisons l’API MongoDB, car notre priorité était fondamentalement d’avoir un environnement de développement/test cohérent utilisant une base de données NoSQL qui pouvait également fonctionner avec Azure Cosmos DB.

Toutefois, si vous envisagez d’utiliser l’API MongoDB pour accéder à Azure Cosmos DB dans Azure pour les applications de production, vous devez analyser les différences de capacités et de performances lors de l’utilisation de l’API MongoDB pour accéder aux bases de données Azure Cosmos DB par rapport à l’utilisation de l’API Azure Cosmos DB Native. S’il n’y a pas de différence, vous pouvez utiliser l’API MongoDB, ce qui vous permet de bénéficier de la prise en charge de deux moteurs de base de données NoSQL en même temps.

Vous pouvez également utiliser des clusters MongoDB comme base de données de production dans le Cloud d’Azure, également avec le [service Azure MongoDB](https://www.mongodb.com/scale/mongodb-azure-service). Mais il ne s’agit pas d’un service PaaS fourni par Microsoft. Dans ce cas, Azure héberge simplement cette solution provenant de MongoDB.

En fait, il s’agit simplement d’une exclusion de responsabilité stipulant que vous ne devez pas toujours utiliser l’API MongoDB sur Azure Cosmos DB, comme nous l’avons fait dans eShopOnContainers, car il s’agissait d’un choix pratique pour les conteneurs Linux. La décision doit être basée sur les besoins spécifiques et les tests que vous devez effectuer pour votre application de production.

### <a name="the-code-use-mongodb-api-in-net-applications"></a>Code : utiliser l’API MongoDB dans les applications .NET

L’API MongoDB pour .NET est basée sur des packages NuGet que vous devez ajouter à vos projets, comme dans le projet Locations.API présenté dans la figure suivante.

![Capture d’écran des dépendances dans les packages NuGet MongoDB.](./media/nosql-database-persistence-infrastructure/mongodb-api-nuget-packages.png)

**Figure 7-22**. Références des packages NuGet de l’API MongoDB dans un projet .NET

Examinons le code figurant dans les sections suivantes.

#### <a name="a-model-used-by-mongodb-api"></a>Modèle utilisé par l’API MongoDB

Tout d’abord, vous devez définir un modèle qui contiendra les données provenant de la base de données dans l’espace mémoire de votre application. Voici un exemple de modèle utilisé pour les emplacements sur eShopOnContainers.

```csharp
using MongoDB.Bson;
using MongoDB.Bson.Serialization.Attributes;
using MongoDB.Driver.GeoJsonObjectModel;
using System.Collections.Generic;

public class Locations
{
    [BsonId]
    [BsonRepresentation(BsonType.ObjectId)]
    public string Id { get; set; }
    public int LocationId { get; set; }
    public string Code { get; set; }
    [BsonRepresentation(BsonType.ObjectId)]
    public string Parent_Id { get; set; }
    public string Description { get; set; }
    public double Latitude { get; set; }
    public double Longitude { get; set; }
    public GeoJsonPoint<GeoJson2DGeographicCoordinates> Location
                                                             { get; private set; }
    public GeoJsonPolygon<GeoJson2DGeographicCoordinates> Polygon
                                                             { get; private set; }
    public void SetLocation(double lon, double lat) => SetPosition(lon, lat);
    public void SetArea(List<GeoJson2DGeographicCoordinates> coordinatesList)
                                                    => SetPolygon(coordinatesList);

    private void SetPosition(double lon, double lat)
    {
        Latitude = lat;
        Longitude = lon;
        Location = new GeoJsonPoint<GeoJson2DGeographicCoordinates>(
            new GeoJson2DGeographicCoordinates(lon, lat));
    }

    private void SetPolygon(List<GeoJson2DGeographicCoordinates> coordinatesList)
    {
        Polygon = new GeoJsonPolygon<GeoJson2DGeographicCoordinates>(
                  new GeoJsonPolygonCoordinates<GeoJson2DGeographicCoordinates>(
                  new GeoJsonLinearRingCoordinates<GeoJson2DGeographicCoordinates>(
                                                                 coordinatesList)));
    }
}
```

Vous pouvez voir qu’il existe plusieurs attributs et types provenant des packages NuGet de MongoDB.

Les bases de données NoSQL conviennent généralement parfaitement pour travailler avec des données hiérarchiques non relationnelles. Dans cet exemple, nous utilisons des types MongoDB spécialement conçus pour les géolocalisations, comme `GeoJson2DGeographicCoordinates`.

#### <a name="retrieve-the-database-and-the-collection"></a>Récupérer la base de données et la collection

Dans eShopOnContainers, nous avons créé un contexte de base de données personnalisé dans lequel nous implémentons le code pour récupérer la base de données et les MongoCollections, comme dans le code suivant.

```csharp
public class LocationsContext
{
    private readonly IMongoDatabase _database = null;

    public LocationsContext(IOptions<LocationSettings> settings)
    {
        var client = new MongoClient(settings.Value.ConnectionString);
        if (client != null)
            _database = client.GetDatabase(settings.Value.Database);
    }

    public IMongoCollection<Locations> Locations
    {
        get
        {
            return _database.GetCollection<Locations>("Locations");
        }
    }
}
```

#### <a name="retrieve-the-data"></a>Récupérer les données

Dans du code C#, comme les contrôleurs d’API web ou l’implémentation de dépôts personnalisés, vous pouvez écrire du code semblable au suivant lors d’une interrogation par le biais de l’API MongoDB. Notez que l’objet `_context` est une instance de la classe `LocationsContext` précédente.

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a>Utiliser env-var dans le fichier docker-compose.override.yml pour la chaîne de connexion MongoDB

Quand vous créez un objet MongoClient, il a besoin d’un paramètre fondamental qui est précisément le paramètre `ConnectionString` pointant vers la base de données appropriée. Dans le cas de eShopOnContainers, la chaîne de connexion peut pointer vers un conteneur d’ancrage local MongoDB local ou vers une base de données de Azure Cosmos DB de production.  Cette chaîne de connexion provient des variables d’environnement définies dans les fichiers `docker-compose.override.yml` utilisés lors du déploiement avec docker-compose ou Visual Studio, comme dans le code YML suivant.

```yml
# docker-compose.override.yml
version: '3.4'
services:
  # Other services
  locations-api:
    environment:
      # Other settings
      - ConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosqldata}

```

La variable d’environnement `ConnectionString` est résolue de la manière suivante : si la variable globale `ESHOP_AZURE_COSMOSDB` est définie dans le fichier `.env` avec la chaîne de connexion Azure Cosmos DB, elle l’utilisera pour accéder à la base de données Azure Cosmos DB dans le cloud. S’il n’est pas défini, il prend la `mongodb://nosqldata` valeur et utilise le conteneur Development MongoDB.

Le code suivant présente le fichier `.env` avec la variable d’environnement globale de la chaîne de connexion Azure Cosmos DB, comme implémenté dans eShopOnContainers :

```yml
# .env file, in eShopOnContainers root folder
# Other Docker environment variables

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost
ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=<YourDockerHostIP>

#ESHOP_AZURE_COSMOSDB=<YourAzureCosmosDBConnData>

#Other environment variables for additional Azure infrastructure assets
#ESHOP_AZURE_REDIS_BASKET_DB=<YourAzureRedisBasketInfo>
#ESHOP_AZURE_STORAGE_CATALOG_URL=<YourAzureStorage_Catalog_BLOB_URL>
#ESHOP_AZURE_SERVICE_BUS=<YourAzureServiceBusInfo>
```

Supprimez les marques de commentaire de la ligne de ESHOP_AZURE_COSMOSDB et mettez-la à jour avec votre chaîne de connexion Azure Cosmos DB obtenue à partir de la Portail Azure, comme expliqué dans [connecter une application MongoDB à Azure Cosmos DB](/azure/cosmos-db/connect-mongodb-account).

Si la `ESHOP_AZURE_COSMOSDB` variable globale est vide, ce qui signifie qu’elle est commentée dans le `.env` fichier, le conteneur utilise une chaîne de connexion MongoDB par défaut. Cette chaîne de connexion pointe vers le conteneur MongoDB local déployé dans eShopOnContainers qui est nommé `nosqldata` et qui a été défini dans le fichier dockr-compose, comme indiqué dans le code suivant. yml :

``` yml
# docker-compose.yml
version: '3.4'
services:
  # ...Other services...
  nosqldata:
    image: mongo
```

#### <a name="additional-resources"></a>Ressources supplémentaires

- **Modélisation de données de document pour des bases de données NoSQL** \
  <https://docs.microsoft.com/azure/cosmos-db/modeling-data>

- **Vaughn Vernon. Le magasin d’agrégats idéal pour la conception de Domain-Driven ?** \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- **Présentation de Azure Cosmos DB : API pour MongoDB**  \
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- **Azure Cosmos DB : création d’une application Web API MongoDB avec .NET et le Portail Azure**  \
  <https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet>

- **Utiliser l’émulateur Azure Cosmos DB pour le développement et le test locaux**  \
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- **Connecter une application MongoDB à Azure Cosmos DB**  \
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- **Image de l’émulateur d’Cosmos DB de l’émulateur (conteneur Windows)**  \
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- **Image de l’arrimeur MongoDB (conteneur Linux et Windows)**  \
  <https://hub.docker.com/_/mongo/>

- **Utilisez MongoChef (Studio 3T) avec un Azure Cosmos DB : API pour le compte MongoDB**  \
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
>[Précédent](infrastructure-persistence-layer-implementation-entity-framework-core.md) 
> [Suivant](microservice-application-layer-web-api-design.md)
