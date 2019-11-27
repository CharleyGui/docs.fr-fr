---
title: Take, clause
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 3082954ef84560ccb70f7a47cd3532f622829392
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349647"
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="db967-102">Take, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db967-102">Take Clause (Visual Basic)</span></span>
<span data-ttu-id="db967-103">Retourne un nombre spécifié d'éléments contigus à partir du début d'une collection.</span><span class="sxs-lookup"><span data-stu-id="db967-103">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db967-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db967-104">Syntax</span></span>  
  
```vb  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="db967-105">Composants</span><span class="sxs-lookup"><span data-stu-id="db967-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="db967-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="db967-106">Required.</span></span> <span data-ttu-id="db967-107">Valeur ou expression qui prend la valeur du nombre d’éléments de la séquence à retourner.</span><span class="sxs-lookup"><span data-stu-id="db967-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db967-108">Notes</span><span class="sxs-lookup"><span data-stu-id="db967-108">Remarks</span></span>  
 <span data-ttu-id="db967-109">La clause `Take` amène une requête à inclure un nombre spécifié d’éléments contigus à partir du début d’une liste de résultats.</span><span class="sxs-lookup"><span data-stu-id="db967-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="db967-110">Le nombre d’éléments à inclure est spécifié par le paramètre `count`.</span><span class="sxs-lookup"><span data-stu-id="db967-110">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="db967-111">Vous pouvez utiliser la clause `Take` avec la clause `Skip` pour retourner une plage de données à partir d’un segment d’une requête.</span><span class="sxs-lookup"><span data-stu-id="db967-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="db967-112">Pour ce faire, transmettez l’index du premier élément de la plage à la clause `Skip` et la taille de la plage à la clause `Take`.</span><span class="sxs-lookup"><span data-stu-id="db967-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="db967-113">Dans ce cas, la clause `Take` doit être spécifiée après la clause `Skip`.</span><span class="sxs-lookup"><span data-stu-id="db967-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="db967-114">Lorsque vous utilisez la clause `Take` dans une requête, vous devrez peut-être également vous assurer que les résultats sont retournés dans un ordre qui permettra à la clause `Take` d’inclure les résultats souhaités.</span><span class="sxs-lookup"><span data-stu-id="db967-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="db967-115">Pour plus d’informations sur la façon de classer les résultats d’une requête, consultez [clause ORDER BY](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="db967-115">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="db967-116">Vous pouvez utiliser la clause `TakeWhile` pour spécifier que seuls certains éléments doivent être retournés, en fonction d’une condition fournie.</span><span class="sxs-lookup"><span data-stu-id="db967-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db967-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="db967-117">Example</span></span>  
 <span data-ttu-id="db967-118">L’exemple de code suivant utilise la clause `Take` avec la clause `Skip` pour retourner des données d’une requête dans des pages.</span><span class="sxs-lookup"><span data-stu-id="db967-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="db967-119">La fonction GetCustomers utilise la clause `Skip` pour ignorer les clients de la liste jusqu’à la valeur d’index de départ fournie, et utilise la clause `Take` pour retourner une page de clients à partir de cette valeur d’index.</span><span class="sxs-lookup"><span data-stu-id="db967-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="db967-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db967-120">See also</span></span>

- [<span data-ttu-id="db967-121">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="db967-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="db967-122">Requêtes</span><span class="sxs-lookup"><span data-stu-id="db967-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="db967-123">Select (clause)</span><span class="sxs-lookup"><span data-stu-id="db967-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="db967-124">From (clause)</span><span class="sxs-lookup"><span data-stu-id="db967-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="db967-125">Order By (clause)</span><span class="sxs-lookup"><span data-stu-id="db967-125">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="db967-126">Take While (clause)</span><span class="sxs-lookup"><span data-stu-id="db967-126">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [<span data-ttu-id="db967-127">Skip (clause)</span><span class="sxs-lookup"><span data-stu-id="db967-127">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
