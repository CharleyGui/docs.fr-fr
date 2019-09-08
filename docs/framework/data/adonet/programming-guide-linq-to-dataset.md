---
title: Guide de programmation (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 977aedd7-0084-46a0-b56f-345787a55da1
ms.openlocfilehash: c971f0a92829df40a14631aaff353a268f277f11
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783204"
---
# <a name="programming-guide-linq-to-dataset"></a><span data-ttu-id="c60d3-102">Guide de programmation (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="c60d3-102">Programming Guide (LINQ to DataSet)</span></span>
<span data-ttu-id="c60d3-103">Cette section fournit des informations conceptuelles et des exemples pour la programmation avec LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="c60d3-103">This section provides conceptual information and examples for programming with LINQ to DataSet.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c60d3-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c60d3-104">In This Section</span></span>  
 [<span data-ttu-id="c60d3-105">Requêtes dans LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="c60d3-105">Queries in LINQ to DataSet</span></span>](queries-in-linq-to-dataset.md)  
 <span data-ttu-id="c60d3-106">Fournit des informations sur la façon d’écrire des requêtes de LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="c60d3-106">Provides information about how to write LINQ to DataSet queries.</span></span>  
  
 [<span data-ttu-id="c60d3-107">Interrogation de DataSets</span><span class="sxs-lookup"><span data-stu-id="c60d3-107">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)  
 <span data-ttu-id="c60d3-108">Explique comment interroger des objets <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="c60d3-108">Describes how to query <xref:System.Data.DataSet> objects.</span></span>  
  
 [<span data-ttu-id="c60d3-109">Comparaison de DataRows</span><span class="sxs-lookup"><span data-stu-id="c60d3-109">Comparing DataRows</span></span>](comparing-datarows-linq-to-dataset.md)  
 <span data-ttu-id="c60d3-110">Explique comment utiliser l'objet <xref:System.Data.DataRowComparer> pour comparer des lignes de données.</span><span class="sxs-lookup"><span data-stu-id="c60d3-110">Describes how to use the <xref:System.Data.DataRowComparer> object to compare data rows.</span></span>  
  
 [<span data-ttu-id="c60d3-111">Création d’un DataTable à partir d’une requête</span><span class="sxs-lookup"><span data-stu-id="c60d3-111">Creating a DataTable From a Query</span></span>](creating-a-datatable-from-a-query-linq-to-dataset.md)  
 <span data-ttu-id="c60d3-112">Fournit des informations sur la <xref:System.Data.DataTable> création d’un à partir d’une <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> requête LINQ to DataSet à l’aide de la méthode.</span><span class="sxs-lookup"><span data-stu-id="c60d3-112">Provides information about creating a <xref:System.Data.DataTable> from a LINQ to DataSet query by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [<span data-ttu-id="c60d3-113">Guide pratique : Implémentez\<CopyToDataTable t > où le type générique T n’est pas un DataRow</span><span class="sxs-lookup"><span data-stu-id="c60d3-113">How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow</span></span>](implement-copytodatatable-where-type-not-a-datarow.md)  
 <span data-ttu-id="c60d3-114">Explique comment implémenter une méthode `CopyToDataTable<T>` personnalisée dans laquelle le paramètre générique T n'est pas du type <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="c60d3-114">Describes how to implement a custom `CopyToDataTable<T>` method where the generic parameter T is not of type <xref:System.Data.DataRow>.</span></span>  
  
 [<span data-ttu-id="c60d3-115">Méthodes génériques Field et SetField</span><span class="sxs-lookup"><span data-stu-id="c60d3-115">Generic Field and SetField Methods</span></span>](generic-field-and-setfield-methods-linq-to-dataset.md)  
 <span data-ttu-id="c60d3-116">Fournit des informations sur les méthodes génériques <xref:System.Data.DataRowExtensions.Field%2A> et <xref:System.Data.DataRowExtensions.SetField%2A>.</span><span class="sxs-lookup"><span data-stu-id="c60d3-116">Provides information about the generic <xref:System.Data.DataRowExtensions.Field%2A> and <xref:System.Data.DataRowExtensions.SetField%2A> methods.</span></span>  
  
 [<span data-ttu-id="c60d3-117">Liaison de données et LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="c60d3-117">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)  
 <span data-ttu-id="c60d3-118">Décrit la liaison de données à l'aide de l'objet <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="c60d3-118">Describes databinding using the <xref:System.Data.DataView> object.</span></span>  
  
 [<span data-ttu-id="c60d3-119">Débogage des requêtes LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="c60d3-119">Debugging LINQ to DataSet Queries</span></span>](debugging-linq-to-dataset-queries.md)  
 <span data-ttu-id="c60d3-120">Fournit des informations sur le débogage et la résolution des problèmes de LINQ to DataSet des requêtes.</span><span class="sxs-lookup"><span data-stu-id="c60d3-120">Provides information about debugging and troubleshooting LINQ to DataSet queries.</span></span>  
  
 [<span data-ttu-id="c60d3-121">Sécurité</span><span class="sxs-lookup"><span data-stu-id="c60d3-121">Security</span></span>](security-linq-to-dataset.md)  
 <span data-ttu-id="c60d3-122">Décrit les problèmes de sécurité dans LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="c60d3-122">Describes security issues in LINQ to DataSet.</span></span>  
  
 [<span data-ttu-id="c60d3-123">Exemples LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="c60d3-123">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)  
 <span data-ttu-id="c60d3-124">Fournit des exemples de requête qui utilisent des opérateurs [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c60d3-124">Provides query examples that use the [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operators.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c60d3-125">Référence</span><span class="sxs-lookup"><span data-stu-id="c60d3-125">Reference</span></span>  
 <xref:System.Data.DataRowComparer>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataView>  
  
## <a name="see-also"></a><span data-ttu-id="c60d3-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c60d3-126">See also</span></span>

- [<span data-ttu-id="c60d3-127">LINQ et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c60d3-127">LINQ and ADO.NET</span></span>](linq-and-ado-net.md)
- [<span data-ttu-id="c60d3-128">LINQ (Language Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="c60d3-128">Language Integrated Query (LINQ)</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
