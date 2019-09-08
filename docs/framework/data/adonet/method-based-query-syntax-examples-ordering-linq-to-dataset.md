---
title: 'Exemples de syntaxe de requête fondée sur une méthode : Classement (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f9ce4fd-e84f-48c0-bb64-89e217236d3e
ms.openlocfilehash: 16a37cb0bc36741ad816d2aa038a1390e3282d9b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794975"
---
# <a name="method-based-query-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="f9395-102">Exemples de syntaxe de requête fondée sur une méthode : Classement (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="f9395-102">Method-Based Query Syntax Examples: Ordering (LINQ to DataSet)</span></span>
<span data-ttu-id="f9395-103">Les exemples de cette rubrique montrent comment utiliser les méthodes <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Reverse%2A> et <xref:System.Linq.Enumerable.ThenBy%2A> pour interroger un <xref:System.Data.DataSet> et classer les résultats à l'aide de la syntaxe d'interrogation de méthode.</span><span class="sxs-lookup"><span data-stu-id="f9395-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>,  <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenBy%2A> methods to query a <xref:System.Data.DataSet> and order the results using the method query syntax.</span></span>  
  
 <span data-ttu-id="f9395-104">La `FillDataSet` méthode utilisée dans ces exemples est spécifiée lors [du chargement des données dans un DataSet](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="f9395-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="f9395-105">Les exemples de cette rubrique utilisent les tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f9395-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f9395-106">Les exemples de cette rubrique utilisent les instructions `using` suivantes / `Imports` :</span><span class="sxs-lookup"><span data-stu-id="f9395-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="f9395-107">Pour plus d’informations, consultez [Guide pratique pour Créez un projet de LINQ to DataSet dans Visual](how-to-create-a-linq-to-dataset-project-in-vs.md)Studio.</span><span class="sxs-lookup"><span data-stu-id="f9395-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="f9395-108">OrderBy</span><span class="sxs-lookup"><span data-stu-id="f9395-108">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="f9395-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="f9395-109">Example</span></span>  
 <span data-ttu-id="f9395-110">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.OrderBy%2A> avec un comparateur personnalisé pour effectuer un tri des noms ne respectant pas la casse.</span><span class="sxs-lookup"><span data-stu-id="f9395-110">This example uses the <xref:System.Linq.Enumerable.OrderBy%2A> method with a custom comparer to do a case-insensitive sort of last names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbycomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbycomparer_mq)]  
  
## <a name="reverse"></a><span data-ttu-id="f9395-111">Reverse</span><span class="sxs-lookup"><span data-stu-id="f9395-111">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="f9395-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="f9395-112">Example</span></span>  
 <span data-ttu-id="f9395-113">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Reverse%2A> pour créer une liste des commandes où `OrderDate` est antérieure au 20 février 2002.</span><span class="sxs-lookup"><span data-stu-id="f9395-113">This example uses the <xref:System.Linq.Enumerable.Reverse%2A> method to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenby"></a><span data-ttu-id="f9395-114">ThenBy</span><span class="sxs-lookup"><span data-stu-id="f9395-114">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="f9395-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="f9395-115">Example</span></span>  
 <span data-ttu-id="f9395-116">Cet exemple utilise les méthodes <xref:System.Linq.Enumerable.OrderBy%2A> et <xref:System.Linq.Enumerable.ThenBy%2A> avec un comparateur personnalisé pour effectuer un premier tri par prix courant, puis un tri décroissant ne respectant pas la casse des noms de produits.</span><span class="sxs-lookup"><span data-stu-id="f9395-116">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.ThenBy%2A> methods with a custom comparer to first sort by list price, and then perform a case-insensitive descending sort of the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingcomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingcomparer_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="f9395-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9395-117">See also</span></span>

- [<span data-ttu-id="f9395-118">Chargement de données dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="f9395-118">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="f9395-119">Exemples LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="f9395-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="f9395-120">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="f9395-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="f9395-121">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9395-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
