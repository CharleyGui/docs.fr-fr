---
title: Not, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 56cdeb80a217dbce15921eddd6a43d8d1b049376
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401457"
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="f66c9-102">Not, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f66c9-102">Not Operator (Visual Basic)</span></span>
<span data-ttu-id="f66c9-103">Effectue une négation logique sur une `Boolean` expression ou une négation au niveau du bit sur une expression numérique.</span><span class="sxs-lookup"><span data-stu-id="f66c9-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f66c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f66c9-104">Syntax</span></span>  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="f66c9-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="f66c9-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="f66c9-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f66c9-106">Required.</span></span> <span data-ttu-id="f66c9-107">Toute expression `Boolean` ou numérique.</span><span class="sxs-lookup"><span data-stu-id="f66c9-107">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="f66c9-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f66c9-108">Required.</span></span> <span data-ttu-id="f66c9-109">Toute expression `Boolean` ou numérique.</span><span class="sxs-lookup"><span data-stu-id="f66c9-109">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f66c9-110">Notes</span><span class="sxs-lookup"><span data-stu-id="f66c9-110">Remarks</span></span>  
 <span data-ttu-id="f66c9-111">Pour `Boolean` les expressions, le tableau suivant illustre la façon dont `result` est déterminé.</span><span class="sxs-lookup"><span data-stu-id="f66c9-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="f66c9-112">Si `expression` est </span><span class="sxs-lookup"><span data-stu-id="f66c9-112">If `expression` is</span></span>|<span data-ttu-id="f66c9-113">La valeur de `result` est</span><span class="sxs-lookup"><span data-stu-id="f66c9-113">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="f66c9-114">Pour les expressions numériques, l' `Not` opérateur inverse les valeurs de bit d’une expression numérique et définit le bit correspondant dans `result` selon le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="f66c9-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="f66c9-115">Si le bit dans `expression` est</span><span class="sxs-lookup"><span data-stu-id="f66c9-115">If bit in `expression` is</span></span>|<span data-ttu-id="f66c9-116">Le bit dans `result` est</span><span class="sxs-lookup"><span data-stu-id="f66c9-116">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="f66c9-117">1</span><span class="sxs-lookup"><span data-stu-id="f66c9-117">1</span></span>|<span data-ttu-id="f66c9-118">0</span><span class="sxs-lookup"><span data-stu-id="f66c9-118">0</span></span>|  
|<span data-ttu-id="f66c9-119">0</span><span class="sxs-lookup"><span data-stu-id="f66c9-119">0</span></span>|<span data-ttu-id="f66c9-120">1</span><span class="sxs-lookup"><span data-stu-id="f66c9-120">1</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="f66c9-121">Étant donné que les opérateurs logiques et au niveau du bit ont une priorité inférieure à celle des autres opérateurs arithmétiques et relationnels, toutes les opérations au niveau du bit doivent être mises entre parenthèses pour garantir une exécution précise.</span><span class="sxs-lookup"><span data-stu-id="f66c9-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="f66c9-122">Types de données</span><span class="sxs-lookup"><span data-stu-id="f66c9-122">Data Types</span></span>  
 <span data-ttu-id="f66c9-123">Pour une négation booléenne, le type de données du résultat est `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="f66c9-123">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="f66c9-124">Pour une négation au niveau du bit, le type de données de résultat est le même que celui de `expression` .</span><span class="sxs-lookup"><span data-stu-id="f66c9-124">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="f66c9-125">Toutefois, si l’expression est `Decimal` , le résultat est `Long` .</span><span class="sxs-lookup"><span data-stu-id="f66c9-125">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="f66c9-126">Surcharge</span><span class="sxs-lookup"><span data-stu-id="f66c9-126">Overloading</span></span>  
 <span data-ttu-id="f66c9-127">L' `Not` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsque son opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="f66c9-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="f66c9-128">Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="f66c9-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f66c9-129">Pour plus d'informations, consultez [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f66c9-129">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f66c9-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="f66c9-130">Example</span></span>  
 <span data-ttu-id="f66c9-131">L’exemple suivant utilise l' `Not` opérateur pour effectuer une négation logique sur une `Boolean` expression.</span><span class="sxs-lookup"><span data-stu-id="f66c9-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="f66c9-132">Le résultat est une `Boolean` valeur qui représente l’inverse de la valeur de l’expression.</span><span class="sxs-lookup"><span data-stu-id="f66c9-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 <span data-ttu-id="f66c9-133">L’exemple précédent produit les résultats de `False` et `True` , respectivement.</span><span class="sxs-lookup"><span data-stu-id="f66c9-133">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f66c9-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="f66c9-134">Example</span></span>  
 <span data-ttu-id="f66c9-135">L’exemple suivant utilise l' `Not` opérateur pour effectuer une négation logique des bits individuels d’une expression numérique.</span><span class="sxs-lookup"><span data-stu-id="f66c9-135">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="f66c9-136">Le bit dans le modèle de résultat est défini à l’inverse du bit correspondant dans le modèle d’opérande, y compris le bit de signe.</span><span class="sxs-lookup"><span data-stu-id="f66c9-136">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 <span data-ttu-id="f66c9-137">L’exemple précédent produit respectivement les résultats-11, – 9 et-7.</span><span class="sxs-lookup"><span data-stu-id="f66c9-137">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f66c9-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f66c9-138">See also</span></span>

- [<span data-ttu-id="f66c9-139">Opérateurs logiques/de bits (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f66c9-139">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="f66c9-140">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f66c9-140">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="f66c9-141">Opérateurs listés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="f66c9-141">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="f66c9-142">Opérateurs de bits et opérateurs logiques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f66c9-142">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
