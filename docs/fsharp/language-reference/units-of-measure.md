---
title: Unités de mesure
description: 'Découvrez comment les valeurs entières et signées de virgule flottante en F # peuvent être associées à des unités de mesure, qui sont généralement utilisées pour indiquer la longueur, le volume et la masse.'
ms.date: 08/15/2020
ms.openlocfilehash: 0262f89e80697dd86161c93fe37381122972b56f
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811572"
---
# <a name="units-of-measure"></a><span data-ttu-id="50dd8-103">Unités de mesure</span><span class="sxs-lookup"><span data-stu-id="50dd8-103">Units of Measure</span></span>

<span data-ttu-id="50dd8-104">Les valeurs de type virgule flottante et entier signé en F # peuvent être associées à des unités de mesure, qui sont généralement utilisées pour indiquer la longueur, le volume, la masse, etc.</span><span class="sxs-lookup"><span data-stu-id="50dd8-104">Floating point and signed integer values in F# can have associated units of measure, which are typically used to indicate length, volume, mass, and so on.</span></span> <span data-ttu-id="50dd8-105">En utilisant des quantités avec des unités, vous permettez au compilateur de vérifier que les relations arithmétiques disposent des unités appropriées, ce qui permet d’éviter les erreurs de programmation.</span><span class="sxs-lookup"><span data-stu-id="50dd8-105">By using quantities with units, you enable the compiler to verify that arithmetic relationships have the correct units, which helps prevent programming errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="50dd8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50dd8-106">Syntax</span></span>

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a><span data-ttu-id="50dd8-107">Notes</span><span class="sxs-lookup"><span data-stu-id="50dd8-107">Remarks</span></span>

<span data-ttu-id="50dd8-108">La syntaxe précédente définit *unit-name* comme unité de mesure.</span><span class="sxs-lookup"><span data-stu-id="50dd8-108">The previous syntax defines *unit-name* as a unit of measure.</span></span> <span data-ttu-id="50dd8-109">La partie facultative est utilisée pour définir une nouvelle mesure en termes d’unités précédemment définies.</span><span class="sxs-lookup"><span data-stu-id="50dd8-109">The optional part is used to define a new measure in terms of previously defined units.</span></span> <span data-ttu-id="50dd8-110">Par exemple, la ligne suivante définit la mesure `cm` (centimètre).</span><span class="sxs-lookup"><span data-stu-id="50dd8-110">For example, the following line defines the measure `cm` (centimeter).</span></span>

```fsharp
[<Measure>] type cm
```

<span data-ttu-id="50dd8-111">La ligne suivante définit la mesure `ml` (milliliter) en tant que centimètre cube ( `cm^3` ).</span><span class="sxs-lookup"><span data-stu-id="50dd8-111">The following line defines the measure `ml` (milliliter) as a cubic centimeter (`cm^3`).</span></span>

```fsharp
[<Measure>] type ml = cm^3
```

<span data-ttu-id="50dd8-112">Dans la syntaxe précédente, *measure* est une formule qui implique des unités.</span><span class="sxs-lookup"><span data-stu-id="50dd8-112">In the previous syntax, *measure* is a formula that involves units.</span></span> <span data-ttu-id="50dd8-113">Dans les formules qui impliquent des unités, les puissances entières sont prises en charge (positives et négatives), les espaces entre les unités indiquent un produit des deux unités, indiquent `*` également un produit d’unités et `/` indiquent un quotient d’unités.</span><span class="sxs-lookup"><span data-stu-id="50dd8-113">In formulas that involve units, integral powers are supported (positive and negative), spaces between units indicate a product of the two units, `*` also indicates a product of units, and `/` indicates a quotient of units.</span></span> <span data-ttu-id="50dd8-114">Pour une unité réciproque, vous pouvez utiliser un entier négatif ou une valeur `/` qui indique une séparation entre le numérateur et le dénominateur d’une formule d’unité.</span><span class="sxs-lookup"><span data-stu-id="50dd8-114">For a reciprocal unit, you can either use a negative integer power or a `/` that indicates a separation between the numerator and denominator of a unit formula.</span></span> <span data-ttu-id="50dd8-115">Les unités multiples dans le dénominateur doivent être placées entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="50dd8-115">Multiple units in the denominator should be surrounded by parentheses.</span></span> <span data-ttu-id="50dd8-116">Les unités séparées par des espaces après un `/` sont interprétées comme faisant partie du dénominateur, mais toutes les unités qui suivent un `*` sont interprétées comme faisant partie du numérateur.</span><span class="sxs-lookup"><span data-stu-id="50dd8-116">Units separated by spaces after a `/` are interpreted as being part of the denominator, but any units following a `*` are interpreted as being part of the numerator.</span></span>

