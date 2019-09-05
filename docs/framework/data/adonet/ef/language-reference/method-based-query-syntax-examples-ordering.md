---
title: 'Exemples de syntaxe de requête fondée sur une méthode : Classement'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5d21b178-d731-471a-8534-1f8184a2ef06
ms.openlocfilehash: 8da335bc2b45153aa00cd28f1a6baf58d11020ce
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250109"
---
# <a name="method-based-query-syntax-examples-ordering"></a><span data-ttu-id="f5b8d-102">Exemples de syntaxe de requête fondée sur une méthode : Classement</span><span class="sxs-lookup"><span data-stu-id="f5b8d-102">Method-Based Query Syntax Examples: Ordering</span></span>
<span data-ttu-id="f5b8d-103">Les exemples de cette rubrique montrent comment utiliser la méthode <xref:System.Linq.Enumerable.ThenBy%2A> pour interroger le [modèle de vente AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) à l’aide de la syntaxe de requête fondée sur une méthode.</span><span class="sxs-lookup"><span data-stu-id="f5b8d-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ThenBy%2A> method to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="f5b8d-104">Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f5b8d-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f5b8d-105">Les exemples de cette rubrique utilisent les instructions `using` suivantes / `Imports` :</span><span class="sxs-lookup"><span data-stu-id="f5b8d-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="thenby"></a><span data-ttu-id="f5b8d-106">ThenBy</span><span class="sxs-lookup"><span data-stu-id="f5b8d-106">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="f5b8d-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="f5b8d-107">Example</span></span>  
 <span data-ttu-id="f5b8d-108">L'exemple ci-dessous de syntaxe de requête fondée sur une méthode utilise <xref:System.Linq.Queryable.OrderBy%2A> et <xref:System.Linq.Queryable.ThenBy%2A> pour retourner une liste de contacts classés par nom, puis par prénom.</span><span class="sxs-lookup"><span data-stu-id="f5b8d-108">The following example in method-based query syntax uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby_mq)]
 [!code-vb[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby_mq)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="f5b8d-109">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="f5b8d-109">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="f5b8d-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="f5b8d-110">Example</span></span>  
 <span data-ttu-id="f5b8d-111">L'exemple ci-dessous utilise les méthodes <xref:System.Linq.Queryable.OrderBy%2A> et <xref:System.Linq.Queryable.ThenByDescending%2A> pour effectuer un premier tri par prix courant, puis un tri décroissant des noms de produits.</span><span class="sxs-lookup"><span data-stu-id="f5b8d-111">The following example uses the <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenByDescending%2A> methods to first sort by list price, and then perform a descending sort of the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescending_mq)]
 [!code-vb[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescending_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="f5b8d-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5b8d-112">See also</span></span>

- [<span data-ttu-id="f5b8d-113">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="f5b8d-113">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
