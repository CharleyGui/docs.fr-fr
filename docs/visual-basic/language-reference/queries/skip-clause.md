---
title: Skip (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: 427d14453260a54bd3f2ab9a8ac75dedacd291f4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359656"
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="aad20-102">Skip, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aad20-102">Skip Clause (Visual Basic)</span></span>
<span data-ttu-id="aad20-103">Ignore un nombre spécifié d’éléments dans une collection, puis retourne les éléments restants.</span><span class="sxs-lookup"><span data-stu-id="aad20-103">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aad20-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aad20-104">Syntax</span></span>  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="aad20-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="aad20-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="aad20-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="aad20-106">Required.</span></span> <span data-ttu-id="aad20-107">Valeur ou expression qui prend la valeur du nombre d’éléments de la séquence à ignorer.</span><span class="sxs-lookup"><span data-stu-id="aad20-107">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aad20-108">Notes</span><span class="sxs-lookup"><span data-stu-id="aad20-108">Remarks</span></span>  
 <span data-ttu-id="aad20-109">La `Skip` clause génère une requête qui ignore les éléments au début d’une liste de résultats et retourne les éléments restants.</span><span class="sxs-lookup"><span data-stu-id="aad20-109">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="aad20-110">Le nombre d’éléments à ignorer est identifié par le `count` paramètre.</span><span class="sxs-lookup"><span data-stu-id="aad20-110">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="aad20-111">Vous pouvez utiliser la `Skip` clause avec la `Take` clause pour retourner une plage de données à partir d’un segment d’une requête.</span><span class="sxs-lookup"><span data-stu-id="aad20-111">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="aad20-112">Pour ce faire, transmettez l’index du premier élément de la plage à la `Skip` clause et la taille de la plage à la `Take` clause.</span><span class="sxs-lookup"><span data-stu-id="aad20-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="aad20-113">Lorsque vous utilisez la `Skip` clause dans une requête, vous devrez peut-être également vous assurer que les résultats sont retournés dans un ordre qui permettra `Skip` à la clause de contourner les résultats souhaités.</span><span class="sxs-lookup"><span data-stu-id="aad20-113">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="aad20-114">Pour plus d’informations sur la façon de classer les résultats d’une requête, consultez [clause ORDER BY](order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="aad20-114">For more information about ordering query results, see [Order By Clause](order-by-clause.md).</span></span>  
  
 <span data-ttu-id="aad20-115">Vous pouvez utiliser la `SkipWhile` clause pour spécifier que seuls certains éléments sont ignorés, en fonction d’une condition fournie.</span><span class="sxs-lookup"><span data-stu-id="aad20-115">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aad20-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="aad20-116">Example</span></span>  
 <span data-ttu-id="aad20-117">L’exemple de code suivant utilise la `Skip` clause avec la `Take` clause pour retourner des données d’une requête dans des pages.</span><span class="sxs-lookup"><span data-stu-id="aad20-117">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="aad20-118">La `GetCustomers` fonction utilise la `Skip` clause pour ignorer les clients de la liste jusqu’à la valeur d’index de départ fournie et utilise la `Take` clause pour retourner une page de clients à partir de cette valeur d’index.</span><span class="sxs-lookup"><span data-stu-id="aad20-118">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="aad20-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aad20-119">See also</span></span>

- [<span data-ttu-id="aad20-120">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aad20-120">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="aad20-121">Requêtes</span><span class="sxs-lookup"><span data-stu-id="aad20-121">Queries</span></span>](index.md)
- [<span data-ttu-id="aad20-122">Clause SELECT</span><span class="sxs-lookup"><span data-stu-id="aad20-122">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="aad20-123">From, clause</span><span class="sxs-lookup"><span data-stu-id="aad20-123">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="aad20-124">Order By (clause)</span><span class="sxs-lookup"><span data-stu-id="aad20-124">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="aad20-125">SkipWhile (clause)</span><span class="sxs-lookup"><span data-stu-id="aad20-125">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="aad20-126">Take (clause)</span><span class="sxs-lookup"><span data-stu-id="aad20-126">Take Clause</span></span>](take-clause.md)
