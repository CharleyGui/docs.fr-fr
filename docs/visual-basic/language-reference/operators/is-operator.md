---
title: Opérateur is
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 1c2d87ef0a8202332c87af552f488d652c400213
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812261"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="d2101-102">Opérateur is (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2101-102">Is operator (Visual Basic)</span></span>

<span data-ttu-id="d2101-103">Compare deux variables de référence d’objet.</span><span class="sxs-lookup"><span data-stu-id="d2101-103">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="d2101-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2101-104">Syntax</span></span>

```vb
result = object1 Is object2
```

## <a name="parts"></a><span data-ttu-id="d2101-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="d2101-105">Parts</span></span>

 `result`  
 <span data-ttu-id="d2101-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d2101-106">Required.</span></span> <span data-ttu-id="d2101-107">Toute `Boolean` valeur.</span><span class="sxs-lookup"><span data-stu-id="d2101-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="d2101-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d2101-108">Required.</span></span> <span data-ttu-id="d2101-109">N’importe quel `Object` nom.</span><span class="sxs-lookup"><span data-stu-id="d2101-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="d2101-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d2101-110">Required.</span></span> <span data-ttu-id="d2101-111">N’importe quel `Object` nom.</span><span class="sxs-lookup"><span data-stu-id="d2101-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2101-112">Notes</span><span class="sxs-lookup"><span data-stu-id="d2101-112">Remarks</span></span>

<span data-ttu-id="d2101-113">L' `Is` opérateur détermine si deux références d’objet font référence au même objet.</span><span class="sxs-lookup"><span data-stu-id="d2101-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="d2101-114">Toutefois, il n’effectue pas de comparaisons de valeurs.</span><span class="sxs-lookup"><span data-stu-id="d2101-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="d2101-115">Si `object1` et `object2` font tous deux référence à la même instance d’objet, `result` est ; dans le `True` cas contraire, `result` est `False` .</span><span class="sxs-lookup"><span data-stu-id="d2101-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>

> [!NOTE]
> <span data-ttu-id="d2101-116">Le `Is` mot clé est également utilisé dans la [sélection... Instruction case](../statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d2101-116">The `Is` keyword is also used in the [Select...Case Statement](../statements/select-case-statement.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="d2101-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="d2101-117">Example</span></span>

<span data-ttu-id="d2101-118">L’exemple suivant utilise l' `Is` opérateur pour comparer des paires de références d’objets.</span><span class="sxs-lookup"><span data-stu-id="d2101-118">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="d2101-119">Les résultats sont assignés à une `Boolean` valeur indiquant si les deux objets sont identiques.</span><span class="sxs-lookup"><span data-stu-id="d2101-119">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>

[!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]

<span data-ttu-id="d2101-120">Comme le montre l’exemple précédent, vous pouvez utiliser l' `Is` opérateur pour tester à la fois les objets à liaison anticipée et les objets à liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="d2101-120">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>

## <a name="use-typeof-operator-with-is-operator"></a><span data-ttu-id="d2101-121">Utiliser l’opérateur TypeOf avec opérateur is</span><span class="sxs-lookup"><span data-stu-id="d2101-121">Use TypeOf operator with Is operator</span></span>

<span data-ttu-id="d2101-122">`Is` l’opérateur peut également être utilisé avec le `TypeOf` mot clé pour créer une `TypeOf` expression... `Is` , qui teste si une variable objet est compatible avec un type de données.</span><span class="sxs-lookup"><span data-stu-id="d2101-122">`Is` operator can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span> <span data-ttu-id="d2101-123">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d2101-123">For example:</span></span>

```vb
If TypeOf sender Is Button Then
```

## <a name="see-also"></a><span data-ttu-id="d2101-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2101-124">See also</span></span>

- [<span data-ttu-id="d2101-125">TypeOf, opérateur</span><span class="sxs-lookup"><span data-stu-id="d2101-125">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="d2101-126">IsNot, opérateur</span><span class="sxs-lookup"><span data-stu-id="d2101-126">IsNot Operator</span></span>](isnot-operator.md)
- [<span data-ttu-id="d2101-127">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d2101-127">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="d2101-128">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d2101-128">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="d2101-129">Opérateurs listés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="d2101-129">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="d2101-130">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="d2101-130">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
