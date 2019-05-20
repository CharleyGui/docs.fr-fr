---
title: Utilisation de bases de données NoSQL comme infrastructure de persistance
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Comprendre l’utilisation des bases de données NoSql en général et d’Azure Cosmos DB en particulier comme option pour implémenter la persistance.
ms.date: 10/08/2018
ms.openlocfilehash: 023904319651ec91000ff036850c773f66d1a267
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644467"
---
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a>Utiliser des bases de données NoSQL comme infrastructure de persistance

Quand vous utilisez des bases de données NoSQL pour votre couche de données d’infrastructure, vous n’utilisez généralement pas un ORM comme Entity Framework Core. À la place, vous utilisez l’API fournie par le moteur NoSQL, comme Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB ou des tables Stockage Azure.

Toutefois, quand vous utilisez une base de données NoSQL, en particulier une base de données orientée document comme Azure Cosmos DB, CouchDB ou RavenDB, la façon dont vous concevez votre modèle avec des agrégats DDD est en partie semblable à la façon dont vous pouvez le faire dans EF Core, en ce qui concerne l’identification des racines d’agrégat, les classes d’entité enfants et les classes d’objets de valeur. Mais finalement, la sélection de la base de données aura un impact sur votre conception.

Quand vous utilisez une base de données orientée document, vous implémentez un agrégat sous la forme d’un document unique, sérialisé au format JSON ou dans un autre format. Toutefois, l’utilisation de la base de données est transparente du point de vue du code du modèle de domaine. Quand vous utilisez une base de données NoSQL, vous utilisez toujours des classes d’entité et des classes de racine d’agrégat, mais avec plus de souplesse que quand vous utilisez EF Core, car la persistance n’est pas relationnelle.

La différence réside dans la façon dont vous rendez ce modèle persistant. Si vous avez implémenté votre modèle de domaine basé sur des classes d’entité OCT, indépendant de la persistance de l’infrastructure, il pourrait sembler que vous pouvez passer à une autre infrastructure de persistance, même des bases de données relationnelles aux bases de données NoSQL. Ça ne doit toutefois pas être votre objectif. Il existe toujours des contraintes et des compromis dans les différentes technologies de base de données : c’est pourquoi vous ne pouvez pas avoir le même modèle pour les bases de données relationnelles et les bases de données NoSQL. Modifier les modèles de persistance n’est pas une tâche triviale, car les transactions et les opérations de persistance sont très différentes.

Par exemple, dans une base de données orientée document, une racine d’agrégat peut avoir plusieurs propriétés de collection enfant. Dans une base de données relationnelle, l’interrogation de plusieurs propriétés de collections enfants n’est pas facile à optimiser, car vous obtenez en retour d’EF une instruction SQL UNION ALL. Il n’est pas simple d’avoir le même modèle de domaine pour les bases de données relationnelles et les bases de données NoSQL, et il est recommandé de ne pas essayer. Vous devez réellement concevoir votre modèle en comprenant comment les données vont être utilisées dans chaque base de données particulière.

Utiliser des bases de données NoSQL présente, entre autre, l’avantage d’avoir des entités plus dénormalisées. De ce fait, vous n’avez pas à définir un mappage de table. Votre modèle de domaine peut être plus flexible que quand vous utilisez une base de données relationnelle.

Quand vous concevez votre modèle de domaine basé sur des agrégats, le passage à des bases de données NoSQL et orientées document peut être encore plus simple que d’utiliser une base de données relationnelle, car les agrégats que vous concevez sont semblables aux documents sérialisés dans une base de données orientée document. Vous pouvez ensuite inclure dans ces « conteneurs » toutes les informations dont vous pouvez avoir besoin pour cet agrégat.

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

