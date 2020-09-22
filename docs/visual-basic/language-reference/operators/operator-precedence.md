---
title: Priorité des opérateurs
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
ms.openlocfilehash: b5649cd2a58fd8d300df58c563aebeed8976c4f5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874790"
---
# <a name="operator-precedence-in-visual-basic"></a><span data-ttu-id="518bb-102">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="518bb-102">Operator Precedence in Visual Basic</span></span>

<span data-ttu-id="518bb-103">Lorsque plusieurs opérations se produisent dans une expression, chaque composant est évalué et résolu dans un ordre prédéterminé appelé *priorité d’opérateur*.</span><span class="sxs-lookup"><span data-stu-id="518bb-103">When several operations occur in an expression, each part is evaluated and resolved in a predetermined order called *operator precedence*.</span></span>

## <a name="precedence-rules"></a><span data-ttu-id="518bb-104">Règles de précédence</span><span class="sxs-lookup"><span data-stu-id="518bb-104">Precedence Rules</span></span>

 <span data-ttu-id="518bb-105">Lorsque des expressions contiennent des opérateurs issus de plusieurs catégories, elles sont évaluées en fonction des règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="518bb-105">When expressions contain operators from more than one category, they are evaluated according to the following rules:</span></span>

- <span data-ttu-id="518bb-106">Les opérateurs arithmétiques et de concaténation ont l’ordre de priorité décrit dans la section suivante, et tous ont une priorité plus élevée que les opérateurs de comparaison, logiques et au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="518bb-106">The arithmetic and concatenation operators have the order of precedence described in the following section, and all have greater precedence than the comparison, logical, and bitwise operators.</span></span>

- <span data-ttu-id="518bb-107">Tous les opérateurs de comparaison ont une priorité égale, et tous ont une priorité plus élevée que les opérateurs logiques et au niveau du bit, mais une priorité plus faible que les opérateurs arithmétiques et de concaténation.</span><span class="sxs-lookup"><span data-stu-id="518bb-107">All comparison operators have equal precedence, and all have greater precedence than the logical and bitwise operators, but lower precedence than the arithmetic and concatenation operators.</span></span>

- <span data-ttu-id="518bb-108">Les opérateurs logiques et au niveau du bit ont l’ordre de priorité décrit dans la section suivante, et tous ont une priorité plus faible que les opérateurs arithmétiques, de concaténation et de comparaison.</span><span class="sxs-lookup"><span data-stu-id="518bb-108">The logical and bitwise operators have the order of precedence described in the following section, and all have lower precedence than the arithmetic, concatenation, and comparison operators.</span></span>

- <span data-ttu-id="518bb-109">Les opérateurs de même priorité sont évalués de gauche à droite dans l’ordre dans lequel ils apparaissent dans l’expression.</span><span class="sxs-lookup"><span data-stu-id="518bb-109">Operators with equal precedence are evaluated left to right in the order in which they appear in the expression.</span></span>

## <a name="precedence-order"></a><span data-ttu-id="518bb-110">Ordre de priorité</span><span class="sxs-lookup"><span data-stu-id="518bb-110">Precedence Order</span></span>

 <span data-ttu-id="518bb-111">Les opérateurs sont évalués dans l’ordre de priorité suivant :</span><span class="sxs-lookup"><span data-stu-id="518bb-111">Operators are evaluated in the following order of precedence:</span></span>

### <a name="await-operator"></a><span data-ttu-id="518bb-112">Await, opérateur</span><span class="sxs-lookup"><span data-stu-id="518bb-112">Await Operator</span></span>

 <span data-ttu-id="518bb-113">Await</span><span class="sxs-lookup"><span data-stu-id="518bb-113">Await</span></span>

