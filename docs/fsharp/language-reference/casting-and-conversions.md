---
title: Cast et conversions
description: Découvrez comment le F# langage de programmation fournit des opérateurs de conversion pour les conversions arithmétiques entre différents types primitifs.
ms.date: 05/16/2016
ms.openlocfilehash: ee4df588caabf58c7b9e18961e217ef8f15fcf93
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630438"
---
# <a name="casting-and-conversions-f"></a><span data-ttu-id="e26d1-103">Cast et conversions (F#)</span><span class="sxs-lookup"><span data-stu-id="e26d1-103">Casting and Conversions (F#)</span></span>

<span data-ttu-id="e26d1-104">Cette rubrique décrit la prise en charge des conversions de types dans F#.</span><span class="sxs-lookup"><span data-stu-id="e26d1-104">This topic describes support for type conversions in F#.</span></span>

## <a name="arithmetic-types"></a><span data-ttu-id="e26d1-105">Types arithmétiques</span><span class="sxs-lookup"><span data-stu-id="e26d1-105">Arithmetic Types</span></span>

<span data-ttu-id="e26d1-106">F#fournit des opérateurs de conversion pour les conversions arithmétiques entre différents types primitifs, tels qu’un entier et des types à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="e26d1-106">F# provides conversion operators for arithmetic conversions between various primitive types, such as between integer and floating point types.</span></span> <span data-ttu-id="e26d1-107">Les opérateurs de conversion intégrale et de caractère ont des formes vérifiées et non vérifiées; les opérateurs à virgule flottante `enum` et l’opérateur de conversion ne le font pas.</span><span class="sxs-lookup"><span data-stu-id="e26d1-107">The integral and char conversion operators have checked and unchecked forms; the floating point operators and the `enum` conversion operator do not.</span></span> <span data-ttu-id="e26d1-108">Les formulaires désactivés sont définis dans `Microsoft.FSharp.Core.Operators` et les formulaires vérifiés sont définis `Microsoft.FSharp.Core.Operators.Checked`dans.</span><span class="sxs-lookup"><span data-stu-id="e26d1-108">The unchecked forms are defined in `Microsoft.FSharp.Core.Operators` and the checked forms are defined in `Microsoft.FSharp.Core.Operators.Checked`.</span></span> <span data-ttu-id="e26d1-109">La vérification des formulaires cochés pour le dépassement de capacité et génère une exception Runtime si la valeur résultante dépasse les limites du type cible.</span><span class="sxs-lookup"><span data-stu-id="e26d1-109">The checked forms check for overflow and generate a runtime exception if the resulting value exceeds the limits of the target type.</span></span>

<span data-ttu-id="e26d1-110">Chacun de ces opérateurs porte le même nom que le nom du type de destination.</span><span class="sxs-lookup"><span data-stu-id="e26d1-110">Each of these operators has the same name as the name of the destination type.</span></span> <span data-ttu-id="e26d1-111">Par exemple, dans le code suivant, dans lequel les types sont annotés explicitement `byte` , apparaît avec deux significations différentes.</span><span class="sxs-lookup"><span data-stu-id="e26d1-111">For example, in the following code, in which the types are explicitly annotated, `byte` appears with two different meanings.</span></span> <span data-ttu-id="e26d1-112">La première occurrence est le type et la seconde est l’opérateur de conversion.</span><span class="sxs-lookup"><span data-stu-id="e26d1-112">The first occurrence is the type and the second is the conversion operator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

<span data-ttu-id="e26d1-113">Le tableau suivant présente les opérateurs de conversion F#définis dans.</span><span class="sxs-lookup"><span data-stu-id="e26d1-113">The following table shows conversion operators defined in F#.</span></span>