[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) est le service de base de données de Microsoft distribué à l’échelle mondiale pour les applications stratégiques. Azure Cosmos DB offre une [distribution globale clés en main](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), permet une [mise à l’échelle élastique des capacités de débit et de stockage](https://docs.microsoft.com/azure/cosmos-db/partition-data) dans le monde entier, garantit des latences inférieures à 10 millisecondes dans le 99e centile, offre [cinq niveaux de cohérence bien définis](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) et garantit une haute disponibilité, le tout couvert par des [contrats SLA parmi les meilleurs du marché](https://azure.microsoft.com/support/legal/sla/cosmos-db/). Azure Cosmos DB [indexe automatiquement les données](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) sans vous obliger à gérer les schémas et les index. Il est multimodèle et prend en charge les modèles de données basés sur des documents, des clés-valeurs, des graphiques et des colonnes.

![Azure Cosmos DB est une base de données de latence faible, dont la distribution mondiale est garantie et à laquelle vous pouvez accéder avec quatre protocoles d’API. ](./media/image19.1.png)
**Figure 7-19**. Distribution globale d’Azure Cosmos DB

Quand vous utilisez un modèle C\# pour implémenter l’agrégat que l’API Azure Cosmos DB doit utiliser, l’agrégat peut être semblable aux classes OCT C\# utilisées avec EF Core. La différence réside dans la façon de les utiliser à partir des couches Application et d’infrastructure, comme dans le code suivant :

```csharp
// C# EXAMPLE OF AN ORDER AGGREGATE BEING PERSISTED WITH AZURE COSMOS DB API
// *** Domain Model Code ***
// Aggregate: Create an Order object with its child entities and/or value objects.
// Then, use AggregateRoot’s methods to add the nested objects so invariants and
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
// *** End of Domain Model Code ***

// *** Infrastructure Code using Cosmos DB Client API ***
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

Toutefois, il existe une limitation dans Azure Cosmos DB du point de vue de l’environnement de développement Docker. Même quand il existe un [émulateur Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/local-emulator) local en mesure de s’exécuter sur un ordinateur de développement local (comme un PC), à compter de fin 2017, il prend en charge uniquement Windows, et Linux pas. 

Il est également possible d’exécuter cet émulateur sur Docker, mais uniquement sur des conteneurs Windows, et pas avec des conteneurs Linux. Cela constitue un handicap initial pour l’environnement de développement si votre application est déployée comme conteneurs Linux, étant donné qu’actuellement, vous ne pouvez pas déployer en même temps des conteneurs Linux et Windows sur Docker pour Windows. Tous les conteneurs en cours de déploiement doivent être soit pour Linux, soit pour Windows.

Le déploiement idéal et plus direct pour une solution de développement/test est celui qui permet de déployer vos systèmes de base de données comme des conteneurs avec vos conteneurs personnalisés, afin que vos environnements de développement/test soient toujours cohérents.

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a>Utiliser l’API MongoDB pour les conteneurs Linux/Windows de développement/test local et Azure Cosmos DB

Les bases de données Cosmos DB prennent en charge l’API MongoDB pour .NET, ainsi que le protocole filaire MongoDB natif. Cela signifie qu’en utilisant des pilotes existants, votre application écrite pour MongoDB peut maintenant communiquer avec Cosmos DB et utiliser des bases de données Cosmos DB au lieu de bases de données MongoDB, comme illustré dans la figure 7-20.

![Cosmos DB prend en charge les API MongoDB pour .NET et le protocole filaire MongoDB ; vous pouvez facilement passer de MongoDB à Cosmos DB. ](./media/image19.2.png)
**Figure 7-20**. Utilisation de l’API et du protocole MongoDB pour accéder à Azure Cosmos DB

C’est une approche très pratique pour les preuves de concept dans les environnements Docker avec des conteneurs Linux, car l’[image Docker MongoDB](https://hub.docker.com/r/_/mongo/) est une image multi-arch qui prend en charge les conteneurs Docker Linux et Docker Windows.

Comme le montre l’image suivante, en utilisant l’API MongoDB, eShopOnContainers prend en charge les conteneurs MongoDB Linux et Windows pour l’environnement de développement local, mais ensuite, vous pouvez passer à une solution cloud PaaS scalable, comme Azure Cosmos DB, simplement en [changeant la chaîne de connexion MongoDB pour pointer vers Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).

![Le microservice Location dans eShopOnContainers est implémenté avec MongoDB, mais vous pouvez le passer sur Cosmos DB en modifiant simplement la chaîne de connexion. ](./media/image20-bis.png)
**Figure 7-21**. eShopOnContainers utilisant des conteneurs MongoDB pour un environnement de développement ou Azure Cosmos DB pour la production

Le service Azure Cosmos DB de production s’exécuterait dans le cloud d’Azure comme service PaaS évolutif.

Vos conteneurs .NET Core personnalisés peuvent s’exécuter sur un hôte Docker de développement local (qui utilise Docker pour Windows sur un ordinateur Windows 10) ou être déployés dans un environnement de production, comme Kubernetes dans Azure AKS ou Azure Service Fabric. Dans ce deuxième environnement, vous déployeriez uniquement les conteneurs personnalisés .NET Core mais pas le conteneur MongoDB puisque vous utiliseriez Azure Cosmos DB dans le cloud pour gérer les données en production.

Le fait que votre solution puisse s’exécuter dans les deux moteurs de base de données, MongoDB ou Azure Cosmos DB, constitue un avantage indéniable de l’utilisation de l’API MongoDB, car les migrations vers d’autres environnements devraient être faciles. Toutefois, il est parfois utile d’utiliser une API native (c’est-à-dire l’API Cosmos DB native) pour tirer pleinement parti des fonctionnalités d’un moteur de base de données spécifique.

Pour obtenir une comparaison supplémentaire entre utiliser simplement MongoDB et utiliser Cosmos DB dans le cloud, consultez les [avantages de l’utilisation d’Azure Cosmos DB dans cette page](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction). 

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a>Analyser votre approche pour les applications de production : API MongoDB et API Cosmos DB

Dans eShopOnContainers, nous utilisons l’API MongoDB, car notre priorité était fondamentalement d’avoir un environnement de développement/test cohérent utilisant une base de données NoSQL qui pourrait également fonctionner avec Azure Cosmos DB.

Toutefois, si vous envisagez d’utiliser l’API MongoDB pour accéder à Azure Cosmos DB dans Azure pour des applications de production, vous devez analyser les différences de capacités et de performances lors de l’utilisation de l’API MongoDB pour accéder aux bases de données Azure Cosmos DB par rapport à l’API Azure Cosmos DB native. S’il n’y a pas de différence, vous pouvez utiliser l’API MongoDB, ce qui vous permet de bénéficier de la prise en charge de deux moteurs de base de données NoSQL en même temps.

Vous pouvez également utiliser des clusters MongoDB comme base de données de production dans le cloud d’Azure, avec le [service Azure MongoDB](https://www.mongodb.com/scale/mongodb-azure-service). Mais il ne s’agit pas d’un service PaaS fourni par Microsoft. Dans ce cas, Azure héberge simplement cette solution provenant de MongoDB.

En fait, il s’agit simplement d’un avertissement stipulant que vous ne devez pas toujours utiliser l’API MongoDB sur Azure Cosmos DB, comme nous l’avons fait dans eShopOnContainers, car il s’agissait d’un choix pratique pour les conteneurs Linux. La décision doit être basée sur les besoins spécifiques et les tests que vous devez effectuer pour votre application de production.

### <a name="the-code-use-mongodb-api-in-net-core-applications"></a>Le code : utiliser l’API MongoDB dans des applications .NET Core

L’API MongoDB pour .NET est basée sur des packages NuGet que vous devez ajouter à vos projets, comme dans le projet Locations.API présenté dans la figure suivante.

![La vue Explorateur de solutions affichant les dépendances dans les packages NuGet MongoDB.](./media/image21-bis.png)

**Figure 7-22**. Références de packages NuGet de l’API MongoDB dans un projet .NET Core

Examinons le code figurant dans les sections suivantes.

#### <a name="a-model-used-by-mongodb-api"></a>Modèle utilisé par l’API MongoDB

Vous devez tout d’abord définir un modèle qui contiendra les données provenant de la base de données dans l’espace mémoire de votre application. Voici un exemple du modèle utilisé pour Locations dans eShopOnContainers.

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

Quand vous créez un objet MongoClient, il a besoin d’un paramètre fondamental qui est précisément le paramètre `ConnectionString` pointant vers la base de données appropriée. Dans le cas d’eShopOnContainers, la chaîne de connexion peut pointer vers un conteneur Docker MongoDB local ou une base de données Azure Cosmos DB de « production ».  Cette chaîne de connexion provient des variables d’environnement définies dans les fichiers `docker-compose.override.yml` utilisés lors du déploiement avec docker-compose ou Visual Studio, comme dans le code YML suivant.

```yml
# docker-compose.override.yml
version: '3.4'
services:
  # Other services
  locations.api:
    environment:
      # Other settings
      - ConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosql.data}

