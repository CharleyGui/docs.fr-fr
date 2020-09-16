---
title: DataSets, DataTables et DataViews
description: Découvrez plusieurs façons d’utiliser un jeu de données ADO.NET, une représentation résidente en mémoire de données qui fournit un modèle de programmation relationnel cohérent.
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: 4e1c0ea5f1de1715ad8e862e6a3ed7370b53c6ce
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555862"
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="8fae3-103">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="8fae3-103">DataSets, DataTables, and DataViews</span></span>

<span data-ttu-id="8fae3-104">L'objet <xref:System.Data.DataSet> ADO.NET est une représentation de données résidente en mémoire qui propose un modèle de programmation relationnel cohérent, quelle que soit la source des données qu'il contient.</span><span class="sxs-lookup"><span data-stu-id="8fae3-104">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="8fae3-105">Un objet <xref:System.Data.DataSet> représente un jeu de données complet, y compris les tables qui contiennent et organisent les données et y appliquent des contraintes, ainsi que les relations entre les tables.</span><span class="sxs-lookup"><span data-stu-id="8fae3-105">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
<span data-ttu-id="8fae3-106">L'utilisation d'un objet <xref:System.Data.DataSet> peut se faire via différentes méthodes qui peuvent être appliquées indépendamment les unes des autres ou combinées.</span><span class="sxs-lookup"><span data-stu-id="8fae3-106">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="8fae3-107">Vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="8fae3-107">You can:</span></span>  
  
