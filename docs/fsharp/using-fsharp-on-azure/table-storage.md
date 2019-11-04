---
title: Bien démarrer avec le stockage Table Azure en F#
description: Stockez des données structurées dans le Cloud à l’aide du stockage table Azure ou Azure Cosmos DB.
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: 6833e2264f7543f50b94892b6980140e4bf1cdd1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424607"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a><span data-ttu-id="6533d-103">Prise en main du stockage table Azure et du Azure Cosmos DB API Table à l’aide de F\#</span><span class="sxs-lookup"><span data-stu-id="6533d-103">Get started with Azure Table storage and the Azure Cosmos DB Table API using F\#</span></span>

<span data-ttu-id="6533d-104">Le stockage table Azure est un service qui stocke des données NoSQL structurées dans le Cloud.</span><span class="sxs-lookup"><span data-stu-id="6533d-104">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="6533d-105">Le stockage table est un magasin de clés/attributs avec une conception sans schéma.</span><span class="sxs-lookup"><span data-stu-id="6533d-105">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="6533d-106">Étant donné que le stockage de tables est sans schéma, il est facile d’adapter vos données à mesure que les besoins de votre application évoluent.</span><span class="sxs-lookup"><span data-stu-id="6533d-106">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="6533d-107">L’accès aux données est rapide et économique pour tous les types d’applications.</span><span class="sxs-lookup"><span data-stu-id="6533d-107">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="6533d-108">Le stockage de table est généralement beaucoup plus économique que le SQL traditionnel pour des volumes de données similaires.</span><span class="sxs-lookup"><span data-stu-id="6533d-108">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="6533d-109">Vous pouvez utiliser le stockage de tables pour stocker des jeux de données flexibles, tels que des données utilisateur pour des applications Web, des carnets d’adresses, des informations sur les appareils et tout autre type de métadonnées requis par votre service.</span><span class="sxs-lookup"><span data-stu-id="6533d-109">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="6533d-110">Vous pouvez stocker n’importe quel nombre d’entités dans une table et un compte de stockage peut contenir un nombre illimité de tables, jusqu’à la limite de capacité du compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="6533d-110">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

<span data-ttu-id="6533d-111">Azure Cosmos DB fournit la API Table pour les applications écrites pour le stockage de tables Azure et qui nécessitent des fonctionnalités Premium telles que :</span><span class="sxs-lookup"><span data-stu-id="6533d-111">Azure Cosmos DB provides the Table API for applications that are written for Azure Table storage and that require premium capabilities such as:</span></span>

- <span data-ttu-id="6533d-112">Distribution mondiale clé en main.</span><span class="sxs-lookup"><span data-stu-id="6533d-112">Turnkey global distribution.</span></span>
- <span data-ttu-id="6533d-113">Débit dédié dans le monde entier.</span><span class="sxs-lookup"><span data-stu-id="6533d-113">Dedicated throughput worldwide.</span></span>
- <span data-ttu-id="6533d-114">Latences à un chiffre en millisecondes au 99e centile.</span><span class="sxs-lookup"><span data-stu-id="6533d-114">Single-digit millisecond latencies at the 99th percentile.</span></span>
- <span data-ttu-id="6533d-115">Haute disponibilité garantie.</span><span class="sxs-lookup"><span data-stu-id="6533d-115">Guaranteed high availability.</span></span>
- <span data-ttu-id="6533d-116">Indexation secondaire automatique.</span><span class="sxs-lookup"><span data-stu-id="6533d-116">Automatic secondary indexing.</span></span>

<span data-ttu-id="6533d-117">Les applications écrites pour le stockage de tables Azure peuvent migrer vers Azure Cosmos DB à l’aide de la API Table sans aucune modification de code et tirer parti des fonctionnalités Premium.</span><span class="sxs-lookup"><span data-stu-id="6533d-117">Applications written for Azure Table storage can migrate to Azure Cosmos DB by using the Table API with no code changes and take advantage of premium capabilities.</span></span> <span data-ttu-id="6533d-118">Le API Table possède des kits de développement logiciel (SDK) clients disponibles pour .NET, Java, Python et node. js.</span><span class="sxs-lookup"><span data-stu-id="6533d-118">The Table API has client SDKs available for .NET, Java, Python, and Node.js.</span></span>

