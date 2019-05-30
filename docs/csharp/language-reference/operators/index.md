---
title: Opérateurs C#
ms.date: 04/30/2019
f1_keywords:
- cs.operators
helpviewer_keywords:
- boolean operators [C#]
- expressions [C#], operators
- logical operators [C#]
- operators [C#]
- Visual C#, operators
- indirection operators [C#]
- assignment operators [C#]
- shift operators [C#]
- relational operators [C#]
- bitwise operators [C#]
- address operators [C#]
- keywords [C#], operators
- arithmetic operators [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: c1f891314a2490d6dbf22977ea5a5f69533b330d
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300320"
---
# <a name="c-operators"></a><span data-ttu-id="aad68-102">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="aad68-102">C# operators</span></span>

<span data-ttu-id="aad68-103">C# fournit plusieurs opérateurs prédéfinis pris en charge par les types intégrés.</span><span class="sxs-lookup"><span data-stu-id="aad68-103">C# provides a number of predefined operators supported by the built-in types.</span></span> <span data-ttu-id="aad68-104">Par exemple, les [opérateurs arithmétiques](arithmetic-operators.md) effectuent des opérations arithmétiques avec des opérandes de types numériques intégrés et les [opérateurs logiques booléens](boolean-logical-operators.md) effectuent des opérations logiques avec les opérandes [bool](../keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="aad68-104">For example, [arithmetic operators](arithmetic-operators.md) perform arithmetic operations with operands of built-in numeric types and [Boolean logical operators](boolean-logical-operators.md) perform logical operations with the [bool](../keywords/bool.md) operands.</span></span>

<span data-ttu-id="aad68-105">Un type défini par l’utilisateur peut surcharger certains opérateurs pour définir le comportement correspondant des opérandes de ce type.</span><span class="sxs-lookup"><span data-stu-id="aad68-105">A user-defined type can overload certain operators to define the corresponding behavior for the operands of that type.</span></span> <span data-ttu-id="aad68-106">Pour plus d’informations, consultez l’article sur le mot clé [opérateur](../keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="aad68-106">For more information, see the [operator](../keywords/operator.md) keyword article.</span></span>

<span data-ttu-id="aad68-107">Les sections suivantes listent les opérateurs C# de la priorité la plus élevée à la plus basse.</span><span class="sxs-lookup"><span data-stu-id="aad68-107">The following sections list the C# operators starting with the highest precedence to the lowest.</span></span> <span data-ttu-id="aad68-108">Les opérateurs inclus dans chaque section partagent le même niveau de priorité.</span><span class="sxs-lookup"><span data-stu-id="aad68-108">The operators within each section share the same precedence level.</span></span>

## <a name="primary-operators"></a><span data-ttu-id="aad68-109">Opérateurs principaux</span><span class="sxs-lookup"><span data-stu-id="aad68-109">Primary operators</span></span>

<span data-ttu-id="aad68-110">Ce sont les opérateurs dont la priorité est la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="aad68-110">These are the highest precedence operators.</span></span>

<span data-ttu-id="aad68-111">[x.y](member-access-operators.md#member-access-operator-) : accès au membre.</span><span class="sxs-lookup"><span data-stu-id="aad68-111">[x.y](member-access-operators.md#member-access-operator-) – member access.</span></span>

<span data-ttu-id="aad68-112">[x?.y](member-access-operators.md#null-conditional-operators--and-) : accès au membre conditionnel Null.</span><span class="sxs-lookup"><span data-stu-id="aad68-112">[x?.y](member-access-operators.md#null-conditional-operators--and-) – null conditional member access.</span></span> <span data-ttu-id="aad68-113">Retourne `null` si l’opérande de gauche prend la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="aad68-113">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="aad68-114">[x?[y]](member-access-operators.md#null-conditional-operators--and-) : accès à l’indexeur de type ou d’élément de tableau conditionnel Null.</span><span class="sxs-lookup"><span data-stu-id="aad68-114">[x?[y]](member-access-operators.md#null-conditional-operators--and-) - null conditional array element or type indexer access.</span></span> <span data-ttu-id="aad68-115">Retourne `null` si l’opérande de gauche prend la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="aad68-115">Returns `null` if the left-hand operand evaluates to `null`.</span></span>

<span data-ttu-id="aad68-116">[f(x)](member-access-operators.md#invocation-operator-) : appel de méthode ou appel de délégué.</span><span class="sxs-lookup"><span data-stu-id="aad68-116">[f(x)](member-access-operators.md#invocation-operator-) – method call or delegate invocation.</span></span>

<span data-ttu-id="aad68-117">[un&#91;x&#93;](member-access-operators.md#indexer-operator-) : accès à l’indexeur de type ou d’élément de tableau.</span><span class="sxs-lookup"><span data-stu-id="aad68-117">[a&#91;x&#93;](member-access-operators.md#indexer-operator-) – array element or type indexer access.</span></span>

<span data-ttu-id="aad68-118">[x++](arithmetic-operators.md#increment-operator-) : incrément suffixé.</span><span class="sxs-lookup"><span data-stu-id="aad68-118">[x++](arithmetic-operators.md#increment-operator-) – postfix increment.</span></span> <span data-ttu-id="aad68-119">Retourne la valeur de x et met à jour l'emplacement de stockage avec la valeur de x augmentée de un (ajoute généralement l'entier 1).</span><span class="sxs-lookup"><span data-stu-id="aad68-119">Returns the value of x and then updates the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="aad68-120">[x--](arithmetic-operators.md#decrement-operator---) : décrément suffixé.</span><span class="sxs-lookup"><span data-stu-id="aad68-120">[x--](arithmetic-operators.md#decrement-operator---) –  postfix decrement.</span></span> <span data-ttu-id="aad68-121">Retourne la valeur de x et met à jour l'emplacement de stockage avec la valeur de x diminuée de un (soustrait généralement l'entier 1).</span><span class="sxs-lookup"><span data-stu-id="aad68-121">Returns the value of x and then updates the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="aad68-122">[new](../keywords/new-operator.md) : instanciation de type.</span><span class="sxs-lookup"><span data-stu-id="aad68-122">[new](../keywords/new-operator.md) – type instantiation.</span></span>

<span data-ttu-id="aad68-123">[typeof](../keywords/typeof.md) : retourne l’objet <xref:System.Type> qui représente l’opérande.</span><span class="sxs-lookup"><span data-stu-id="aad68-123">[typeof](../keywords/typeof.md) – returns the <xref:System.Type> object representing the operand.</span></span>

<span data-ttu-id="aad68-124">[checked](../keywords/checked.md) : active le contrôle de dépassement de capacité pour les opérations sur les entiers.</span><span class="sxs-lookup"><span data-stu-id="aad68-124">[checked](../keywords/checked.md) – enables overflow checking for integer operations.</span></span>

<span data-ttu-id="aad68-125">[unchecked](../keywords/unchecked.md) : désactive le contrôle de dépassement de capacité pour les opérations sur les entiers.</span><span class="sxs-lookup"><span data-stu-id="aad68-125">[unchecked](../keywords/unchecked.md) – disables overflow checking for integer operations.</span></span> <span data-ttu-id="aad68-126">Il s'agit du comportement de compilateur par défaut.</span><span class="sxs-lookup"><span data-stu-id="aad68-126">This is the default compiler behavior.</span></span>

<span data-ttu-id="aad68-127">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produit la valeur par défaut du type T.</span><span class="sxs-lookup"><span data-stu-id="aad68-127">[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – produces the default value of type T.</span></span>

<span data-ttu-id="aad68-128">[nameof](../keywords/nameof.md) : obtient le nom simple (non qualifié) d’une variable, d’un type ou d’un membre sous forme de chaîne constante.</span><span class="sxs-lookup"><span data-stu-id="aad68-128">[nameof](../keywords/nameof.md) - obtains the simple (unqualified) name of a variable, type, or member as a constant string.</span></span>

<span data-ttu-id="aad68-129">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) : déclare et retourne une instance de délégué.</span><span class="sxs-lookup"><span data-stu-id="aad68-129">[delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – declares and returns a delegate instance.</span></span>

<span data-ttu-id="aad68-130">[sizeof](../keywords/sizeof.md) : retourne la taille en octets de l’opérande du type.</span><span class="sxs-lookup"><span data-stu-id="aad68-130">[sizeof](../keywords/sizeof.md) – returns the size in bytes of the type operand.</span></span>

<span data-ttu-id="aad68-131">[stackalloc](../keywords/stackalloc.md) : alloue un bloc de mémoire dans la pile.</span><span class="sxs-lookup"><span data-stu-id="aad68-131">[stackalloc](../keywords/stackalloc.md) - allocates a block of memory on the stack.</span></span>

<span data-ttu-id="aad68-132">[->](pointer-related-operators.md#pointer-member-access-operator--) : indirection de pointeur associé à l’accès au membre.</span><span class="sxs-lookup"><span data-stu-id="aad68-132">[->](pointer-related-operators.md#pointer-member-access-operator--) – pointer indirection combined with member access.</span></span>

## <a name="unary-operators"></a><span data-ttu-id="aad68-133">Les opérateurs unaires.</span><span class="sxs-lookup"><span data-stu-id="aad68-133">Unary operators</span></span>

<span data-ttu-id="aad68-134">Ces opérateurs ont une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.</span><span class="sxs-lookup"><span data-stu-id="aad68-134">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="aad68-135">[+x](addition-operator.md) : retourne la valeur de x.</span><span class="sxs-lookup"><span data-stu-id="aad68-135">[+x](addition-operator.md) – returns the value of x.</span></span>

<span data-ttu-id="aad68-136">[-x](subtraction-operator.md) : négation numérique.</span><span class="sxs-lookup"><span data-stu-id="aad68-136">[-x](subtraction-operator.md) – numeric negation.</span></span>

<span data-ttu-id="aad68-137">[\!x](boolean-logical-operators.md#logical-negation-operator-) : négation logique.</span><span class="sxs-lookup"><span data-stu-id="aad68-137">[\!x](boolean-logical-operators.md#logical-negation-operator-) – logical negation.</span></span>

<span data-ttu-id="aad68-138">[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-) : complément au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="aad68-138">[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – bitwise complement.</span></span>

<span data-ttu-id="aad68-139">[++x](arithmetic-operators.md#increment-operator-) : incrément préfixé.</span><span class="sxs-lookup"><span data-stu-id="aad68-139">[++x](arithmetic-operators.md#increment-operator-) – prefix increment.</span></span> <span data-ttu-id="aad68-140">Retourne la valeur de x après avoir mis à jour l'emplacement de stockage avec la valeur de x augmentée de un (ajoute généralement l'entier 1).</span><span class="sxs-lookup"><span data-stu-id="aad68-140">Returns the value of x after updating the storage location with the value of x that is one greater (typically adds the integer 1).</span></span>

<span data-ttu-id="aad68-141">[--x](arithmetic-operators.md#decrement-operator---) : décrément préfixé.</span><span class="sxs-lookup"><span data-stu-id="aad68-141">[--x](arithmetic-operators.md#decrement-operator---) – prefix decrement.</span></span> <span data-ttu-id="aad68-142">Retourne la valeur de x après avoir mis à jour l’emplacement de stockage avec la valeur de x diminuée d’une unité (soustrait généralement l’entier 1).</span><span class="sxs-lookup"><span data-stu-id="aad68-142">Returns the value of x after updating the storage location with the value of x that is one less (typically subtracts the integer 1).</span></span>

<span data-ttu-id="aad68-143">[(T)x](invocation-operator.md) : cast de type.</span><span class="sxs-lookup"><span data-stu-id="aad68-143">[(T)x](invocation-operator.md) – type casting.</span></span>

<span data-ttu-id="aad68-144">[await](../keywords/await.md) : attend un `Task`.</span><span class="sxs-lookup"><span data-stu-id="aad68-144">[await](../keywords/await.md) – awaits a `Task`.</span></span>

<span data-ttu-id="aad68-145">[&x](pointer-related-operators.md#address-of-operator-) – adresse d’une variable.</span><span class="sxs-lookup"><span data-stu-id="aad68-145">[&x](pointer-related-operators.md#address-of-operator-) – address of a variable.</span></span>

<span data-ttu-id="aad68-146">[\*x](pointer-related-operators.md#pointer-indirection-operator-) – indirection de pointeur ou déréférencement.</span><span class="sxs-lookup"><span data-stu-id="aad68-146">[\*x](pointer-related-operators.md#pointer-indirection-operator-) – pointer indirection, or dereference.</span></span>

<span data-ttu-id="aad68-147">[Opérateur true ](true-false-operators.md) : retourne la valeur [bool](../keywords/bool.md) `true` pour indiquer qu’un opérande est true.</span><span class="sxs-lookup"><span data-stu-id="aad68-147">[true operator](true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely true.</span></span>

<span data-ttu-id="aad68-148">[Opérateur false](true-false-operators.md) : retourne la valeur [bool](../keywords/bool.md) `true` pour indiquer qu’un opérande est false.</span><span class="sxs-lookup"><span data-stu-id="aad68-148">[false operator](true-false-operators.md) - returns the [bool](../keywords/bool.md) value `true` to indicate that an operand is definitely false.</span></span>

## <a name="multiplicative-operators"></a><span data-ttu-id="aad68-149">Opérateurs multiplicatifs</span><span class="sxs-lookup"><span data-stu-id="aad68-149">Multiplicative operators</span></span>

<span data-ttu-id="aad68-150">Ces opérateurs ont une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.</span><span class="sxs-lookup"><span data-stu-id="aad68-150">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="aad68-151">[x \* y](arithmetic-operators.md#multiplication-operator-) : multiplication.</span><span class="sxs-lookup"><span data-stu-id="aad68-151">[x \* y](arithmetic-operators.md#multiplication-operator-) – multiplication.</span></span>

<span data-ttu-id="aad68-152">[x / y](arithmetic-operators.md#division-operator-) : division.</span><span class="sxs-lookup"><span data-stu-id="aad68-152">[x / y](arithmetic-operators.md#division-operator-) – division.</span></span> <span data-ttu-id="aad68-153">Si les opérandes sont des entiers, le résultat est un entier tronqué vers zéro (par exemple, `-7 / 2 is -3`).</span><span class="sxs-lookup"><span data-stu-id="aad68-153">If the operands are integers, the result is an integer truncated toward zero (for example, `-7 / 2 is -3`).</span></span>

<span data-ttu-id="aad68-154">[x % y](arithmetic-operators.md#remainder-operator-) : reste.</span><span class="sxs-lookup"><span data-stu-id="aad68-154">[x % y](arithmetic-operators.md#remainder-operator-) – remainder.</span></span> <span data-ttu-id="aad68-155">Si les opérandes sont des entiers, cet opérateur renvoie le reste de la division de x par y.</span><span class="sxs-lookup"><span data-stu-id="aad68-155">If the operands are integers, this returns the remainder of dividing x by y.</span></span>  <span data-ttu-id="aad68-156">Si `q = x / y` et `r = x % y`, alors `x = q * y + r`.</span><span class="sxs-lookup"><span data-stu-id="aad68-156">If `q = x / y` and `r = x % y`, then `x = q * y + r`.</span></span>

## <a name="additive-operators"></a><span data-ttu-id="aad68-157">Opérateurs additifs</span><span class="sxs-lookup"><span data-stu-id="aad68-157">Additive operators</span></span>

<span data-ttu-id="aad68-158">Ces opérateurs ont une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.</span><span class="sxs-lookup"><span data-stu-id="aad68-158">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="aad68-159">[x + y](arithmetic-operators.md#addition-operator-) : addition.</span><span class="sxs-lookup"><span data-stu-id="aad68-159">[x + y](arithmetic-operators.md#addition-operator-) – addition.</span></span>

<span data-ttu-id="aad68-160">[x – y](arithmetic-operators.md#subtraction-operator--) : soustraction.</span><span class="sxs-lookup"><span data-stu-id="aad68-160">[x – y](arithmetic-operators.md#subtraction-operator--) – subtraction.</span></span>

## <a name="shift-operators"></a><span data-ttu-id="aad68-161">Opérateurs de décalage</span><span class="sxs-lookup"><span data-stu-id="aad68-161">Shift operators</span></span>

<span data-ttu-id="aad68-162">Ces opérateurs ont une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.</span><span class="sxs-lookup"><span data-stu-id="aad68-162">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="aad68-163">[x <\<  y](bitwise-and-shift-operators.md#left-shift-operator-) : décalage des bits vers la gauche et remplissage avec zéro à droite.</span><span class="sxs-lookup"><span data-stu-id="aad68-163">[x <\<  y](bitwise-and-shift-operators.md#left-shift-operator-) – shift bits left and fill with zero on the right.</span></span>

<span data-ttu-id="aad68-164">[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) : décalage des bits vers la droite.</span><span class="sxs-lookup"><span data-stu-id="aad68-164">[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – shift bits right.</span></span> <span data-ttu-id="aad68-165">Si l'opérande de gauche est `int` ou `long`, alors les bits de gauche sont remplis avec le bit de signe.</span><span class="sxs-lookup"><span data-stu-id="aad68-165">If the left operand is `int` or `long`, then left bits are filled with the sign bit.</span></span> <span data-ttu-id="aad68-166">Si l'opérande de gauche est `uint` ou `ulong`, alors les bits de gauche sont remplis avec zéro.</span><span class="sxs-lookup"><span data-stu-id="aad68-166">If the left operand is `uint` or `ulong`, then left bits are filled with zero.</span></span>

## <a name="relational-and-type-testing-operators"></a><span data-ttu-id="aad68-167">Opérateurs relationnels et de test de type</span><span class="sxs-lookup"><span data-stu-id="aad68-167">Relational and type-testing operators</span></span>

<span data-ttu-id="aad68-168">Ces opérateurs ont une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.</span><span class="sxs-lookup"><span data-stu-id="aad68-168">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="aad68-169">[x \< y](comparison-operators.md#less-than-operator-) : inférieur à (true si x est inférieur à y).</span><span class="sxs-lookup"><span data-stu-id="aad68-169">[x \< y](comparison-operators.md#less-than-operator-) – less than (true if x is less than y).</span></span>

<span data-ttu-id="aad68-170">[x > y](comparison-operators.md#greater-than-operator-) : supérieur à (true si x est supérieur à y).</span><span class="sxs-lookup"><span data-stu-id="aad68-170">[x > y](comparison-operators.md#greater-than-operator-) – greater than (true if x is greater than y).</span></span>

<span data-ttu-id="aad68-171">[x \<= y](comparison-operators.md#less-than-or-equal-operator-) : supérieur ou égal à.</span><span class="sxs-lookup"><span data-stu-id="aad68-171">[x \<= y](comparison-operators.md#less-than-or-equal-operator-) – less than or equal to.</span></span>

<span data-ttu-id="aad68-172">[x >= y](comparison-operators.md#greater-than-or-equal-operator-) : supérieur ou égal à.</span><span class="sxs-lookup"><span data-stu-id="aad68-172">[x >= y](comparison-operators.md#greater-than-or-equal-operator-) – greater than or equal to.</span></span>

<span data-ttu-id="aad68-173">[is](../keywords/is.md) : compatibilité du type.</span><span class="sxs-lookup"><span data-stu-id="aad68-173">[is](../keywords/is.md) – type compatibility.</span></span> <span data-ttu-id="aad68-174">Retourne true si l’opérande de gauche évalué peut être converti en type spécifié dans l’opérande de droite (type statique).</span><span class="sxs-lookup"><span data-stu-id="aad68-174">Returns true if the evaluated left operand can be cast to the type specified in the right operand (a static type).</span></span>

<span data-ttu-id="aad68-175">[as](../keywords/as.md) : conversion de type.</span><span class="sxs-lookup"><span data-stu-id="aad68-175">[as](../keywords/as.md) – type conversion.</span></span> <span data-ttu-id="aad68-176">Retourne l'opérande de gauche converti en type spécifié par l'opérande de droite (type statique), mais `as` retourne `null` où `(T)x` lèverait une exception.</span><span class="sxs-lookup"><span data-stu-id="aad68-176">Returns the left operand cast to the type specified by the right operand (a static type), but `as` returns `null` where `(T)x` would throw an exception.</span></span>

## <a name="equality-operators"></a><span data-ttu-id="aad68-177">Opérateurs d'égalité</span><span class="sxs-lookup"><span data-stu-id="aad68-177">Equality operators</span></span>

<span data-ttu-id="aad68-178">Ces opérateurs ont une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.</span><span class="sxs-lookup"><span data-stu-id="aad68-178">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="aad68-179">[x == y](equality-operators.md#equality-operator-) : égalité.</span><span class="sxs-lookup"><span data-stu-id="aad68-179">[x == y](equality-operators.md#equality-operator-) – equality.</span></span> <span data-ttu-id="aad68-180">Par défaut, pour les types de référence autres que `string`, cet opérateur retourne l'égalité de référence (test d'identité).</span><span class="sxs-lookup"><span data-stu-id="aad68-180">By default, for reference types other than `string`, this returns reference equality (identity test).</span></span> <span data-ttu-id="aad68-181">Toutefois, des types peuvent surcharger `==`, donc si votre objectif est de tester l'identité, il est préférable d'utiliser la méthode `ReferenceEquals` sur `object`.</span><span class="sxs-lookup"><span data-stu-id="aad68-181">However, types can overload `==`, so if your intent is to test identity, it is best to use the `ReferenceEquals` method on `object`.</span></span>

<span data-ttu-id="aad68-182">[x != y](equality-operators.md#inequality-operator-) : différent.</span><span class="sxs-lookup"><span data-stu-id="aad68-182">[x != y](equality-operators.md#inequality-operator-) – not equal.</span></span> <span data-ttu-id="aad68-183">Consultez le commentaire sur `==`.</span><span class="sxs-lookup"><span data-stu-id="aad68-183">See comment for `==`.</span></span> <span data-ttu-id="aad68-184">Si un type surcharge `==`, alors il doit surcharger `!=`.</span><span class="sxs-lookup"><span data-stu-id="aad68-184">If a type overloads `==`, then it must overload `!=`.</span></span>

## <a name="logical-and-operator"></a><span data-ttu-id="aad68-185">Opérateur AND logique</span><span class="sxs-lookup"><span data-stu-id="aad68-185">Logical AND operator</span></span>

<span data-ttu-id="aad68-186">Cet opérateur a une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.</span><span class="sxs-lookup"><span data-stu-id="aad68-186">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="aad68-187">`x & y` – [AND logique](boolean-logical-operators.md#logical-and-operator-) dans le cas des opérandes `bool` ou [AND logique au niveau du bit](bitwise-and-shift-operators.md#logical-and-operator-) dans le cas des opérandes de type intégral.</span><span class="sxs-lookup"><span data-stu-id="aad68-187">`x & y` – [logical AND](boolean-logical-operators.md#logical-and-operator-) for the `bool` operands or [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) for the operands of the integral types.</span></span>

## <a name="logical-xor-operator"></a><span data-ttu-id="aad68-188">Opérateur XOR logique</span><span class="sxs-lookup"><span data-stu-id="aad68-188">Logical XOR operator</span></span>

<span data-ttu-id="aad68-189">Cet opérateur a une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.</span><span class="sxs-lookup"><span data-stu-id="aad68-189">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="aad68-190">`x ^ y` – [XOR logique](boolean-logical-operators.md#logical-exclusive-or-operator-) dans le cas des opérandes `bool` ou [XOR logique au niveau du bit](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) dans le cas des opérandes de type intégral.</span><span class="sxs-lookup"><span data-stu-id="aad68-190">`x ^ y` – [logical XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) for the `bool` operands or [bitwise logical XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) for the operands of the integral types.</span></span>

## <a name="logical-or-operator"></a><span data-ttu-id="aad68-191">Opérateur OU logique</span><span class="sxs-lookup"><span data-stu-id="aad68-191">Logical OR operator</span></span>

<span data-ttu-id="aad68-192">Cet opérateur a une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.</span><span class="sxs-lookup"><span data-stu-id="aad68-192">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="aad68-193">`x | y` – [OR logique](boolean-logical-operators.md#logical-or-operator-) dans le cas des opérandes `bool` ou [OR logique au niveau du bit](bitwise-and-shift-operators.md#logical-or-operator-) dans le cas des opérandes de type intégral.</span><span class="sxs-lookup"><span data-stu-id="aad68-193">`x | y` – [logical OR](boolean-logical-operators.md#logical-or-operator-) for the `bool` operands or [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) for the operands of the integral types.</span></span>

## <a name="conditional-and-operator"></a><span data-ttu-id="aad68-194">Opérateur AND conditionnel</span><span class="sxs-lookup"><span data-stu-id="aad68-194">Conditional AND operator</span></span>

<span data-ttu-id="aad68-195">Cet opérateur a une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.</span><span class="sxs-lookup"><span data-stu-id="aad68-195">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="aad68-196">[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) : ET logique.</span><span class="sxs-lookup"><span data-stu-id="aad68-196">[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – logical AND.</span></span> <span data-ttu-id="aad68-197">Si le premier opérande prend la valeur false, C# n’évalue pas le second opérande.</span><span class="sxs-lookup"><span data-stu-id="aad68-197">If the first operand evaluates to false, then C# does not evaluate the second operand.</span></span>

## <a name="conditional-or-operator"></a><span data-ttu-id="aad68-198">Opérateur OR conditionnel</span><span class="sxs-lookup"><span data-stu-id="aad68-198">Conditional OR operator</span></span>

<span data-ttu-id="aad68-199">Cet opérateur a une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.</span><span class="sxs-lookup"><span data-stu-id="aad68-199">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="aad68-200">[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) : OU logique.</span><span class="sxs-lookup"><span data-stu-id="aad68-200">[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – logical OR.</span></span> <span data-ttu-id="aad68-201">Si le premier opérande prend la valeur true, C# n’évalue pas le second opérande.</span><span class="sxs-lookup"><span data-stu-id="aad68-201">If the first operand evaluates to true, then C# does not evaluate the second operand.</span></span>

## <a name="null-coalescing-operator"></a><span data-ttu-id="aad68-202">Opérateur de fusion de Null</span><span class="sxs-lookup"><span data-stu-id="aad68-202">Null-coalescing operator</span></span>

<span data-ttu-id="aad68-203">Cet opérateur a une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.</span><span class="sxs-lookup"><span data-stu-id="aad68-203">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="aad68-204">[x ?? y](null-coalescing-operator.md) : retourne `x` si non `null` ; dans le cas contraire, retourne `y`.</span><span class="sxs-lookup"><span data-stu-id="aad68-204">[x ?? y](null-coalescing-operator.md) – returns `x` if it is non-`null`; otherwise, returns `y`.</span></span>

## <a name="conditional-operator"></a><span data-ttu-id="aad68-205">Opérateur conditionnel</span><span class="sxs-lookup"><span data-stu-id="aad68-205">Conditional operator</span></span>

<span data-ttu-id="aad68-206">Cet opérateur a une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.</span><span class="sxs-lookup"><span data-stu-id="aad68-206">This operator has higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="aad68-207">[t ? x : y](conditional-operator.md) : si le test `t` prend la valeur true, alors évalue et retourne `x` ; sinon, évalue et retourne `y`.</span><span class="sxs-lookup"><span data-stu-id="aad68-207">[t ? x : y](conditional-operator.md) – if test `t` evaluates to true, then evaluate and return `x`; otherwise, evaluate and return `y`.</span></span>

## <a name="assignment-and-lambda-operators"></a><span data-ttu-id="aad68-208">Opérateurs d’affectation et lambda</span><span class="sxs-lookup"><span data-stu-id="aad68-208">Assignment and lambda operators</span></span>

<span data-ttu-id="aad68-209">Ces opérateurs ont une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.</span><span class="sxs-lookup"><span data-stu-id="aad68-209">These operators have higher precedence than the next section and lower precedence than the previous section.</span></span>

<span data-ttu-id="aad68-210">[x = y](assignment-operator.md) : affectation.</span><span class="sxs-lookup"><span data-stu-id="aad68-210">[x = y](assignment-operator.md) – assignment.</span></span>

<span data-ttu-id="aad68-211">[x += y](arithmetic-operators.md#compound-assignment) : incrément.</span><span class="sxs-lookup"><span data-stu-id="aad68-211">[x += y](arithmetic-operators.md#compound-assignment) – increment.</span></span> <span data-ttu-id="aad68-212">Additionne la valeur de `y` à la valeur de `x`, stocke le résultat dans `x` et retourne la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="aad68-212">Add the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="aad68-213">Si `x` désigne un [événement](../keywords/event.md), `y` doit être une méthode appropriée que C# ajoute en tant que gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="aad68-213">If `x` designates an [event](../keywords/event.md), then `y` must be an appropriate method that C# adds as an event handler.</span></span>

<span data-ttu-id="aad68-214">[x -= y](arithmetic-operators.md#compound-assignment) : décrément.</span><span class="sxs-lookup"><span data-stu-id="aad68-214">[x -= y](arithmetic-operators.md#compound-assignment) – decrement.</span></span> <span data-ttu-id="aad68-215">Soustrait la valeur de `y` de la valeur de `x`, stocke le résultat dans `x` et retourne la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="aad68-215">Subtract the value of `y` from the value of `x`, store the result in `x`, and return the new value.</span></span> <span data-ttu-id="aad68-216">Si `x` désigne un [événement](../keywords/event.md), `y` doit être une méthode appropriée que C# supprime en tant que gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="aad68-216">If `x` designates an [event](../keywords/event.md), then `y` must be an appropriate method that C# removes as an event handler.</span></span>

<span data-ttu-id="aad68-217">[x \*= y](arithmetic-operators.md#compound-assignment) : affectation de multiplication.</span><span class="sxs-lookup"><span data-stu-id="aad68-217">[x \*= y](arithmetic-operators.md#compound-assignment) – multiplication assignment.</span></span> <span data-ttu-id="aad68-218">Multiplie la valeur de `y` par la valeur de `x`, stocke le résultat dans `x` et retourne la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="aad68-218">Multiply the value of `y` to the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="aad68-219">[x /= y](arithmetic-operators.md#compound-assignment) : affectation de division.</span><span class="sxs-lookup"><span data-stu-id="aad68-219">[x /= y](arithmetic-operators.md#compound-assignment) – division assignment.</span></span> <span data-ttu-id="aad68-220">Divise la valeur de `x` par la valeur de `y`, stocke le résultat dans `x` et retourne la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="aad68-220">Divide the value of `x` by the value of `y`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="aad68-221">[x %= y](arithmetic-operators.md#compound-assignment) : assignation de reste.</span><span class="sxs-lookup"><span data-stu-id="aad68-221">[x %= y](arithmetic-operators.md#compound-assignment) – remainder assignment.</span></span> <span data-ttu-id="aad68-222">Divise la valeur de `x` par la valeur de `y`, stocke le reste dans `x` et retourne la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="aad68-222">Divide the value of `x` by the value of `y`, store the remainder in `x`, and return the new value.</span></span>

<span data-ttu-id="aad68-223">[x &= y](boolean-logical-operators.md#compound-assignment) : affectation ET.</span><span class="sxs-lookup"><span data-stu-id="aad68-223">[x &= y](boolean-logical-operators.md#compound-assignment) – AND assignment.</span></span> <span data-ttu-id="aad68-224">Assigne l'opérateur AND à la valeur de `y` et la valeur de `x`, stocke le résultat dans `x` et retourne la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="aad68-224">AND the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="aad68-225">[x &#124;= y](boolean-logical-operators.md#compound-assignment) : affectation OU.</span><span class="sxs-lookup"><span data-stu-id="aad68-225">[x &#124;= y](boolean-logical-operators.md#compound-assignment) – OR assignment.</span></span> <span data-ttu-id="aad68-226">Assigne l'opérateur OR à la valeur de `y` et la valeur de `x`, stocke le résultat dans `x` et retourne la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="aad68-226">OR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="aad68-227">[x ^= y](boolean-logical-operators.md#compound-assignment) : affectation XOR.</span><span class="sxs-lookup"><span data-stu-id="aad68-227">[x ^= y](boolean-logical-operators.md#compound-assignment) – XOR assignment.</span></span> <span data-ttu-id="aad68-228">Assigne l'opérateur XOR à la valeur de `y` et la valeur de `x`, stocke le résultat dans `x` et retourne la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="aad68-228">XOR the value of `y` with the value of `x`, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="aad68-229">[x <<= y](bitwise-and-shift-operators.md#compound-assignment) : affectation de décalage vers la gauche.</span><span class="sxs-lookup"><span data-stu-id="aad68-229">[x <<= y](bitwise-and-shift-operators.md#compound-assignment) – left-shift assignment.</span></span> <span data-ttu-id="aad68-230">Décale la valeur de `x` vers la gauche de `y` places, stocke le résultat dans `x` et retourne la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="aad68-230">Shift the value of `x` left by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="aad68-231">[x >>= y](bitwise-and-shift-operators.md#compound-assignment) : affectation de décalage vers la droite.</span><span class="sxs-lookup"><span data-stu-id="aad68-231">[x >>= y](bitwise-and-shift-operators.md#compound-assignment) – right-shift assignment.</span></span> <span data-ttu-id="aad68-232">Décale la valeur de `x` vers la droite de `y` places, stocke le résultat dans `x` et retourne la nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="aad68-232">Shift the value of `x` right by `y` places, store the result in `x`, and return the new value.</span></span>

<span data-ttu-id="aad68-233">[=>](lambda-operator.md) : déclaration lambda.</span><span class="sxs-lookup"><span data-stu-id="aad68-233">[=>](lambda-operator.md) – lambda declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="aad68-234">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aad68-234">See also</span></span>

- [<span data-ttu-id="aad68-235">Référence C#</span><span class="sxs-lookup"><span data-stu-id="aad68-235">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="aad68-236">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="aad68-236">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="aad68-237">C#</span><span class="sxs-lookup"><span data-stu-id="aad68-237">C#</span></span>](../../index.md)
- [<span data-ttu-id="aad68-238">Opérateurs surchargeables</span><span class="sxs-lookup"><span data-stu-id="aad68-238">Overloadable operators</span></span>](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [<span data-ttu-id="aad68-239">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="aad68-239">C# Keywords</span></span>](../keywords/index.md)
