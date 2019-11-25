---
title: Take While, clause
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 23b7c84a9f896161a66059fcb1f30753d3b863d5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347110"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="10800-102">Take While, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10800-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="10800-103">Inclut les éléments d’une collection tant qu’une condition spécifiée a la valeur `true` et ignore les éléments restants.</span><span class="sxs-lookup"><span data-stu-id="10800-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10800-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10800-104">Syntax</span></span>  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="10800-105">Composants</span><span class="sxs-lookup"><span data-stu-id="10800-105">Parts</span></span>  
  
|<span data-ttu-id="10800-106">Terme</span><span class="sxs-lookup"><span data-stu-id="10800-106">Term</span></span>|<span data-ttu-id="10800-107">Définition</span><span class="sxs-lookup"><span data-stu-id="10800-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="10800-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="10800-108">Required.</span></span> <span data-ttu-id="10800-109">An expression that represents a condition to test elements for.</span><span class="sxs-lookup"><span data-stu-id="10800-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="10800-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="10800-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10800-111">Notes</span><span class="sxs-lookup"><span data-stu-id="10800-111">Remarks</span></span>  
 <span data-ttu-id="10800-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span><span class="sxs-lookup"><span data-stu-id="10800-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="10800-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span><span class="sxs-lookup"><span data-stu-id="10800-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="10800-114">The `expression` is ignored for the remaining results.</span><span class="sxs-lookup"><span data-stu-id="10800-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="10800-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span><span class="sxs-lookup"><span data-stu-id="10800-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="10800-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span><span class="sxs-lookup"><span data-stu-id="10800-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="10800-117">The `Take While` clause is most useful when you are working with an ordered query result.</span><span class="sxs-lookup"><span data-stu-id="10800-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10800-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="10800-118">Example</span></span>  
 <span data-ttu-id="10800-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span><span class="sxs-lookup"><span data-stu-id="10800-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="10800-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10800-120">See also</span></span>

- [<span data-ttu-id="10800-121">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10800-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="10800-122">Requêtes</span><span class="sxs-lookup"><span data-stu-id="10800-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="10800-123">Select (clause)</span><span class="sxs-lookup"><span data-stu-id="10800-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="10800-124">From (clause)</span><span class="sxs-lookup"><span data-stu-id="10800-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="10800-125">Take (clause)</span><span class="sxs-lookup"><span data-stu-id="10800-125">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="10800-126">Skip While (clause)</span><span class="sxs-lookup"><span data-stu-id="10800-126">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="10800-127">Where (clause)</span><span class="sxs-lookup"><span data-stu-id="10800-127">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