### <a name="arithmetic-and-concatenation-operators"></a><span data-ttu-id="518bb-114">Opérateurs arithmétiques et de concaténation</span><span class="sxs-lookup"><span data-stu-id="518bb-114">Arithmetic and Concatenation Operators</span></span>

 <span data-ttu-id="518bb-115">Élévation à la puissance ( `^` )</span><span class="sxs-lookup"><span data-stu-id="518bb-115">Exponentiation (`^`)</span></span>

 <span data-ttu-id="518bb-116">Négation et identité unaire ( `+` , `–` )</span><span class="sxs-lookup"><span data-stu-id="518bb-116">Unary identity and negation (`+`, `–`)</span></span>

 <span data-ttu-id="518bb-117">Multiplication et Division à virgule flottante ( `*` , `/` )</span><span class="sxs-lookup"><span data-stu-id="518bb-117">Multiplication and floating-point division (`*`, `/`)</span></span>

 <span data-ttu-id="518bb-118">Division d’entier ( `\` )</span><span class="sxs-lookup"><span data-stu-id="518bb-118">Integer division (`\`)</span></span>

 <span data-ttu-id="518bb-119">Arithmétique modulaire ( `Mod` )</span><span class="sxs-lookup"><span data-stu-id="518bb-119">Modular arithmetic (`Mod`)</span></span>

 <span data-ttu-id="518bb-120">Addition et soustraction ( `+` , `–` )</span><span class="sxs-lookup"><span data-stu-id="518bb-120">Addition and subtraction (`+`, `–`)</span></span>

 <span data-ttu-id="518bb-121">Concaténation de chaînes ( `&` )</span><span class="sxs-lookup"><span data-stu-id="518bb-121">String concatenation (`&`)</span></span>

 <span data-ttu-id="518bb-122">Décalage binaire arithmétique ( `<<` , `>>` )</span><span class="sxs-lookup"><span data-stu-id="518bb-122">Arithmetic bit shift (`<<`, `>>`)</span></span>

### <a name="comparison-operators"></a><span data-ttu-id="518bb-123">Opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="518bb-123">Comparison Operators</span></span>

 <span data-ttu-id="518bb-124">Tous les opérateurs de comparaison ( `=` , `<>` , `<` , `<=` , `>` , `>=` , `Is` , `IsNot` , `Like` , `TypeOf` ... `Is` )</span><span class="sxs-lookup"><span data-stu-id="518bb-124">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span></span>

### <a name="logical-and-bitwise-operators"></a><span data-ttu-id="518bb-125">Opérateurs de bits et opérateurs logiques</span><span class="sxs-lookup"><span data-stu-id="518bb-125">Logical and Bitwise Operators</span></span>

 <span data-ttu-id="518bb-126">Négation ( `Not` )</span><span class="sxs-lookup"><span data-stu-id="518bb-126">Negation (`Not`)</span></span>

 <span data-ttu-id="518bb-127">Conjonction ( `And` , `AndAlso` )</span><span class="sxs-lookup"><span data-stu-id="518bb-127">Conjunction (`And`, `AndAlso`)</span></span>

 <span data-ttu-id="518bb-128">Disjonction inclusive ( `Or` , `OrElse` )</span><span class="sxs-lookup"><span data-stu-id="518bb-128">Inclusive disjunction (`Or`, `OrElse`)</span></span>

 <span data-ttu-id="518bb-129">Disjonction exclusive ( `Xor` )</span><span class="sxs-lookup"><span data-stu-id="518bb-129">Exclusive disjunction (`Xor`)</span></span>

### <a name="comments"></a><span data-ttu-id="518bb-130">Commentaires</span><span class="sxs-lookup"><span data-stu-id="518bb-130">Comments</span></span>

 <span data-ttu-id="518bb-131">L' `=` opérateur est uniquement l’opérateur de comparaison d’égalité, et non l’opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="518bb-131">The `=` operator is only the equality comparison operator, not the assignment operator.</span></span>

 <span data-ttu-id="518bb-132">L’opérateur de concaténation de chaînes ( `&` ) n’est pas un opérateur arithmétique, mais en priorité il est groupé avec les opérateurs arithmétiques.</span><span class="sxs-lookup"><span data-stu-id="518bb-132">The string concatenation operator (`&`) is not an arithmetic operator, but in precedence it is grouped with the arithmetic operators.</span></span>

 <span data-ttu-id="518bb-133">Les `Is` `IsNot` opérateurs et sont des opérateurs de comparaison de référence d’objet.</span><span class="sxs-lookup"><span data-stu-id="518bb-133">The `Is` and `IsNot` operators are object reference comparison operators.</span></span> <span data-ttu-id="518bb-134">Elles ne comparent pas les valeurs de deux objets ; ils vérifient uniquement si deux variables d’objet font référence à la même instance d’objet.</span><span class="sxs-lookup"><span data-stu-id="518bb-134">They do not compare the values of two objects; they check only to determine whether two object variables refer to the same object instance.</span></span>

## <a name="associativity"></a><span data-ttu-id="518bb-135">Associativité</span><span class="sxs-lookup"><span data-stu-id="518bb-135">Associativity</span></span>

 <span data-ttu-id="518bb-136">Lorsque des opérateurs de priorité égale apparaissent ensemble dans une expression, par exemple multiplication et Division, le compilateur évalue chaque opération à mesure qu’elle le rencontre de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="518bb-136">When operators of equal precedence appear together in an expression, for example multiplication and division, the compiler evaluates each operation as it encounters it from left to right.</span></span> <span data-ttu-id="518bb-137">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="518bb-137">The following example illustrates this.</span></span>

```vb
Dim n1 As Integer = 96 / 8 / 4
Dim n2 As Integer = (96 / 8) / 4
Dim n3 As Integer = 96 / (8 / 4)
```

 <span data-ttu-id="518bb-138">La première expression évalue la division 96/8 (qui donne 12), puis la division 12/4, qui donne trois valeurs.</span><span class="sxs-lookup"><span data-stu-id="518bb-138">The first expression evaluates the division 96 / 8 (which results in 12) and then the division 12 / 4, which results in three.</span></span> <span data-ttu-id="518bb-139">Étant donné que le compilateur évalue les opérations de `n1` gauche à droite, l’évaluation est la même lorsque cet ordre est explicitement indiqué pour `n2` .</span><span class="sxs-lookup"><span data-stu-id="518bb-139">Because the compiler evaluates the operations for `n1` from left to right, the evaluation is the same when that order is explicitly indicated for `n2`.</span></span> <span data-ttu-id="518bb-140">Et ont tous les deux `n1` `n2` la valeur trois.</span><span class="sxs-lookup"><span data-stu-id="518bb-140">Both `n1` and `n2` have a result of three.</span></span> <span data-ttu-id="518bb-141">En revanche, `n3` a le résultat 48, car les parenthèses forcent le compilateur à évaluer 8/4 en premier.</span><span class="sxs-lookup"><span data-stu-id="518bb-141">By contrast, `n3` has a result of 48, because the parentheses force the compiler to evaluate 8 / 4 first.</span></span>

 <span data-ttu-id="518bb-142">En raison de ce comportement, on dit que les opérateurs sont *associatifs à gauche* dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="518bb-142">Because of this behavior, operators are said to be *left associative* in Visual Basic.</span></span>

## <a name="overriding-precedence-and-associativity"></a><span data-ttu-id="518bb-143">Substitution de la priorité et de l’associativité</span><span class="sxs-lookup"><span data-stu-id="518bb-143">Overriding Precedence and Associativity</span></span>

 <span data-ttu-id="518bb-144">Vous pouvez utiliser des parenthèses pour forcer l’évaluation de certaines parties d’une expression avant d’autres.</span><span class="sxs-lookup"><span data-stu-id="518bb-144">You can use parentheses to force some parts of an expression to be evaluated before others.</span></span> <span data-ttu-id="518bb-145">Cela peut remplacer l’ordre de priorité et l’associativité à gauche.</span><span class="sxs-lookup"><span data-stu-id="518bb-145">This can override both the order of precedence and the left associativity.</span></span> <span data-ttu-id="518bb-146">Visual Basic effectue toujours des opérations placées entre parenthèses avant celles extérieures à.</span><span class="sxs-lookup"><span data-stu-id="518bb-146">Visual Basic always performs operations that are enclosed in parentheses before those outside.</span></span> <span data-ttu-id="518bb-147">Toutefois, entre parenthèses, il gère la priorité et l’associativité ordinaires, sauf si vous utilisez des parenthèses entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="518bb-147">However, within parentheses, it maintains ordinary precedence and associativity, unless you use parentheses within the parentheses.</span></span> <span data-ttu-id="518bb-148">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="518bb-148">The following example illustrates this.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="518bb-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="518bb-149">See also</span></span>

- [<span data-ttu-id="518bb-150">= (Opérateur)</span><span class="sxs-lookup"><span data-stu-id="518bb-150">= Operator</span></span>](assignment-operator.md)
- [<span data-ttu-id="518bb-151">Is, opérateur</span><span class="sxs-lookup"><span data-stu-id="518bb-151">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="518bb-152">IsNot, opérateur</span><span class="sxs-lookup"><span data-stu-id="518bb-152">IsNot Operator</span></span>](isnot-operator.md)
- [<span data-ttu-id="518bb-153">Like, opérateur</span><span class="sxs-lookup"><span data-stu-id="518bb-153">Like Operator</span></span>](like-operator.md)
- [<span data-ttu-id="518bb-154">TypeOf, opérateur</span><span class="sxs-lookup"><span data-stu-id="518bb-154">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="518bb-155">Await (opérateur)</span><span class="sxs-lookup"><span data-stu-id="518bb-155">Await Operator</span></span>](await-operator.md)
- [<span data-ttu-id="518bb-156">Opérateurs listés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="518bb-156">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="518bb-157">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="518bb-157">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