|<span data-ttu-id="e26d1-114">Opérateur</span><span class="sxs-lookup"><span data-stu-id="e26d1-114">Operator</span></span>|<span data-ttu-id="e26d1-115">Description</span><span class="sxs-lookup"><span data-stu-id="e26d1-115">Description</span></span>|
|--------|-----------|
|`byte`|<span data-ttu-id="e26d1-116">Convertit en Byte, un type non signé 8 bits.</span><span class="sxs-lookup"><span data-stu-id="e26d1-116">Convert to byte, an 8-bit unsigned type.</span></span>|
|`sbyte`|<span data-ttu-id="e26d1-117">Convertir en octet signé.</span><span class="sxs-lookup"><span data-stu-id="e26d1-117">Convert to signed byte.</span></span>|
|`int16`|<span data-ttu-id="e26d1-118">Convertit en entier 16 bits signé.</span><span class="sxs-lookup"><span data-stu-id="e26d1-118">Convert to a 16-bit signed integer.</span></span>|
|`uint16`|<span data-ttu-id="e26d1-119">Convertit en entier 16 bits non signé.</span><span class="sxs-lookup"><span data-stu-id="e26d1-119">Convert to a 16-bit unsigned integer.</span></span>|
|`int32, int`|<span data-ttu-id="e26d1-120">Convertit en entier signé 32 bits.</span><span class="sxs-lookup"><span data-stu-id="e26d1-120">Convert to a 32-bit signed integer.</span></span>|
|`uint32`|<span data-ttu-id="e26d1-121">Convertit en entier non signé 32 bits.</span><span class="sxs-lookup"><span data-stu-id="e26d1-121">Convert to a 32-bit unsigned integer.</span></span>|
|`int64`|<span data-ttu-id="e26d1-122">Convertit en entier signé 64 bits.</span><span class="sxs-lookup"><span data-stu-id="e26d1-122">Convert to a 64-bit signed integer.</span></span>|
|`uint64`|<span data-ttu-id="e26d1-123">Convertit en entier non signé 64 bits.</span><span class="sxs-lookup"><span data-stu-id="e26d1-123">Convert to a 64-bit unsigned integer.</span></span>|
|`nativeint`|<span data-ttu-id="e26d1-124">Convertit en entier natif.</span><span class="sxs-lookup"><span data-stu-id="e26d1-124">Convert to a native integer.</span></span>|
|`unativeint`|<span data-ttu-id="e26d1-125">Convertit en entier natif non signé.</span><span class="sxs-lookup"><span data-stu-id="e26d1-125">Convert to an unsigned native integer.</span></span>|
|`float, double`|<span data-ttu-id="e26d1-126">Convertit en nombre à virgule flottante IEEE double précision 64 bits.</span><span class="sxs-lookup"><span data-stu-id="e26d1-126">Convert to a 64-bit double-precision IEEE floating point number.</span></span>|
|`float32, single`|<span data-ttu-id="e26d1-127">Convertit en nombre à virgule flottante IEEE simple précision 32 bits.</span><span class="sxs-lookup"><span data-stu-id="e26d1-127">Convert to a 32-bit single-precision IEEE floating point number.</span></span>|
|`decimal`|<span data-ttu-id="e26d1-128">Convertit en `System.Decimal`.</span><span class="sxs-lookup"><span data-stu-id="e26d1-128">Convert to `System.Decimal`.</span></span>|
|`char`|<span data-ttu-id="e26d1-129">Convertit en `System.Char`, un caractère Unicode.</span><span class="sxs-lookup"><span data-stu-id="e26d1-129">Convert to `System.Char`, a Unicode character.</span></span>|
|`enum`|<span data-ttu-id="e26d1-130">Convertit en type énuméré.</span><span class="sxs-lookup"><span data-stu-id="e26d1-130">Convert to an enumerated type.</span></span>|

<span data-ttu-id="e26d1-131">En plus des types primitifs intégrés, vous pouvez utiliser ces opérateurs avec des types qui `op_Explicit` implémentent `op_Implicit` des méthodes ou avec des signatures appropriées.</span><span class="sxs-lookup"><span data-stu-id="e26d1-131">In addition to built-in primitive types, you can use these operators with types that implement `op_Explicit` or `op_Implicit` methods with appropriate signatures.</span></span> <span data-ttu-id="e26d1-132">Par exemple, l' `int` opérateur de conversion fonctionne avec n’importe quel type qui fournit `op_Explicit` une méthode statique qui prend le type comme paramètre `int`et retourne.</span><span class="sxs-lookup"><span data-stu-id="e26d1-132">For example, the `int` conversion operator works with any type that provides a static method `op_Explicit` that takes the type as a parameter and returns `int`.</span></span> <span data-ttu-id="e26d1-133">En tant qu’exception particulière à la règle générale, que les méthodes ne peuvent pas être surchargées par le type de `op_Explicit` retour `op_Implicit`, vous pouvez le faire pour et.</span><span class="sxs-lookup"><span data-stu-id="e26d1-133">As a special exception to the general rule that methods cannot be overloaded by return type, you can do this for `op_Explicit` and `op_Implicit`.</span></span>

## <a name="enumerated-types"></a><span data-ttu-id="e26d1-134">Types énumérés</span><span class="sxs-lookup"><span data-stu-id="e26d1-134">Enumerated Types</span></span>

