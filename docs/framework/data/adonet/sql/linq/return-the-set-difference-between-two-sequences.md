---
title: 'Comment : retourner la différence définie entre deux séquences'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 49a8d22377ef1f7d0fde16880a82002754e1bbc4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200327"
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="4d39f-102">Comment : retourner la différence définie entre deux séquences</span><span class="sxs-lookup"><span data-stu-id="4d39f-102">Return the Set Difference Between Two Sequences</span></span>

<span data-ttu-id="4d39f-103">Utilisez l'opérateur <xref:System.Linq.Queryable.Except%2A> pour retourner la différence définie entre deux séquences.</span><span class="sxs-lookup"><span data-stu-id="4d39f-103">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d39f-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="4d39f-104">Example</span></span>  

 <span data-ttu-id="4d39f-105">Cet exemple utilise <xref:System.Linq.Queryable.Except%2A> pour retourner une séquence de tous les pays/régions dans lesquels `Customers` Live, mais dans lesquels aucune activité n’est en `Employees` direct.</span><span class="sxs-lookup"><span data-stu-id="4d39f-105">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries/regions in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="4d39f-106">Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], l'opération <xref:System.Linq.Queryable.Except%2A> est correctement définie sur les jeux uniquement.</span><span class="sxs-lookup"><span data-stu-id="4d39f-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="4d39f-107">La sémantique pour les multijeux n'est pas définie.</span><span class="sxs-lookup"><span data-stu-id="4d39f-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d39f-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d39f-108">See also</span></span>

- [<span data-ttu-id="4d39f-109">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="4d39f-109">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="4d39f-110">Traduction des opérateurs de requête standard</span><span class="sxs-lookup"><span data-stu-id="4d39f-110">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
