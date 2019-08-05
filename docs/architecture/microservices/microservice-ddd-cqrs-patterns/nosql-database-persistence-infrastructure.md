---
title: Utilisation de bases de données NoSQL comme infrastructure de persistance
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Comprendre l’utilisation des bases de données NoSql en général et d’Azure Cosmos DB en particulier comme option pour implémenter la persistance.
ms.date: 10/08/2018
ms.openlocfilehash: 023904319651ec91000ff036850c773f66d1a267
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676336"
---
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="dc517-103">Utiliser des bases de données NoSQL comme infrastructure de persistance</span><span class="sxs-lookup"><span data-stu-id="dc517-103">Use NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="dc517-104">Quand vous utilisez des bases de données NoSQL pour votre couche de données d’infrastructure, vous n’utilisez généralement pas un ORM comme Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="dc517-104">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="dc517-105">À la place, vous utilisez l’API fournie par le moteur NoSQL, comme Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB ou des tables Stockage Azure.</span><span class="sxs-lookup"><span data-stu-id="dc517-105">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="dc517-106">Toutefois, quand vous utilisez une base de données NoSQL, en particulier une base de données orientée document comme Azure Cosmos DB, CouchDB ou RavenDB, la façon dont vous concevez votre modèle avec des agrégats DDD est en partie semblable à la façon dont vous pouvez le faire dans EF Core, en ce qui concerne l’identification des racines d’agrégat, les classes d’entité enfants et les classes d’objets de valeur.</span><span class="sxs-lookup"><span data-stu-id="dc517-106">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="dc517-107">Mais finalement, la sélection de la base de données aura un impact sur votre conception.</span><span class="sxs-lookup"><span data-stu-id="dc517-107">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="dc517-108">Quand vous utilisez une base de données orientée document, vous implémentez un agrégat sous la forme d’un document unique, sérialisé au format JSON ou dans un autre format.</span><span class="sxs-lookup"><span data-stu-id="dc517-108">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="dc517-109">Toutefois, l’utilisation de la base de données est transparente du point de vue du code du modèle de domaine.</span><span class="sxs-lookup"><span data-stu-id="dc517-109">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="dc517-110">Quand vous utilisez une base de données NoSQL, vous utilisez toujours des classes d’entité et des classes de racine d’agrégat, mais avec plus de souplesse que quand vous utilisez EF Core, car la persistance n’est pas relationnelle.</span><span class="sxs-lookup"><span data-stu-id="dc517-110">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="dc517-111">La différence réside dans la façon dont vous rendez ce modèle persistant.</span><span class="sxs-lookup"><span data-stu-id="dc517-111">The difference is in how you persist that model.</span></span> <span data-ttu-id="dc517-112">Si vous avez implémenté votre modèle de domaine basé sur des classes d’entité OCT, indépendant de la persistance de l’infrastructure, il pourrait sembler que vous pouvez passer à une autre infrastructure de persistance, même des bases de données relationnelles aux bases de données NoSQL.</span><span class="sxs-lookup"><span data-stu-id="dc517-112">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="dc517-113">Ça ne doit toutefois pas être votre objectif.</span><span class="sxs-lookup"><span data-stu-id="dc517-113">However, that should not be your goal.</span></span> <span data-ttu-id="dc517-114">Il existe toujours des contraintes et des compromis dans les différentes technologies de base de données : c’est pourquoi vous ne pouvez pas avoir le même modèle pour les bases de données relationnelles et les bases de données NoSQL.</span><span class="sxs-lookup"><span data-stu-id="dc517-114">There are always constraints and trade-offs in the different database technologies, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="dc517-115">Modifier les modèles de persistance n’est pas une tâche triviale, car les transactions et les opérations de persistance sont très différentes.</span><span class="sxs-lookup"><span data-stu-id="dc517-115">Changing persistence models is not a trivial task, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="dc517-116">Par exemple, dans une base de données orientée document, une racine d’agrégat peut avoir plusieurs propriétés de collection enfant.</span><span class="sxs-lookup"><span data-stu-id="dc517-116">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="dc517-117">Dans une base de données relationnelle, l’interrogation de plusieurs propriétés de collections enfants n’est pas facile à optimiser, car vous obtenez en retour d’EF une instruction SQL UNION ALL.</span><span class="sxs-lookup"><span data-stu-id="dc517-117">In a relational database, querying multiple child collection properties is not easily optimized, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="dc517-118">Il n’est pas simple d’avoir le même modèle de domaine pour les bases de données relationnelles et les bases de données NoSQL, et il est recommandé de ne pas essayer.</span><span class="sxs-lookup"><span data-stu-id="dc517-118">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try to do it.</span></span> <span data-ttu-id="dc517-119">Vous devez réellement concevoir votre modèle en comprenant comment les données vont être utilisées dans chaque base de données particulière.</span><span class="sxs-lookup"><span data-stu-id="dc517-119">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="dc517-120">Utiliser des bases de données NoSQL présente, entre autre, l’avantage d’avoir des entités plus dénormalisées. De ce fait, vous n’avez pas à définir un mappage de table.</span><span class="sxs-lookup"><span data-stu-id="dc517-120">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="dc517-121">Votre modèle de domaine peut être plus flexible que quand vous utilisez une base de données relationnelle.</span><span class="sxs-lookup"><span data-stu-id="dc517-121">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="dc517-122">Quand vous concevez votre modèle de domaine basé sur des agrégats, le passage à des bases de données NoSQL et orientées document peut être encore plus simple que d’utiliser une base de données relationnelle, car les agrégats que vous concevez sont semblables aux documents sérialisés dans une base de données orientée document.</span><span class="sxs-lookup"><span data-stu-id="dc517-122">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="dc517-123">Vous pouvez ensuite inclure dans ces « conteneurs » toutes les informations dont vous pouvez avoir besoin pour cet agrégat.</span><span class="sxs-lookup"><span data-stu-id="dc517-123">Then you can include in those “bags” all the information you might need for that aggregate.</span></span>

