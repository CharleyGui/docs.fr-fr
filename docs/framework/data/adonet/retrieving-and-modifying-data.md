---
title: Récupération et modification de données
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: 65c373ecff004e219527754bf2e9cc56837dc305
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980052"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a><span data-ttu-id="fa951-102">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fa951-102">Retrieving and Modifying Data in ADO.NET</span></span>
<span data-ttu-id="fa951-103">Une fonction principale de toute application de base de données consiste à se connecter à une source de données et extraire les données qu'elle contient.</span><span class="sxs-lookup"><span data-stu-id="fa951-103">A primary function of any database application is connecting to a data source and retrieving the data that it contains.</span></span> <span data-ttu-id="fa951-104">Les fournisseurs de données de .NET Framework de ADO.NET jouent le rôle de pont entre une application et une source de données, ce qui vous permet d’exécuter des commandes ainsi que de récupérer des données à l’aide d’un **DataReader** ou d’un **DataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="fa951-104">The .NET Framework data providers of ADO.NET serve as a bridge between an application and a data source, allowing you to execute commands as well as to retrieve data by using a **DataReader** or a **DataAdapter**.</span></span> <span data-ttu-id="fa951-105">Une fonction clé de toute application de base de données est la capacité à mettre à jour les données stockées dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="fa951-105">A key function of any database application is the ability to update the data that is stored in the database.</span></span> <span data-ttu-id="fa951-106">Dans ADO.NET, la mise à jour des données implique l’utilisation des objets **DataAdapter** et <xref:System.Data.DataSet>, ainsi que des objets **Command** . Il peut également impliquer l’utilisation de transactions.</span><span class="sxs-lookup"><span data-stu-id="fa951-106">In ADO.NET, updating data involves using the **DataAdapter** and <xref:System.Data.DataSet>, and **Command** objects; and it may also involve using transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa951-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="fa951-107">In This Section</span></span>  
 [<span data-ttu-id="fa951-108">Connexion à une source de données</span><span class="sxs-lookup"><span data-stu-id="fa951-108">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)  
 <span data-ttu-id="fa951-109">Décrit comment établir une connexion à une source de données et comment travailler avec des événements de connexion.</span><span class="sxs-lookup"><span data-stu-id="fa951-109">Describes how to establish a connection to a data source and how to work with connection events.</span></span>  
  
 [<span data-ttu-id="fa951-110">Chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="fa951-110">Connection Strings</span></span>](connection-strings.md)  
 <span data-ttu-id="fa951-111">Contient des rubriques qui décrivent divers aspects de l'utilisation de chaînes de connexion, y compris des mots clés de chaîne de connexion, des informations de sécurité, ainsi que de leur stockage et leur extraction.</span><span class="sxs-lookup"><span data-stu-id="fa951-111">Contains topics describing various aspects of using connection strings, including connection string keywords, security info, and storing and retrieving them.</span></span>  
  
 [<span data-ttu-id="fa951-112">Regroupement de connexions</span><span class="sxs-lookup"><span data-stu-id="fa951-112">Connection Pooling</span></span>](connection-pooling.md)  
 <span data-ttu-id="fa951-113">Décrit le regroupement de connexions pour les fournisseurs de données .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fa951-113">Describes connection pooling for the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="fa951-114">Commandes et paramètres</span><span class="sxs-lookup"><span data-stu-id="fa951-114">Commands and Parameters</span></span>](commands-and-parameters.md)  
 <span data-ttu-id="fa951-115">Contient des rubriques qui décrivent comment créer des commandes et des générateurs de commande, configurer des paramètres et exécuter des commandes pour extraire et modifier des données.</span><span class="sxs-lookup"><span data-stu-id="fa951-115">Contains topics describing how to create commands and command builders, configure parameters, and how to execute commands to retrieve and modify data.</span></span>  
  
 [<span data-ttu-id="fa951-116">DataAdapters et DataReaders</span><span class="sxs-lookup"><span data-stu-id="fa951-116">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)  
 <span data-ttu-id="fa951-117">Contient des rubriques qui décrivent les objets DataReader et DataAdapter, les paramètres, la gestion des événements DataAdapter et l'exécution d'opérations par lots.</span><span class="sxs-lookup"><span data-stu-id="fa951-117">Contains topics describing DataReaders, DataAdapters, parameters, handling DataAdapter events and performing batch operations.</span></span>  
  
 [<span data-ttu-id="fa951-118">Transactions et accès concurrentiel</span><span class="sxs-lookup"><span data-stu-id="fa951-118">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)  
 <span data-ttu-id="fa951-119">Contient des rubriques qui décrivent comment effectuer des transactions locales, des transactions distribuées et travailler avec l’accès concurrentiel optimiste.</span><span class="sxs-lookup"><span data-stu-id="fa951-119">Contains topics describing how to perform local transactions, distributed transactions, and work with optimistic concurrency.</span></span>  
  
 [<span data-ttu-id="fa951-120">Récupération de valeurs d’identité ou de numérotation automatique</span><span class="sxs-lookup"><span data-stu-id="fa951-120">Retrieving Identity or Autonumber Values</span></span>](retrieving-identity-or-autonumber-values.md)  
 <span data-ttu-id="fa951-121">Fournit un exemple de mappage des valeurs générées pour une colonne d' **identité** dans une table SQL Server ou pour un champ **AutoNumber** d’une table Microsoft Access, à une colonne d’une ligne insérée dans une table.</span><span class="sxs-lookup"><span data-stu-id="fa951-121">Provides an example of mapping the values generated for an **identity** column in a SQL Server table or for an **Autonumber** field in a Microsoft Access table, to a column of an inserted row in a table.</span></span> <span data-ttu-id="fa951-122">Traite de la fusion de valeurs d'identité dans un `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="fa951-122">Discusses merging identity values in a `DataTable`.</span></span>  
  
 [<span data-ttu-id="fa951-123">Récupération de données binaires</span><span class="sxs-lookup"><span data-stu-id="fa951-123">Retrieving Binary Data</span></span>](retrieving-binary-data.md)  
 <span data-ttu-id="fa951-124">Décrit comment récupérer des données binaires ou des structures de données volumineuses à l’aide de `CommandBehavior`.`SequentialAccess`</span><span class="sxs-lookup"><span data-stu-id="fa951-124">Describes how to retrieve binary data or large data structures using `CommandBehavior`.`SequentialAccess`</span></span> <span data-ttu-id="fa951-125">pour modifier le comportement par défaut d’un `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="fa951-125">to modify the default behavior of a `DataReader`.</span></span>  
  
 [<span data-ttu-id="fa951-126">Modification des données avec les procédures stockées</span><span class="sxs-lookup"><span data-stu-id="fa951-126">Modifying Data with Stored Procedures</span></span>](modifying-data-with-stored-procedures.md)  
 <span data-ttu-id="fa951-127">Décrit comment utiliser des paramètres d'entrée et sortie de procédure stockée afin d'insérer une ligne dans une base de données et retourner une nouvelle valeur d'identité.</span><span class="sxs-lookup"><span data-stu-id="fa951-127">Describes how to use stored procedure input parameters and output parameters to insert a row in a database, returning a new identity value.</span></span>  
  
 [<span data-ttu-id="fa951-128">Récupération des informations de schéma de base de données</span><span class="sxs-lookup"><span data-stu-id="fa951-128">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)  
 <span data-ttu-id="fa951-129">Décrit la manière d'obtenir des bases de données ou des catalogues disponibles, des tables et des vues dans une base de données, des contraintes existantes pour des tables et d'autres informations de schéma à partir d'une source de données.</span><span class="sxs-lookup"><span data-stu-id="fa951-129">Describes how to obtain available databases or catalogs, tables and views in a database, constraints that exist for tables, and other schema information from a data source.</span></span>  
  
 [<span data-ttu-id="fa951-130">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="fa951-130">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="fa951-131">Décrit le modèle fabrique de fournisseurs et illustre l'utilisation des classes de base dans l'espace de noms `System.Data.Common`.</span><span class="sxs-lookup"><span data-stu-id="fa951-131">Describes the provider factory model and demonstrates how to use the base classes in the `System.Data.Common` namespace.</span></span>  
  
 [<span data-ttu-id="fa951-132">Suivi des données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fa951-132">Data Tracing in ADO.NET</span></span>](data-tracing.md)  
 <span data-ttu-id="fa951-133">Décrit la manière dont ADO.NET offre une fonctionnalité intégrée de traçage de données.</span><span class="sxs-lookup"><span data-stu-id="fa951-133">Describes how ADO.NET provides built-in data tracing functionality.</span></span>  
  
 [<span data-ttu-id="fa951-134">Performance Counters</span><span class="sxs-lookup"><span data-stu-id="fa951-134">Performance Counters</span></span>](performance-counters.md)  
 <span data-ttu-id="fa951-135">Décrit les compteurs de performance disponibles pour `SqlClient` et `OracleClient`.</span><span class="sxs-lookup"><span data-stu-id="fa951-135">Describes performance counters available for `SqlClient` and `OracleClient`.</span></span>  
  
 [<span data-ttu-id="fa951-136">Programmation asynchrone</span><span class="sxs-lookup"><span data-stu-id="fa951-136">Asynchronous Programming</span></span>](asynchronous-programming.md)  
 <span data-ttu-id="fa951-137">Décrit la prise en charge de ADO.NET pour la programmation asynchrone.</span><span class="sxs-lookup"><span data-stu-id="fa951-137">Describes ADO.NET support for asynchronous programming.</span></span>  
  
 [<span data-ttu-id="fa951-138">Prise en charge du streaming pour SqlClient</span><span class="sxs-lookup"><span data-stu-id="fa951-138">SqlClient Streaming Support</span></span>](sqlclient-streaming-support.md)  
 <span data-ttu-id="fa951-139">Explique comment écrire des applications qui diffusent en continu des données à partir de SQL Server sans qu’elles soient entièrement chargées en mémoire.</span><span class="sxs-lookup"><span data-stu-id="fa951-139">Discusses how to write applications that stream data from SQL Server without having it fully loaded in memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa951-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa951-140">See also</span></span>

- [<span data-ttu-id="fa951-141">Mappages de types de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fa951-141">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="fa951-142">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="fa951-142">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="fa951-143">Sécurisation des applications ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fa951-143">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)
- [<span data-ttu-id="fa951-144">SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fa951-144">SQL Server and ADO.NET</span></span>](./sql/index.md)
- [<span data-ttu-id="fa951-145">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fa951-145">ADO.NET Overview</span></span>](ado-net-overview.md)