<span data-ttu-id="6533d-119">Pour plus d’informations, consultez [Introduction à Azure Cosmos DB API table](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span><span class="sxs-lookup"><span data-stu-id="6533d-119">For more information, see [Introduction to Azure Cosmos DB Table API](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span></span>

## <a name="about-this-tutorial"></a><span data-ttu-id="6533d-120">À propos de ce didacticiel</span><span class="sxs-lookup"><span data-stu-id="6533d-120">About this tutorial</span></span>

<span data-ttu-id="6533d-121">Ce didacticiel montre comment écrire F# du code pour effectuer des tâches courantes à l’aide du stockage table Azure ou de la API table Azure Cosmos dB, notamment la création et la suppression d’une table et l’insertion, la mise à jour, la suppression et l’interrogation de données de table.</span><span class="sxs-lookup"><span data-stu-id="6533d-121">This tutorial shows how to write F# code to do some common tasks using Azure Table storage or the Azure Cosmos DB Table API, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6533d-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6533d-122">Prerequisites</span></span>

<span data-ttu-id="6533d-123">Pour utiliser ce guide, vous devez d’abord [créer un compte de stockage Azure ou un](/azure/storage/storage-create-storage-account) compte de [Azure Cosmos DB](https://azure.microsoft.com/try/cosmosdb/).</span><span class="sxs-lookup"><span data-stu-id="6533d-123">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account) or [Azure Cosmos DB account](https://azure.microsoft.com/try/cosmosdb/).</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="6533d-124">Créer un F# script et démarrer F# interactive</span><span class="sxs-lookup"><span data-stu-id="6533d-124">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="6533d-125">Les exemples de cet article peuvent être utilisés dans une F# application ou un F# script.</span><span class="sxs-lookup"><span data-stu-id="6533d-125">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="6533d-126">Pour créer un F# script, créez un fichier avec l’extension `.fsx`, par exemple `tables.fsx`, dans votre F# environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="6533d-126">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="6533d-127">Ensuite, utilisez un [Gestionnaire de package](package-management.md) comme [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) pour installer le package `WindowsAzure.Storage` et référencez `WindowsAzure.Storage.dll` dans votre script à l’aide d’une directive `#r`.</span><span class="sxs-lookup"><span data-stu-id="6533d-127">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="6533d-128">Réexécutez-le pour `Microsoft.WindowsAzure.ConfigurationManager` afin d’obtenir l’espace de noms Microsoft. Azure.</span><span class="sxs-lookup"><span data-stu-id="6533d-128">Do it again for `Microsoft.WindowsAzure.ConfigurationManager` in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="6533d-129">Ajouter des déclarations d’espace de noms</span><span class="sxs-lookup"><span data-stu-id="6533d-129">Add namespace declarations</span></span>

<span data-ttu-id="6533d-130">Ajoutez les instructions `open` suivantes en haut du fichier `tables.fsx` :</span><span class="sxs-lookup"><span data-stu-id="6533d-130">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a><span data-ttu-id="6533d-131">Récupérer votre chaîne de connexion de stockage Azure</span><span class="sxs-lookup"><span data-stu-id="6533d-131">Get your Azure Storage connection string</span></span>

<span data-ttu-id="6533d-132">Si vous vous connectez à un service de table de stockage Azure, vous aurez besoin de votre chaîne de connexion pour ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="6533d-132">If you're connecting to Azure Storage Table service, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="6533d-133">Vous pouvez copier votre chaîne de connexion à partir du Portail Azure.</span><span class="sxs-lookup"><span data-stu-id="6533d-133">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="6533d-134">Pour plus d’informations sur les chaînes de connexion, consultez [configurer des chaînes de connexion de stockage](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="6533d-134">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

### <a name="get-your-azure-cosmos-db-connection-string"></a><span data-ttu-id="6533d-135">Obtient votre chaîne de connexion Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="6533d-135">Get your Azure Cosmos DB connection string</span></span>

<span data-ttu-id="6533d-136">Si vous vous connectez à Azure Cosmos DB, vous aurez besoin de votre chaîne de connexion pour ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="6533d-136">If you're connecting to Azure Cosmos DB, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="6533d-137">Vous pouvez copier votre chaîne de connexion à partir du Portail Azure.</span><span class="sxs-lookup"><span data-stu-id="6533d-137">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="6533d-138">Dans le Portail Azure, dans votre compte Cosmos DB, accédez à **paramètres** > **chaîne de connexion**, puis cliquez sur le bouton **copier** pour copier votre chaîne de connexion principale.</span><span class="sxs-lookup"><span data-stu-id="6533d-138">In the Azure portal, in your Cosmos DB account, go to **Settings** > **Connection String**, and click the **Copy** button to copy your Primary Connection String.</span></span>

<span data-ttu-id="6533d-139">Pour le didacticiel, entrez votre chaîne de connexion dans votre script, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="6533d-139">For the tutorial, enter your connection string in your script, like the following example:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="6533d-140">Toutefois, cela n’est **pas recommandé** pour les projets réels.</span><span class="sxs-lookup"><span data-stu-id="6533d-140">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="6533d-141">Votre clé de compte de stockage est similaire au mot de passe racine de votre compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="6533d-141">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="6533d-142">Veillez toujours à protéger votre clé de compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="6533d-142">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="6533d-143">Évitez de la distribuer à d’autres utilisateurs, de la coder en dur ou de l’enregistrer dans un fichier texte brut accessible à d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="6533d-143">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="6533d-144">Vous pouvez régénérer votre clé à l’aide du portail Azure si vous pensez qu’elle a peut-être été compromise.</span><span class="sxs-lookup"><span data-stu-id="6533d-144">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="6533d-145">Pour les applications réelles, la meilleure façon de gérer votre chaîne de connexion de stockage se trouve dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="6533d-145">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="6533d-146">Pour extraire la chaîne de connexion d’un fichier de configuration, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="6533d-146">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="6533d-147">L’utilisation d’Azure Configuration Manager est facultative.</span><span class="sxs-lookup"><span data-stu-id="6533d-147">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="6533d-148">Vous pouvez également utiliser une API telle que le type `ConfigurationManager` de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6533d-148">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="6533d-149">Analyser la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="6533d-149">Parse the connection string</span></span>

<span data-ttu-id="6533d-150">Pour analyser la chaîne de connexion, utilisez :</span><span class="sxs-lookup"><span data-stu-id="6533d-150">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="6533d-151">Cela retourne un `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="6533d-151">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="6533d-152">Créer le client du service de table</span><span class="sxs-lookup"><span data-stu-id="6533d-152">Create the Table service client</span></span>

<span data-ttu-id="6533d-153">La classe `CloudTableClient` vous permet de récupérer des tables et des entités dans le stockage table.</span><span class="sxs-lookup"><span data-stu-id="6533d-153">The `CloudTableClient` class enables you to retrieve tables and entities in Table storage.</span></span> <span data-ttu-id="6533d-154">Voici un moyen de créer le client de service :</span><span class="sxs-lookup"><span data-stu-id="6533d-154">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="6533d-155">Vous êtes maintenant prêt à écrire du code qui lit et écrit des données dans le stockage de table.</span><span class="sxs-lookup"><span data-stu-id="6533d-155">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

### <a name="create-a-table"></a><span data-ttu-id="6533d-156">Créer une table</span><span class="sxs-lookup"><span data-stu-id="6533d-156">Create a table</span></span>

<span data-ttu-id="6533d-157">Cet exemple montre comment créer une table si elle n’existe pas déjà :</span><span class="sxs-lookup"><span data-stu-id="6533d-157">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a><span data-ttu-id="6533d-158">Ajouter une entité à une table</span><span class="sxs-lookup"><span data-stu-id="6533d-158">Add an entity to a table</span></span>

<span data-ttu-id="6533d-159">Une entité doit avoir un type qui hérite de `TableEntity`.</span><span class="sxs-lookup"><span data-stu-id="6533d-159">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="6533d-160">Vous pouvez étendre `TableEntity` comme vous le souhaitez, mais votre type *doit* avoir un constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="6533d-160">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="6533d-161">Seules les propriétés qui ont à la fois `get` et `set` sont stockées dans votre table Azure.</span><span class="sxs-lookup"><span data-stu-id="6533d-161">Only properties that have both `get` and `set` are stored in your Azure Table.</span></span>

<span data-ttu-id="6533d-162">La clé de partition et de ligne d’une entité identifie de façon unique l’entité dans la table.</span><span class="sxs-lookup"><span data-stu-id="6533d-162">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="6533d-163">Les entités avec la même clé de partition peuvent être interrogées plus rapidement que celles avec des clés de partition différentes, mais l’utilisation de clés de partition diverses permet une plus grande évolutivité des opérations parallèles.</span><span class="sxs-lookup"><span data-stu-id="6533d-163">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="6533d-164">Voici un exemple de `Customer` qui utilise la `lastName` comme clé de partition et la `firstName` comme clé de ligne.</span><span class="sxs-lookup"><span data-stu-id="6533d-164">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="6533d-165">À présent, ajoutez `Customer` à la table.</span><span class="sxs-lookup"><span data-stu-id="6533d-165">Now add `Customer` to the table.</span></span> <span data-ttu-id="6533d-166">Pour ce faire, créez un `TableOperation` qui s’exécute sur la table.</span><span class="sxs-lookup"><span data-stu-id="6533d-166">To do so, create a `TableOperation` that executes on the table.</span></span> <span data-ttu-id="6533d-167">Dans ce cas, vous créez une opération `Insert`.</span><span class="sxs-lookup"><span data-stu-id="6533d-167">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a><span data-ttu-id="6533d-168">Insérer un lot d’entités</span><span class="sxs-lookup"><span data-stu-id="6533d-168">Insert a batch of entities</span></span>

<span data-ttu-id="6533d-169">Vous pouvez insérer un lot d’entités dans une table à l’aide d’une seule opération d’écriture.</span><span class="sxs-lookup"><span data-stu-id="6533d-169">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="6533d-170">Les opérations de traitement par lots vous permettent de combiner des opérations en une seule exécution, mais elles présentent des restrictions :</span><span class="sxs-lookup"><span data-stu-id="6533d-170">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="6533d-171">Vous pouvez effectuer des mises à jour, des suppressions et des insertions dans la même opération de traitement par lot.</span><span class="sxs-lookup"><span data-stu-id="6533d-171">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="6533d-172">Une opération par lot peut inclure jusqu’à 100 entités.</span><span class="sxs-lookup"><span data-stu-id="6533d-172">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="6533d-173">Toutes les entités d’une opération de traitement par lot doivent avoir la même clé de partition.</span><span class="sxs-lookup"><span data-stu-id="6533d-173">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="6533d-174">Bien qu’il soit possible d’exécuter une requête dans le cadre d’une opération de traitement par lot, il doit s’agir de la seule opération dans le lot.</span><span class="sxs-lookup"><span data-stu-id="6533d-174">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="6533d-175">Voici du code qui combine deux insertions dans une opération de traitement par lot :</span><span class="sxs-lookup"><span data-stu-id="6533d-175">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="6533d-176">Récupérer toutes les entités d’une partition</span><span class="sxs-lookup"><span data-stu-id="6533d-176">Retrieve all entities in a partition</span></span>

<span data-ttu-id="6533d-177">Pour interroger une table pour toutes les entités d’une partition, utilisez un objet `TableQuery`.</span><span class="sxs-lookup"><span data-stu-id="6533d-177">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="6533d-178">Ici, vous filtrez les entités où « Smith » est la clé de partition.</span><span class="sxs-lookup"><span data-stu-id="6533d-178">Here, you filter for entities where "Smith" is the partition key.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

<span data-ttu-id="6533d-179">Vous allez maintenant imprimer les résultats :</span><span class="sxs-lookup"><span data-stu-id="6533d-179">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="6533d-180">Récupérer une plage d’entités dans une partition</span><span class="sxs-lookup"><span data-stu-id="6533d-180">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="6533d-181">Si vous ne souhaitez pas interroger toutes les entités d’une partition, vous pouvez spécifier une plage en combinant le filtre de clé de partition avec un filtre de clé de ligne.</span><span class="sxs-lookup"><span data-stu-id="6533d-181">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="6533d-182">Ici, vous utilisez deux filtres pour obtenir toutes les entités dans la partition « Smith » où la clé de ligne (prénom) commence par une lettre antérieure à « M » dans l’alphabet.</span><span class="sxs-lookup"><span data-stu-id="6533d-182">Here, you use two filters to get all entities in the "Smith" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="6533d-183">Vous allez maintenant imprimer les résultats :</span><span class="sxs-lookup"><span data-stu-id="6533d-183">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a><span data-ttu-id="6533d-184">Récupérer une seule entité</span><span class="sxs-lookup"><span data-stu-id="6533d-184">Retrieve a single entity</span></span>

<span data-ttu-id="6533d-185">Vous pouvez écrire une requête pour récupérer une seule entité spécifique.</span><span class="sxs-lookup"><span data-stu-id="6533d-185">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="6533d-186">Ici, vous utilisez un `TableOperation` pour spécifier le client « Ben Smith ».</span><span class="sxs-lookup"><span data-stu-id="6533d-186">Here, you use a `TableOperation` to specify the customer "Ben Smith".</span></span> <span data-ttu-id="6533d-187">Au lieu d’une collection, vous récupérez une `Customer`.</span><span class="sxs-lookup"><span data-stu-id="6533d-187">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="6533d-188">La méthode la plus rapide pour récupérer une seule entité à partir du service de table consiste à spécifier à la fois la clé de partition et la clé de ligne dans une requête.</span><span class="sxs-lookup"><span data-stu-id="6533d-188">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="6533d-189">Vous allez maintenant imprimer les résultats :</span><span class="sxs-lookup"><span data-stu-id="6533d-189">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a><span data-ttu-id="6533d-190">Remplacer une entité</span><span class="sxs-lookup"><span data-stu-id="6533d-190">Replace an entity</span></span>

<span data-ttu-id="6533d-191">Pour mettre à jour une entité, récupérez-la à partir du service de table, modifiez l’objet d’entité, puis enregistrez les modifications dans le service de table à l’aide d’une opération `Replace`.</span><span class="sxs-lookup"><span data-stu-id="6533d-191">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="6533d-192">Cela entraîne le remplacement complet de l’entité sur le serveur, sauf si l’entité sur le serveur a changé depuis sa récupération, auquel cas l’opération échoue.</span><span class="sxs-lookup"><span data-stu-id="6533d-192">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation fails.</span></span> <span data-ttu-id="6533d-193">Cet échec consiste à empêcher votre application de remplacer par inadvertance les modifications à partir d’autres sources.</span><span class="sxs-lookup"><span data-stu-id="6533d-193">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a><span data-ttu-id="6533d-194">Insérer ou remplacer une entité</span><span class="sxs-lookup"><span data-stu-id="6533d-194">Insert-or-replace an entity</span></span>

<span data-ttu-id="6533d-195">Parfois, vous ne savez pas si une entité existe dans la table.</span><span class="sxs-lookup"><span data-stu-id="6533d-195">Sometimes, you don't know whether an entity exists in the table.</span></span> <span data-ttu-id="6533d-196">Et si c’est le cas, les valeurs actuelles stockées dans celui-ci ne sont plus nécessaires.</span><span class="sxs-lookup"><span data-stu-id="6533d-196">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="6533d-197">Vous pouvez utiliser `InsertOrReplace` pour créer l’entité, ou la remplacer si elle existe, quel que soit son état.</span><span class="sxs-lookup"><span data-stu-id="6533d-197">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="6533d-198">Interroger un sous-ensemble de propriétés d’entité</span><span class="sxs-lookup"><span data-stu-id="6533d-198">Query a subset of entity properties</span></span>

<span data-ttu-id="6533d-199">Une requête de table peut récupérer uniquement quelques propriétés à partir d’une entité, et non pas toutes.</span><span class="sxs-lookup"><span data-stu-id="6533d-199">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="6533d-200">Cette technique, appelée projection, peut améliorer les performances des requêtes, en particulier pour les entités volumineuses.</span><span class="sxs-lookup"><span data-stu-id="6533d-200">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="6533d-201">Ici, vous retournez uniquement les adresses de messagerie à l’aide de `DynamicTableEntity` et `EntityResolver`.</span><span class="sxs-lookup"><span data-stu-id="6533d-201">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="6533d-202">Notez que la projection n’est pas prise en charge sur l’émulateur de stockage local, de sorte que ce code s’exécute uniquement lorsque vous utilisez un compte sur le service de table.</span><span class="sxs-lookup"><span data-stu-id="6533d-202">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="6533d-203">Récupérer des entités dans des pages de manière asynchrone</span><span class="sxs-lookup"><span data-stu-id="6533d-203">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="6533d-204">Si vous lisez un grand nombre d’entités et que vous souhaitez les traiter à mesure qu’elles sont récupérées au lieu d’attendre qu’elles soient retournées, vous pouvez utiliser une requête segmentée.</span><span class="sxs-lookup"><span data-stu-id="6533d-204">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="6533d-205">Ici, vous retournez les résultats dans les pages à l’aide d’un flux de travail asynchrone afin que l’exécution ne soit pas bloquée pendant que vous attendez un grand nombre de résultats à retourner.</span><span class="sxs-lookup"><span data-stu-id="6533d-205">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

<span data-ttu-id="6533d-206">Vous exécutez maintenant ce calcul de façon synchrone :</span><span class="sxs-lookup"><span data-stu-id="6533d-206">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a><span data-ttu-id="6533d-207">Supprimer une entité</span><span class="sxs-lookup"><span data-stu-id="6533d-207">Delete an entity</span></span>

<span data-ttu-id="6533d-208">Vous pouvez supprimer une entité après l’avoir récupérée.</span><span class="sxs-lookup"><span data-stu-id="6533d-208">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="6533d-209">Comme pour la mise à jour d’une entité, cette opération échoue si l’entité a changé depuis que vous l’avez récupérée.</span><span class="sxs-lookup"><span data-stu-id="6533d-209">As with updating an entity, this fails if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a><span data-ttu-id="6533d-210">Supprimer une table</span><span class="sxs-lookup"><span data-stu-id="6533d-210">Delete a table</span></span>

<span data-ttu-id="6533d-211">Vous pouvez supprimer une table d’un compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="6533d-211">You can delete a table from a storage account.</span></span> <span data-ttu-id="6533d-212">Une table qui a été supprimée ne peut pas être recréée pendant une période de temps après la suppression.</span><span class="sxs-lookup"><span data-stu-id="6533d-212">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a><span data-ttu-id="6533d-213">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="6533d-213">Next steps</span></span>

<span data-ttu-id="6533d-214">Maintenant que vous avez appris les principes de base du stockage table, suivez ces liens pour en savoir plus sur les tâches de stockage plus complexes et le Azure Cosmos DB API Table.</span><span class="sxs-lookup"><span data-stu-id="6533d-214">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks and the Azure Cosmos DB Table API.</span></span>

- [<span data-ttu-id="6533d-215">Présentation de Azure Cosmos DB API Table</span><span class="sxs-lookup"><span data-stu-id="6533d-215">Introduction to Azure Cosmos DB Table API</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [<span data-ttu-id="6533d-216">Référence de la bibliothèque cliente de stockage pour .NET</span><span class="sxs-lookup"><span data-stu-id="6533d-216">Storage Client Library for .NET reference</span></span>](https://docs.microsoft.com/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="6533d-217">Fournisseur de type de stockage Azure</span><span class="sxs-lookup"><span data-stu-id="6533d-217">Azure Storage Type Provider</span></span>](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="6533d-218">Blog de l’équipe stockage Azure</span><span class="sxs-lookup"><span data-stu-id="6533d-218">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [<span data-ttu-id="6533d-219">Configuration de chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="6533d-219">Configuring Connection Strings</span></span>](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
