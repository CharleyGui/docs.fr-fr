---
title: Retourner l'union définie de deux séquences
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 0fe32d8c3c37e99a50ca03262dc6184337b4450e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200199"
---
# <a name="return-the-set-union-of-two-sequences"></a><span data-ttu-id="2b4cd-102">Retourner l'union définie de deux séquences</span><span class="sxs-lookup"><span data-stu-id="2b4cd-102">Return the Set Union of Two Sequences</span></span>

<span data-ttu-id="2b4cd-103">Utilisez l'opérateur <xref:System.Linq.Queryable.Union%2A> pour retourner l'union définie de deux séquences.</span><span class="sxs-lookup"><span data-stu-id="2b4cd-103">Use the <xref:System.Linq.Queryable.Union%2A> operator to return the set union of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b4cd-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="2b4cd-104">Example</span></span>  

 <span data-ttu-id="2b4cd-105">Cet exemple utilise <xref:System.Linq.Queryable.Union%2A> pour retourner une séquence de tous les pays/régions dans lesquels il existe `Customers` soit ou `Employees` .</span><span class="sxs-lookup"><span data-stu-id="2b4cd-105">This example uses <xref:System.Linq.Queryable.Union%2A> to return a sequence of all countries/regions in which there are either `Customers` or `Employees`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 <span data-ttu-id="2b4cd-106">Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , l' <xref:System.Linq.Queryable.Union%2A> opérateur est défini pour les multijeux comme la concaténation non ordonnée des multijeux (le résultat de la [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) clause dans SQL).</span><span class="sxs-lookup"><span data-stu-id="2b4cd-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Union%2A> operator is defined for multisets as the unordered concatenation of the multisets (effectively the result of the [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) clause in SQL).</span></span>

<span data-ttu-id="2b4cd-107">Pour plus d’informations et d’exemples, consultez <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2b4cd-107">For more info and examples, see <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2b4cd-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b4cd-108">See also</span></span>

- [<span data-ttu-id="2b4cd-109">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="2b4cd-109">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="2b4cd-110">Traduction des opérateurs de requête standard</span><span class="sxs-lookup"><span data-stu-id="2b4cd-110">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
