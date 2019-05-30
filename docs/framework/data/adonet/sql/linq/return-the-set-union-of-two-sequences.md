---
title: Retourner l'union définie de deux séquences
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 9ade12c42ac6a307c341bc5be26430fb56e51ee5
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380038"
---
# <a name="return-the-set-union-of-two-sequences"></a><span data-ttu-id="53fad-102">Retourner l'union définie de deux séquences</span><span class="sxs-lookup"><span data-stu-id="53fad-102">Return the Set Union of Two Sequences</span></span>
<span data-ttu-id="53fad-103">Utilisez l'opérateur <xref:System.Linq.Queryable.Union%2A> pour retourner l'union définie de deux séquences.</span><span class="sxs-lookup"><span data-stu-id="53fad-103">Use the <xref:System.Linq.Queryable.Union%2A> operator to return the set union of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53fad-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="53fad-104">Example</span></span>  
 <span data-ttu-id="53fad-105">Cet exemple utilise <xref:System.Linq.Queryable.Union%2A> pour retourner une séquence de tous les pays/régions dans lesquels sont soit `Customers` ou `Employees`.</span><span class="sxs-lookup"><span data-stu-id="53fad-105">This example uses <xref:System.Linq.Queryable.Union%2A> to return a sequence of all countries/regions in which there are either `Customers` or `Employees`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 <span data-ttu-id="53fad-106">Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], le <xref:System.Linq.Queryable.Union%2A> opérateur est défini pour des multijeux comme la concaténation non ordonnée des multijeux (le résultat de la [ `UNION ALL` ](https://docs.microsoft.com/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-2017) clause dans SQL).</span><span class="sxs-lookup"><span data-stu-id="53fad-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Union%2A> operator is defined for multisets as the unordered concatenation of the multisets (effectively the result of the [`UNION ALL`](https://docs.microsoft.com/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-2017) clause in SQL).</span></span>

<span data-ttu-id="53fad-107">Pour plus d’informations et des exemples, consultez <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="53fad-107">For more info and examples, see <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="53fad-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53fad-108">See also</span></span>

- [<span data-ttu-id="53fad-109">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="53fad-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="53fad-110">Traduction des opérateurs de requête standard</span><span class="sxs-lookup"><span data-stu-id="53fad-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
