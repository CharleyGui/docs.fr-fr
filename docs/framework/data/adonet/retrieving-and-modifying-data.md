---
title: Récupération et modification de données
description: Dans le .NET Framework, les fournisseurs de données dans ADO.NET jouent le rôle de pont entre une application et une source de données pour lire et mettre à jour des données.
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: f916324dc829526a5e6b0078021b09786755f666
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286609"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a><span data-ttu-id="226e5-103">Extraction et modification de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="226e5-103">Retrieving and Modifying Data in ADO.NET</span></span>
<span data-ttu-id="226e5-104">Une fonction principale de toute application de base de données consiste à se connecter à une source de données et extraire les données qu'elle contient.</span><span class="sxs-lookup"><span data-stu-id="226e5-104">A primary function of any database application is connecting to a data source and retrieving the data that it contains.</span></span> <span data-ttu-id="226e5-105">Les fournisseurs de données de .NET Framework de ADO.NET jouent le rôle de pont entre une application et une source de données, ce qui vous permet d’exécuter des commandes ainsi que de récupérer des données à l’aide d’un **DataReader** ou d’un **DataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="226e5-105">The .NET Framework data providers of ADO.NET serve as a bridge between an application and a data source, allowing you to execute commands as well as to retrieve data by using a **DataReader** or a **DataAdapter**.</span></span> <span data-ttu-id="226e5-106">Une fonction clé de toute application de base de données est la capacité à mettre à jour les données stockées dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="226e5-106">A key function of any database application is the ability to update the data that is stored in the database.</span></span> <span data-ttu-id="226e5-107">Dans ADO.NET, la mise à jour des données implique l’utilisation des objets **DataAdapter** et <xref:System.Data.DataSet> , et des objets **Command** , et peut également impliquer l’utilisation de transactions.</span><span class="sxs-lookup"><span data-stu-id="226e5-107">In ADO.NET, updating data involves using the **DataAdapter** and <xref:System.Data.DataSet>, and **Command** objects; and it may also involve using transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="226e5-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="226e5-108">In This Section</span></span>  
 [<span data-ttu-id="226e5-109">Connexion à une source de données</span><span class="sxs-lookup"><span data-stu-id="226e5-109">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)  
 <span data-ttu-id="226e5-110">Décrit comment établir une connexion à une source de données et comment travailler avec des événements de connexion.</span><span class="sxs-lookup"><span data-stu-id="226e5-110">Describes how to establish a connection to a data source and how to work with connection events.</span></span>  
  
 [<span data-ttu-id="226e5-111">Chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="226e5-111">Connection Strings</span></span>](connection-strings.md)  
 <span data-ttu-id="226e5-112">Contient des rubriques qui décrivent divers aspects de l'utilisation de chaînes de connexion, y compris des mots clés de chaîne de connexion, des informations de sécurité, ainsi que de leur stockage et leur extraction.</span><span class="sxs-lookup"><span data-stu-id="226e5-112">Contains topics describing various aspects of using connection strings, including connection string keywords, security info, and storing and retrieving them.</span></span>  
  
 [<span data-ttu-id="226e5-113">Regroupement de connexions</span><span class="sxs-lookup"><span data-stu-id="226e5-113">Connection Pooling</span></span>](connection-pooling.md)  
 <span data-ttu-id="226e5-114">Décrit le regroupement de connexions pour les fournisseurs de données .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="226e5-114">Describes connection pooling for the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="226e5-115">Commandes et paramètres</span><span class="sxs-lookup"><span data-stu-id="226e5-115">Commands and Parameters</span></span>](commands-and-parameters.md)  
 <span data-ttu-id="226e5-116">Contient des rubriques qui décrivent comment créer des commandes et des générateurs de commande, configurer des paramètres et exécuter des commandes pour extraire et modifier des données.</span><span class="sxs-lookup"><span data-stu-id="226e5-116">Contains topics describing how to create commands and command builders, configure parameters, and how to execute commands to retrieve and modify data.</span></span>  
  
 [<span data-ttu-id="226e5-117">DataAdapters et DataReaders</span><span class="sxs-lookup"><span data-stu-id="226e5-117">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)  
 <span data-ttu-id="226e5-118">Contient des rubriques qui décrivent les objets DataReader et DataAdapter, les paramètres, la gestion des événements DataAdapter et l'exécution d'opérations par lots.</span><span class="sxs-lookup"><span data-stu-id="226e5-118">Contains topics describing DataReaders, DataAdapters, parameters, handling DataAdapter events and performing batch operations.</span></span>  
  
 [<span data-ttu-id="226e5-119">Transactions et accès simultané</span><span class="sxs-lookup"><span data-stu-id="226e5-119">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)  
 <span data-ttu-id="226e5-120">Contient des rubriques qui décrivent comment effectuer des transactions locales, des transactions distribuées et travailler avec l’accès concurrentiel optimiste.</span><span class="sxs-lookup"><span data-stu-id="226e5-120">Contains topics describing how to perform local transactions, distributed transactions, and work with optimistic concurrency.</span></span>  
  
 [<span data-ttu-id="226e5-121">Récupération de valeurs d’identité ou de numérotation automatique</span><span class="sxs-lookup"><span data-stu-id="226e5-121">Retrieving Identity or Autonumber Values</span></span>](retrieving-identity-or-autonumber-values.md)  
 <span data-ttu-id="226e5-122">Fournit un exemple de mappage des valeurs générées pour une colonne d' **identité** dans une table SQL Server ou pour un champ **AutoNumber** d’une table Microsoft Access, à une colonne d’une ligne insérée dans une table.</span><span class="sxs-lookup"><span data-stu-id="226e5-122">Provides an example of mapping the values generated for an **identity** column in a SQL Server table or for an **Autonumber** field in a Microsoft Access table, to a column of an inserted row in a table.</span></span> <span data-ttu-id="226e5-123">Traite de la fusion de valeurs d'identité dans un `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="226e5-123">Discusses merging identity values in a `DataTable`.</span></span>  
  
 [<span data-ttu-id="226e5-124">Récupération de données binaires</span><span class="sxs-lookup"><span data-stu-id="226e5-124">Retrieving Binary Data</span></span>](retrieving-binary-data.md)  
 <span data-ttu-id="226e5-125">Décrit comment récupérer des données binaires ou des structures de données volumineuses à l’aide de `CommandBehavior` .`SequentialAccess`</span><span class="sxs-lookup"><span data-stu-id="226e5-125">Describes how to retrieve binary data or large data structures using `CommandBehavior`.`SequentialAccess`</span></span> <span data-ttu-id="226e5-126">pour modifier le comportement par défaut d’un `DataReader` .</span><span class="sxs-lookup"><span data-stu-id="226e5-126">to modify the default behavior of a `DataReader`.</span></span>  
  
 [<span data-ttu-id="226e5-127">Modification des données avec les procédures stockées</span><span class="sxs-lookup"><span data-stu-id="226e5-127">Modifying Data with Stored Procedures</span></span>](modifying-data-with-stored-procedures.md)  
 <span data-ttu-id="226e5-128">Décrit comment utiliser des paramètres d'entrée et sortie de procédure stockée afin d'insérer une ligne dans une base de données et retourner une nouvelle valeur d'identité.</span><span class="sxs-lookup"><span data-stu-id="226e5-128">Describes how to use stored procedure input parameters and output parameters to insert a row in a database, returning a new identity value.</span></span>  
  
 [<span data-ttu-id="226e5-129">Récupération des informations de schéma de base de données</span><span class="sxs-lookup"><span data-stu-id="226e5-129">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)  
 <span data-ttu-id="226e5-130">Décrit la manière d'obtenir des bases de données ou des catalogues disponibles, des tables et des vues dans une base de données, des contraintes existantes pour des tables et d'autres informations de schéma à partir d'une source de données.</span><span class="sxs-lookup"><span data-stu-id="226e5-130">Describes how to obtain available databases or catalogs, tables and views in a database, constraints that exist for tables, and other schema information from a data source.</span></span>  
  
 [<span data-ttu-id="226e5-131">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="226e5-131">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="226e5-132">Décrit le modèle fabrique de fournisseurs et illustre l'utilisation des classes de base dans l'espace de noms `System.Data.Common`.</span><span class="sxs-lookup"><span data-stu-id="226e5-132">Describes the provider factory model and demonstrates how to use the base classes in the `System.Data.Common` namespace.</span></span>  
  
 [<span data-ttu-id="226e5-133">Suivi des données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="226e5-133">Data Tracing in ADO.NET</span></span>](data-tracing.md)  
 <span data-ttu-id="226e5-134">Décrit la manière dont ADO.NET offre une fonctionnalité intégrée de traçage de données.</span><span class="sxs-lookup"><span data-stu-id="226e5-134">Describes how ADO.NET provides built-in data tracing functionality.</span></span>  
  
 [<span data-ttu-id="226e5-135">Compteurs de performances</span><span class="sxs-lookup"><span data-stu-id="226e5-135">Performance Counters</span></span>](performance-counters.md)  
 <span data-ttu-id="226e5-136">Décrit les compteurs de performance disponibles pour `SqlClient` et `OracleClient`.</span><span class="sxs-lookup"><span data-stu-id="226e5-136">Describes performance counters available for `SqlClient` and `OracleClient`.</span></span>  
  
 [<span data-ttu-id="226e5-137">Programmation asynchrone</span><span class="sxs-lookup"><span data-stu-id="226e5-137">Asynchronous Programming</span></span>](asynchronous-programming.md)  
 <span data-ttu-id="226e5-138">Décrit la prise en charge de ADO.NET pour la programmation asynchrone.</span><span class="sxs-lookup"><span data-stu-id="226e5-138">Describes ADO.NET support for asynchronous programming.</span></span>  
  
 [<span data-ttu-id="226e5-139">Prise en charge de la diffusion en continu pour SqlClient</span><span class="sxs-lookup"><span data-stu-id="226e5-139">SqlClient Streaming Support</span></span>](sqlclient-streaming-support.md)  
 <span data-ttu-id="226e5-140">Explique comment écrire des applications qui diffusent en continu des données à partir de SQL Server sans qu’elles soient entièrement chargées en mémoire.</span><span class="sxs-lookup"><span data-stu-id="226e5-140">Discusses how to write applications that stream data from SQL Server without having it fully loaded in memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="226e5-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="226e5-141">See also</span></span>

- [<span data-ttu-id="226e5-142">Mappages de types de données dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="226e5-142">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="226e5-143">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="226e5-143">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="226e5-144">Sécurisation des applications ADO.NET</span><span class="sxs-lookup"><span data-stu-id="226e5-144">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)
- [<span data-ttu-id="226e5-145">SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="226e5-145">SQL Server and ADO.NET</span></span>](./sql/index.md)
- [<span data-ttu-id="226e5-146">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="226e5-146">ADO.NET Overview</span></span>](ado-net-overview.md)
