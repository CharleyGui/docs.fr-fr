---
title: Take, clause (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 32a4c7fd7f1e2f6fe640f3f53f15579f014759d5
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004719"
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="97727-102">Take, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97727-102">Take Clause (Visual Basic)</span></span>
<span data-ttu-id="97727-103">Retourne un nombre spécifié d'éléments contigus à partir du début d'une collection.</span><span class="sxs-lookup"><span data-stu-id="97727-103">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97727-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97727-104">Syntax</span></span>  
  
```vb  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="97727-105">Composants</span><span class="sxs-lookup"><span data-stu-id="97727-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="97727-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="97727-106">Required.</span></span> <span data-ttu-id="97727-107">Valeur ou expression qui prend la valeur du nombre d’éléments de la séquence à retourner.</span><span class="sxs-lookup"><span data-stu-id="97727-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97727-108">Notes</span><span class="sxs-lookup"><span data-stu-id="97727-108">Remarks</span></span>  
 <span data-ttu-id="97727-109">La clause `Take` fait en sorte qu’une requête inclue un nombre spécifié d’éléments contigus à partir du début d’une liste de résultats.</span><span class="sxs-lookup"><span data-stu-id="97727-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="97727-110">Le nombre d’éléments à inclure est spécifié par le paramètre `count`.</span><span class="sxs-lookup"><span data-stu-id="97727-110">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="97727-111">Vous pouvez utiliser la clause `Take` avec la clause `Skip` pour retourner une plage de données à partir de n’importe quel segment d’une requête.</span><span class="sxs-lookup"><span data-stu-id="97727-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="97727-112">Pour ce faire, transmettez l’index du premier élément de la plage à la clause `Skip` et la taille de la plage à la clause `Take`.</span><span class="sxs-lookup"><span data-stu-id="97727-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="97727-113">Dans ce cas, la clause `Take` doit être spécifiée après la clause `Skip`.</span><span class="sxs-lookup"><span data-stu-id="97727-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="97727-114">Lorsque vous utilisez la clause `Take` dans une requête, vous devrez peut-être également vous assurer que les résultats sont retournés dans un ordre qui permet à la clause `Take` d’inclure les résultats prévus.</span><span class="sxs-lookup"><span data-stu-id="97727-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="97727-115">Pour plus d’informations sur la façon de classer les résultats d’une requête, consultez [clause ORDER BY](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="97727-115">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="97727-116">Vous pouvez utiliser la clause `TakeWhile` pour spécifier que seuls certains éléments doivent être retournés, en fonction d’une condition fournie.</span><span class="sxs-lookup"><span data-stu-id="97727-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97727-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="97727-117">Example</span></span>  
 <span data-ttu-id="97727-118">L’exemple de code suivant utilise la clause `Take` conjointement avec la clause `Skip` pour retourner des données d’une requête dans des pages.</span><span class="sxs-lookup"><span data-stu-id="97727-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="97727-119">La fonction GetCustomers utilise la clause `Skip` pour ignorer les clients de la liste jusqu’à la valeur d’index de départ fournie et utilise la clause `Take` pour retourner une page de clients à partir de cette valeur d’index.</span><span class="sxs-lookup"><span data-stu-id="97727-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="97727-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97727-120">See also</span></span>

- [<span data-ttu-id="97727-121">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="97727-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="97727-122">Requêtes</span><span class="sxs-lookup"><span data-stu-id="97727-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="97727-123">Select (clause)</span><span class="sxs-lookup"><span data-stu-id="97727-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="97727-124">From (clause)</span><span class="sxs-lookup"><span data-stu-id="97727-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="97727-125">Order By (clause)</span><span class="sxs-lookup"><span data-stu-id="97727-125">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="97727-126">Take While (clause)</span><span class="sxs-lookup"><span data-stu-id="97727-126">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [<span data-ttu-id="97727-127">Skip (clause)</span><span class="sxs-lookup"><span data-stu-id="97727-127">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
