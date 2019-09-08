---
title: "Comment : déterminer si certains ou tous les éléments d'une séquence remplissent une condition"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
ms.openlocfilehash: 7de65579cb41641aded0b9a320fac59804959ff5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782230"
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a><span data-ttu-id="bb7fb-102">Comment : déterminer si certains ou tous les éléments d'une séquence remplissent une condition</span><span class="sxs-lookup"><span data-stu-id="bb7fb-102">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>
<span data-ttu-id="bb7fb-103">L'opérateur <xref:System.Linq.Enumerable.All%2A> retourne `true` si tous les éléments d'une séquence remplissent une condition.</span><span class="sxs-lookup"><span data-stu-id="bb7fb-103">The <xref:System.Linq.Enumerable.All%2A> operator returns `true` if all elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="bb7fb-104">L'opérateur <xref:System.Linq.Queryable.Any%2A> retourne `true` si un élément d'une séquence remplit une condition.</span><span class="sxs-lookup"><span data-stu-id="bb7fb-104">The <xref:System.Linq.Queryable.Any%2A> operator returns `true` if any element in a sequence satisfies a condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb7fb-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="bb7fb-105">Example</span></span>  
 <span data-ttu-id="bb7fb-106">L'exemple suivant retourne une séquence de clients possédant au moins une commande.</span><span class="sxs-lookup"><span data-stu-id="bb7fb-106">The following example returns a sequence of customers that have at least one order.</span></span> <span data-ttu-id="bb7fb-107">La `Where` clause prend la / `where` valeur si`true` le donné`Customer` a un `Order`.</span><span class="sxs-lookup"><span data-stu-id="bb7fb-107">The `Where`/`where` clause evaluates to `true` if the given `Customer` has any `Order`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="bb7fb-108">Exemples</span><span class="sxs-lookup"><span data-stu-id="bb7fb-108">Example</span></span>  
 <span data-ttu-id="bb7fb-109">Le code Visual Basic suivant détermine la liste des clients qui n'ont pas passé de commande et vérifie qu'un nom de contact est fourni pour chaque client de cette liste.</span><span class="sxs-lookup"><span data-stu-id="bb7fb-109">The following Visual Basic code determines the list of customers who have not placed orders, and ensures that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a><span data-ttu-id="bb7fb-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="bb7fb-110">Example</span></span>  
 <span data-ttu-id="bb7fb-111">L'exemple C# suivant retourne une séquence de clients dont la `ShipCity` des commandes commence par la lettre C.</span><span class="sxs-lookup"><span data-stu-id="bb7fb-111">The following C# example returns a sequence of customers whose orders have a `ShipCity` beginning with "C".</span></span> <span data-ttu-id="bb7fb-112">Il retourne également les clients qui n'ont pas de commandes.</span><span class="sxs-lookup"><span data-stu-id="bb7fb-112">Also included in the return are customers who have no orders.</span></span> <span data-ttu-id="bb7fb-113">De par sa conception, l'opérateur <xref:System.Linq.Queryable.All%2A> retourne `true` pour une séquence vide. Les clients qui n'ont pas de commande sont supprimés de la sortie de la console à l'aide de l'opérateur `Count`.</span><span class="sxs-lookup"><span data-stu-id="bb7fb-113">(By design, the <xref:System.Linq.Queryable.All%2A> operator returns `true` for an empty sequence.) Customers with no orders are eliminated in the console output by using the `Count` operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="bb7fb-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb7fb-114">See also</span></span>

- [<span data-ttu-id="bb7fb-115">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="bb7fb-115">Query Examples</span></span>](query-examples.md)