<span data-ttu-id="dc517-124">Par exemple, le code JSON suivant est un exemple d’implémentation d’un agrégat de commandes lors de l’utilisation d’une base de données orientée document.</span><span class="sxs-lookup"><span data-stu-id="dc517-124">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="dc517-125">Il est semblable à l’agrégat de commandes que nous avons implémenté dans l’exemple eShopOnContainers, mais sans utiliser EF Core au-dessous.</span><span class="sxs-lookup"><span data-stu-id="dc517-125">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

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

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a><span data-ttu-id="dc517-126">Introduction à Azure Cosmos DB et à l’API Cosmos DB native</span><span class="sxs-lookup"><span data-stu-id="dc517-126">Introduction to Azure Cosmos DB and the native Cosmos DB API</span></span>

<span data-ttu-id="dc517-127">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) est le service de base de données de Microsoft distribué à l’échelle mondiale pour les applications stratégiques.</span><span class="sxs-lookup"><span data-stu-id="dc517-127">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) is Microsoft's globally distributed database service for mission-critical applications.</span></span> <span data-ttu-id="dc517-128">Azure Cosmos DB offre une [distribution globale clés en main](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), permet une [mise à l’échelle élastique des capacités de débit et de stockage](https://docs.microsoft.com/azure/cosmos-db/partition-data) dans le monde entier, garantit des latences inférieures à 10 millisecondes dans le 99e centile, offre [cinq niveaux de cohérence bien définis](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) et garantit une haute disponibilité, le tout couvert par des [contrats SLA parmi les meilleurs du marché](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span><span class="sxs-lookup"><span data-stu-id="dc517-128">Azure Cosmos DB provides [turn-key global distribution](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastic scaling of throughput and storage](https://docs.microsoft.com/azure/cosmos-db/partition-data) worldwide, single-digit millisecond latencies at the 99th percentile, [five well-defined consistency levels](https://docs.microsoft.com/azure/cosmos-db/consistency-levels), and guaranteed high availability, all backed by [industry-leading SLAs](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span></span> <span data-ttu-id="dc517-129">Azure Cosmos DB [indexe automatiquement les données](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) sans vous obliger à gérer les schémas et les index.</span><span class="sxs-lookup"><span data-stu-id="dc517-129">Azure Cosmos DB [automatically indexes data](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) without requiring you to deal with schema and index management.</span></span> <span data-ttu-id="dc517-130">Il est multimodèle et prend en charge les modèles de données basés sur des documents, des clés-valeurs, des graphiques et des colonnes.</span><span class="sxs-lookup"><span data-stu-id="dc517-130">It is multi-model and supports document, key-value, graph, and columnar data models.</span></span>

<span data-ttu-id="dc517-131">![Azure Cosmos DB est une base de données de latence faible, dont la distribution mondiale est garantie et à laquelle vous pouvez accéder avec quatre protocoles d’API.</span><span class="sxs-lookup"><span data-stu-id="dc517-131">![Azure Cosmos DB is a globally distributed guaranteed low-latency database that can be accessed with four API protocols.</span></span> <span data-ttu-id="dc517-132">](./media/image19.1.png)
**Figure 7-19**.</span><span class="sxs-lookup"><span data-stu-id="dc517-132">](./media/image19.1.png)
**Figure 7-19**.</span></span> <span data-ttu-id="dc517-133">Distribution globale d’Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="dc517-133">Azure Cosmos DB global distribution</span></span>

