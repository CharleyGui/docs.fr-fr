---
title: Priorité des opérateurs en Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operators [Visual Basic], precedence
- operator precedence
- logical operators [Visual Basic], precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators [Visual Basic]
- operators [Visual Basic], precedence
- precedence [Visual Basic], of operators
- comparison operators [Visual Basic], precedence
- math operators [Visual Basic]
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
ms.openlocfilehash: c420a34a18f9e8fb55411a062e6a47ab38e98978
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69611493"
---
# <a name="operator-precedence-in-visual-basic"></a><span data-ttu-id="8e1a7-102">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8e1a7-102">Operator Precedence in Visual Basic</span></span>
<span data-ttu-id="8e1a7-103">Lorsque plusieurs opérations se produisent dans une expression, chaque composant est évalué et résolu dans un ordre prédéterminé appelé *priorité d’opérateur*.</span><span class="sxs-lookup"><span data-stu-id="8e1a7-103">When several operations occur in an expression, each part is evaluated and resolved in a predetermined order called *operator precedence*.</span></span>

## <a name="precedence-rules"></a><span data-ttu-id="8e1a7-104">Règles de précédence</span><span class="sxs-lookup"><span data-stu-id="8e1a7-104">Precedence Rules</span></span>
 <span data-ttu-id="8e1a7-105">Lorsque des expressions contiennent des opérateurs issus de plusieurs catégories, elles sont évaluées en fonction des règles suivantes:</span><span class="sxs-lookup"><span data-stu-id="8e1a7-105">When expressions contain operators from more than one category, they are evaluated according to the following rules:</span></span>

- <span data-ttu-id="8e1a7-106">Les opérateurs arithmétiques et de concaténation ont l’ordre de priorité décrit dans la section suivante, et tous ont une priorité plus élevée que les opérateurs de comparaison, logiques et au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="8e1a7-106">The arithmetic and concatenation operators have the order of precedence described in the following section, and all have greater precedence than the comparison, logical, and bitwise operators.</span></span>

- <span data-ttu-id="8e1a7-107">Tous les opérateurs de comparaison ont une priorité égale, et tous ont une priorité plus élevée que les opérateurs logiques et au niveau du bit, mais une priorité plus faible que les opérateurs arithmétiques et de concaténation.</span><span class="sxs-lookup"><span data-stu-id="8e1a7-107">All comparison operators have equal precedence, and all have greater precedence than the logical and bitwise operators, but lower precedence than the arithmetic and concatenation operators.</span></span>

- <span data-ttu-id="8e1a7-108">Les opérateurs logiques et au niveau du bit ont l’ordre de priorité décrit dans la section suivante, et tous ont une priorité plus faible que les opérateurs arithmétiques, de concaténation et de comparaison.</span><span class="sxs-lookup"><span data-stu-id="8e1a7-108">The logical and bitwise operators have the order of precedence described in the following section, and all have lower precedence than the arithmetic, concatenation, and comparison operators.</span></span>

- <span data-ttu-id="8e1a7-109">Les opérateurs de même priorité sont évalués de gauche à droite dans l’ordre dans lequel ils apparaissent dans l’expression.</span><span class="sxs-lookup"><span data-stu-id="8e1a7-109">Operators with equal precedence are evaluated left to right in the order in which they appear in the expression.</span></span>

## <a name="precedence-order"></a><span data-ttu-id="8e1a7-110">Ordre de priorité</span><span class="sxs-lookup"><span data-stu-id="8e1a7-110">Precedence Order</span></span>
 <span data-ttu-id="8e1a7-111">Les opérateurs sont évalués dans l’ordre de priorité suivant:</span><span class="sxs-lookup"><span data-stu-id="8e1a7-111">Operators are evaluated in the following order of precedence:</span></span>

### <a name="await-operator"></a><span data-ttu-id="8e1a7-112">Await, opérateur</span><span class="sxs-lookup"><span data-stu-id="8e1a7-112">Await Operator</span></span>
 <span data-ttu-id="8e1a7-113">Await</span><span class="sxs-lookup"><span data-stu-id="8e1a7-113">Await</span></span>

