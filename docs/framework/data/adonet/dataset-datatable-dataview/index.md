---
title: DataSets, DataTables et DataViews
description: Découvrez plusieurs façons d’utiliser un jeu de données ADO.NET, une représentation résidente en mémoire de données qui fournit un modèle de programmation relationnel cohérent.
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: f6562452261cbc1f7ee36fb264b858646a42e4f5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286894"
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="ee84f-103">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="ee84f-103">DataSets, DataTables, and DataViews</span></span>
<span data-ttu-id="ee84f-104">L'objet <xref:System.Data.DataSet> ADO.NET est une représentation de données résidente en mémoire qui propose un modèle de programmation relationnel cohérent, quelle que soit la source des données qu'il contient.</span><span class="sxs-lookup"><span data-stu-id="ee84f-104">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="ee84f-105">Un objet <xref:System.Data.DataSet> représente un jeu de données complet, y compris les tables qui contiennent et organisent les données et y appliquent des contraintes, ainsi que les relations entre les tables.</span><span class="sxs-lookup"><span data-stu-id="ee84f-105">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
 <span data-ttu-id="ee84f-106">L'utilisation d'un objet <xref:System.Data.DataSet> peut se faire via différentes méthodes qui peuvent être appliquées indépendamment les unes des autres ou combinées.</span><span class="sxs-lookup"><span data-stu-id="ee84f-106">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="ee84f-107">Vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="ee84f-107">You can:</span></span>  
  