```

La variable d’environnement `ConnectionString` est résolue de la façon suivante : si la variable globale `ESHOP_AZURE_COSMOSDB` est définie dans le fichier `.env` avec la chaîne de connexion Azure Cosmos DB, elle l’utilise pour accéder à la base de données Azure Cosmos DB dans le cloud. Si elle n’est pas définie, elle prend la valeur mongodb://nosql.data et utilise le conteneur de développement mongodb.

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

Vous devez décommenter la ligne ESHOP_AZURE_COSMOSDB et la mettre à jour avec votre chaîne de connexion Azure Cosmos DB obtenue à partir du portail Azure, comme expliqué dans [Connecter une application MongoDB à Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).

Si la variable globale `ESHOP_AZURE_COSMOSDB` est vide, ce qui signifie qu’elle est en commentaire dans le fichier `.env`, le conteneur utilise une chaîne de connexion MongoDB par défaut pointant vers le conteneur MongoDB local déployé dans eShopOnContainers et nommé `nosql.data`, qui a été défini dans le fichier docker-compose, comme le montre le code .yml suivant. 

``` yml
# docker-compose.yml
version: '3.4'
services:
  # ...Other services...
  nosql.data:
    image: mongo
```

#### <a name="additional-resources"></a>Ressources supplémentaires

- **Modélisation de données de document pour des bases de données NoSQL** \
  <https://docs.microsoft.com/azure/cosmos-db/modeling-data>

- **Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?** \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- **Présentation de l’API Azure Cosmos DB pour MongoDB**  \
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- **Azure Cosmos DB : développer une application web API MongoDB avec .NET et le portail Azure**  \
  [https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet](https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet )

- **Utiliser l’émulateur Azure Cosmos DB pour le développement et le test locaux**  \
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- **Connecter une application MongoDB à Azure Cosmos DB**  \
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- **The Cosmos DB Emulator Docker image (Windows Container)**  \
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- **The MongoDB Docker image (Linux and Windows Container)**  \
  <https://hub.docker.com/\_/mongo/>

- **Utiliser MongoChef (Studio 3T) avec un compte d’API Azure Cosmos DB pour MongoDB**  \
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
>[Précédent](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
>[Suivant](microservice-application-layer-web-api-design.md)
