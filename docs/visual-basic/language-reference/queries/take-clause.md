---
title: Take (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: f2377d8d1635912885a310b2b0429a6a00083b47
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869679"
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="26e63-102">Take, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26e63-102">Take Clause (Visual Basic)</span></span>

<span data-ttu-id="26e63-103">Retourne un nombre spécifié d'éléments contigus à partir du début d'une collection.</span><span class="sxs-lookup"><span data-stu-id="26e63-103">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26e63-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26e63-104">Syntax</span></span>  
  
```vb  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="26e63-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="26e63-105">Parts</span></span>  

 `count`  
 <span data-ttu-id="26e63-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="26e63-106">Required.</span></span> <span data-ttu-id="26e63-107">Valeur ou expression qui prend la valeur du nombre d’éléments de la séquence à retourner.</span><span class="sxs-lookup"><span data-stu-id="26e63-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26e63-108">Notes</span><span class="sxs-lookup"><span data-stu-id="26e63-108">Remarks</span></span>  

 <span data-ttu-id="26e63-109">La `Take` clause force une requête à inclure un nombre spécifié d’éléments contigus à partir du début d’une liste de résultats.</span><span class="sxs-lookup"><span data-stu-id="26e63-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="26e63-110">Le nombre d’éléments à inclure est spécifié par le `count` paramètre.</span><span class="sxs-lookup"><span data-stu-id="26e63-110">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="26e63-111">Vous pouvez utiliser la `Take` clause avec la `Skip` clause pour retourner une plage de données à partir d’un segment d’une requête.</span><span class="sxs-lookup"><span data-stu-id="26e63-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="26e63-112">Pour ce faire, transmettez l’index du premier élément de la plage à la `Skip` clause et la taille de la plage à la `Take` clause.</span><span class="sxs-lookup"><span data-stu-id="26e63-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="26e63-113">Dans ce cas, la `Take` clause doit être spécifiée après la `Skip` clause.</span><span class="sxs-lookup"><span data-stu-id="26e63-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="26e63-114">Lorsque vous utilisez la `Take` clause dans une requête, vous devrez peut-être également vous assurer que les résultats sont retournés dans un ordre qui permettra `Take` à la clause d’inclure les résultats souhaités.</span><span class="sxs-lookup"><span data-stu-id="26e63-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="26e63-115">Pour plus d’informations sur la façon de classer les résultats d’une requête, consultez [clause ORDER BY](order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="26e63-115">For more information about ordering query results, see [Order By Clause](order-by-clause.md).</span></span>  
  
 <span data-ttu-id="26e63-116">Vous pouvez utiliser la `TakeWhile` clause pour spécifier que seuls certains éléments doivent être retournés, en fonction d’une condition fournie.</span><span class="sxs-lookup"><span data-stu-id="26e63-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26e63-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="26e63-117">Example</span></span>  

 <span data-ttu-id="26e63-118">L’exemple de code suivant utilise la `Take` clause avec la `Skip` clause pour retourner des données d’une requête dans des pages.</span><span class="sxs-lookup"><span data-stu-id="26e63-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="26e63-119">La fonction GetCustomers utilise la `Skip` clause pour ignorer les clients de la liste jusqu’à la valeur d’index de départ fournie et utilise la `Take` clause pour retourner une page de clients à partir de cette valeur d’index.</span><span class="sxs-lookup"><span data-stu-id="26e63-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="26e63-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26e63-120">See also</span></span>

- [<span data-ttu-id="26e63-121">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="26e63-121">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="26e63-122">Requêtes</span><span class="sxs-lookup"><span data-stu-id="26e63-122">Queries</span></span>](index.md)
- [<span data-ttu-id="26e63-123">Clause SELECT</span><span class="sxs-lookup"><span data-stu-id="26e63-123">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="26e63-124">From, clause</span><span class="sxs-lookup"><span data-stu-id="26e63-124">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="26e63-125">Clause ORDER BY</span><span class="sxs-lookup"><span data-stu-id="26e63-125">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="26e63-126">Take While (clause)</span><span class="sxs-lookup"><span data-stu-id="26e63-126">Take While Clause</span></span>](take-while-clause.md)
- [<span data-ttu-id="26e63-127">Skip (clause)</span><span class="sxs-lookup"><span data-stu-id="26e63-127">Skip Clause</span></span>](skip-clause.md)