- <span data-ttu-id="ee84f-108">Créer par programmation un objet <xref:System.Data.DataTable>, <xref:System.Data.DataRelation> et <xref:System.Data.Constraint> dans un objet <xref:System.Data.DataSet>, puis remplir les tables de données.</span><span class="sxs-lookup"><span data-stu-id="ee84f-108">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
- <span data-ttu-id="ee84f-109">Remplir l'objet <xref:System.Data.DataSet> de tables de données provenant d'une source de données relationnelles existante à l'aide d'un objet `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="ee84f-109">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
- <span data-ttu-id="ee84f-110">Charger et rendre persistent le contenu de l'objet <xref:System.Data.DataSet> à l'aide de XML.</span><span class="sxs-lookup"><span data-stu-id="ee84f-110">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="ee84f-111">Pour plus d’informations, consultez [Utilisation de XML dans un DataSet](using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="ee84f-111">For more information, see [Using XML in a DataSet](using-xml-in-a-dataset.md).</span></span>  
  
 <span data-ttu-id="ee84f-112">Un objet <xref:System.Data.DataSet> fortement typé peut aussi être transporté au moyen d’un service web XML.</span><span class="sxs-lookup"><span data-stu-id="ee84f-112">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="ee84f-113">Le design de l’objet <xref:System.Data.DataSet> le rend idéal pour le transport de données à l’aide des services web XML.</span><span class="sxs-lookup"><span data-stu-id="ee84f-113">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="ee84f-114">Pour une vue d’ensemble des services web XML, consultez [Vue d’ensemble des services web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ee84f-114">For an overview of XML Web services, see [XML Web Services Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span></span> <span data-ttu-id="ee84f-115">Pour obtenir un exemple d’utilisation d’un <xref:System.Data.DataSet> à partir d’un service web XML, consultez [Consommation d’un DataSet à partir d’un service web XML](consuming-a-dataset-from-an-xml-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="ee84f-115">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ee84f-116">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ee84f-116">In This Section</span></span>  
 [<span data-ttu-id="ee84f-117">Création d’un DataSet</span><span class="sxs-lookup"><span data-stu-id="ee84f-117">Creating a DataSet</span></span>](creating-a-dataset.md)  
 <span data-ttu-id="ee84f-118">Décrit la syntaxe permettant de créer une instance d'un objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="ee84f-118">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="ee84f-119">Ajout d'un nouveau DataTable à un DataSet</span><span class="sxs-lookup"><span data-stu-id="ee84f-119">Adding a DataTable to a DataSet</span></span>](adding-a-datatable-to-a-dataset.md)  
 <span data-ttu-id="ee84f-120">Explique comment créer et ajouter des tables et des colonnes à un objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="ee84f-120">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="ee84f-121">Ajout de DataRelations</span><span class="sxs-lookup"><span data-stu-id="ee84f-121">Adding DataRelations</span></span>](adding-datarelations.md)  
 <span data-ttu-id="ee84f-122">Explique comment créer des relations entre différentes tables d'un objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="ee84f-122">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="ee84f-123">Parcours des DataRelations</span><span class="sxs-lookup"><span data-stu-id="ee84f-123">Navigating DataRelations</span></span>](navigating-datarelations.md)  
 <span data-ttu-id="ee84f-124">Explique comment utiliser les relations entre différentes tables d'un objet <xref:System.Data.DataSet> afin de retourner les lignes enfants ou parentes d'une relation parent-enfant.</span><span class="sxs-lookup"><span data-stu-id="ee84f-124">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 [<span data-ttu-id="ee84f-125">Fusion de contenu de DataSet</span><span class="sxs-lookup"><span data-stu-id="ee84f-125">Merging DataSet Contents</span></span>](merging-dataset-contents.md)  
 <span data-ttu-id="ee84f-126">Décrit comment fusionner le contenu d’un tableau <xref:System.Data.DataSet>, <xref:System.Data.DataTable> ou <xref:System.Data.DataRow> dans un autre objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="ee84f-126">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="ee84f-127">Copie de contenu de DataSet</span><span class="sxs-lookup"><span data-stu-id="ee84f-127">Copying DataSet Contents</span></span>](copying-dataset-contents.md)  
 <span data-ttu-id="ee84f-128">Explique comment créer une copie d'un objet <xref:System.Data.DataSet> susceptible de contenir un schéma et des données spécifiées.</span><span class="sxs-lookup"><span data-stu-id="ee84f-128">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 [<span data-ttu-id="ee84f-129">Gestion des événements de DataSet</span><span class="sxs-lookup"><span data-stu-id="ee84f-129">Handling DataSet Events</span></span>](handling-dataset-events.md)  
 <span data-ttu-id="ee84f-130">Décrit les événements d'un objet <xref:System.Data.DataSet> et comment les utiliser.</span><span class="sxs-lookup"><span data-stu-id="ee84f-130">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 [<span data-ttu-id="ee84f-131">Datasets typés</span><span class="sxs-lookup"><span data-stu-id="ee84f-131">Typed DataSets</span></span>](typed-datasets.md)  
 <span data-ttu-id="ee84f-132">Explique ce qu'est un objet <xref:System.Data.DataSet> typé et comment en créer un et l'utiliser.</span><span class="sxs-lookup"><span data-stu-id="ee84f-132">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="ee84f-133">DataTables</span><span class="sxs-lookup"><span data-stu-id="ee84f-133">DataTables</span></span>](datatables.md)  
 <span data-ttu-id="ee84f-134">Explique comment créer un objet <xref:System.Data.DataTable>, définir le schéma et manipuler les données.</span><span class="sxs-lookup"><span data-stu-id="ee84f-134">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="ee84f-135">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="ee84f-135">DataTableReaders</span></span>](datatablereaders.md)  
 <span data-ttu-id="ee84f-136">Explique comment créer et utiliser un <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="ee84f-136">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="ee84f-137">DataViews</span><span class="sxs-lookup"><span data-stu-id="ee84f-137">DataViews</span></span>](dataviews.md)  
 <span data-ttu-id="ee84f-138">Décrit la façon de créer et d'utiliser des `DataViews` et d'utiliser des événements <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="ee84f-138">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 [<span data-ttu-id="ee84f-139">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="ee84f-139">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="ee84f-140">Explique comment l'objet <xref:System.Data.DataSet> interagit avec XML en tant que source de données, notamment en ce qui concerne le chargement et la persistance du contenu d'un objet <xref:System.Data.DataSet> en tant que données XML.</span><span class="sxs-lookup"><span data-stu-id="ee84f-140">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 [<span data-ttu-id="ee84f-141">Consommation d’un DataSet à partir d’un service web XML</span><span class="sxs-lookup"><span data-stu-id="ee84f-141">Consuming a DataSet from an XML Web Service</span></span>](consuming-a-dataset-from-an-xml-web-service.md)  
 <span data-ttu-id="ee84f-142">Explique comment créer un service web XML qui utilise un <xref:System.Data.DataSet> pour le transport des données.</span><span class="sxs-lookup"><span data-stu-id="ee84f-142">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ee84f-143">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="ee84f-143">Related Sections</span></span>  
 [<span data-ttu-id="ee84f-144">Nouveautés dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ee84f-144">What's New in ADO.NET</span></span>](../whats-new.md)  
 <span data-ttu-id="ee84f-145">Introduit des fonctionnalités nouvelles dans ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="ee84f-145">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="ee84f-146">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ee84f-146">ADO.NET Overview</span></span>](../ado-net-overview.md)  
 <span data-ttu-id="ee84f-147">Propose une introduction à la conception et aux composants de la technologie ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="ee84f-147">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="ee84f-148">Remplissage d’un DataSet à partir d’un DataAdapter</span><span class="sxs-lookup"><span data-stu-id="ee84f-148">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="ee84f-149">Explique comment charger un **DataSet** avec des données provenant d’une source de données.</span><span class="sxs-lookup"><span data-stu-id="ee84f-149">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 [<span data-ttu-id="ee84f-150">Mise à jour des sources de données avec les DataAdapter</span><span class="sxs-lookup"><span data-stu-id="ee84f-150">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="ee84f-151">Explique comment répercuter à la source de données les modifications apportées aux données d’un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="ee84f-151">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 [<span data-ttu-id="ee84f-152">Ajout de contraintes existantes à un DataSet</span><span class="sxs-lookup"><span data-stu-id="ee84f-152">Adding Existing Constraints to a DataSet</span></span>](../adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="ee84f-153">Explique comment remplir un **DataSet** avec les informations de clé primaire d’une source de données.</span><span class="sxs-lookup"><span data-stu-id="ee84f-153">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee84f-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee84f-154">See also</span></span>

- [<span data-ttu-id="ee84f-155">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ee84f-155">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="ee84f-156">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ee84f-156">ADO.NET Overview</span></span>](../ado-net-overview.md)