<span data-ttu-id="dc517-134">Quand vous utilisez un modèle C\# pour implémenter l’agrégat que l’API Azure Cosmos DB doit utiliser, l’agrégat peut être semblable aux classes OCT C\# utilisées avec EF Core.</span><span class="sxs-lookup"><span data-stu-id="dc517-134">When you use a C\# model to implement the aggregate to be used by the Azure Cosmos DB API, the aggregate can be similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="dc517-135">La différence réside dans la façon de les utiliser à partir des couches Application et d’infrastructure, comme dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="dc517-135">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

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

<span data-ttu-id="dc517-136">Comme vous pouvez le voir, la façon dont vous utilisez votre modèle de domaine peut être semblable à la façon dont vous l’utilisez dans votre couche de modèle de domaine quand l’infrastructure est EF.</span><span class="sxs-lookup"><span data-stu-id="dc517-136">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="dc517-137">Vous utilisez toujours les mêmes méthodes de racine d’agrégat pour garantir la cohérence, les invariants et les validations au sein de l’agrégat.</span><span class="sxs-lookup"><span data-stu-id="dc517-137">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="dc517-138">Toutefois, quand vous rendez votre modèle persistant dans la base de données NoSQL, le code et l’API changent considérablement par rapport au code EF Core ou à tout autre code associé à des bases de données relationnelles.</span><span class="sxs-lookup"><span data-stu-id="dc517-138">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a><span data-ttu-id="dc517-139">Implémenter du code .NET ciblant MongoDB et Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="dc517-139">Implement .NET code targeting MongoDB and Azure Cosmos DB</span></span>

### <a name="use-azure-cosmos-db-from-net-containers"></a><span data-ttu-id="dc517-140">Utiliser Azure Cosmos DB à partir de conteneurs .NET</span><span class="sxs-lookup"><span data-stu-id="dc517-140">Use Azure Cosmos DB from .NET containers</span></span>

<span data-ttu-id="dc517-141">Vous pouvez accéder aux bases de données Azure Cosmos DB à partir du code .NET en cours d’exécution dans des conteneurs, comme à partir de n’importe quelle autre application .NET.</span><span class="sxs-lookup"><span data-stu-id="dc517-141">You can access Azure Cosmos DB databases from .NET code running in containers, like from any other .NET application.</span></span> <span data-ttu-id="dc517-142">Par exemple, les microservices Locations.API et Marketing.API dans eShopOnContainers sont implémentés afin de pouvoir consommer des bases de données Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="dc517-142">For instance, the Locations.API and Marketing.API microservices in eShopOnContainers are implemented so they can consume Azure Cosmos DB databases.</span></span>

