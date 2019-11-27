---
title: IsNot, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 616506f64d20e1f150b443433f1b69040136a5ba
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336073"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="5fc96-102">Opérateur IsNot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5fc96-102">IsNot Operator (Visual Basic)</span></span>

<span data-ttu-id="5fc96-103">Compare deux variables de référence d’objet.</span><span class="sxs-lookup"><span data-stu-id="5fc96-103">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="5fc96-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5fc96-104">Syntax</span></span>

```vb
result = object1 IsNot object2
```

## <a name="parts"></a><span data-ttu-id="5fc96-105">Composants</span><span class="sxs-lookup"><span data-stu-id="5fc96-105">Parts</span></span>
 <span data-ttu-id="5fc96-106">`result` (obligatoire).</span><span class="sxs-lookup"><span data-stu-id="5fc96-106">`result` Required.</span></span> <span data-ttu-id="5fc96-107">Valeur `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="5fc96-107">A `Boolean` value.</span></span>

 <span data-ttu-id="5fc96-108">`object1` (obligatoire).</span><span class="sxs-lookup"><span data-stu-id="5fc96-108">`object1` Required.</span></span> <span data-ttu-id="5fc96-109">Toute variable ou expression `Object`.</span><span class="sxs-lookup"><span data-stu-id="5fc96-109">Any `Object` variable or expression.</span></span>

 <span data-ttu-id="5fc96-110">`object2` (obligatoire).</span><span class="sxs-lookup"><span data-stu-id="5fc96-110">`object2` Required.</span></span> <span data-ttu-id="5fc96-111">Toute variable ou expression `Object`.</span><span class="sxs-lookup"><span data-stu-id="5fc96-111">Any `Object` variable or expression.</span></span>

## <a name="remarks"></a><span data-ttu-id="5fc96-112">Notes</span><span class="sxs-lookup"><span data-stu-id="5fc96-112">Remarks</span></span>
 <span data-ttu-id="5fc96-113">L’opérateur `IsNot` détermine si deux références d’objet font référence à des objets différents.</span><span class="sxs-lookup"><span data-stu-id="5fc96-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="5fc96-114">Toutefois, il n’effectue pas de comparaisons de valeurs.</span><span class="sxs-lookup"><span data-stu-id="5fc96-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="5fc96-115">Si `object1` et `object2` font tous deux référence à la même instance d’objet, `result` est `False`. Si ce n’est pas le cas, `result` est `True`.</span><span class="sxs-lookup"><span data-stu-id="5fc96-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>

 <span data-ttu-id="5fc96-116">`IsNot` est l’opposé de l’opérateur `Is`.</span><span class="sxs-lookup"><span data-stu-id="5fc96-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="5fc96-117">L’avantage de `IsNot` est que vous pouvez éviter la syntaxe compliquée avec `Not` et `Is`, ce qui peut être difficile à lire.</span><span class="sxs-lookup"><span data-stu-id="5fc96-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>

 <span data-ttu-id="5fc96-118">Vous pouvez utiliser les opérateurs `Is` et `IsNot` pour tester à la fois les objets à liaison anticipée et les objets à liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="5fc96-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>

## <a name="example"></a><span data-ttu-id="5fc96-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="5fc96-119">Example</span></span>
 <span data-ttu-id="5fc96-120">L’exemple de code suivant utilise à la fois l’opérateur `Is` et l’opérateur `IsNot` pour effectuer la même comparaison.</span><span class="sxs-lookup"><span data-stu-id="5fc96-120">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>

 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="see-also"></a><span data-ttu-id="5fc96-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5fc96-121">See also</span></span>

- [<span data-ttu-id="5fc96-122">Is (opérateur)</span><span class="sxs-lookup"><span data-stu-id="5fc96-122">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="5fc96-123">TypeOf (opérateur)</span><span class="sxs-lookup"><span data-stu-id="5fc96-123">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="5fc96-124">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5fc96-124">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="5fc96-125">Guide pratique : déterminer si deux objets sont identiques</span><span class="sxs-lookup"><span data-stu-id="5fc96-125">How to: Test Whether Two Objects Are the Same</span></span>](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