<span data-ttu-id="50dd8-117">Vous pouvez utiliser 1 dans les expressions d’unité, soit pour indiquer une quantité sans dimension, soit avec d’autres unités, comme dans le numérateur.</span><span class="sxs-lookup"><span data-stu-id="50dd8-117">You can use 1 in unit expressions, either alone to indicate a dimensionless quantity, or together with other units, such as in the numerator.</span></span> <span data-ttu-id="50dd8-118">Par exemple, les unités d’un taux sont écrites sous la forme `1/s` , où `s` indique des secondes.</span><span class="sxs-lookup"><span data-stu-id="50dd8-118">For example, the units for a rate would be written as `1/s`, where `s` indicates seconds.</span></span> <span data-ttu-id="50dd8-119">Les parenthèses ne sont pas utilisées dans les formules d’unité.</span><span class="sxs-lookup"><span data-stu-id="50dd8-119">Parentheses are not used in unit formulas.</span></span> <span data-ttu-id="50dd8-120">Vous ne spécifiez pas de constantes de conversion numérique dans les formules d’unité ; Toutefois, vous pouvez définir des constantes de conversion avec des unités séparément et les utiliser dans des calculs Check Unit.</span><span class="sxs-lookup"><span data-stu-id="50dd8-120">You do not specify numeric conversion constants in the unit formulas; however, you can define conversion constants with units separately and use them in unit-checked computations.</span></span>

<span data-ttu-id="50dd8-121">Les formules d’unités qui signifient la même chose peuvent être écrites de différentes façons équivalentes.</span><span class="sxs-lookup"><span data-stu-id="50dd8-121">Unit formulas that mean the same thing can be written in various equivalent ways.</span></span> <span data-ttu-id="50dd8-122">Par conséquent, le compilateur convertit les formules d’unités sous une forme cohérente, ce qui convertit les puissances négatives en valeurs réciproques, regroupe les unités en un seul numérateur et un dénominateur, et alphabetizes les unités dans le numérateur et le dénominateur.</span><span class="sxs-lookup"><span data-stu-id="50dd8-122">Therefore, the compiler converts unit formulas into a consistent form, which converts negative powers to reciprocals, groups units into a single numerator and a denominator, and alphabetizes the units in the numerator and denominator.</span></span>

<span data-ttu-id="50dd8-123">Par exemple, les formules `kg m s^-2` d’unité et `m /s s * kg` sont toutes deux converties en `kg m/s^2` .</span><span class="sxs-lookup"><span data-stu-id="50dd8-123">For example, the unit formulas `kg m s^-2` and `m /s s * kg` are both converted to `kg m/s^2`.</span></span>

<span data-ttu-id="50dd8-124">Les unités de mesure sont utilisées dans les expressions à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="50dd8-124">You use units of measure in floating point expressions.</span></span> <span data-ttu-id="50dd8-125">L’utilisation de nombres à virgule flottante avec des unités de mesure associées ajoute un autre niveau de sécurité de type et permet d’éviter les erreurs d’incompatibilité d’unités qui peuvent se produire dans les formules lorsque vous utilisez des nombres à virgule flottante faiblement typés.</span><span class="sxs-lookup"><span data-stu-id="50dd8-125">Using floating point numbers together with associated units of measure adds another level of type safety and helps avoid the unit mismatch errors that can occur in formulas when you use weakly typed floating point numbers.</span></span> <span data-ttu-id="50dd8-126">Si vous écrivez une expression à virgule flottante qui utilise des unités, les unités de l’expression doivent correspondre.</span><span class="sxs-lookup"><span data-stu-id="50dd8-126">If you write a floating point expression that uses units, the units in the expression must match.</span></span>

<span data-ttu-id="50dd8-127">Vous pouvez annoter des littéraux à l’aide d’une formule d’unité entre crochets pointus, comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="50dd8-127">You can annotate literals with a unit formula in angle brackets, as shown in the following examples.</span></span>