<span data-ttu-id="dc517-143">Toutefois, il existe une limitation dans Azure Cosmos DB du point de vue de l’environnement de développement Docker.</span><span class="sxs-lookup"><span data-stu-id="dc517-143">However, there’s a limitation in Azure Cosmos DB from a Docker development environment point of view.</span></span> <span data-ttu-id="dc517-144">Même quand il existe un [émulateur Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/local-emulator) local en mesure de s’exécuter sur un ordinateur de développement local (comme un PC), à compter de fin 2017, il prend en charge uniquement Windows, et Linux pas.</span><span class="sxs-lookup"><span data-stu-id="dc517-144">Even when there’s a on-premises [Azure Cosmos DB Emulator](https://docs.microsoft.com/azure/cosmos-db/local-emulator) able to run in a local development machine (like a PC), as of late 2017, it just supports Windows, not Linux.</span></span> 

<span data-ttu-id="dc517-145">Il est également possible d’exécuter cet émulateur sur Docker, mais uniquement sur des conteneurs Windows, et pas avec des conteneurs Linux.</span><span class="sxs-lookup"><span data-stu-id="dc517-145">There is also the possibility to run this emulator on Docker, but just on Windows Containers, not with Linux Containers.</span></span> <span data-ttu-id="dc517-146">Cela constitue un handicap initial pour l’environnement de développement si votre application est déployée comme conteneurs Linux, étant donné qu’actuellement, vous ne pouvez pas déployer en même temps des conteneurs Linux et Windows sur Docker pour Windows.</span><span class="sxs-lookup"><span data-stu-id="dc517-146">That is an initial handicap for the development environment if your application is deployed as Linux containers, since, currently, you cannot deploy Linux and Windows Containers on Docker for Windows at the same time.</span></span> <span data-ttu-id="dc517-147">Tous les conteneurs en cours de déploiement doivent être soit pour Linux, soit pour Windows.</span><span class="sxs-lookup"><span data-stu-id="dc517-147">Either all containers being deployed have to be for Linux or for Windows.</span></span>

<span data-ttu-id="dc517-148">Le déploiement idéal et plus direct pour une solution de développement/test est celui qui permet de déployer vos systèmes de base de données comme des conteneurs avec vos conteneurs personnalisés, afin que vos environnements de développement/test soient toujours cohérents.</span><span class="sxs-lookup"><span data-stu-id="dc517-148">The ideal and more straightforward deployment for a dev/test solution is to be able to deploy your database systems as containers along with your custom containers so your dev/test environments are always consistent.</span></span>

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a><span data-ttu-id="dc517-149">Utiliser l’API MongoDB pour les conteneurs Linux/Windows de développement/test local et Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="dc517-149">Use MongoDB API for local dev/test Linux/Windows containers plus Azure Cosmos DB</span></span>

<span data-ttu-id="dc517-150">Les bases de données Cosmos DB prennent en charge l’API MongoDB pour .NET, ainsi que le protocole filaire MongoDB natif.</span><span class="sxs-lookup"><span data-stu-id="dc517-150">Cosmos DB databases support MongoDB API for .NET as well as the native MongoDB wire protocol.</span></span> <span data-ttu-id="dc517-151">Cela signifie qu’en utilisant des pilotes existants, votre application écrite pour MongoDB peut maintenant communiquer avec Cosmos DB et utiliser des bases de données Cosmos DB au lieu de bases de données MongoDB, comme illustré dans la figure 7-20.</span><span class="sxs-lookup"><span data-stu-id="dc517-151">This means that by using existing drivers, your application written for MongoDB can now communicate with Cosmos DB and use Cosmos DB databases instead of MongoDB databases, as shown in Figure 7-20.</span></span>

<span data-ttu-id="dc517-152">![Cosmos DB prend en charge les API MongoDB pour .NET et le protocole filaire MongoDB ; vous pouvez facilement passer de MongoDB à Cosmos DB. ](./media/image19.2.png)
**Figure 7-20**.</span><span class="sxs-lookup"><span data-stu-id="dc517-152">![Cosmos DB supports MongoDB API for .NET and MongoDB wire protocol, you can easily switch from MongoDb to Cosmos DB.](./media/image19.2.png)
**Figure 7-20**.</span></span> <span data-ttu-id="dc517-153">Utilisation de l’API et du protocole MongoDB pour accéder à Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="dc517-153">Using MongoDB API and protocol to access Azure Cosmos DB</span></span>

<span data-ttu-id="dc517-154">C’est une approche très pratique pour les preuves de concept dans les environnements Docker avec des conteneurs Linux, car l’[image Docker MongoDB](https://hub.docker.com/r/_/mongo/) est une image multi-arch qui prend en charge les conteneurs Docker Linux et Docker Windows.</span><span class="sxs-lookup"><span data-stu-id="dc517-154">This is a very convenient approach for proof of concepts in Docker environments with Linux containers because the [MongoDB Docker image](https://hub.docker.com/r/_/mongo/) is a multi-arch image that supports Docker Linux containers and Docker Windows containers.</span></span>

<span data-ttu-id="dc517-155">Comme le montre l’image suivante, en utilisant l’API MongoDB, eShopOnContainers prend en charge les conteneurs MongoDB Linux et Windows pour l’environnement de développement local, mais ensuite, vous pouvez passer à une solution cloud PaaS scalable, comme Azure Cosmos DB, simplement en [changeant la chaîne de connexion MongoDB pour pointer vers Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="dc517-155">As shown in the following image, by using the MongoDB API, eShopOnContainers supports MongoDB Linux and Windows containers for the local development environment but then, you can move to a scalable, PaaS cloud solution as Azure Cosmos DB by simply [changing the MongoDB connection string to point to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

<span data-ttu-id="dc517-156">![Le microservice Location dans eShopOnContainers est implémenté avec MongoDB, mais vous pouvez le passer sur Cosmos DB en modifiant simplement la chaîne de connexion. ](./media/image20-bis.png)
**Figure 7-21**.</span><span class="sxs-lookup"><span data-stu-id="dc517-156">![The Location microservice in eShopOnContainers is implemented using MongoDB, but can be switched over to Cosmos DB by just changing the connection string.](./media/image20-bis.png)
**Figure 7-21**.</span></span> <span data-ttu-id="dc517-157">eShopOnContainers utilisant des conteneurs MongoDB pour un environnement de développement ou Azure Cosmos DB pour la production</span><span class="sxs-lookup"><span data-stu-id="dc517-157">eShopOnContainers using MongoDB containers for dev-env or Azure Cosmos DB for production</span></span>

<span data-ttu-id="dc517-158">Le service Azure Cosmos DB de production s’exécuterait dans le cloud d’Azure comme service PaaS évolutif.</span><span class="sxs-lookup"><span data-stu-id="dc517-158">The production Azure Cosmos DB would be running in Azure’s cloud as a PaaS and scalable service.</span></span>

<span data-ttu-id="dc517-159">Vos conteneurs .NET Core personnalisés peuvent s’exécuter sur un hôte Docker de développement local (qui utilise Docker pour Windows sur un ordinateur Windows 10) ou être déployés dans un environnement de production, comme Kubernetes dans Azure AKS ou Azure Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="dc517-159">Your custom .NET Core containers can run on a local development Docker host (that is using Docker for Windows in a Windows 10 machine) or be deployed into a production environment, like Kubernetes in Azure AKS or Azure Service Fabric.</span></span> <span data-ttu-id="dc517-160">Dans ce deuxième environnement, vous déployeriez uniquement les conteneurs personnalisés .NET Core mais pas le conteneur MongoDB puisque vous utiliseriez Azure Cosmos DB dans le cloud pour gérer les données en production.</span><span class="sxs-lookup"><span data-stu-id="dc517-160">In this second environment, you would deploy only the .NET Core custom containers but not the MongoDB container since you’d be using Azure Cosmos DB in the cloud for handling the data in production.</span></span>

<span data-ttu-id="dc517-161">Le fait que votre solution puisse s’exécuter dans les deux moteurs de base de données, MongoDB ou Azure Cosmos DB, constitue un avantage indéniable de l’utilisation de l’API MongoDB, car les migrations vers d’autres environnements devraient être faciles.</span><span class="sxs-lookup"><span data-stu-id="dc517-161">A clear benefit of using the MongoDB API is that your solution could run in both database engines, MongoDB or Azure Cosmos DB, so migrations to different environments should be easy.</span></span> <span data-ttu-id="dc517-162">Toutefois, il est parfois utile d’utiliser une API native (c’est-à-dire l’API Cosmos DB native) pour tirer pleinement parti des fonctionnalités d’un moteur de base de données spécifique.</span><span class="sxs-lookup"><span data-stu-id="dc517-162">However, sometimes it is worthwhile to use a native API (that is the native Cosmos DB API) in order to take full advantage of the capabilities of a specific database engine.</span></span>

<span data-ttu-id="dc517-163">Pour obtenir une comparaison supplémentaire entre utiliser simplement MongoDB et utiliser Cosmos DB dans le cloud, consultez les [avantages de l’utilisation d’Azure Cosmos DB dans cette page](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).</span><span class="sxs-lookup"><span data-stu-id="dc517-163">For further comparison between simply using MongoDB versus Cosmos DB in the cloud, see the [Benefits of using Azure Cosmos DB in this page](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).</span></span> 

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a><span data-ttu-id="dc517-164">Analyser votre approche pour les applications de production : API MongoDB et API Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="dc517-164">Analyze your approach for production applications: MongoDB API vs. Cosmos DB API</span></span>

<span data-ttu-id="dc517-165">Dans eShopOnContainers, nous utilisons l’API MongoDB, car notre priorité était fondamentalement d’avoir un environnement de développement/test cohérent utilisant une base de données NoSQL qui pourrait également fonctionner avec Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="dc517-165">In eShopOnContainers, we’re using MongoDB API because our priority was fundamentally to have a consistent dev/test environment using a NoSQL database that could also work with Azure Cosmos DB.</span></span>

<span data-ttu-id="dc517-166">Toutefois, si vous envisagez d’utiliser l’API MongoDB pour accéder à Azure Cosmos DB dans Azure pour des applications de production, vous devez analyser les différences de capacités et de performances lors de l’utilisation de l’API MongoDB pour accéder aux bases de données Azure Cosmos DB par rapport à l’API Azure Cosmos DB native.</span><span class="sxs-lookup"><span data-stu-id="dc517-166">However, if you planning to use MongoDB API to access Azure Cosmos DB in Azure for production applications, you should analyze the differences in capabilities and performance when using MongoDB API to access Azure Cosmos DB databases compared to using the native Azure Cosmos DB API.</span></span> <span data-ttu-id="dc517-167">S’il n’y a pas de différence, vous pouvez utiliser l’API MongoDB, ce qui vous permet de bénéficier de la prise en charge de deux moteurs de base de données NoSQL en même temps.</span><span class="sxs-lookup"><span data-stu-id="dc517-167">If it is similar you can use MongoDB API and you get the benefit of supporting two NoSQL database engines at the same time.</span></span>

<span data-ttu-id="dc517-168">Vous pouvez également utiliser des clusters MongoDB comme base de données de production dans le cloud d’Azure, avec le [service Azure MongoDB](https://www.mongodb.com/scale/mongodb-azure-service).</span><span class="sxs-lookup"><span data-stu-id="dc517-168">You could also use MongoDB clusters as the production database in Azure’s cloud, too, with [MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service).</span></span> <span data-ttu-id="dc517-169">Mais il ne s’agit pas d’un service PaaS fourni par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="dc517-169">But that is not a PaaS service provided by Microsoft.</span></span> <span data-ttu-id="dc517-170">Dans ce cas, Azure héberge simplement cette solution provenant de MongoDB.</span><span class="sxs-lookup"><span data-stu-id="dc517-170">In this case, Azure is just hosting that solution coming from MongoDB.</span></span>

<span data-ttu-id="dc517-171">En fait, il s’agit simplement d’un avertissement stipulant que vous ne devez pas toujours utiliser l’API MongoDB sur Azure Cosmos DB, comme nous l’avons fait dans eShopOnContainers, car il s’agissait d’un choix pratique pour les conteneurs Linux.</span><span class="sxs-lookup"><span data-stu-id="dc517-171">Basically, this is just a disclaimer stating that you shouldn’t always use MongoDB API against Azure Cosmos DB, as we did in eShopOnContainers because it was a convenient choice for Linux containers.</span></span> <span data-ttu-id="dc517-172">La décision doit être basée sur les besoins spécifiques et les tests que vous devez effectuer pour votre application de production.</span><span class="sxs-lookup"><span data-stu-id="dc517-172">The decision should be based on the specific needs and tests you need to do for your production application.</span></span>

### <a name="the-code-use-mongodb-api-in-net-core-applications"></a><span data-ttu-id="dc517-173">Le code : utiliser l’API MongoDB dans des applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="dc517-173">The code: Use MongoDB API in .NET Core applications</span></span>

<span data-ttu-id="dc517-174">L’API MongoDB pour .NET est basée sur des packages NuGet que vous devez ajouter à vos projets, comme dans le projet Locations.API présenté dans la figure suivante.</span><span class="sxs-lookup"><span data-stu-id="dc517-174">MongoDB API for .NET is based on NuGet packages that you need to add to your projects, like in the Locations.API project shown in the following figure.</span></span>

![La vue Explorateur de solutions affichant les dépendances dans les packages NuGet MongoDB.](./media/image21-bis.png)

<span data-ttu-id="dc517-176">**Figure 7-22**.</span><span class="sxs-lookup"><span data-stu-id="dc517-176">**Figure 7-22**.</span></span> <span data-ttu-id="dc517-177">Références de packages NuGet de l’API MongoDB dans un projet .NET Core</span><span class="sxs-lookup"><span data-stu-id="dc517-177">MongoDB API NuGet packages references in a .NET Core project</span></span>

<span data-ttu-id="dc517-178">Examinons le code figurant dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="dc517-178">Let's investigate the code in the following sections.</span></span>

#### <a name="a-model-used-by-mongodb-api"></a><span data-ttu-id="dc517-179">Modèle utilisé par l’API MongoDB</span><span class="sxs-lookup"><span data-stu-id="dc517-179">A Model used by MongoDB API</span></span>

<span data-ttu-id="dc517-180">Vous devez tout d’abord définir un modèle qui contiendra les données provenant de la base de données dans l’espace mémoire de votre application.</span><span class="sxs-lookup"><span data-stu-id="dc517-180">First, you need to define a model that will hold the data coming from the database in your application’s memory space.</span></span> <span data-ttu-id="dc517-181">Voici un exemple du modèle utilisé pour Locations dans eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="dc517-181">Here’s an example of the model used for Locations at eShopOnContainers.</span></span>

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

<span data-ttu-id="dc517-182">Vous pouvez voir qu’il existe plusieurs attributs et types provenant des packages NuGet de MongoDB.</span><span class="sxs-lookup"><span data-stu-id="dc517-182">You can see there are a few attributes and types coming from the MongoDB NuGet packages.</span></span>

<span data-ttu-id="dc517-183">Les bases de données NoSQL conviennent généralement parfaitement pour travailler avec des données hiérarchiques non relationnelles.</span><span class="sxs-lookup"><span data-stu-id="dc517-183">NoSQL databases are usually very well suited for working with non-relational hierarchical data.</span></span> <span data-ttu-id="dc517-184">Dans cet exemple, nous utilisons des types MongoDB spécialement conçus pour les géolocalisations, comme `GeoJson2DGeographicCoordinates`.</span><span class="sxs-lookup"><span data-stu-id="dc517-184">In this example, we are using MongoDB types especially made for geo-locations, like `GeoJson2DGeographicCoordinates`.</span></span>

#### <a name="retrieve-the-database-and-the-collection"></a><span data-ttu-id="dc517-185">Récupérer la base de données et la collection</span><span class="sxs-lookup"><span data-stu-id="dc517-185">Retrieve the database and the collection</span></span>

<span data-ttu-id="dc517-186">Dans eShopOnContainers, nous avons créé un contexte de base de données personnalisé dans lequel nous implémentons le code pour récupérer la base de données et les MongoCollections, comme dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="dc517-186">In eShopOnContainers, we have created a custom database context where we implement the code to retrieve the database and the MongoCollections, as in the following code.</span></span>

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

#### <a name="retrieve-the-data"></a><span data-ttu-id="dc517-187">Récupérer les données</span><span class="sxs-lookup"><span data-stu-id="dc517-187">Retrieve the data</span></span>

<span data-ttu-id="dc517-188">Dans du code C#, comme les contrôleurs d’API web ou l’implémentation de dépôts personnalisés, vous pouvez écrire du code semblable au suivant lors d’une interrogation par le biais de l’API MongoDB.</span><span class="sxs-lookup"><span data-stu-id="dc517-188">In C# code, like Web API controllers or custom Repositories implementation, you can write similar code to the following when querying through the MongoDB API.</span></span> <span data-ttu-id="dc517-189">Notez que l’objet `_context` est une instance de la classe `LocationsContext` précédente.</span><span class="sxs-lookup"><span data-stu-id="dc517-189">Note that the `_context` object is an instance of the previous `LocationsContext` class.</span></span>

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a><span data-ttu-id="dc517-190">Utiliser env-var dans le fichier docker-compose.override.yml pour la chaîne de connexion MongoDB</span><span class="sxs-lookup"><span data-stu-id="dc517-190">Use an env-var in the docker-compose.override.yml file for the MongoDB connection string</span></span>

<span data-ttu-id="dc517-191">Quand vous créez un objet MongoClient, il a besoin d’un paramètre fondamental qui est précisément le paramètre `ConnectionString` pointant vers la base de données appropriée.</span><span class="sxs-lookup"><span data-stu-id="dc517-191">When creating a MongoClient object, it needs a fundamental parameter which is precisely the `ConnectionString` parameter pointing to the right database.</span></span> <span data-ttu-id="dc517-192">Dans le cas d’eShopOnContainers, la chaîne de connexion peut pointer vers un conteneur Docker MongoDB local ou une base de données Azure Cosmos DB de « production ».</span><span class="sxs-lookup"><span data-stu-id="dc517-192">In the case of eShopOnContainers, the connection string can point to a local MongoDB Docker container or to a “production” Azure Cosmos DB database.</span></span>  <span data-ttu-id="dc517-193">Cette chaîne de connexion provient des variables d’environnement définies dans les fichiers `docker-compose.override.yml` utilisés lors du déploiement avec docker-compose ou Visual Studio, comme dans le code YML suivant.</span><span class="sxs-lookup"><span data-stu-id="dc517-193">That connection string comes from the environment variables defined in the `docker-compose.override.yml` files used when deploying with docker-compose or Visual Studio, as in the following yml code.</span></span>

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

<span data-ttu-id="dc517-194">La variable d’environnement `ConnectionString` est résolue de la façon suivante : si la variable globale `ESHOP_AZURE_COSMOSDB` est définie dans le fichier `.env` avec la chaîne de connexion Azure Cosmos DB, elle l’utilise pour accéder à la base de données Azure Cosmos DB dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="dc517-194">The `ConnectionString` environment variable is resolved this way: If the `ESHOP_AZURE_COSMOSDB` global variable is defined in the `.env` file with the Azure Cosmos DB connection string, it will use it to access the Azure Cosmos DB database in the cloud.</span></span> <span data-ttu-id="dc517-195">Si elle n’est pas définie, elle prend la valeur mongodb://nosql.data et utilise le conteneur de développement mongodb.</span><span class="sxs-lookup"><span data-stu-id="dc517-195">If it’s not defined, it will take the mongodb://nosql.data value and use the development mongodb container.</span></span>

<span data-ttu-id="dc517-196">Le code suivant présente le fichier `.env` avec la variable d’environnement globale de la chaîne de connexion Azure Cosmos DB, comme implémenté dans eShopOnContainers :</span><span class="sxs-lookup"><span data-stu-id="dc517-196">The following code shows the `.env` file with the Azure Cosmos DB connection string global environment variable, as implemented in eShopOnContainers:</span></span>

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

<span data-ttu-id="dc517-197">Vous devez décommenter la ligne ESHOP_AZURE_COSMOSDB et la mettre à jour avec votre chaîne de connexion Azure Cosmos DB obtenue à partir du portail Azure, comme expliqué dans [Connecter une application MongoDB à Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span><span class="sxs-lookup"><span data-stu-id="dc517-197">You should uncomment the ESHOP_AZURE_COSMOSDB line and update it with your Azure Cosmos DB connection string obtained from the Azure portal as explained in [Connect a MongoDB application to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

<span data-ttu-id="dc517-198">Si la variable globale `ESHOP_AZURE_COSMOSDB` est vide, ce qui signifie qu’elle est en commentaire dans le fichier `.env`, le conteneur utilise une chaîne de connexion MongoDB par défaut pointant vers le conteneur MongoDB local déployé dans eShopOnContainers et nommé `nosql.data`, qui a été défini dans le fichier docker-compose, comme le montre le code .yml suivant.</span><span class="sxs-lookup"><span data-stu-id="dc517-198">If the `ESHOP_AZURE_COSMOSDB` global variable is empty, meaning that it is commented out in the `.env` file, then the container uses a default MongoDB connection string pointing to the local MongoDB container deployed in eShopOnContainers which is named `nosql.data` and was defined at the docker-compose file, as shown in the following .yml code.</span></span> 

``` yml
# docker-compose.yml
version: '3.4'
services:
  # ...Other services...
  nosql.data:
    image: mongo
```

#### <a name="additional-resources"></a><span data-ttu-id="dc517-199">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="dc517-199">Additional resources</span></span>

- <span data-ttu-id="dc517-200">**Modélisation de données de document pour des bases de données NoSQL** </span><span class="sxs-lookup"><span data-stu-id="dc517-200">**Modeling document data for NoSQL databases** </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/modeling-data>

- <span data-ttu-id="dc517-201">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**</span><span class="sxs-lookup"><span data-stu-id="dc517-201">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**</span></span> \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- <span data-ttu-id="dc517-202">**Présentation de l’API Azure Cosmos DB pour MongoDB**  </span><span class="sxs-lookup"><span data-stu-id="dc517-202">**Introduction to Azure Cosmos DB: API for MongoDB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- <span data-ttu-id="dc517-203">**Azure Cosmos DB : développer une application web API MongoDB avec .NET et le portail Azure**  </span><span class="sxs-lookup"><span data-stu-id="dc517-203">**Azure Cosmos DB: Build a MongoDB API web app with .NET and the Azure portal**  </span></span>\
  [https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet](https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet )

- <span data-ttu-id="dc517-204">**Utiliser l’émulateur Azure Cosmos DB pour le développement et le test locaux**  </span><span class="sxs-lookup"><span data-stu-id="dc517-204">**Use the Azure Cosmos DB Emulator for local development and testing**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- <span data-ttu-id="dc517-205">**Connecter une application MongoDB à Azure Cosmos DB**  </span><span class="sxs-lookup"><span data-stu-id="dc517-205">**Connect a MongoDB application to Azure Cosmos DB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- <span data-ttu-id="dc517-206">**The Cosmos DB Emulator Docker image (Windows Container)**   </span><span class="sxs-lookup"><span data-stu-id="dc517-206">**The Cosmos DB Emulator Docker image (Windows Container)**  </span></span>\
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- <span data-ttu-id="dc517-207">**The MongoDB Docker image (Linux and Windows Container)**   </span><span class="sxs-lookup"><span data-stu-id="dc517-207">**The MongoDB Docker image (Linux and Windows Container)**  </span></span>\
  <https://hub.docker.com/\_/mongo/>

- <span data-ttu-id="dc517-208">**Utiliser MongoChef (Studio 3T) avec un compte d’API Azure Cosmos DB pour MongoDB**  </span><span class="sxs-lookup"><span data-stu-id="dc517-208">**Use MongoChef (Studio 3T) with an Azure Cosmos DB: API for MongoDB account**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
><span data-ttu-id="dc517-209">[Précédent](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
>[Suivant](microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="dc517-209">[Previous](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
[Next](microservice-application-layer-web-api-design.md)</span></span>
