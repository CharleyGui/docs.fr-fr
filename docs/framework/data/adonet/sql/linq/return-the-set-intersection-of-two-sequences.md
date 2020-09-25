---
title: Retourner l'intersection définie de deux séquences
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 421ec544345e41f910bf80c855a3a6b4de1c46a6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200223"
---
# <a name="return-the-set-intersection-of-two-sequences"></a><span data-ttu-id="95add-102">Retourner l'intersection définie de deux séquences</span><span class="sxs-lookup"><span data-stu-id="95add-102">Return the Set Intersection of Two Sequences</span></span>

<span data-ttu-id="95add-103">Utilisez l'opérateur <xref:System.Linq.Queryable.Intersect%2A> pour retourner l'intersection définie de deux séquences.</span><span class="sxs-lookup"><span data-stu-id="95add-103">Use the <xref:System.Linq.Queryable.Intersect%2A> operator to return the set intersection of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95add-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="95add-104">Example</span></span>  

 <span data-ttu-id="95add-105">Cet exemple utilise <xref:System.Linq.Queryable.Intersect%2A> pour retourner une séquence de tous les pays/régions dans lesquels `Customers` et en `Employees` direct.</span><span class="sxs-lookup"><span data-stu-id="95add-105">This example uses <xref:System.Linq.Queryable.Intersect%2A> to return a sequence of all countries/regions in which both `Customers` and `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 <span data-ttu-id="95add-106">Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], l'opération <xref:System.Linq.Queryable.Intersect%2A> est correctement définie sur les jeux uniquement.</span><span class="sxs-lookup"><span data-stu-id="95add-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Intersect%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="95add-107">La sémantique pour les multijeux n'est pas définie.</span><span class="sxs-lookup"><span data-stu-id="95add-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95add-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95add-108">See also</span></span>

- [<span data-ttu-id="95add-109">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="95add-109">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="95add-110">Traduction des opérateurs de requête standard</span><span class="sxs-lookup"><span data-stu-id="95add-110">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
