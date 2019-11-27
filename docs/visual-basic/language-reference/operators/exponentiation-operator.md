---
title: ^, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponentiation
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
ms.openlocfilehash: b9860b7b6e076fc9c0288818aa9e4f2c0fc4c356
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331106"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="96d99-102">^, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96d99-102">^ Operator (Visual Basic)</span></span>

<span data-ttu-id="96d99-103">Élève un nombre à la puissance d’un autre nombre.</span><span class="sxs-lookup"><span data-stu-id="96d99-103">Raises a number to the power of another number.</span></span>

## <a name="syntax"></a><span data-ttu-id="96d99-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96d99-104">Syntax</span></span>

```vb
number ^ exponent
```

## <a name="parts"></a><span data-ttu-id="96d99-105">Composants</span><span class="sxs-lookup"><span data-stu-id="96d99-105">Parts</span></span>

`number`\
<span data-ttu-id="96d99-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="96d99-106">Required.</span></span> <span data-ttu-id="96d99-107">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="96d99-107">Any numeric expression.</span></span>

`exponent`\
<span data-ttu-id="96d99-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="96d99-108">Required.</span></span> <span data-ttu-id="96d99-109">Toute expression numérique.</span><span class="sxs-lookup"><span data-stu-id="96d99-109">Any numeric expression.</span></span>

## <a name="result"></a><span data-ttu-id="96d99-110">Résultat</span><span class="sxs-lookup"><span data-stu-id="96d99-110">Result</span></span>

<span data-ttu-id="96d99-111">Le résultat est `number` élevé à la puissance de `exponent`, toujours en tant que valeur de `Double`.</span><span class="sxs-lookup"><span data-stu-id="96d99-111">The result is `number` raised to the power of `exponent`, always as a `Double` value.</span></span>

## <a name="supported-types"></a><span data-ttu-id="96d99-112">Types pris en charge</span><span class="sxs-lookup"><span data-stu-id="96d99-112">Supported Types</span></span>

<span data-ttu-id="96d99-113">`Double`</span><span class="sxs-lookup"><span data-stu-id="96d99-113">`Double`.</span></span> <span data-ttu-id="96d99-114">Les opérandes de tout type différent sont convertis en `Double`.</span><span class="sxs-lookup"><span data-stu-id="96d99-114">Operands of any different type are converted to `Double`.</span></span>

## <a name="remarks"></a><span data-ttu-id="96d99-115">Notes</span><span class="sxs-lookup"><span data-stu-id="96d99-115">Remarks</span></span>