<span data-ttu-id="e26d1-135">L' `enum` opérateur est un opérateur générique qui accepte un paramètre de type qui représente le type du `enum` vers lequel effectuer la conversion.</span><span class="sxs-lookup"><span data-stu-id="e26d1-135">The `enum` operator is a generic operator that takes one type parameter that represents the type of the `enum` to convert to.</span></span> <span data-ttu-id="e26d1-136">Quand elle est convertie en un type énuméré, les tentatives d’inférence de type permettent de `enum` déterminer le type du vers lequel vous souhaitez effectuer la conversion.</span><span class="sxs-lookup"><span data-stu-id="e26d1-136">When it converts to an enumerated type, type inference attempts to determine the type of the `enum` that you want to convert to.</span></span> <span data-ttu-id="e26d1-137">Dans l’exemple suivant, la variable `col1` n’est pas annotée explicitement, mais son type est déduit du test d’égalité ultérieur.</span><span class="sxs-lookup"><span data-stu-id="e26d1-137">In the following example, the variable `col1` is not explicitly annotated, but its type is inferred from the later equality test.</span></span> <span data-ttu-id="e26d1-138">Par conséquent, le compilateur peut déduire que vous convertissez `Color` en une énumération.</span><span class="sxs-lookup"><span data-stu-id="e26d1-138">Therefore, the compiler can deduce that you are converting to a `Color` enumeration.</span></span> <span data-ttu-id="e26d1-139">Vous pouvez également fournir une annotation de type, comme `col2` dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="e26d1-139">Alternatively, you can supply a type annotation, as with `col2` in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

<span data-ttu-id="e26d1-140">Vous pouvez également spécifier explicitement le type d’énumération cible comme paramètre de type, comme dans le code suivant:</span><span class="sxs-lookup"><span data-stu-id="e26d1-140">You can also specify the target enumeration type explicitly as a type parameter, as in the following code:</span></span>

```fsharp
let col3 = enum<Color> 3
```

<span data-ttu-id="e26d1-141">Notez que les conversions d’énumération fonctionnent uniquement si le type sous-jacent de l’énumération est compatible avec le type en cours de conversion.</span><span class="sxs-lookup"><span data-stu-id="e26d1-141">Note that the enumeration casts work only if the underlying type of the enumeration is compatible with the type being converted.</span></span> <span data-ttu-id="e26d1-142">Dans le code suivant, la compilation échoue en raison de l’incompatibilité entre `int32` et `uint32`.</span><span class="sxs-lookup"><span data-stu-id="e26d1-142">In the following code, the conversion fails to compile because of the mismatch between `int32` and `uint32`.</span></span>

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