```fsharp
1.0<cm>
55.0<miles/hour>
```

<span data-ttu-id="50dd8-128">Vous ne placez pas d’espace entre le nombre et le Chevron ; Toutefois, vous pouvez inclure un suffixe littéral, tel que `f` , comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="50dd8-128">You do not put a space between the number and the angle bracket; however, you can include a literal suffix such as `f`, as in the following example.</span></span>

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

<span data-ttu-id="50dd8-129">Une telle annotation modifie le type du littéral de son type primitif (tel que `float` ) en un type dimensionné, tel que `float<cm>` ou, dans ce cas, `float<miles/hour>` .</span><span class="sxs-lookup"><span data-stu-id="50dd8-129">Such an annotation changes the type of the literal from its primitive type (such as `float`) to a dimensioned type, such as `float<cm>` or, in this case, `float<miles/hour>`.</span></span> <span data-ttu-id="50dd8-130">Une annotation d’unité de `<1>` indique une quantité sans dimension, et son type est équivalent au type primitif sans paramètre d’unité.</span><span class="sxs-lookup"><span data-stu-id="50dd8-130">A unit annotation of `<1>` indicates a dimensionless quantity, and its type is equivalent to the primitive type without a unit parameter.</span></span>

<span data-ttu-id="50dd8-131">Le type d’une unité de mesure est une virgule flottante ou un type intégral signé avec une annotation d’unité supplémentaire, indiquée entre crochets.</span><span class="sxs-lookup"><span data-stu-id="50dd8-131">The type of a unit of measure is a floating point or signed integral type together with an extra unit annotation, indicated in brackets.</span></span> <span data-ttu-id="50dd8-132">Ainsi, lorsque vous écrivez le type d’une conversion de `g` (grammes) à `kg` (kilogrammes), vous décrivez les types comme suit.</span><span class="sxs-lookup"><span data-stu-id="50dd8-132">Thus, when you write the type of a conversion from `g` (grams) to `kg` (kilograms), you describe the types as follows.</span></span>

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

<span data-ttu-id="50dd8-133">Les unités de mesure sont utilisées pour la vérification des unités au moment de la compilation, mais ne sont pas conservées dans l’environnement d’exécution.</span><span class="sxs-lookup"><span data-stu-id="50dd8-133">Units of measure are used for compile-time unit checking but are not persisted in the run-time environment.</span></span> <span data-ttu-id="50dd8-134">Par conséquent, elles n’affectent pas les performances.</span><span class="sxs-lookup"><span data-stu-id="50dd8-134">Therefore, they do not affect performance.</span></span>

<span data-ttu-id="50dd8-135">Les unités de mesure peuvent être appliquées à n’importe quel type, pas seulement aux types à virgule flottante ; Toutefois, seuls les types à virgule flottante, les types intégraux signés et les types décimaux prennent en charge les quantités dimensionnelles.</span><span class="sxs-lookup"><span data-stu-id="50dd8-135">Units of measure can be applied to any type, not just floating point types; however, only floating point types, signed integral types, and decimal types support dimensioned quantities.</span></span> <span data-ttu-id="50dd8-136">Par conséquent, il est judicieux d’utiliser des unités de mesure sur les types primitifs et sur les agrégats qui contiennent ces types primitifs.</span><span class="sxs-lookup"><span data-stu-id="50dd8-136">Therefore, it only makes sense to use units of measure on the primitive types and on aggregates that contain these primitive types.</span></span>

<span data-ttu-id="50dd8-137">L’exemple suivant illustre l’utilisation d’unités de mesure.</span><span class="sxs-lookup"><span data-stu-id="50dd8-137">The following example illustrates the use of units of measure.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]

<span data-ttu-id="50dd8-138">L’exemple de code suivant montre comment convertir un nombre à virgule flottante sans dimension en valeur à virgule flottante dimensionnée.</span><span class="sxs-lookup"><span data-stu-id="50dd8-138">The following code example illustrates how to convert from a dimensionless floating point number to a dimensioned floating point value.</span></span> <span data-ttu-id="50dd8-139">Vous multipliez simplement par 1,0, en appliquant les dimensions aux 1,0.</span><span class="sxs-lookup"><span data-stu-id="50dd8-139">You just multiply by 1.0, applying the dimensions to the 1.0.</span></span> <span data-ttu-id="50dd8-140">Vous pouvez l’extraire dans une fonction comme `degreesFahrenheit` .</span><span class="sxs-lookup"><span data-stu-id="50dd8-140">You can abstract this into a function like `degreesFahrenheit`.</span></span>

