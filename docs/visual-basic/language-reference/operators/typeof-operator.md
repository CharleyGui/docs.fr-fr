---
title: TypeOf, opérateur (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- TypeOf
- vb.TypeOf
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators [Visual Basic]
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types [Visual Basic]
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
ms.openlocfilehash: c6028f524a16b836310f0c8d564205244515cdc9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701282"
---
# <a name="typeof-operator-visual-basic"></a><span data-ttu-id="4dc4f-102">TypeOf, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4dc4f-102">TypeOf Operator (Visual Basic)</span></span>
<span data-ttu-id="4dc4f-103">Vérifie si le type d’exécution du résultat d’une expression est compatible avec le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="4dc4f-103">Checks whether the runtime type of an expression's result is type-compatible with the specified type.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="4dc4f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4dc4f-104">Syntax</span></span>  
  
```vb  
result = TypeOf objectexpression Is typename  
```  
  
```vb  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a><span data-ttu-id="4dc4f-105">Composants</span><span class="sxs-lookup"><span data-stu-id="4dc4f-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="4dc4f-106">Retourné.</span><span class="sxs-lookup"><span data-stu-id="4dc4f-106">Returned.</span></span> <span data-ttu-id="4dc4f-107">Valeur `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="4dc4f-107">A `Boolean` value.</span></span>  
  
 `objectexpression`  
 <span data-ttu-id="4dc4f-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4dc4f-108">Required.</span></span> <span data-ttu-id="4dc4f-109">Toute expression ayant pour résultat un type référence.</span><span class="sxs-lookup"><span data-stu-id="4dc4f-109">Any expression that evaluates to a reference type.</span></span>  
  
 `typename`  
 <span data-ttu-id="4dc4f-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4dc4f-110">Required.</span></span> <span data-ttu-id="4dc4f-111">Tout nom de type de données.</span><span class="sxs-lookup"><span data-stu-id="4dc4f-111">Any data type name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4dc4f-112">Notes</span><span class="sxs-lookup"><span data-stu-id="4dc4f-112">Remarks</span></span>  
 <span data-ttu-id="4dc4f-113">L'opérateur `TypeOf` détermine si le type d'exécution de `objectexpression` est compatible avec `typename`.</span><span class="sxs-lookup"><span data-stu-id="4dc4f-113">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span></span> <span data-ttu-id="4dc4f-114">La compatibilité dépend de la catégorie du type de `typename`.</span><span class="sxs-lookup"><span data-stu-id="4dc4f-114">The compatibility depends on the type category of `typename`.</span></span> <span data-ttu-id="4dc4f-115">Le tableau suivant illustre la manière dont la compatibilité est déterminée.</span><span class="sxs-lookup"><span data-stu-id="4dc4f-115">The following table shows how compatibility is determined.</span></span>  
  
|<span data-ttu-id="4dc4f-116">Catégorie de type de `typename`</span><span class="sxs-lookup"><span data-stu-id="4dc4f-116">Type category of `typename`</span></span>|<span data-ttu-id="4dc4f-117">Critère de compatibilité</span><span class="sxs-lookup"><span data-stu-id="4dc4f-117">Compatibility criterion</span></span>|  
|---------------------------------|-----------------------------|  
|<span data-ttu-id="4dc4f-118">Classe</span><span class="sxs-lookup"><span data-stu-id="4dc4f-118">Class</span></span>|<span data-ttu-id="4dc4f-119">`objectexpression` est de type `typename` ou hérite de `typename`</span><span class="sxs-lookup"><span data-stu-id="4dc4f-119">`objectexpression` is of type `typename` or inherits from `typename`</span></span>|  
|<span data-ttu-id="4dc4f-120">Structure</span><span class="sxs-lookup"><span data-stu-id="4dc4f-120">Structure</span></span>|<span data-ttu-id="4dc4f-121">`objectexpression` est de type `typename`</span><span class="sxs-lookup"><span data-stu-id="4dc4f-121">`objectexpression` is of type `typename`</span></span>|  
|<span data-ttu-id="4dc4f-122">Interface</span><span class="sxs-lookup"><span data-stu-id="4dc4f-122">Interface</span></span>|<span data-ttu-id="4dc4f-123">`objectexpression` implémente `typename` ou hérite d'une classe qui implémente `typename`</span><span class="sxs-lookup"><span data-stu-id="4dc4f-123">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span></span>|  
  
 <span data-ttu-id="4dc4f-124">Si le type de l'exécution de `objectexpression` satisfait le critère de compatibilité, `result` est `True`.</span><span class="sxs-lookup"><span data-stu-id="4dc4f-124">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span></span> <span data-ttu-id="4dc4f-125">Sinon, `result` est `False`.</span><span class="sxs-lookup"><span data-stu-id="4dc4f-125">Otherwise, `result` is `False`.</span></span>  <span data-ttu-id="4dc4f-126">Si `objectexpression` est null, alors `TypeOf`...`Is` retourne `False`, et ...`IsNot` retourne `True`.</span><span class="sxs-lookup"><span data-stu-id="4dc4f-126">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span></span>  
  
 <span data-ttu-id="4dc4f-127">`TypeOf` est toujours utilisé avec le mot clé `Is` pour construire une expression `TypeOf`...`Is`, ou avec le mot clé `IsNot` pour construire une expression `TypeOf`...`IsNot`.</span><span class="sxs-lookup"><span data-stu-id="4dc4f-127">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4dc4f-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="4dc4f-128">Example</span></span>  
 <span data-ttu-id="4dc4f-129">L'exemple suivant utilise des expressions `TypeOf`...`Is` pour tester la compatibilité du type de deux variables de référence d'objet avec différents types de données.</span><span class="sxs-lookup"><span data-stu-id="4dc4f-129">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span></span>  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 <span data-ttu-id="4dc4f-130">La variable `refInteger` a un type au moment de l'exécution de `Integer`.</span><span class="sxs-lookup"><span data-stu-id="4dc4f-130">The variable `refInteger` has a run-time type of `Integer`.</span></span> <span data-ttu-id="4dc4f-131">Il est compatible avec `Integer` mais pas avec `Double`.</span><span class="sxs-lookup"><span data-stu-id="4dc4f-131">It is compatible with `Integer` but not with `Double`.</span></span> <span data-ttu-id="4dc4f-132">La variable `refForm` a un type au moment de l'exécution de <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="4dc4f-132">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="4dc4f-133">Il est compatible avec <xref:System.Windows.Forms.Form> car il s'agit de son type, avec <xref:System.Windows.Forms.Control> car <xref:System.Windows.Forms.Form> hérite de <xref:System.Windows.Forms.Control>, et avec <xref:System.ComponentModel.IComponent> car <xref:System.Windows.Forms.Form> hérite de <xref:System.ComponentModel.Component>, qui implémente <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="4dc4f-133">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="4dc4f-134">Toutefois, `refForm` n'est pas compatible avec <xref:System.Windows.Forms.Label>.</span><span class="sxs-lookup"><span data-stu-id="4dc4f-134">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dc4f-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4dc4f-135">See also</span></span>

- [<span data-ttu-id="4dc4f-136">Is (opérateur)</span><span class="sxs-lookup"><span data-stu-id="4dc4f-136">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="4dc4f-137">IsNot (opérateur)</span><span class="sxs-lookup"><span data-stu-id="4dc4f-137">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="4dc4f-138">Opérateurs de comparaison dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4dc4f-138">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="4dc4f-139">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4dc4f-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="4dc4f-140">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="4dc4f-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="4dc4f-141">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="4dc4f-141">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
