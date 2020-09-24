---
title: "Exemples de syntaxe d'expression de requête : classement"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcbc9625-7cf7-476e-85d2-058f12682f54
ms.openlocfilehash: ed03fc248ed48f56998bc27f7e880b1e8aa443d2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156782"
---
# <a name="query-expression-syntax-examples-ordering"></a><span data-ttu-id="b7464-102">Exemples de syntaxe d'expression de requête : classement</span><span class="sxs-lookup"><span data-stu-id="b7464-102">Query Expression Syntax Examples: Ordering</span></span>

<span data-ttu-id="b7464-103">Les exemples de cette rubrique montrent comment utiliser les `OrderBy` méthodes et `OrderByDescending` pour interroger le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) à l’aide de la syntaxe d’expression de requête.</span><span class="sxs-lookup"><span data-stu-id="b7464-103">The examples in this topic demonstrate how to use the `OrderBy` and `OrderByDescending` methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="b7464-104">Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b7464-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="b7464-105">Les exemples de cette rubrique utilisent les `using` / `Imports` instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="b7464-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="orderby"></a><span data-ttu-id="b7464-106">OrderBy</span><span class="sxs-lookup"><span data-stu-id="b7464-106">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="b7464-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="b7464-107">Example</span></span>  

 <span data-ttu-id="b7464-108">L'exemple suivant utilise <xref:System.Linq.Enumerable.OrderBy%2A> pour retourner une liste de contacts classés par nom de famille.</span><span class="sxs-lookup"><span data-stu-id="b7464-108">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="b7464-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="b7464-109">Example</span></span>  

 <span data-ttu-id="b7464-110">L'exemple suivant utilise <xref:System.Linq.Enumerable.OrderBy%2A> pour trier une liste de contacts par longueur du nom de famille.</span><span class="sxs-lookup"><span data-stu-id="b7464-110">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="b7464-111">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="b7464-111">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="b7464-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="b7464-112">Example</span></span>  

 <span data-ttu-id="b7464-113">L'exemple suivant utilise `orderby… descending` (`Order By … Descending` en Visual Basic), qui est l'équivalent de la méthode <xref:System.Linq.Enumerable.OrderByDescending%2A>, pour trier la liste de prix du plus élevé au plus bas.</span><span class="sxs-lookup"><span data-stu-id="b7464-113">The following example uses `orderby… descending` (`Order By … Descending` in Visual Basic), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="thenby"></a><span data-ttu-id="b7464-114">ThenBy</span><span class="sxs-lookup"><span data-stu-id="b7464-114">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="b7464-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="b7464-115">Example</span></span>  

 <span data-ttu-id="b7464-116">L'exemple suivant utilise <xref:System.Linq.Queryable.OrderBy%2A> et <xref:System.Linq.Queryable.ThenBy%2A> pour retourner une liste de contacts classée par nom de famille, puis par prénom.</span><span class="sxs-lookup"><span data-stu-id="b7464-116">The following example uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby)]
 [!code-vb[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="b7464-117">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="b7464-117">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="b7464-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="b7464-118">Example</span></span>  

 <span data-ttu-id="b7464-119">L'exemple suivant utilise `OrderBy… Descending`, qui est l'équivalent de la méthode <xref:System.Linq.Enumerable.ThenByDescending%2A>, pour trier une liste de produits, d'abord par nom, puis par prix, du plus élevé au plus bas.</span><span class="sxs-lookup"><span data-stu-id="b7464-119">The following example uses `OrderBy… Descending`, which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="b7464-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7464-120">See also</span></span>

- [<span data-ttu-id="b7464-121">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="b7464-121">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
