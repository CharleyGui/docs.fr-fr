---
title: Opérateur IsNot (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 0a83b48e5e415bd6ca0c777cef6d34f7127691b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966934"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="6484a-102">Opérateur IsNot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6484a-102">IsNot Operator (Visual Basic)</span></span>
<span data-ttu-id="6484a-103">Compare deux variables de référence d’objet.</span><span class="sxs-lookup"><span data-stu-id="6484a-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6484a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6484a-104">Syntax</span></span>  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a><span data-ttu-id="6484a-105">Composants</span><span class="sxs-lookup"><span data-stu-id="6484a-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="6484a-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="6484a-106">Required.</span></span> <span data-ttu-id="6484a-107">Valeur `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="6484a-107">A `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="6484a-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="6484a-108">Required.</span></span> <span data-ttu-id="6484a-109">Toute `Object` variable ou expression.</span><span class="sxs-lookup"><span data-stu-id="6484a-109">Any `Object` variable or expression.</span></span>  
  
 `object2`  
 <span data-ttu-id="6484a-110">Requis.</span><span class="sxs-lookup"><span data-stu-id="6484a-110">Required.</span></span> <span data-ttu-id="6484a-111">Toute `Object` variable ou expression.</span><span class="sxs-lookup"><span data-stu-id="6484a-111">Any `Object` variable or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6484a-112">Notes</span><span class="sxs-lookup"><span data-stu-id="6484a-112">Remarks</span></span>  
 <span data-ttu-id="6484a-113">L' `IsNot` opérateur détermine si deux références d’objet font référence à des objets différents.</span><span class="sxs-lookup"><span data-stu-id="6484a-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="6484a-114">Toutefois, il n’effectue pas de comparaisons de valeurs.</span><span class="sxs-lookup"><span data-stu-id="6484a-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="6484a-115">Si `object1` et `False` `result` `result` `True`font tous deux référence à la même instance d’objet, est; dans le cas contraire, est. `object2`</span><span class="sxs-lookup"><span data-stu-id="6484a-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>  
  
 <span data-ttu-id="6484a-116">`IsNot`est l’opposé de l' `Is` opérateur.</span><span class="sxs-lookup"><span data-stu-id="6484a-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="6484a-117">L’avantage de `IsNot` est que vous pouvez éviter la syntaxe maladroite `Is`avec `Not` et, ce qui peut être difficile à lire.</span><span class="sxs-lookup"><span data-stu-id="6484a-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>  
  
 <span data-ttu-id="6484a-118">Vous pouvez utiliser les `Is` opérateurs `IsNot` et pour tester à la fois les objets à liaison anticipée et les objets à liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="6484a-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6484a-119">L' `IsNot` opérateur ne peut pas être utilisé pour comparer des expressions `TypeOf` retournées par l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="6484a-119">The `IsNot` operator cannot be used to compare expressions returned from the `TypeOf` operator.</span></span> <span data-ttu-id="6484a-120">Au lieu de cela, vous `Not` devez `Is` utiliser les opérateurs et.</span><span class="sxs-lookup"><span data-stu-id="6484a-120">Instead, you must use the `Not` and `Is` operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6484a-121">Exemples</span><span class="sxs-lookup"><span data-stu-id="6484a-121">Example</span></span>  
 <span data-ttu-id="6484a-122">L’exemple de code suivant utilise à `Is` la fois l' `IsNot` opérateur et l’opérateur pour effectuer la même comparaison.</span><span class="sxs-lookup"><span data-stu-id="6484a-122">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>  
  
 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]  
  
## <a name="see-also"></a><span data-ttu-id="6484a-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6484a-123">See also</span></span>

- [<span data-ttu-id="6484a-124">Is (opérateur)</span><span class="sxs-lookup"><span data-stu-id="6484a-124">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="6484a-125">TypeOf (opérateur)</span><span class="sxs-lookup"><span data-stu-id="6484a-125">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="6484a-126">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6484a-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="6484a-127">Guide pratique pour Teste si deux objets sont identiques</span><span class="sxs-lookup"><span data-stu-id="6484a-127">How to: Test Whether Two Objects Are the Same</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
