---
title: Données distribuées
description: Architecture des applications .NET natives Cloud pour Azure | Données distribuées pour les applications Cloud natives
ms.date: 06/30/2019
ms.openlocfilehash: 92086c52b02360e90461aea9ad23a2068224e187
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183132"
---
# <a name="distributed-data-for-cloud-native-apps"></a><span data-ttu-id="2a5e4-103">Données distribuées pour les applications Cloud natives</span><span class="sxs-lookup"><span data-stu-id="2a5e4-103">Distributed data for cloud-native apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="2a5e4-104">Lors de la construction d’un système Cloud natif qui se compose de nombreux microservices indépendants, la façon dont vous pensez aux modifications du stockage de données.</span><span class="sxs-lookup"><span data-stu-id="2a5e4-104">When constructing a cloud-native system that consists of many independent microservices, the way you think about data storage changes.</span></span>

<span data-ttu-id="2a5e4-105">Les applications monolithiques traditionnelles favorisent une banque de données centralisée illustrée dans la figure 5-1.</span><span class="sxs-lookup"><span data-stu-id="2a5e4-105">Traditional monolithic applications favor a centralized data store shown in Figure 5-1.</span></span> 

![Base de données monolithique unique](./media/single-monolithic-database.png)

<span data-ttu-id="2a5e4-107">**Figure 5-1**.</span><span class="sxs-lookup"><span data-stu-id="2a5e4-107">**Figure 5-1**.</span></span> <span data-ttu-id="2a5e4-108">Base de données monolithique unique</span><span class="sxs-lookup"><span data-stu-id="2a5e4-108">Single monolithic database</span></span>

<span data-ttu-id="2a5e4-109">Notez dans la figure précédente comment tous les composants d’application consomment une base de données relationnelle unique.</span><span class="sxs-lookup"><span data-stu-id="2a5e4-109">Note in the previous figure how all of the application components consume a single relational database.</span></span>

<span data-ttu-id="2a5e4-110">Cette approche présente de nombreux avantages.</span><span class="sxs-lookup"><span data-stu-id="2a5e4-110">There are many benefits to this approach.</span></span> <span data-ttu-id="2a5e4-111">Il est facile d’interroger les données réparties sur plusieurs tables et il est facile d’implémenter des [transactions ACID](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) qui garantissent la cohérence des données.</span><span class="sxs-lookup"><span data-stu-id="2a5e4-111">It's straightforward to query data spread across  multiple tables, and it's straightforward to implement [ACID transactions](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) that ensure data consistency.</span></span> <span data-ttu-id="2a5e4-112">Vous obtenez toujours une *cohérence immédiate*: toutes vos mises à jour de données ou aucune d’elles ne le fait.</span><span class="sxs-lookup"><span data-stu-id="2a5e4-112">You always end up with *immediate consistency*: either all your data updates or none of it does.</span></span>

<span data-ttu-id="2a5e4-113">Les systèmes natifs du Cloud favorisent une architecture de données illustrée dans la figure 5-2, dans laquelle chaque microservice possède et encapsule ses propres données.</span><span class="sxs-lookup"><span data-stu-id="2a5e4-113">Cloud-native systems favor a data architecture shown in Figure 5-2 in which each microservice owns and encapsulates its own data.</span></span>

![Plusieurs bases de données entre les microservices](./media/data-across-microservices.png)

<span data-ttu-id="2a5e4-115">**Figure 5-2**.</span><span class="sxs-lookup"><span data-stu-id="2a5e4-115">**Figure 5-2**.</span></span> <span data-ttu-id="2a5e4-116">Plusieurs bases de données entre les microservices</span><span class="sxs-lookup"><span data-stu-id="2a5e4-116">Multiple databases across microservices</span></span>

<span data-ttu-id="2a5e4-117">Notez comment, dans la figure précédente, chaque microservice possède et encapsule le magasin de données informatique et expose uniquement des données au monde extérieur à partir de son API publique.</span><span class="sxs-lookup"><span data-stu-id="2a5e4-117">Note how in the previous figure each microservice owns and encapsulates it data store and only exposes data to the outside world from its public API.</span></span>
 
<span data-ttu-id="2a5e4-118">Ce modèle permet à chaque microservice d’évoluer indépendamment sans avoir à coordonner les modifications du schéma de données avec d’autres microservices.</span><span class="sxs-lookup"><span data-stu-id="2a5e4-118">This model enables each microservice to evolve independently without having to coordinate data schema changes with other microservices.</span></span> <span data-ttu-id="2a5e4-119">Chaque microservice est libre d’implémenter le type de magasin de données (base de données relationnelle, base de données de documents, magasin clé-valeur) qui correspond le mieux à ses besoins.</span><span class="sxs-lookup"><span data-stu-id="2a5e4-119">Each microservice is free to implement the data store (relational database, document database, key-value store) type that best matches its needs.</span></span> <span data-ttu-id="2a5e4-120">Lors de l’exécution, chaque microservice peut mettre à l’échelle ses données en conséquence.</span><span class="sxs-lookup"><span data-stu-id="2a5e4-120">At runtime, each microservice can scale its data accordingly.</span></span> <span data-ttu-id="2a5e4-121">Cela est illustré dans la figure 5-3 :</span><span class="sxs-lookup"><span data-stu-id="2a5e4-121">This is shown in Figure 5-3:</span></span>

![Persistance des données polyglotte](./media/polyglot-data-persistence.png)

<span data-ttu-id="2a5e4-123">**Figure 5-3**.</span><span class="sxs-lookup"><span data-stu-id="2a5e4-123">**Figure 5-3**.</span></span> <span data-ttu-id="2a5e4-124">Persistance des données polyglotte</span><span class="sxs-lookup"><span data-stu-id="2a5e4-124">Polyglot data persistence</span></span>

<span data-ttu-id="2a5e4-125">Notez comment, dans la figure précédente, le catalogue de produits et les microservices d’inventaire adoptent les bases de données relationnelles, le microservice de commande, une base de données de documents NoSql et le microservice de panier d’achat, qui est un magasin de valeurs de clé externe.</span><span class="sxs-lookup"><span data-stu-id="2a5e4-125">Note how in the previous figure the product catalog and inventory microservices adopt relational databases, the ordering microservice, a NoSql document database, and the shopping cart microservice, which is an external key-value store.</span></span> <span data-ttu-id="2a5e4-126">Bien que les bases de données relationnelles restent pertinentes pour les microservices avec des données complexes, les bases de données NoSQL ont acquis une popularité considérable, offrant ainsi une adaptation, une recherche rapide et une haute disponibilité.</span><span class="sxs-lookup"><span data-stu-id="2a5e4-126">While relational databases remain relevant for microservices with complex data, NoSQL databases have gained considerable popularity, providing adaptability, fast lookup, and high availability.</span></span> <span data-ttu-id="2a5e4-127">Leur nature sans schéma permet aux développeurs de quitter une architecture de classes de données typées et de ORM, ce qui rend la modification coûteuse et fastidieuse.</span><span class="sxs-lookup"><span data-stu-id="2a5e4-127">Their schemaless nature allows developers to move away from an architecture of typed data classes and ORMs that make change expensive and time-consuming.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2a5e4-128">[Précédent](service-mesh-communication-infrastructure.md)
>[Suivant](data-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="2a5e4-128">[Previous](service-mesh-communication-infrastructure.md)
[Next](data-patterns.md)</span></span>