<span data-ttu-id="e26d1-143">Pour plus d’informations, consultez [énumérations](enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="e26d1-143">For more information, see [Enumerations](enumerations.md).</span></span>

## <a name="casting-object-types"></a><span data-ttu-id="e26d1-144">Cast de types d’objet</span><span class="sxs-lookup"><span data-stu-id="e26d1-144">Casting Object Types</span></span>

<span data-ttu-id="e26d1-145">La conversion entre les types dans une hiérarchie d’objets est fondamentale pour la programmation orientée objet.</span><span class="sxs-lookup"><span data-stu-id="e26d1-145">Conversion between types in an object hierarchy is fundamental to object-oriented programming.</span></span> <span data-ttu-id="e26d1-146">Il existe deux types de conversions de base: la conversion ascendante (cast) et la conversion vers le haut (passer).</span><span class="sxs-lookup"><span data-stu-id="e26d1-146">There are two basic types of conversions: casting up (upcasting) and casting down (downcasting).</span></span> <span data-ttu-id="e26d1-147">Effectuer un cast vers le haut d’une hiérarchie signifie effectuer un cast à partir d’une référence d’objet dérivé vers une référence d’objet de base.</span><span class="sxs-lookup"><span data-stu-id="e26d1-147">Casting up a hierarchy means casting from a derived object reference to a base object reference.</span></span> <span data-ttu-id="e26d1-148">Ce type de conversion est garanti fonctionner tant que la classe de base est dans la hiérarchie d’héritage de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="e26d1-148">Such a cast is guaranteed to work as long as the base class is in the inheritance hierarchy of the derived class.</span></span> <span data-ttu-id="e26d1-149">La conversion descendante d’une hiérarchie, d’une référence d’objet de base à une référence d’objet dérivée, ne fonctionne que si l’objet est réellement une instance du type de destination (dérivé) correct ou un type dérivé du type de destination.</span><span class="sxs-lookup"><span data-stu-id="e26d1-149">Casting down a hierarchy, from a base object reference to a derived object reference, succeeds only if the object actually is an instance of the correct destination (derived) type or a type derived from the destination type.</span></span>

<span data-ttu-id="e26d1-150">F#fournit des opérateurs pour ces types de conversions.</span><span class="sxs-lookup"><span data-stu-id="e26d1-150">F# provides operators for these types of conversions.</span></span> <span data-ttu-id="e26d1-151">L' `:>` opérateur effectue un cast vers le haut de la `:?>` hiérarchie et l’opérateur convertit la hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="e26d1-151">The `:>` operator casts up the hierarchy, and the `:?>` operator casts down the hierarchy.</span></span>

### <a name="upcasting"></a><span data-ttu-id="e26d1-152">Un upcast</span><span class="sxs-lookup"><span data-stu-id="e26d1-152">Upcasting</span></span>

<span data-ttu-id="e26d1-153">Dans de nombreux langages orientés objet, la conversion est implicite; dans F#, les règles sont légèrement différentes.</span><span class="sxs-lookup"><span data-stu-id="e26d1-153">In many object-oriented languages, upcasting is implicit; in F#, the rules are slightly different.</span></span> <span data-ttu-id="e26d1-154">Le cast est appliqué automatiquement quand vous transmettez des arguments aux méthodes sur un type d’objet.</span><span class="sxs-lookup"><span data-stu-id="e26d1-154">Upcasting is applied automatically when you pass arguments to methods on an object type.</span></span> <span data-ttu-id="e26d1-155">Toutefois, pour les fonctions liées à Let dans un module, le transtypage n’est pas automatique, sauf si le type de paramètre est déclaré comme étant un type flexible.</span><span class="sxs-lookup"><span data-stu-id="e26d1-155">However, for let-bound functions in a module, upcasting is not automatic, unless the parameter type is declared as a flexible type.</span></span> <span data-ttu-id="e26d1-156">Pour plus d’informations, consultez [types flexibles](flexible-Types.md).</span><span class="sxs-lookup"><span data-stu-id="e26d1-156">For more information, see [Flexible Types](flexible-Types.md).</span></span>

<span data-ttu-id="e26d1-157">L' `:>` opérateur effectue un cast statique, ce qui signifie que le succès du cast est déterminé au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="e26d1-157">The `:>` operator performs a static cast, which means that the success of the cast is determined at compile time.</span></span> <span data-ttu-id="e26d1-158">Si un cast qui utilise `:>` des compilations réussit, il s’agit d’un cast valide qui n’a aucun risque d’échec au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e26d1-158">If a cast that uses `:>` compiles successfully, it is a valid cast and has no chance of failure at run time.</span></span>

<span data-ttu-id="e26d1-159">Vous pouvez également utiliser l' `upcast` opérateur pour effectuer une telle conversion.</span><span class="sxs-lookup"><span data-stu-id="e26d1-159">You can also use the `upcast` operator to perform such a conversion.</span></span> <span data-ttu-id="e26d1-160">L’expression suivante spécifie une conversion vers le haut de la hiérarchie:</span><span class="sxs-lookup"><span data-stu-id="e26d1-160">The following expression specifies a conversion up the hierarchy:</span></span>

```fsharp
upcast expression
```

<span data-ttu-id="e26d1-161">Lorsque vous utilisez l’opérateur de transtypage, le compilateur tente de déduire le type vers lequel vous effectuez la conversion à partir du contexte.</span><span class="sxs-lookup"><span data-stu-id="e26d1-161">When you use the upcast operator, the compiler attempts to infer the type you are converting to from the context.</span></span> <span data-ttu-id="e26d1-162">Si le compilateur ne parvient pas à déterminer le type cible, le compilateur signale une erreur.</span><span class="sxs-lookup"><span data-stu-id="e26d1-162">If the compiler is unable to determine the target type, the compiler reports an error.</span></span>

### <a name="downcasting"></a><span data-ttu-id="e26d1-163">Passer</span><span class="sxs-lookup"><span data-stu-id="e26d1-163">Downcasting</span></span>

<span data-ttu-id="e26d1-164">L' `:?>` opérateur effectue un cast dynamique, ce qui signifie que le succès du cast est déterminé au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e26d1-164">The `:?>` operator performs a dynamic cast, which means that the success of the cast is determined at run time.</span></span> <span data-ttu-id="e26d1-165">Un cast qui utilise l' `:?>` opérateur n’est pas vérifié au moment de la compilation; mais au moment de l’exécution, une tentative est effectuée pour effectuer un cast vers le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="e26d1-165">A cast that uses the `:?>` operator is not checked at compile time; but at run time, an attempt is made to cast to the specified type.</span></span> <span data-ttu-id="e26d1-166">Si l’objet est compatible avec le type cible, le cast se déroule correctement.</span><span class="sxs-lookup"><span data-stu-id="e26d1-166">If the object is compatible with the target type, the cast succeeds.</span></span> <span data-ttu-id="e26d1-167">Si l’objet n’est pas compatible avec le type cible, le runtime lève `InvalidCastException`une.</span><span class="sxs-lookup"><span data-stu-id="e26d1-167">If the object is not compatible with the target type, the runtime raises an `InvalidCastException`.</span></span>

<span data-ttu-id="e26d1-168">Vous pouvez également utiliser l' `downcast` opérateur pour effectuer une conversion de type dynamique.</span><span class="sxs-lookup"><span data-stu-id="e26d1-168">You can also use the `downcast` operator to perform a dynamic type conversion.</span></span> <span data-ttu-id="e26d1-169">L’expression suivante spécifie une conversion descendante de la hiérarchie en un type déduit à partir du contexte du programme:</span><span class="sxs-lookup"><span data-stu-id="e26d1-169">The following expression specifies a conversion down the hierarchy to a type that is inferred from program context:</span></span>

```fsharp
downcast expression
```

<span data-ttu-id="e26d1-170">Comme pour l' `upcast` opérateur, si le compilateur ne peut pas déduire un type cible spécifique à partir du contexte, il signale une erreur.</span><span class="sxs-lookup"><span data-stu-id="e26d1-170">As for the `upcast` operator, if the compiler cannot infer a specific target type from the context, it reports an error.</span></span>

<span data-ttu-id="e26d1-171">Le code suivant illustre l’utilisation des `:>` opérateurs et. `:?>`</span><span class="sxs-lookup"><span data-stu-id="e26d1-171">The following code illustrates the use of the `:>` and `:?>` operators.</span></span> <span data-ttu-id="e26d1-172">Le code illustre l’utilisation de `:?>` l’opérateur lorsque vous savez que la conversion réussira, car elle `InvalidCastException` lève une exception en cas d’échec de la conversion.</span><span class="sxs-lookup"><span data-stu-id="e26d1-172">The code illustrates that the `:?>` operator is best used when you know that conversion will succeed, because it throws `InvalidCastException` if the conversion fails.</span></span> <span data-ttu-id="e26d1-173">Si vous ne savez pas qu’une conversion est réussie, un test de type qui utilise `match` une expression est mieux, car il évite la surcharge liée à la génération d’une exception.</span><span class="sxs-lookup"><span data-stu-id="e26d1-173">If you do not know that a conversion will succeed, a type test that uses a `match` expression is better because it avoids the overhead of generating an exception.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

<span data-ttu-id="e26d1-174">Étant donné que `downcast` les `upcast` opérateurs génériques et s’appuient sur l’inférence de type pour déterminer l’argument et le type de retour, dans le code ci-dessus, vous pouvez remplacer</span><span class="sxs-lookup"><span data-stu-id="e26d1-174">Because generic operators `downcast` and `upcast` rely on type inference to determine the argument and return type, in the above code, you can replace</span></span>

```fsharp
let base1 = d1 :> Base1
```

<span data-ttu-id="e26d1-175">par</span><span class="sxs-lookup"><span data-stu-id="e26d1-175">with</span></span>

```fsharp
let base1 = upcast d1
```

<span data-ttu-id="e26d1-176">Dans le code précédent, le type d’argument et les types `Derived1` de `Base1`retour sont respectivement et.</span><span class="sxs-lookup"><span data-stu-id="e26d1-176">In the previous code, the argument type and return types are `Derived1` and `Base1`, respectively.</span></span>

<span data-ttu-id="e26d1-177">Pour plus d’informations sur les tests de type, consultez [expressions de correspondance](match-Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e26d1-177">For more information about type tests, see [Match Expressions](match-Expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e26d1-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e26d1-178">See also</span></span>

- [<span data-ttu-id="e26d1-179">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="e26d1-179">F# Language Reference</span></span>](index.md)
