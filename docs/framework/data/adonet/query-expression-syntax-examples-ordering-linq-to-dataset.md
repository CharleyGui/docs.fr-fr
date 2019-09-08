---
title: 'Exemples de syntaxe d’expression de requête : Classement (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 653a4a97-1e4a-4b2d-8d24-7dbe1f2a5c84
ms.openlocfilehash: 932f5e4f6073844a951d06dabec45e5ff3e743bf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782995"
---
# <a name="query-expression-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="41d9c-102">Exemples de syntaxe d’expression de requête : Classement (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="41d9c-102">Query Expression Syntax Examples: Ordering (LINQ to DataSet)</span></span>
<span data-ttu-id="41d9c-103">Les exemples de cette rubrique montrent comment utiliser les méthodes <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A> et <xref:System.Linq.Enumerable.ThenByDescending%2A> pour interroger un <xref:System.Data.DataSet> et classer les résultats à l'aide de la syntaxe d'expression de requête.</span><span class="sxs-lookup"><span data-stu-id="41d9c-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results using the query expression syntax.</span></span>  
  
 <span data-ttu-id="41d9c-104">La `FillDataSet` méthode utilisée dans ces exemples est spécifiée lors [du chargement des données dans un DataSet](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="41d9c-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="41d9c-105">Les exemples de cette rubrique utilisent les tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="41d9c-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="41d9c-106">Les exemples de cette rubrique utilisent les instructions `using` suivantes / `Imports` :</span><span class="sxs-lookup"><span data-stu-id="41d9c-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="41d9c-107">Pour plus d'informations, voir [Procédure : Créez un projet de LINQ to DataSet dans Visual](how-to-create-a-linq-to-dataset-project-in-vs.md)Studio.</span><span class="sxs-lookup"><span data-stu-id="41d9c-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="41d9c-108">OrderBy</span><span class="sxs-lookup"><span data-stu-id="41d9c-108">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="41d9c-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="41d9c-109">Example</span></span>  
 <span data-ttu-id="41d9c-110">Cet exemple utilise <xref:System.Linq.Enumerable.OrderBy%2A> pour retourner une liste de contacts classés par nom de famille.</span><span class="sxs-lookup"><span data-stu-id="41d9c-110">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="41d9c-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="41d9c-111">Example</span></span>  
 <span data-ttu-id="41d9c-112">Cet exemple utilise <xref:System.Linq.Enumerable.OrderBy%2A> pour trier une liste de contacts par longueur du nom de famille.</span><span class="sxs-lookup"><span data-stu-id="41d9c-112">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="41d9c-113">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="41d9c-113">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="41d9c-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="41d9c-114">Example</span></span>  
 <span data-ttu-id="41d9c-115">Cet exemple utilise `orderby… descending` (`Order By … Descending`), qui est l'équivalent de la méthode <xref:System.Linq.Enumerable.OrderByDescending%2A>, pour trier la liste de prix du plus élevé au plus bas.</span><span class="sxs-lookup"><span data-stu-id="41d9c-115">This example uses `orderby… descending` (`Order By … Descending`), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="reverse"></a><span data-ttu-id="41d9c-116">Reverse</span><span class="sxs-lookup"><span data-stu-id="41d9c-116">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="41d9c-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="41d9c-117">Example</span></span>  
 <span data-ttu-id="41d9c-118">Cet exemple utilise <xref:System.Linq.Enumerable.Reverse%2A> pour créer une liste de commandes où `OrderDate` est antérieure au 20 février 2002.</span><span class="sxs-lookup"><span data-stu-id="41d9c-118">This example uses <xref:System.Linq.Enumerable.Reverse%2A> to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="41d9c-119">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="41d9c-119">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="41d9c-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="41d9c-120">Example</span></span>  
 <span data-ttu-id="41d9c-121">Cet exemple utilise `OrderBy… Descending`, qui est l'équivalent de la méthode <xref:System.Linq.Enumerable.ThenByDescending%2A>, pour trier une liste de produits, d'abord par nom, puis par prix courant, du plus élevé au plus bas.</span><span class="sxs-lookup"><span data-stu-id="41d9c-121">This example uses `OrderBy… Descending` , which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price, from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="41d9c-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41d9c-122">See also</span></span>

- [<span data-ttu-id="41d9c-123">Chargement de données dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="41d9c-123">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="41d9c-124">Exemples LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="41d9c-124">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="41d9c-125">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="41d9c-125">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="41d9c-126">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41d9c-126">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