<span data-ttu-id="50dd8-141">En outre, lorsque vous transmettez des valeurs dimensionnées à des fonctions qui attendent des nombres à virgule flottante sans dimension, vous devez annuler les unités ou effectuer un cast en à `float` l’aide de l' `float` opérateur.</span><span class="sxs-lookup"><span data-stu-id="50dd8-141">Also, when you pass dimensioned values to functions that expect dimensionless floating point numbers, you must cancel out the units or cast to `float` by using the `float` operator.</span></span> <span data-ttu-id="50dd8-142">Dans cet exemple, vous divisez par `1.0<degC>` pour les arguments à `printf` , car `printf` attend des quantités sans dimension.</span><span class="sxs-lookup"><span data-stu-id="50dd8-142">In this example, you divide by `1.0<degC>` for the arguments to `printf` because `printf` expects dimensionless quantities.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

<span data-ttu-id="50dd8-143">L’exemple de session suivant montre les sorties de et les entrées de ce code.</span><span class="sxs-lookup"><span data-stu-id="50dd8-143">The following example session shows the outputs from and inputs to this code.</span></span>

```console
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a><span data-ttu-id="50dd8-144">Utilisation d’unités génériques</span><span class="sxs-lookup"><span data-stu-id="50dd8-144">Using Generic Units</span></span>

<span data-ttu-id="50dd8-145">Vous pouvez écrire des fonctions génériques qui opèrent sur des données qui ont une unité de mesure associée.</span><span class="sxs-lookup"><span data-stu-id="50dd8-145">You can write generic functions that operate on data that has an associated unit of measure.</span></span> <span data-ttu-id="50dd8-146">Pour ce faire, vous devez spécifier un type avec une unité générique comme paramètre de type, comme indiqué dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="50dd8-146">You do this by specifying a type together with a generic unit as a type parameter, as shown in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]

## <a name="creating-aggregate-types-with-generic-units"></a><span data-ttu-id="50dd8-147">Création de types d’agrégats avec des unités génériques</span><span class="sxs-lookup"><span data-stu-id="50dd8-147">Creating Aggregate Types with Generic Units</span></span>

<span data-ttu-id="50dd8-148">Le code suivant montre comment créer un type d’agrégat qui se compose de valeurs à virgule flottante individuelles qui ont des unités génériques.</span><span class="sxs-lookup"><span data-stu-id="50dd8-148">The following code shows how to create an aggregate type that consists of individual floating point values that have units that are generic.</span></span> <span data-ttu-id="50dd8-149">Cela permet de créer un type unique qui fonctionne avec diverses unités.</span><span class="sxs-lookup"><span data-stu-id="50dd8-149">This enables a single type to be created that works with a variety of units.</span></span> <span data-ttu-id="50dd8-150">En outre, les unités génériques préservent la cohérence des types en s’assurant qu’un type générique qui a un ensemble d’unités est un type différent du même type générique avec un autre ensemble d’unités.</span><span class="sxs-lookup"><span data-stu-id="50dd8-150">Also, generic units preserve type safety by ensuring that a generic type that has one set of units is a different type than the same generic type with a different set of units.</span></span> <span data-ttu-id="50dd8-151">La base de cette technique est que l' `Measure` attribut peut être appliqué au paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="50dd8-151">The basis of this technique is that the `Measure` attribute can be applied to the type parameter.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]

## <a name="units-at-runtime"></a><span data-ttu-id="50dd8-152">Unités au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="50dd8-152">Units at Runtime</span></span>

<span data-ttu-id="50dd8-153">Les unités de mesure sont utilisées pour la vérification de type statique.</span><span class="sxs-lookup"><span data-stu-id="50dd8-153">Units of measure are used for static type checking.</span></span> <span data-ttu-id="50dd8-154">Lorsque les valeurs à virgule flottante sont compilées, les unités de mesure sont éliminées, de sorte que les unités sont perdues au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="50dd8-154">When floating point values are compiled, the units of measure are eliminated, so the units are lost at run time.</span></span> <span data-ttu-id="50dd8-155">Par conséquent, toute tentative d’implémentation de la fonctionnalité qui dépend de la vérification des unités au moment de l’exécution n’est pas possible.</span><span class="sxs-lookup"><span data-stu-id="50dd8-155">Therefore, any attempt to implement functionality that depends on checking the units at run time is not possible.</span></span> <span data-ttu-id="50dd8-156">Par exemple, l’implémentation d’une `ToString` fonction pour imprimer les unités n’est pas possible.</span><span class="sxs-lookup"><span data-stu-id="50dd8-156">For example, implementing a `ToString` function to print out the units is not possible.</span></span>

## <a name="conversions"></a><span data-ttu-id="50dd8-157">Conversions</span><span class="sxs-lookup"><span data-stu-id="50dd8-157">Conversions</span></span>

<span data-ttu-id="50dd8-158">Pour convertir un type qui a des unités (par exemple, `float<'u>` ) en un type qui n’a pas d’unités, vous pouvez utiliser la fonction de conversion standard.</span><span class="sxs-lookup"><span data-stu-id="50dd8-158">To convert a type that has units (for example, `float<'u>`) to a type that does not have units, you can use the standard conversion function.</span></span> <span data-ttu-id="50dd8-159">Par exemple, vous pouvez utiliser `float` pour convertir en une `float` valeur qui n’a pas d’unités, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="50dd8-159">For example, you can use `float` to convert to a `float` value that does not have units, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

<span data-ttu-id="50dd8-160">Pour convertir une valeur sans unité en une valeur qui a des unités, vous pouvez multiplier par une valeur 1 ou 1,0 qui est annotée avec les unités appropriées.</span><span class="sxs-lookup"><span data-stu-id="50dd8-160">To convert a unitless value to a value that has units, you can multiply by a 1 or 1.0 value that is annotated with the appropriate units.</span></span> <span data-ttu-id="50dd8-161">Toutefois, pour écrire des couches d’interopérabilité, il existe également des fonctions explicites que vous pouvez utiliser pour convertir des valeurs sans unité en valeurs avec unités.</span><span class="sxs-lookup"><span data-stu-id="50dd8-161">However, for writing interoperability layers, there are also some explicit functions that you can use to convert unitless values to values with units.</span></span> <span data-ttu-id="50dd8-162">Celles-ci se trouvent dans le module [FSharp. Core. LanguagePrimitives](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-languageprimitives.html) .</span><span class="sxs-lookup"><span data-stu-id="50dd8-162">These are in the [FSharp.Core.LanguagePrimitives](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-languageprimitives.html) module.</span></span> <span data-ttu-id="50dd8-163">Par exemple, pour effectuer une conversion d’une unité sans unité `float` en `float<cm>` , utilisez [FloatWithMeasure](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-languageprimitives.html#FloatWithMeasure), comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="50dd8-163">For example, to convert from a unitless `float` to a `float<cm>`, use [FloatWithMeasure](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-languageprimitives.html#FloatWithMeasure), as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]

## <a name="units-of-measure-in-the-f-core-library"></a><span data-ttu-id="50dd8-164">Unités de mesure dans la bibliothèque principale F #</span><span class="sxs-lookup"><span data-stu-id="50dd8-164">Units of Measure in the F# Core library</span></span>

<span data-ttu-id="50dd8-165">Une bibliothèque d’unités est disponible dans l' `FSharp.Data.UnitSystems.SI` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="50dd8-165">A unit library is available in the `FSharp.Data.UnitSystems.SI` namespace.</span></span> <span data-ttu-id="50dd8-166">Elle comprend des unités SI dans leur forme de symbole (comme `m` pour le compteur) dans le `UnitSymbols` sous-espace de noms, et leur nom complet (comme `meter` pour le compteur) dans le `UnitNames` sous-espace de noms.</span><span class="sxs-lookup"><span data-stu-id="50dd8-166">It includes SI units in both their symbol form (like `m` for meter) in the `UnitSymbols` sub-namespace, and their full name (like `meter` for meter) in the `UnitNames` sub-namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="50dd8-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50dd8-167">See also</span></span>

- [<span data-ttu-id="50dd8-168">Informations de référence sur le langage F #</span><span class="sxs-lookup"><span data-stu-id="50dd8-168">F# Language Reference</span></span>](index.md)