- <span data-ttu-id="8fae3-108">Créer par programmation un objet <xref:System.Data.DataTable>, <xref:System.Data.DataRelation> et <xref:System.Data.Constraint> dans un objet <xref:System.Data.DataSet>, puis remplir les tables de données.</span><span class="sxs-lookup"><span data-stu-id="8fae3-108">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
- <span data-ttu-id="8fae3-109">Remplir l'objet <xref:System.Data.DataSet> de tables de données provenant d'une source de données relationnelles existante à l'aide d'un objet `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="8fae3-109">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
- <span data-ttu-id="8fae3-110">Charger et rendre persistent le contenu de l'objet <xref:System.Data.DataSet> à l'aide de XML.</span><span class="sxs-lookup"><span data-stu-id="8fae3-110">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="8fae3-111">Pour plus d’informations, consultez [Utilisation de XML dans un DataSet](using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="8fae3-111">For more information, see [Using XML in a DataSet](using-xml-in-a-dataset.md).</span></span>  
  
<span data-ttu-id="8fae3-112">Un objet <xref:System.Data.DataSet> fortement typé peut aussi être transporté au moyen d’un service web XML.</span><span class="sxs-lookup"><span data-stu-id="8fae3-112">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="8fae3-113">Le design de l’objet <xref:System.Data.DataSet> le rend idéal pour le transport de données à l’aide des services web XML.</span><span class="sxs-lookup"><span data-stu-id="8fae3-113">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="8fae3-114">Pour une vue d’ensemble des services web XML, consultez [Vue d’ensemble des services web XML](/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8fae3-114">For an overview of XML Web services, see [XML Web Services Overview](/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span></span> <span data-ttu-id="8fae3-115">Pour obtenir un exemple d’utilisation d’un <xref:System.Data.DataSet> à partir d’un service web XML, consultez [Consommation d’un DataSet à partir d’un service web XML](consuming-a-dataset-from-an-xml-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="8fae3-115">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8fae3-116">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="8fae3-116">In this section</span></span>

 [<span data-ttu-id="8fae3-117">Conseils de sécurité</span><span class="sxs-lookup"><span data-stu-id="8fae3-117">Security guidance</span></span>](security-guidance.md)  
 <span data-ttu-id="8fae3-118">Fournit des conseils de sécurité pour <xref:System.Data.DataSet> et <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="8fae3-118">Provides security guidance for <xref:System.Data.DataSet> and <xref:System.Data.DataTable>.</span></span>

 [<span data-ttu-id="8fae3-119">Création d’un DataSet</span><span class="sxs-lookup"><span data-stu-id="8fae3-119">Creating a DataSet</span></span>](creating-a-dataset.md)  
 <span data-ttu-id="8fae3-120">Décrit la syntaxe permettant de créer une instance d'un objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="8fae3-120">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="8fae3-121">Ajout d'un nouveau DataTable à un DataSet</span><span class="sxs-lookup"><span data-stu-id="8fae3-121">Adding a DataTable to a DataSet</span></span>](adding-a-datatable-to-a-dataset.md)  
 <span data-ttu-id="8fae3-122">Explique comment créer et ajouter des tables et des colonnes à un objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="8fae3-122">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="8fae3-123">Ajout de DataRelations</span><span class="sxs-lookup"><span data-stu-id="8fae3-123">Adding DataRelations</span></span>](adding-datarelations.md)  
 <span data-ttu-id="8fae3-124">Explique comment créer des relations entre différentes tables d'un objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="8fae3-124">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="8fae3-125">Parcours des DataRelations</span><span class="sxs-lookup"><span data-stu-id="8fae3-125">Navigating DataRelations</span></span>](navigating-datarelations.md)  
 <span data-ttu-id="8fae3-126">Explique comment utiliser les relations entre différentes tables d'un objet <xref:System.Data.DataSet> afin de retourner les lignes enfants ou parentes d'une relation parent-enfant.</span><span class="sxs-lookup"><span data-stu-id="8fae3-126">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 [<span data-ttu-id="8fae3-127">Fusion de contenu de DataSet</span><span class="sxs-lookup"><span data-stu-id="8fae3-127">Merging DataSet Contents</span></span>](merging-dataset-contents.md)  
 <span data-ttu-id="8fae3-128">Décrit comment fusionner le contenu d’un tableau <xref:System.Data.DataSet>, <xref:System.Data.DataTable> ou <xref:System.Data.DataRow> dans un autre objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="8fae3-128">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="8fae3-129">Copie de contenu de DataSet</span><span class="sxs-lookup"><span data-stu-id="8fae3-129">Copying DataSet Contents</span></span>](copying-dataset-contents.md)  
 <span data-ttu-id="8fae3-130">Explique comment créer une copie d'un objet <xref:System.Data.DataSet> susceptible de contenir un schéma et des données spécifiées.</span><span class="sxs-lookup"><span data-stu-id="8fae3-130">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 [<span data-ttu-id="8fae3-131">Gestion des événements de DataSet</span><span class="sxs-lookup"><span data-stu-id="8fae3-131">Handling DataSet Events</span></span>](handling-dataset-events.md)  
 <span data-ttu-id="8fae3-132">Décrit les événements d'un objet <xref:System.Data.DataSet> et comment les utiliser.</span><span class="sxs-lookup"><span data-stu-id="8fae3-132">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 [<span data-ttu-id="8fae3-133">Datasets typés</span><span class="sxs-lookup"><span data-stu-id="8fae3-133">Typed DataSets</span></span>](typed-datasets.md)  
 <span data-ttu-id="8fae3-134">Explique ce qu'est un objet <xref:System.Data.DataSet> typé et comment en créer un et l'utiliser.</span><span class="sxs-lookup"><span data-stu-id="8fae3-134">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="8fae3-135">DataTables</span><span class="sxs-lookup"><span data-stu-id="8fae3-135">DataTables</span></span>](datatables.md)  
 <span data-ttu-id="8fae3-136">Explique comment créer un objet <xref:System.Data.DataTable>, définir le schéma et manipuler les données.</span><span class="sxs-lookup"><span data-stu-id="8fae3-136">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="8fae3-137">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="8fae3-137">DataTableReaders</span></span>](datatablereaders.md)  
 <span data-ttu-id="8fae3-138">Explique comment créer et utiliser un <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="8fae3-138">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="8fae3-139">DataViews</span><span class="sxs-lookup"><span data-stu-id="8fae3-139">DataViews</span></span>](dataviews.md)  
 <span data-ttu-id="8fae3-140">Décrit la façon de créer et d'utiliser des `DataViews` et d'utiliser des événements <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="8fae3-140">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 [<span data-ttu-id="8fae3-141">Utilisation de XML dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="8fae3-141">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="8fae3-142">Explique comment l'objet <xref:System.Data.DataSet> interagit avec XML en tant que source de données, notamment en ce qui concerne le chargement et la persistance du contenu d'un objet <xref:System.Data.DataSet> en tant que données XML.</span><span class="sxs-lookup"><span data-stu-id="8fae3-142">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 [<span data-ttu-id="8fae3-143">Consommation d’un DataSet à partir d’un service web XML</span><span class="sxs-lookup"><span data-stu-id="8fae3-143">Consuming a DataSet from an XML Web Service</span></span>](consuming-a-dataset-from-an-xml-web-service.md)  
 <span data-ttu-id="8fae3-144">Explique comment créer un service web XML qui utilise un <xref:System.Data.DataSet> pour le transport des données.</span><span class="sxs-lookup"><span data-stu-id="8fae3-144">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8fae3-145">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="8fae3-145">Related sections</span></span>

 [<span data-ttu-id="8fae3-146">Nouveautés dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8fae3-146">What's New in ADO.NET</span></span>](../whats-new.md)  
 <span data-ttu-id="8fae3-147">Introduit des fonctionnalités nouvelles dans ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="8fae3-147">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="8fae3-148">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8fae3-148">ADO.NET Overview</span></span>](../ado-net-overview.md)  
 <span data-ttu-id="8fae3-149">Propose une introduction à la conception et aux composants de la technologie ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="8fae3-149">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="8fae3-150">Remplissage d'un DataSet à partir d'un DataAdapter</span><span class="sxs-lookup"><span data-stu-id="8fae3-150">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="8fae3-151">Explique comment charger un **DataSet** avec des données provenant d’une source de données.</span><span class="sxs-lookup"><span data-stu-id="8fae3-151">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 [<span data-ttu-id="8fae3-152">Mise à jour des sources de données avec les DataAdapter</span><span class="sxs-lookup"><span data-stu-id="8fae3-152">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="8fae3-153">Explique comment répercuter à la source de données les modifications apportées aux données d’un **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="8fae3-153">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 [<span data-ttu-id="8fae3-154">Ajout de contraintes existantes à un DataSet</span><span class="sxs-lookup"><span data-stu-id="8fae3-154">Adding Existing Constraints to a DataSet</span></span>](../adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="8fae3-155">Explique comment remplir un **DataSet** avec les informations de clé primaire d’une source de données.</span><span class="sxs-lookup"><span data-stu-id="8fae3-155">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fae3-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8fae3-156">See also</span></span>

- [<span data-ttu-id="8fae3-157">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8fae3-157">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="8fae3-158">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8fae3-158">ADO.NET Overview</span></span>](../ado-net-overview.md)