<span data-ttu-id="96d99-116">Visual Basic effectue toujours une élévation à la puissance dans le [type de données double](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="96d99-116">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span>

<span data-ttu-id="96d99-117">La valeur de `exponent` peut être fractionnaire, négative ou les deux.</span><span class="sxs-lookup"><span data-stu-id="96d99-117">The value of `exponent` can be fractional, negative, or both.</span></span>

<span data-ttu-id="96d99-118">Lorsque plusieurs élévations à une puissance sont effectuées dans une même expression, l’opérateur `^` est évalué à mesure qu’il est rencontré de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="96d99-118">When more than one exponentiation is performed in a single expression, the `^` operator is evaluated as it is encountered from left to right.</span></span>

> [!NOTE]
> <span data-ttu-id="96d99-119">L’opérateur `^` peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure.</span><span class="sxs-lookup"><span data-stu-id="96d99-119">The `^` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="96d99-120">Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="96d99-120">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="96d99-121">Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="96d99-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="example"></a><span data-ttu-id="96d99-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="96d99-122">Example</span></span>

<span data-ttu-id="96d99-123">L’exemple suivant utilise l’opérateur `^` pour élever un nombre à la puissance d’un exposant.</span><span class="sxs-lookup"><span data-stu-id="96d99-123">The following example uses the `^` operator to raise a number to the power of an exponent.</span></span> <span data-ttu-id="96d99-124">Le résultat est le premier opérande élevé à la puissance de la seconde.</span><span class="sxs-lookup"><span data-stu-id="96d99-124">The result is the first operand raised to the power of the second.</span></span>

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

<span data-ttu-id="96d99-125">L’exemple précédent produit les résultats suivants :</span><span class="sxs-lookup"><span data-stu-id="96d99-125">The preceding example produces the following results:</span></span>

<span data-ttu-id="96d99-126">`exp1` a la valeur 4 (2 au carré).</span><span class="sxs-lookup"><span data-stu-id="96d99-126">`exp1` is set to 4 (2 squared).</span></span>

<span data-ttu-id="96d99-127">`exp2` est défini sur 19683 (3 cube, puis sur cette valeur cube).</span><span class="sxs-lookup"><span data-stu-id="96d99-127">`exp2` is set to 19683 (3 cubed, then that value cubed).</span></span>

<span data-ttu-id="96d99-128">`exp3` est défini sur-125 (-5 Cubed).</span><span class="sxs-lookup"><span data-stu-id="96d99-128">`exp3` is set to -125 (-5 cubed).</span></span>

<span data-ttu-id="96d99-129">`exp4` est défini sur 625 (-5 sur la quatrième puissance).</span><span class="sxs-lookup"><span data-stu-id="96d99-129">`exp4` is set to 625 (-5 to the fourth power).</span></span>

<span data-ttu-id="96d99-130">`exp5` a la valeur 2 (racine du cube de 8).</span><span class="sxs-lookup"><span data-stu-id="96d99-130">`exp5` is set to 2 (cube root of 8).</span></span>

<span data-ttu-id="96d99-131">`exp6` a la valeur 0,5 (1,0 divisée par la racine du cube de 8).</span><span class="sxs-lookup"><span data-stu-id="96d99-131">`exp6` is set to 0.5 (1.0 divided by the cube root of 8).</span></span>

<span data-ttu-id="96d99-132">Notez l’importance des parenthèses dans les expressions de l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="96d99-132">Note the importance of the parentheses in the expressions in the preceding example.</span></span> <span data-ttu-id="96d99-133">En raison de la *priorité des opérateurs*, Visual Basic exécute normalement l’opérateur `^` avant les autres, même l’opérateur unaire `–`.</span><span class="sxs-lookup"><span data-stu-id="96d99-133">Because of *operator precedence*, Visual Basic normally performs the `^` operator before any others, even the unary `–` operator.</span></span> <span data-ttu-id="96d99-134">Si `exp4` et `exp6` ont été calculés sans parenthèses, ils auraient produit les résultats suivants :</span><span class="sxs-lookup"><span data-stu-id="96d99-134">If `exp4` and `exp6` had been calculated without parentheses, they would have produced the following results:</span></span>

<span data-ttu-id="96d99-135">`exp4 = -5 ^ 4` serait calculé comme (5 à la quatrième puissance), ce qui se traduirait par-625.</span><span class="sxs-lookup"><span data-stu-id="96d99-135">`exp4 = -5 ^ 4` would be calculated as –(5 to the fourth power), which would result in -625.</span></span>

<span data-ttu-id="96d99-136">`exp6 = 8 ^ -1.0 / 3.0` est calculé comme (8 à-1 puissance, ou 0,125) divisé par 3,0, ce qui se traduirait par 0.041666666666666666666666666666667.</span><span class="sxs-lookup"><span data-stu-id="96d99-136">`exp6 = 8 ^ -1.0 / 3.0` would be calculated as (8 to the –1 power, or 0.125) divided by 3.0, which would result in 0.041666666666666666666666666666667.</span></span>

## <a name="see-also"></a><span data-ttu-id="96d99-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96d99-137">See also</span></span>

- [<span data-ttu-id="96d99-138">^=, opérateur</span><span class="sxs-lookup"><span data-stu-id="96d99-138">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="96d99-139">Opérateurs arithmétiques</span><span class="sxs-lookup"><span data-stu-id="96d99-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="96d99-140">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="96d99-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="96d99-141">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="96d99-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="96d99-142">Opérateurs arithmétiques dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="96d99-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
