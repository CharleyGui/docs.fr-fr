---
title: IsNot (opérateur)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- comparison operators [Visual Basic]
- TypeOf...IsNot expression
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: ea978f8874cee20fb3a005189fd846f7564da777
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811039"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="60279-102">Opérateur IsNot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60279-102">IsNot Operator (Visual Basic)</span></span>

<span data-ttu-id="60279-103">Compare deux variables de référence d’objet.</span><span class="sxs-lookup"><span data-stu-id="60279-103">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="60279-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60279-104">Syntax</span></span>

```vb
result = object1 IsNot object2
```

## <a name="parts"></a><span data-ttu-id="60279-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="60279-105">Parts</span></span>

- `result`

  <span data-ttu-id="60279-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="60279-106">Required.</span></span> <span data-ttu-id="60279-107">Valeur `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="60279-107">A `Boolean` value.</span></span>

- `object1`

  <span data-ttu-id="60279-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="60279-108">Required.</span></span> <span data-ttu-id="60279-109">Toute `Object` variable ou expression.</span><span class="sxs-lookup"><span data-stu-id="60279-109">Any `Object` variable or expression.</span></span>

- `object2`

  <span data-ttu-id="60279-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="60279-110">Required.</span></span> <span data-ttu-id="60279-111">Toute `Object` variable ou expression.</span><span class="sxs-lookup"><span data-stu-id="60279-111">Any `Object` variable or expression.</span></span>

## <a name="remarks"></a><span data-ttu-id="60279-112">Notes</span><span class="sxs-lookup"><span data-stu-id="60279-112">Remarks</span></span>

<span data-ttu-id="60279-113">L' `IsNot` opérateur détermine si deux références d’objet font référence à des objets différents.</span><span class="sxs-lookup"><span data-stu-id="60279-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="60279-114">Toutefois, il n’effectue pas de comparaisons de valeurs.</span><span class="sxs-lookup"><span data-stu-id="60279-114">However, it doesn't perform value comparisons.</span></span> <span data-ttu-id="60279-115">Si `object1` et `object2` les deux font référence exactement à la même instance d’objet, `result` est `False` ; sinon, `result` est `True` .</span><span class="sxs-lookup"><span data-stu-id="60279-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they don't, `result` is `True`.</span></span>

<span data-ttu-id="60279-116">`IsNot` est l’opposé de l' `Is` opérateur.</span><span class="sxs-lookup"><span data-stu-id="60279-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="60279-117">L’avantage de `IsNot` est que vous pouvez éviter la syntaxe maladroite avec `Not` et `Is` , ce qui peut être difficile à lire.</span><span class="sxs-lookup"><span data-stu-id="60279-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>

 <span data-ttu-id="60279-118">Vous pouvez utiliser les `Is` `IsNot` opérateurs et pour tester à la fois les objets à liaison anticipée et les objets à liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="60279-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>

## <a name="example"></a><span data-ttu-id="60279-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="60279-119">Example</span></span>

<span data-ttu-id="60279-120">L’exemple de code suivant utilise à la fois l' `Is` opérateur et l' `IsNot` opérateur pour effectuer la même comparaison.</span><span class="sxs-lookup"><span data-stu-id="60279-120">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>

[!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="use-typeof-operator-with-isnot-operator"></a><span data-ttu-id="60279-121">Utiliser l’opérateur TypeOf avec l’opérateur IsNot</span><span class="sxs-lookup"><span data-stu-id="60279-121">Use TypeOf operator with IsNot operator</span></span>

<span data-ttu-id="60279-122">À partir de Visual Basic 14, vous pouvez utiliser l' `TypeOf` opérateur avec l' `IsNot` opérateur pour tester si un objet n’est *pas* compatible avec un type de données.</span><span class="sxs-lookup"><span data-stu-id="60279-122">Starting with Visual Basic 14, you can use the `TypeOf` operator with the `IsNot` operator to test whether an object is *not* compatible with a data type.</span></span> <span data-ttu-id="60279-123">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="60279-123">For example:</span></span>

```vb
If TypeOf sender IsNot Button Then
```

## <a name="see-also"></a><span data-ttu-id="60279-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60279-124">See also</span></span>

- [<span data-ttu-id="60279-125">Is, opérateur</span><span class="sxs-lookup"><span data-stu-id="60279-125">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="60279-126">TypeOf, opérateur</span><span class="sxs-lookup"><span data-stu-id="60279-126">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="60279-127">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="60279-127">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="60279-128">Comment : déterminer si deux objets sont identiques</span><span class="sxs-lookup"><span data-stu-id="60279-128">How to: Test Whether Two Objects Are the Same</span></span>](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
