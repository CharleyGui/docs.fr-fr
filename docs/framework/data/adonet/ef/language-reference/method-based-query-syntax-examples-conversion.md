---
title: 'Exemples de syntaxe de requête fondée sur une méthode : conversion'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 19f66872-d5ab-49f8-969f-e53f9632a13d
ms.openlocfilehash: e2b5ae3b7c7733216f18914c497d080fe8d71a8e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192085"
---
# <a name="method-based-query-syntax-examples-conversion"></a><span data-ttu-id="1d652-102">Exemples de syntaxe de requête fondée sur une méthode : conversion</span><span class="sxs-lookup"><span data-stu-id="1d652-102">Method-Based Query Syntax Examples: Conversion</span></span>

<span data-ttu-id="1d652-103">Les exemples de cette rubrique montrent comment utiliser les <xref:System.Linq.Enumerable.ToArray%2A> méthodes, <xref:System.Linq.Enumerable.ToDictionary%2A> et <xref:System.Linq.Enumerable.ToList%2A> pour interroger le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) à l’aide de la syntaxe de requête fondée sur une méthode.</span><span class="sxs-lookup"><span data-stu-id="1d652-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> and <xref:System.Linq.Enumerable.ToList%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="1d652-104">Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1d652-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="1d652-105">Les exemples de cette rubrique utilisent les `using` / `Imports` instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="1d652-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="toarray"></a><span data-ttu-id="1d652-106">ToArray</span><span class="sxs-lookup"><span data-stu-id="1d652-106">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="1d652-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="1d652-107">Example</span></span>  

 <span data-ttu-id="1d652-108">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.ToArray%2A> pour évaluer immédiatement une séquence dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="1d652-108">The following example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="1d652-109">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="1d652-109">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="1d652-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="1d652-110">Example</span></span>  

 <span data-ttu-id="1d652-111">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.ToDictionary%2A> pour évaluer immédiatement une séquence et une expression clé associée dans un dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="1d652-111">The following example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="1d652-112">ToList</span><span class="sxs-lookup"><span data-stu-id="1d652-112">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="1d652-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="1d652-113">Example</span></span>  

 <span data-ttu-id="1d652-114">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.ToList%2A> pour évaluer immédiatement une séquence dans un objet <xref:System.Collections.Generic.List%601> où `T` est de type <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="1d652-114">The following example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToList](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#tolist)]
 [!code-vb[DP L2E Examples#ToList](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="1d652-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d652-115">See also</span></span>

- [<span data-ttu-id="1d652-116">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="1d652-116">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