### <a name="arithmetic-and-concatenation-operators"></a><span data-ttu-id="8e1a7-114">Opérateurs arithmétiques et de concaténation</span><span class="sxs-lookup"><span data-stu-id="8e1a7-114">Arithmetic and Concatenation Operators</span></span>
 <span data-ttu-id="8e1a7-115">Élévation à`^`la puissance ()</span><span class="sxs-lookup"><span data-stu-id="8e1a7-115">Exponentiation (`^`)</span></span>

 <span data-ttu-id="8e1a7-116">Négation et identité unaire (`+`, `–`)</span><span class="sxs-lookup"><span data-stu-id="8e1a7-116">Unary identity and negation (`+`, `–`)</span></span>

 <span data-ttu-id="8e1a7-117">Multiplication et Division à virgule flottante (`*`, `/`)</span><span class="sxs-lookup"><span data-stu-id="8e1a7-117">Multiplication and floating-point division (`*`, `/`)</span></span>

 <span data-ttu-id="8e1a7-118">Division d’entier`\`()</span><span class="sxs-lookup"><span data-stu-id="8e1a7-118">Integer division (`\`)</span></span>

 <span data-ttu-id="8e1a7-119">Modulo arithmétique (`Mod`)</span><span class="sxs-lookup"><span data-stu-id="8e1a7-119">Modulus arithmetic (`Mod`)</span></span>

 <span data-ttu-id="8e1a7-120">Addition et soustraction (`+`, `–`)</span><span class="sxs-lookup"><span data-stu-id="8e1a7-120">Addition and subtraction (`+`, `–`)</span></span>

 <span data-ttu-id="8e1a7-121">Concaténation de chaînes`&`()</span><span class="sxs-lookup"><span data-stu-id="8e1a7-121">String concatenation (`&`)</span></span>

 <span data-ttu-id="8e1a7-122">Décalage binaire arithmétique (`<<`, `>>`)</span><span class="sxs-lookup"><span data-stu-id="8e1a7-122">Arithmetic bit shift (`<<`, `>>`)</span></span>

### <a name="comparison-operators"></a><span data-ttu-id="8e1a7-123">Opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="8e1a7-123">Comparison Operators</span></span>
 <span data-ttu-id="8e1a7-124">Tous les opérateurs de`=`comparaison `<>`( `<`, `<=`, `>`, `>=`,,, `Is`, ,`IsNot` ,..`TypeOf`. `Like` `Is`)</span><span class="sxs-lookup"><span data-stu-id="8e1a7-124">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span></span>

### <a name="logical-and-bitwise-operators"></a><span data-ttu-id="8e1a7-125">Opérateurs de bits et opérateurs logiques</span><span class="sxs-lookup"><span data-stu-id="8e1a7-125">Logical and Bitwise Operators</span></span>
 <span data-ttu-id="8e1a7-126">Négation (`Not`)</span><span class="sxs-lookup"><span data-stu-id="8e1a7-126">Negation (`Not`)</span></span>

 <span data-ttu-id="8e1a7-127">Conjonction`And`( `AndAlso`,)</span><span class="sxs-lookup"><span data-stu-id="8e1a7-127">Conjunction (`And`, `AndAlso`)</span></span>

 <span data-ttu-id="8e1a7-128">Disjonction inclusive (`Or`, `OrElse`)</span><span class="sxs-lookup"><span data-stu-id="8e1a7-128">Inclusive disjunction (`Or`, `OrElse`)</span></span>

 <span data-ttu-id="8e1a7-129">Disjonction exclusive (`Xor`)</span><span class="sxs-lookup"><span data-stu-id="8e1a7-129">Exclusive disjunction (`Xor`)</span></span>

### <a name="comments"></a><span data-ttu-id="8e1a7-130">Commentaires</span><span class="sxs-lookup"><span data-stu-id="8e1a7-130">Comments</span></span>
 <span data-ttu-id="8e1a7-131">L' `=` opérateur est uniquement l’opérateur de comparaison d’égalité, et non l’opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="8e1a7-131">The `=` operator is only the equality comparison operator, not the assignment operator.</span></span>

 <span data-ttu-id="8e1a7-132">L’opérateur de concaténation de`&`chaînes () n’est pas un opérateur arithmétique, mais en priorité il est groupé avec les opérateurs arithmétiques.</span><span class="sxs-lookup"><span data-stu-id="8e1a7-132">The string concatenation operator (`&`) is not an arithmetic operator, but in precedence it is grouped with the arithmetic operators.</span></span>

 <span data-ttu-id="8e1a7-133">Les `Is` opérateurs `IsNot` et sont des opérateurs de comparaison de référence d’objet.</span><span class="sxs-lookup"><span data-stu-id="8e1a7-133">The `Is` and `IsNot` operators are object reference comparison operators.</span></span> <span data-ttu-id="8e1a7-134">Elles ne comparent pas les valeurs de deux objets; ils vérifient uniquement si deux variables d’objet font référence à la même instance d’objet.</span><span class="sxs-lookup"><span data-stu-id="8e1a7-134">They do not compare the values of two objects; they check only to determine whether two object variables refer to the same object instance.</span></span>

## <a name="associativity"></a><span data-ttu-id="8e1a7-135">l'associativité</span><span class="sxs-lookup"><span data-stu-id="8e1a7-135">Associativity</span></span>
 <span data-ttu-id="8e1a7-136">Lorsque des opérateurs de priorité égale apparaissent ensemble dans une expression, par exemple multiplication et Division, le compilateur évalue chaque opération à mesure qu’elle le rencontre de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="8e1a7-136">When operators of equal precedence appear together in an expression, for example multiplication and division, the compiler evaluates each operation as it encounters it from left to right.</span></span> <span data-ttu-id="8e1a7-137">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="8e1a7-137">The following example illustrates this.</span></span>

```vb
Dim n1 As Integer = 96 / 8 / 4
Dim n2 As Integer = (96 / 8) / 4
Dim n3 As Integer = 96 / (8 / 4)
```

 <span data-ttu-id="8e1a7-138">La première expression évalue la division 96/8 (qui donne 12), puis la division 12/4, qui donne trois valeurs.</span><span class="sxs-lookup"><span data-stu-id="8e1a7-138">The first expression evaluates the division 96 / 8 (which results in 12) and then the division 12 / 4, which results in three.</span></span> <span data-ttu-id="8e1a7-139">Étant donné que le compilateur évalue les `n1` opérations de gauche à droite, l’évaluation est la même lorsque cet ordre est explicitement indiqué `n2`pour.</span><span class="sxs-lookup"><span data-stu-id="8e1a7-139">Because the compiler evaluates the operations for `n1` from left to right, the evaluation is the same when that order is explicitly indicated for `n2`.</span></span> <span data-ttu-id="8e1a7-140">`n1` Et`n2` ont tous les deux la valeur trois.</span><span class="sxs-lookup"><span data-stu-id="8e1a7-140">Both `n1` and `n2` have a result of three.</span></span> <span data-ttu-id="8e1a7-141">En revanche, `n3` a le résultat 48, car les parenthèses forcent le compilateur à évaluer 8/4 en premier.</span><span class="sxs-lookup"><span data-stu-id="8e1a7-141">By contrast, `n3` has a result of 48, because the parentheses force the compiler to evaluate 8 / 4 first.</span></span>

 <span data-ttu-id="8e1a7-142">En raison de ce comportement, on dit que les opérateurs sont associatifs à *gauche* dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8e1a7-142">Because of this behavior, operators are said to be *left associative* in Visual Basic.</span></span>

## <a name="overriding-precedence-and-associativity"></a><span data-ttu-id="8e1a7-143">Substitution de la priorité et de l’associativité</span><span class="sxs-lookup"><span data-stu-id="8e1a7-143">Overriding Precedence and Associativity</span></span>
 <span data-ttu-id="8e1a7-144">Vous pouvez utiliser des parenthèses pour forcer l’évaluation de certaines parties d’une expression avant d’autres.</span><span class="sxs-lookup"><span data-stu-id="8e1a7-144">You can use parentheses to force some parts of an expression to be evaluated before others.</span></span> <span data-ttu-id="8e1a7-145">Cela peut remplacer l’ordre de priorité et l’associativité à gauche.</span><span class="sxs-lookup"><span data-stu-id="8e1a7-145">This can override both the order of precedence and the left associativity.</span></span> <span data-ttu-id="8e1a7-146">Visual Basic effectue toujours des opérations placées entre parenthèses avant celles extérieures à.</span><span class="sxs-lookup"><span data-stu-id="8e1a7-146">Visual Basic always performs operations that are enclosed in parentheses before those outside.</span></span> <span data-ttu-id="8e1a7-147">Toutefois, entre parenthèses, il gère la priorité et l’associativité ordinaires, sauf si vous utilisez des parenthèses entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="8e1a7-147">However, within parentheses, it maintains ordinary precedence and associativity, unless you use parentheses within the parentheses.</span></span> <span data-ttu-id="8e1a7-148">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="8e1a7-148">The following example illustrates this.</span></span>

```vb
Dim a, b, c, d, e, f, g As Double
a = 8.0
b = 3.0
c = 4.0
d = 2.0
e = 1.0
f = a - b + c / d * e
' The preceding line sets f to 7.0. Because of natural operator
' precedence and associativity, it is exactly equivalent to the
' following line.
f = (a - b) + ((c / d) * e)
' The following line overrides the natural operator precedence
' and left associativity.
g = (a - (b + c)) / (d * e)
' The preceding line sets g to 0.5.
```

## <a name="see-also"></a><span data-ttu-id="8e1a7-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e1a7-149">See also</span></span>

- [<span data-ttu-id="8e1a7-150">= (opérateur)</span><span class="sxs-lookup"><span data-stu-id="8e1a7-150">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [<span data-ttu-id="8e1a7-151">Is (opérateur)</span><span class="sxs-lookup"><span data-stu-id="8e1a7-151">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="8e1a7-152">IsNot (opérateur)</span><span class="sxs-lookup"><span data-stu-id="8e1a7-152">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="8e1a7-153">Like (opérateur)</span><span class="sxs-lookup"><span data-stu-id="8e1a7-153">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="8e1a7-154">TypeOf (opérateur)</span><span class="sxs-lookup"><span data-stu-id="8e1a7-154">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="8e1a7-155">Await (opérateur)</span><span class="sxs-lookup"><span data-stu-id="8e1a7-155">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)
- [<span data-ttu-id="8e1a7-156">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="8e1a7-156">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="8e1a7-157">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="8e1a7-157">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
