---
title: 'Exemples de syntaxe d’expression de requête : Opérateurs d’élément'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 32268fe2-de18-4065-8060-f250def83837
ms.openlocfilehash: ddd352fe3bf731c2d436937616d21c0a7257acdc
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398469"
---
# <a name="query-expression-syntax-examples-element-operators"></a><span data-ttu-id="a3a94-102">Exemples de syntaxe d’expression de requête : Opérateurs d’élément</span><span class="sxs-lookup"><span data-stu-id="a3a94-102">Query Expression Syntax Examples: Element Operators</span></span>
<span data-ttu-id="a3a94-103">Les exemples de cette rubrique montrent comment utiliser la <xref:System.Linq.Enumerable.First%2A> méthode pour interroger le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) à l’aide de la syntaxe d’expression de requête.</span><span class="sxs-lookup"><span data-stu-id="a3a94-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using the query expression syntax.</span></span> <span data-ttu-id="a3a94-104">Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a3a94-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="a3a94-105">Les exemples de cette rubrique utilisent les instructions `using` suivantes / `Imports` :</span><span class="sxs-lookup"><span data-stu-id="a3a94-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="a3a94-106">Première</span><span class="sxs-lookup"><span data-stu-id="a3a94-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="a3a94-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="a3a94-107">Example</span></span>  
 <span data-ttu-id="a3a94-108">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.First%2A> pour retourner le premier contact dont le prénom est « Brooke ».</span><span class="sxs-lookup"><span data-stu-id="a3a94-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is "Brooke".</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="a3a94-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3a94-109">See also</span></span>

- [<span data-ttu-id="a3a94-110">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="a3a94-110">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
