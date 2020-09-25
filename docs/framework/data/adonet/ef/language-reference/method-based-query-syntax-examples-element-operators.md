---
title: "Exemples de syntaxe de requête fondée sur une méthode : opérateurs d'élément"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 96d393a34af69935e75582ef1954ddd661a355f0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192046"
---
# <a name="method-based-query-syntax-examples-element-operators"></a><span data-ttu-id="9caec-102">Exemples de syntaxe de requête fondée sur une méthode : opérateurs d'élément</span><span class="sxs-lookup"><span data-stu-id="9caec-102">Method-Based Query Syntax Examples: Element Operators</span></span>

<span data-ttu-id="9caec-103">Les exemples de cette rubrique montrent comment utiliser la <xref:System.Linq.Enumerable.First%2A> méthode pour interroger le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) à l’aide de la syntaxe de requête fondée sur une méthode.</span><span class="sxs-lookup"><span data-stu-id="9caec-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="9caec-104">Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="9caec-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="9caec-105">L’exemple de cette rubrique utilise les `using` / `Imports` instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="9caec-105">The example in this topic uses the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="9caec-106">Premier</span><span class="sxs-lookup"><span data-stu-id="9caec-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="9caec-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="9caec-107">Example</span></span>  

 <span data-ttu-id="9caec-108">L’exemple suivant utilise la <xref:System.Linq.Enumerable.First%2A> méthode pour rechercher la première adresse de messagerie qui commence par’Caroline'.</span><span class="sxs-lookup"><span data-stu-id="9caec-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to find the first email address that starts with 'caroline'.</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="9caec-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9caec-109">See also</span></span>

- [<span data-ttu-id="9caec-110">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="9caec-110">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
