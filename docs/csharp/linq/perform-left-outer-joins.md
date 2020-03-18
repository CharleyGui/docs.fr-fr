---
title: Effectuer des jointures externes gauches (LINQ en C#)
description: Découvrez comment effectuer des jointures externes gauches à l’aide de LINQ en C#.
ms.date: 12/01/2016
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: cc08a1c8670623a10d1e0bf10221d02037a8d7bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688577"
---
# <a name="perform-left-outer-joins"></a><span data-ttu-id="ef080-103">Effectuer des jointures externes gauches</span><span class="sxs-lookup"><span data-stu-id="ef080-103">Perform left outer joins</span></span>

<span data-ttu-id="ef080-104">Une jointure externe gauche est une jointure dans laquelle chaque élément de la première collection est retourné, qu’elle ait ou non des éléments corrélés dans la deuxième collection.</span><span class="sxs-lookup"><span data-stu-id="ef080-104">A left outer join is a join in which each element of the first collection is returned, regardless of whether it has any correlated elements in the second collection.</span></span> <span data-ttu-id="ef080-105">Vous pouvez utiliser LINQ pour effectuer une jointure externe gauche en appelant la méthode <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> sur les résultats d’une jointure groupée.</span><span class="sxs-lookup"><span data-stu-id="ef080-105">You can use LINQ to perform a left outer join by calling the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join.</span></span>

## <a name="example"></a><span data-ttu-id="ef080-106"> Exemple</span><span class="sxs-lookup"><span data-stu-id="ef080-106">Example</span></span>

<span data-ttu-id="ef080-107">L’exemple suivant montre comment utiliser la méthode <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> sur les résultats d’une jointure groupée pour effectuer une jointure externe gauche.</span><span class="sxs-lookup"><span data-stu-id="ef080-107">The following example demonstrates how to use the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join to perform a left outer join.</span></span>

<span data-ttu-id="ef080-108">Pour créer une jointure externe gauche entre deux collections, la première étape consiste à effectuer une jointure interne à l’aide d’une jointure groupée.</span><span class="sxs-lookup"><span data-stu-id="ef080-108">The first step in producing a left outer join of two collections is to perform an inner join by using a group join.</span></span> <span data-ttu-id="ef080-109">(Voir [Perform inner se joint](perform-inner-joins.md) pour une explication de ce processus.) Dans cet exemple, `Person` la liste des objets est `Pet` jointe à `Person` la `Pet.Owner`liste des objets sur la base d’un objet qui correspond .</span><span class="sxs-lookup"><span data-stu-id="ef080-109">(See [Perform inner joins](perform-inner-joins.md) for an explanation of this process.) In this example, the list of `Person` objects is inner-joined to the list of `Pet` objects based on a `Person` object that matches `Pet.Owner`.</span></span>

<span data-ttu-id="ef080-110">La deuxième étape consiste à inclure tous les éléments de la première collection (celle de gauche) dans le jeu de résultats, y compris les éléments sans correspondance dans la collection de droite.</span><span class="sxs-lookup"><span data-stu-id="ef080-110">The second step is to include each element of the first (left) collection in the result set even if that element has no matches in the right collection.</span></span> <span data-ttu-id="ef080-111">Pour cela, appelez <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> sur chaque séquence d’éléments correspondants de la jointure groupée.</span><span class="sxs-lookup"><span data-stu-id="ef080-111">This is accomplished by calling <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> on each sequence of matching elements from the group join.</span></span> <span data-ttu-id="ef080-112">Dans cet exemple, la méthode <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> est appelée sur chaque séquence d’objets `Pet` correspondants.</span><span class="sxs-lookup"><span data-stu-id="ef080-112">In this example, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> is called on each sequence of matching `Pet` objects.</span></span> <span data-ttu-id="ef080-113">La méthode retourne une collection qui contient uniquement une valeur par défaut si la séquence des objets `Pet` correspondants à un objet `Person` est vide, ce qui garantit que chaque objet `Person` est représenté dans la collection de résultats.</span><span class="sxs-lookup"><span data-stu-id="ef080-113">The method returns a collection that contains a single, default value if the sequence of matching `Pet` objects is empty for any `Person` object, thereby ensuring that each `Person` object is represented in the result collection.</span></span>

> [!NOTE]
> <span data-ttu-id="ef080-114">La valeur par défaut pour un type référence est `null`. L’exemple recherche donc une référence null avant d’accéder à chaque élément de chaque collection `Pet`.</span><span class="sxs-lookup"><span data-stu-id="ef080-114">The default value for a reference type is `null`; therefore, the example checks for a null reference before accessing each element of each `Pet` collection.</span></span>

[!code-csharp[CsLINQProgJoining#7](~/samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]

## <a name="see-also"></a><span data-ttu-id="ef080-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef080-115">See also</span></span>

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [<span data-ttu-id="ef080-116">Effectuer des jointures intérieures</span><span class="sxs-lookup"><span data-stu-id="ef080-116">Perform inner joins</span></span>](perform-inner-joins.md)
- [<span data-ttu-id="ef080-117">Effectuer des jointures groupées</span><span class="sxs-lookup"><span data-stu-id="ef080-117">Perform grouped joins</span></span>](perform-grouped-joins.md)
- [<span data-ttu-id="ef080-118">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="ef080-118">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)
