---
title: "Exemples de syntaxe d'expression de requête : partition"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e41aed0-3be9-4f75-98de-860a85552a3c
ms.openlocfilehash: 548701f375b550e3a533a012bf34dc686ed42ac1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203603"
---
# <a name="query-expression-syntax-examples-partitioning"></a><span data-ttu-id="26ab5-102">Exemples de syntaxe d'expression de requête : partition</span><span class="sxs-lookup"><span data-stu-id="26ab5-102">Query Expression Syntax Examples: Partitioning</span></span>

<span data-ttu-id="26ab5-103">Les exemples de cette rubrique montrent comment utiliser les <xref:System.Linq.Enumerable.Skip%2A> méthodes et <xref:System.Linq.Enumerable.Take%2A> pour interroger le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) à l’aide de la syntaxe d’expression de requête.</span><span class="sxs-lookup"><span data-stu-id="26ab5-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="26ab5-104">Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="26ab5-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="26ab5-105">Les exemples de cette rubrique utilisent les `using` / `Imports` instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="26ab5-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="26ab5-106">Ignorer</span><span class="sxs-lookup"><span data-stu-id="26ab5-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="26ab5-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="26ab5-107">Example</span></span>  

 <span data-ttu-id="26ab5-108">L'exemple suivant utilise la méthode <xref:System.Linq.Enumerable.Skip%2A> pour obtenir toutes les adresses de Seattle, à l'exception des deux premières.</span><span class="sxs-lookup"><span data-stu-id="26ab5-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="26ab5-109">Take</span><span class="sxs-lookup"><span data-stu-id="26ab5-109">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="26ab5-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="26ab5-110">Example</span></span>  

 <span data-ttu-id="26ab5-111">L'exemple suivant utilise la méthode <xref:System.Linq.Enumerable.Take%2A> pour obtenir les trois premières adresses de Seattle.</span><span class="sxs-lookup"><span data-stu-id="26ab5-111">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="26ab5-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26ab5-112">See also</span></span>

- [<span data-ttu-id="26ab5-113">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="26ab5-113">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
