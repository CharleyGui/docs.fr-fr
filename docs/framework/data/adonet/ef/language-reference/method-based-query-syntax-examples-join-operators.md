---
title: 'Exemples de syntaxe de requête fondée sur une méthode : opérateurs de jointure'
description: Utilisez ces exemples pour apprendre à utiliser les méthodes Join et GroupJoin pour interroger un modèle à l’aide de la syntaxe de requête fondée sur une méthode dans LINQ to Entities.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d00f0efa-9084-4c17-843f-54904fcb4204
ms.openlocfilehash: 7f02379f4ececb75981ab262f22ebdeb510739ed
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191956"
---
# <a name="method-based-query-syntax-examples-join-operators"></a><span data-ttu-id="c6cef-103">Exemples de syntaxe de requête fondée sur une méthode : opérateurs de jointure</span><span class="sxs-lookup"><span data-stu-id="c6cef-103">Method-Based Query Syntax Examples: Join Operators</span></span>

<span data-ttu-id="c6cef-104">Les exemples de cette rubrique montrent comment utiliser les <xref:System.Linq.Enumerable.Join%2A> méthodes et <xref:System.Linq.Enumerable.GroupJoin%2A> pour interroger le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) à l’aide de la syntaxe de requête fondée sur une méthode.</span><span class="sxs-lookup"><span data-stu-id="c6cef-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="c6cef-105">Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c6cef-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="c6cef-106">Les exemples de cette rubrique utilisent les `using` / `Imports` instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="c6cef-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="c6cef-107">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="c6cef-107">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="c6cef-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="c6cef-108">Example</span></span>  

 <span data-ttu-id="c6cef-109">L'exemple ci-dessous effectue une jointure <xref:System.Linq.Enumerable.GroupJoin%2A> sur les tables SalesOrderHeader et SalesOrderDetail pour trouver le nombre de commandes par client.</span><span class="sxs-lookup"><span data-stu-id="c6cef-109">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="c6cef-110">Une jointure de groupe est l'équivalent d'une jointure externe gauche qui retourne chaque élément de la première source de données (gauche), même s'il n'y a pas d'éléments corrélés dans l'autre source de données.</span><span class="sxs-lookup"><span data-stu-id="c6cef-110">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2_mq)]
 [!code-vb[DP L2E Examples#GroupJoin2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2_mq)]  
  
### <a name="example"></a><span data-ttu-id="c6cef-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="c6cef-111">Example</span></span>  

 <span data-ttu-id="c6cef-112">L'exemple ci-dessous effectue une jointure <xref:System.Linq.Enumerable.GroupJoin%2A> sur les tables Contact et SalesOrderHeader pour trouver le nombre de commandes par contact.</span><span class="sxs-lookup"><span data-stu-id="c6cef-112">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="c6cef-113">Le nombre de commandes et les ID de chaque contact sont affichés.</span><span class="sxs-lookup"><span data-stu-id="c6cef-113">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin_mq)]
 [!code-vb[DP L2E Examples#GroupJoin_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin_mq)]  
  
## <a name="join"></a><span data-ttu-id="c6cef-114">Join</span><span class="sxs-lookup"><span data-stu-id="c6cef-114">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="c6cef-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="c6cef-115">Example</span></span>  

 <span data-ttu-id="c6cef-116">L'exemple ci-dessous effectue une jointure sur les tables Contact et SalesOrderHeader.</span><span class="sxs-lookup"><span data-stu-id="c6cef-116">The following example performs a join over the Contact and SalesOrderHeader tables.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP L2E Examples#JoinSimple_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a><span data-ttu-id="c6cef-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="c6cef-117">Example</span></span>  

 <span data-ttu-id="c6cef-118">L'exemple suivant effectue une jointure sur les tables Contact et SalesOrderHeader, en regroupant les résultats par ID de contact.</span><span class="sxs-lookup"><span data-stu-id="c6cef-118">The following example performs a join over the Contact and SalesOrderHeader tables, grouping the results by contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP L2E Examples#JoinWithGroupedResults_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="c6cef-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6cef-119">See also</span></span>

- [<span data-ttu-id="c6cef-120">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="c6cef-120">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
