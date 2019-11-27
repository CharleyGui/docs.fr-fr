---
title: Is, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 52fbb39ab0a36c8b947b78f464fad26be05ce204
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349536"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="d38f8-102">Is, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d38f8-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="d38f8-103">Compare deux variables de référence d’objet.</span><span class="sxs-lookup"><span data-stu-id="d38f8-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d38f8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d38f8-104">Syntax</span></span>  
  
```vb  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="d38f8-105">Composants</span><span class="sxs-lookup"><span data-stu-id="d38f8-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="d38f8-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="d38f8-106">Required.</span></span> <span data-ttu-id="d38f8-107">Toute valeur `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="d38f8-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="d38f8-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="d38f8-108">Required.</span></span> <span data-ttu-id="d38f8-109">N’importe quel nom de `Object`.</span><span class="sxs-lookup"><span data-stu-id="d38f8-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="d38f8-110">Requis.</span><span class="sxs-lookup"><span data-stu-id="d38f8-110">Required.</span></span> <span data-ttu-id="d38f8-111">N’importe quel nom de `Object`.</span><span class="sxs-lookup"><span data-stu-id="d38f8-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d38f8-112">Notes</span><span class="sxs-lookup"><span data-stu-id="d38f8-112">Remarks</span></span>  
 <span data-ttu-id="d38f8-113">L’opérateur `Is` détermine si deux références d’objet font référence au même objet.</span><span class="sxs-lookup"><span data-stu-id="d38f8-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="d38f8-114">Toutefois, il n’effectue pas de comparaisons de valeurs.</span><span class="sxs-lookup"><span data-stu-id="d38f8-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="d38f8-115">Si `object1` et `object2` font tous deux référence à la même instance d’objet, `result` est `True`. Si ce n’est pas le cas, `result` est `False`.</span><span class="sxs-lookup"><span data-stu-id="d38f8-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="d38f8-116">`Is` peut également être utilisé avec le mot clé `TypeOf` pour créer une expression `TypeOf`...`Is`, qui teste si une variable objet est compatible avec un type de données.</span><span class="sxs-lookup"><span data-stu-id="d38f8-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d38f8-117">Le mot clé `Is` est également utilisé dans la [sélection... Instruction case](../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d38f8-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d38f8-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="d38f8-118">Example</span></span>  
 <span data-ttu-id="d38f8-119">L’exemple suivant utilise l’opérateur `Is` pour comparer des paires de références d’objets.</span><span class="sxs-lookup"><span data-stu-id="d38f8-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="d38f8-120">Les résultats sont assignés à une valeur `Boolean` indiquant si les deux objets sont identiques.</span><span class="sxs-lookup"><span data-stu-id="d38f8-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 <span data-ttu-id="d38f8-121">Comme le montre l’exemple précédent, vous pouvez utiliser l’opérateur `Is` pour tester à la fois les objets à liaison anticipée et les objets à liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="d38f8-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d38f8-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d38f8-122">See also</span></span>

- [<span data-ttu-id="d38f8-123">TypeOf (opérateur)</span><span class="sxs-lookup"><span data-stu-id="d38f8-123">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="d38f8-124">IsNot (opérateur)</span><span class="sxs-lookup"><span data-stu-id="d38f8-124">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="d38f8-125">Opérateurs de comparaison dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d38f8-125">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="d38f8-126">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d38f8-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="d38f8-127">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="d38f8-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="d38f8-128">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="d38f8-128">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
