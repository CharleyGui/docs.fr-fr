---
title: Indications de mise en forme du code F#
description: Apprenez des lignes directrices pour le formatage du code F.
ms.date: 11/04/2019
ms.openlocfilehash: b8be70dd29a04e71614308164e541b99a1724305
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739554"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="79adb-103">Indications de mise en forme du code F#</span><span class="sxs-lookup"><span data-stu-id="79adb-103">F# code formatting guidelines</span></span>

<span data-ttu-id="79adb-104">Cet article offre des lignes directrices sur la façon de formater votre code afin que votre code F est :</span><span class="sxs-lookup"><span data-stu-id="79adb-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="79adb-105">Plus lisible</span><span class="sxs-lookup"><span data-stu-id="79adb-105">More legible</span></span>
* <span data-ttu-id="79adb-106">Conformément aux conventions appliquées par les outils de formatage dans Visual Studio et d’autres éditeurs</span><span class="sxs-lookup"><span data-stu-id="79adb-106">In accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="79adb-107">Semblable à d’autres codes en ligne</span><span class="sxs-lookup"><span data-stu-id="79adb-107">Similar to other code online</span></span>

<span data-ttu-id="79adb-108">Ces lignes directrices sont basées sur [un guide complet des conventions de formatage de F par](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) [Anh-Dung Phan](https://github.com/dungpa).</span><span class="sxs-lookup"><span data-stu-id="79adb-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="79adb-109">Règles générales d’indentation</span><span class="sxs-lookup"><span data-stu-id="79adb-109">General rules for indentation</span></span>

<span data-ttu-id="79adb-110">F ' utilise l’espace blanc significatif par défaut.</span><span class="sxs-lookup"><span data-stu-id="79adb-110">F# uses significant white space by default.</span></span> <span data-ttu-id="79adb-111">Les lignes directrices suivantes visent à fournir des conseils sur la façon de jongler avec certains défis que cela peut imposer.</span><span class="sxs-lookup"><span data-stu-id="79adb-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="79adb-112">Utilisation d’espaces</span><span class="sxs-lookup"><span data-stu-id="79adb-112">Using spaces</span></span>

<span data-ttu-id="79adb-113">Lorsque l’indentation est nécessaire, vous devez utiliser des espaces, pas des onglets.</span><span class="sxs-lookup"><span data-stu-id="79adb-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="79adb-114">Au moins un espace est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="79adb-114">At least one space is required.</span></span> <span data-ttu-id="79adb-115">Votre organisation peut créer des normes de codage pour spécifier le nombre d’espaces à utiliser pour l’indentation; deux, trois ou quatre espaces d’indentation à chaque niveau où l’indentation se produit est typique.</span><span class="sxs-lookup"><span data-stu-id="79adb-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three, or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="79adb-116">**Nous recommandons quatre espaces par indentation.**</span><span class="sxs-lookup"><span data-stu-id="79adb-116">**We recommend four spaces per indentation.**</span></span>

<span data-ttu-id="79adb-117">Cela dit, l’indentation des programmes est une question subjective.</span><span class="sxs-lookup"><span data-stu-id="79adb-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="79adb-118">Les variations sont OK, mais la première règle que vous devez suivre est *la cohérence de l’indentation*.</span><span class="sxs-lookup"><span data-stu-id="79adb-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="79adb-119">Choisissez un style d’indentation généralement accepté et utilisez-le systématiquement dans votre base de code.</span><span class="sxs-lookup"><span data-stu-id="79adb-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-white-space"></a><span data-ttu-id="79adb-120">Formater l’espace blanc</span><span class="sxs-lookup"><span data-stu-id="79adb-120">Formatting white space</span></span>

<span data-ttu-id="79adb-121">L’espace blanc est sensible à l’espace blanc.</span><span class="sxs-lookup"><span data-stu-id="79adb-121">F# is white space sensitive.</span></span> <span data-ttu-id="79adb-122">Bien que la plupart des sémantiques de l’espace blanc sont couverts par l’indentation appropriée, il ya d’autres choses à considérer.</span><span class="sxs-lookup"><span data-stu-id="79adb-122">Although most semantics from white space are covered by proper indentation, there are some other things to consider.</span></span>

### <a name="formatting-operators-in-arithmetic-expressions"></a><span data-ttu-id="79adb-123">Formater les opérateurs dans les expressions arithmétiques</span><span class="sxs-lookup"><span data-stu-id="79adb-123">Formatting operators in arithmetic expressions</span></span>

<span data-ttu-id="79adb-124">Utilisez toujours l’espace blanc autour des expressions arithmétiques binaires :</span><span class="sxs-lookup"><span data-stu-id="79adb-124">Always use white space around binary arithmetic expressions:</span></span>

```fsharp
let subtractThenAdd x = x - 1 + 3
```

<span data-ttu-id="79adb-125">Les `-` opérateurs non anistes doivent toujours être immédiatement suivis par la valeur qu’ils némentent :</span><span class="sxs-lookup"><span data-stu-id="79adb-125">Unary `-` operators should always be immediately followed by the value they are negating:</span></span>

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

<span data-ttu-id="79adb-126">L’ajout d’un `-` caractère d’espace blanc après l’opérateur peut conduire à la confusion pour les autres.</span><span class="sxs-lookup"><span data-stu-id="79adb-126">Adding a white-space character after the `-` operator can lead to confusion for others.</span></span>

<span data-ttu-id="79adb-127">En résumé, il est important de toujours :</span><span class="sxs-lookup"><span data-stu-id="79adb-127">In summary, it's important to always:</span></span>

* <span data-ttu-id="79adb-128">Entourer les opérateurs binaires d’espace blanc</span><span class="sxs-lookup"><span data-stu-id="79adb-128">Surround binary operators with white space</span></span>
* <span data-ttu-id="79adb-129">N’ont jamais d’espace blanc de fuite après un opérateur unary</span><span class="sxs-lookup"><span data-stu-id="79adb-129">Never have trailing white space after a unary operator</span></span>

<span data-ttu-id="79adb-130">La ligne directrice de l’opérateur arithmétique binaire est particulièrement importante.</span><span class="sxs-lookup"><span data-stu-id="79adb-130">The binary arithmetic operator guideline is especially important.</span></span> <span data-ttu-id="79adb-131">Ne pas entourer un opérateur binaire, `-` lorsqu’il est combiné avec certains `-`choix de formatage, pourrait conduire à l’interpréter comme un unary .</span><span class="sxs-lookup"><span data-stu-id="79adb-131">Failing to surround a binary `-` operator, when combined with certain formatting choices, could lead to interpreting it as a unary `-`.</span></span>

### <a name="surround-a-custom-operator-definition-with-white-space"></a><span data-ttu-id="79adb-132">Entourez une définition d’opérateur personnalisé avec l’espace blanc</span><span class="sxs-lookup"><span data-stu-id="79adb-132">Surround a custom operator definition with white space</span></span>

<span data-ttu-id="79adb-133">Utilisez toujours l’espace blanc pour entourer une définition de l’opérateur :</span><span class="sxs-lookup"><span data-stu-id="79adb-133">Always use white space to surround an operator definition:</span></span>

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

<span data-ttu-id="79adb-134">Pour tout opérateur personnalisé `*` qui commence par et qui a plus d’un caractère, vous devez ajouter un espace blanc au début de la définition pour éviter une ambiguïté compilateur.</span><span class="sxs-lookup"><span data-stu-id="79adb-134">For any custom operator that starts with `*` and that has more than one character, you need to add a white space to the beginning of the definition to avoid a compiler ambiguity.</span></span> <span data-ttu-id="79adb-135">Pour cette raison, nous vous recommandons tout simplement d’entourer les définitions de tous les opérateurs avec un seul caractère d’espace blanc.</span><span class="sxs-lookup"><span data-stu-id="79adb-135">Because of this, we recommend that you simply surround the definitions of all operators with a single white-space character.</span></span>

### <a name="surround-function-parameter-arrows-with-white-space"></a><span data-ttu-id="79adb-136">Entourer les flèches de paramètres de fonction avec l’espace blanc</span><span class="sxs-lookup"><span data-stu-id="79adb-136">Surround function parameter arrows with white space</span></span>

<span data-ttu-id="79adb-137">Lors de la définition de la signature `->` d’une fonction, utilisez l’espace blanc autour du symbole :</span><span class="sxs-lookup"><span data-stu-id="79adb-137">When defining the signature of a function, use white space around the `->` symbol:</span></span>

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a><span data-ttu-id="79adb-138">Entourer les arguments de fonction avec l’espace blanc</span><span class="sxs-lookup"><span data-stu-id="79adb-138">Surround function arguments with white space</span></span>

<span data-ttu-id="79adb-139">Lors de la définition d’une fonction, utilisez l’espace blanc autour de chaque argument.</span><span class="sxs-lookup"><span data-stu-id="79adb-139">When defining a function, use white space around each argument.</span></span>

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="place-parameters-on-a-new-line-for-long-member-definitions"></a><span data-ttu-id="79adb-140">Placez les paramètres sur une nouvelle ligne pour les définitions de membres longs</span><span class="sxs-lookup"><span data-stu-id="79adb-140">Place parameters on a new line for long member definitions</span></span>

<span data-ttu-id="79adb-141">Si vous avez une définition de membre très longue, placez les paramètres sur de nouvelles lignes et en indent une portée.</span><span class="sxs-lookup"><span data-stu-id="79adb-141">If you have a very long member definition, place the parameters on new lines and indent them one scope.</span></span>

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(
        aVeryLongType: AVeryLongTypeThatYouNeedToUse
        aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
        aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
        // ... the body of the method follows
```

<span data-ttu-id="79adb-142">Cela s’applique également aux constructeurs :</span><span class="sxs-lookup"><span data-stu-id="79adb-142">This also applies to constructors:</span></span>

```fsharp
type C(
    aVeryLongType: AVeryLongTypeThatYouNeedToUse
    aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
    aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
    // ... the body of the class follows
```

### <a name="type-annotations"></a><span data-ttu-id="79adb-143">Annotations de type</span><span class="sxs-lookup"><span data-stu-id="79adb-143">Type annotations</span></span>

#### <a name="right-pad-function-argument-type-annotations"></a><span data-ttu-id="79adb-144">Annotations de type d’argument de fonction de fonction de right-pad</span><span class="sxs-lookup"><span data-stu-id="79adb-144">Right-pad function argument type annotations</span></span>

<span data-ttu-id="79adb-145">Lors de la définition des arguments avec des `:` annotations de type, utilisez l’espace blanc après le symbole:</span><span class="sxs-lookup"><span data-stu-id="79adb-145">When defining arguments with type annotations, use white space after the `:` symbol:</span></span>

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a><span data-ttu-id="79adb-146">Annotations de type retour surround avec l’espace blanc</span><span class="sxs-lookup"><span data-stu-id="79adb-146">Surround return type annotations with white space</span></span>

<span data-ttu-id="79adb-147">Dans une fonction let-lié ou une annotation de type de valeur (type `:` de retour dans le cas d’une fonction), utilisez l’espace blanc avant et après le symbole :</span><span class="sxs-lookup"><span data-stu-id="79adb-147">In a let-bound function or value type annotation (return type in the case of a function), use white space before and after the `:` symbol:</span></span>

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="79adb-148">Formater les lignes blanches</span><span class="sxs-lookup"><span data-stu-id="79adb-148">Formatting blank lines</span></span>

* <span data-ttu-id="79adb-149">Séparez les définitions de fonction et de classe de haut niveau avec deux lignes blanches.</span><span class="sxs-lookup"><span data-stu-id="79adb-149">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="79adb-150">Les définitions de méthode à l’intérieur d’une classe sont séparées par une seule ligne blanche.</span><span class="sxs-lookup"><span data-stu-id="79adb-150">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="79adb-151">Des lignes blanches supplémentaires peuvent être utilisées (avec parcimonie) pour séparer les groupes de fonctions connexes.</span><span class="sxs-lookup"><span data-stu-id="79adb-151">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="79adb-152">Des lignes blanches peuvent être omises entre un groupe d’une ligne (par exemple, un ensemble d’implémentations factices).</span><span class="sxs-lookup"><span data-stu-id="79adb-152">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="79adb-153">Utilisez des lignes blanches dans les fonctions, avec parcimonie, pour indiquer les sections logiques.</span><span class="sxs-lookup"><span data-stu-id="79adb-153">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="79adb-154">Formater les commentaires</span><span class="sxs-lookup"><span data-stu-id="79adb-154">Formatting comments</span></span>

<span data-ttu-id="79adb-155">Généralement préfèrent plusieurs commentaires à double slash sur ml-style commentaires bloc.</span><span class="sxs-lookup"><span data-stu-id="79adb-155">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="79adb-156">Les commentaires inline devraient capitaliser la première lettre.</span><span class="sxs-lookup"><span data-stu-id="79adb-156">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="79adb-157">Conventions d'attribution d'un nom</span><span class="sxs-lookup"><span data-stu-id="79adb-157">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="79adb-158">Utilisez camelCase pour les valeurs et les fonctions liées à la classe, liées à l’expression et liées aux motifs</span><span class="sxs-lookup"><span data-stu-id="79adb-158">Use camelCase for class-bound, expression-bound, and pattern-bound values and functions</span></span>

<span data-ttu-id="79adb-159">Il est commun et accepté de style F ' d’utiliser camelCase pour tous les noms liés comme des variables locales ou dans les correspondances de modèle et les définitions de fonction.</span><span class="sxs-lookup"><span data-stu-id="79adb-159">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="79adb-160">Les fonctions liées localement dans les classes devraient également utiliser camelCase.</span><span class="sxs-lookup"><span data-stu-id="79adb-160">Locally bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="79adb-161">Utilisez camelCase pour des fonctions publiques liées au module</span><span class="sxs-lookup"><span data-stu-id="79adb-161">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="79adb-162">Lorsqu’une fonction reliée par un module fait partie d’une API publique, elle doit utiliser camelCase :</span><span class="sxs-lookup"><span data-stu-id="79adb-162">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="79adb-163">Utilisez camelCase pour des valeurs et des fonctions internes et privées liées au module</span><span class="sxs-lookup"><span data-stu-id="79adb-163">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="79adb-164">Utilisez camelCase pour des valeurs privées liées au module, y compris les suivantes :</span><span class="sxs-lookup"><span data-stu-id="79adb-164">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="79adb-165">Fonctions ad hoc dans les scripts</span><span class="sxs-lookup"><span data-stu-id="79adb-165">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="79adb-166">Valeurs constituant la mise en œuvre interne d’un module ou d’un type</span><span class="sxs-lookup"><span data-stu-id="79adb-166">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="79adb-167">Utilisez camelCase pour les paramètres</span><span class="sxs-lookup"><span data-stu-id="79adb-167">Use camelCase for parameters</span></span>

<span data-ttu-id="79adb-168">Tous les paramètres doivent utiliser camelCase conformément aux conventions de nommage .NET.</span><span class="sxs-lookup"><span data-stu-id="79adb-168">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="79adb-169">Utilisez PascalCase pour les modules</span><span class="sxs-lookup"><span data-stu-id="79adb-169">Use PascalCase for modules</span></span>

<span data-ttu-id="79adb-170">Tous les modules (haut niveau, interne, privé, imbriqué) doivent utiliser PascalCase.</span><span class="sxs-lookup"><span data-stu-id="79adb-170">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="79adb-171">Utilisez PascalCase pour les déclarations de type, les membres et les étiquettes</span><span class="sxs-lookup"><span data-stu-id="79adb-171">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="79adb-172">Les classes, les interfaces, les structs, les recensements, les délégués, les dossiers et les syndicats discriminés devraient tous être nommés avec PascalCase.</span><span class="sxs-lookup"><span data-stu-id="79adb-172">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="79adb-173">Les membres des types et des étiquettes pour les documents et les syndicats discriminés devraient également utiliser PascalCase.</span><span class="sxs-lookup"><span data-stu-id="79adb-173">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

```fsharp
type IMyInterface =
    abstract Something: int

type MyClass() =
    member this.MyMethod(x, y) = x + y

type MyRecord = { IntVal: int; StringVal: string }

type SchoolPerson =
    | Professor
    | Student
    | Advisor
    | Administrator
```

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="79adb-174">Utilisez PascalCase pour des constructions intrinsèques à .NET</span><span class="sxs-lookup"><span data-stu-id="79adb-174">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="79adb-175">Les espaces de noms, les`.dll` exceptions, les événements et les noms de projets/noms devraient également utiliser PascalCase.</span><span class="sxs-lookup"><span data-stu-id="79adb-175">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="79adb-176">Non seulement cela rend la consommation d’autres langues .NET se sentent plus naturels pour les consommateurs, il est également compatible avec les conventions de nommage .NET que vous êtes susceptible de rencontrer.</span><span class="sxs-lookup"><span data-stu-id="79adb-176">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="79adb-177">Éviter les souligne dans les noms</span><span class="sxs-lookup"><span data-stu-id="79adb-177">Avoid underscores in names</span></span>

<span data-ttu-id="79adb-178">Historiquement, certaines bibliothèques de F ont utilisé des soulignements dans les noms.</span><span class="sxs-lookup"><span data-stu-id="79adb-178">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="79adb-179">Cependant, ce n’est plus largement accepté, en partie parce qu’il se heurte à des conventions de nommage .NET.</span><span class="sxs-lookup"><span data-stu-id="79adb-179">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="79adb-180">Cela dit, certains programmeurs de F’emploient des souligne fortement, en partie pour des raisons historiques, et la tolérance et le respect sont importants.</span><span class="sxs-lookup"><span data-stu-id="79adb-180">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="79adb-181">Cependant, sachez que le style est souvent détesté par d’autres qui ont le choix de l’utiliser ou non.</span><span class="sxs-lookup"><span data-stu-id="79adb-181">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="79adb-182">Une exception comprend l’interopération avec les composants autochtones, où les soulignements sont communs.</span><span class="sxs-lookup"><span data-stu-id="79adb-182">One exception includes interoperating with native components, where underscores are common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="79adb-183">Utiliser des opérateurs FMD standard</span><span class="sxs-lookup"><span data-stu-id="79adb-183">Use standard F# operators</span></span>

<span data-ttu-id="79adb-184">Les opérateurs suivants sont définis dans la bibliothèque standard de F et doivent être utilisés au lieu de définir des équivalents.</span><span class="sxs-lookup"><span data-stu-id="79adb-184">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="79adb-185">L’utilisation de ces opérateurs est recommandée car elle tend à rendre le code plus lisible et idiomatique.</span><span class="sxs-lookup"><span data-stu-id="79adb-185">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="79adb-186">Les développeurs ayant une formation en OCaml ou dans d’autres langages de programmation fonctionnel peuvent être habitués à différents idiomes.</span><span class="sxs-lookup"><span data-stu-id="79adb-186">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="79adb-187">La liste suivante résume les opérateurs de FMD recommandés.</span><span class="sxs-lookup"><span data-stu-id="79adb-187">The following list summarizes the recommended F# operators.</span></span>

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Discard away a value
x + y // Overloaded addition (including string concatenation)
x - y // Overloaded subtraction
x * y // Overloaded multiplication
x / y // Overloaded division
x % y // Overloaded modulus
x && y // Lazy/short-cut "and"
x || y // Lazy/short-cut "or"
x <<< y // Bitwise left shift
x >>> y // Bitwise right shift
x ||| y // Bitwise or, also for working with “flags” enumeration
x &&& y // Bitwise and, also for working with “flags” enumeration
x ^^^ y // Bitwise xor, also for working with “flags” enumeration
```

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="79adb-188">Utilisez la syntaxe préfixe pour les génériques (`Foo<T>`) de préférence à la syntaxe postfixe (`T Foo`)</span><span class="sxs-lookup"><span data-stu-id="79adb-188">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="79adb-189">F ' hérite à la fois du style postfix ML de nommer les types génériques (par exemple, `int list`) ainsi que le style préfixe .NET (par exemple, `list<int>`).</span><span class="sxs-lookup"><span data-stu-id="79adb-189">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="79adb-190">Préférez le style .NET, à l’exception de cinq types spécifiques:</span><span class="sxs-lookup"><span data-stu-id="79adb-190">Prefer the .NET style, except for five specific types:</span></span>

1. <span data-ttu-id="79adb-191">Pour les listes de F, `int list` utilisez `list<int>`le formulaire postfix : plutôt que .</span><span class="sxs-lookup"><span data-stu-id="79adb-191">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="79adb-192">Pour les options F, utilisez `int option` le `option<int>`formulaire postfixe : plutôt que .</span><span class="sxs-lookup"><span data-stu-id="79adb-192">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="79adb-193">Pour les options de valeur F, `int voption` utilisez `voption<int>`le formulaire postfix : plutôt que .</span><span class="sxs-lookup"><span data-stu-id="79adb-193">For F# Value Options, use the postfix form: `int voption` rather than `voption<int>`.</span></span>
4. <span data-ttu-id="79adb-194">Pour les tableaux de F, utilisez `int[]` le `int array` `array<int>`nom syntaxique plutôt que ou .</span><span class="sxs-lookup"><span data-stu-id="79adb-194">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
5. <span data-ttu-id="79adb-195">Pour les cellules `int ref` de `ref<int>` `Ref<int>`référence, utilisez plutôt que ou .</span><span class="sxs-lookup"><span data-stu-id="79adb-195">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="79adb-196">Pour tous les autres types, utilisez le formulaire de préfixe.</span><span class="sxs-lookup"><span data-stu-id="79adb-196">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="79adb-197">Formatage tuples</span><span class="sxs-lookup"><span data-stu-id="79adb-197">Formatting tuples</span></span>

<span data-ttu-id="79adb-198">Une instantanéie de tuple devrait être parenthèse, et les virgules délimitantes à `(1, 2)`l’intérieur devraient être suivies d’un seul espace, par exemple: , `(x, y, z)`.</span><span class="sxs-lookup"><span data-stu-id="79adb-198">A tuple instantiation should be parenthesized, and the delimiting commas within it should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="79adb-199">Il est communément admis d’omettre les parenthèses dans l’appariement des modèles de tuples :</span><span class="sxs-lookup"><span data-stu-id="79adb-199">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

<span data-ttu-id="79adb-200">Il est également communément admis d’omettre les parenthèses si le tuple est la valeur de retour d’une fonction :</span><span class="sxs-lookup"><span data-stu-id="79adb-200">It is also commonly accepted to omit parentheses if the tuple is the return value of a function:</span></span>

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

<span data-ttu-id="79adb-201">En résumé, préférez les instantanéiations de tuple entre parenthèses, mais lorsque vous utilisez des tuples pour l’appariement des motifs ou une valeur de retour, il est considéré comme très bien d’éviter les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="79adb-201">In summary, prefer parenthesized tuple instantiations, but when using tuples for pattern matching or a return value, it is considered fine to avoid parentheses.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="79adb-202">Formater les déclarations syndicales discriminatoires</span><span class="sxs-lookup"><span data-stu-id="79adb-202">Formatting discriminated union declarations</span></span>

<span data-ttu-id="79adb-203">Définition `|` de type indent par quatre espaces :</span><span class="sxs-lookup"><span data-stu-id="79adb-203">Indent `|` in type definition by four spaces:</span></span>

```fsharp
// OK
type Volume =
    | Liter of float
    | FluidOunce of float
    | ImperialPint of float

// Not OK
type Volume =
| Liter of float
| USPint of float
| ImperialPint of float
```

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="79adb-204">Formater les syndicats discriminés</span><span class="sxs-lookup"><span data-stu-id="79adb-204">Formatting discriminated unions</span></span>

<span data-ttu-id="79adb-205">Les unions discriminées instantanées qui se divisent entre plusieurs lignes devraient donner aux données contenues une nouvelle portée avec l’indentation :</span><span class="sxs-lookup"><span data-stu-id="79adb-205">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="79adb-206">La parenthèse de clôture peut également être sur une nouvelle ligne :</span><span class="sxs-lookup"><span data-stu-id="79adb-206">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="79adb-207">Formater les déclarations d’enregistrement</span><span class="sxs-lookup"><span data-stu-id="79adb-207">Formatting record declarations</span></span>

<span data-ttu-id="79adb-208">Indent `{` dans la définition de type par quatre espaces et commencer la liste de champ sur la même ligne:</span><span class="sxs-lookup"><span data-stu-id="79adb-208">Indent `{` in type definition by four spaces and start the field list on the same line:</span></span>

```fsharp
// OK
type PostalAddress =
    { Address: string
      City: string
      Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Not OK
type PostalAddress =
  { Address: string
    City: string
    Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Unusual in F#
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
```

<span data-ttu-id="79adb-209">Placer le jeton d’ouverture sur une nouvelle ligne et le jeton de clôture sur une nouvelle ligne est préférable si vous déclarez les implémentations d’interface ou les membres sur le dossier:</span><span class="sxs-lookup"><span data-stu-id="79adb-209">Placing the opening token on a new line and the closing token on a new line is preferable if you are declaring interface implementations or members on the record:</span></span>

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a><span data-ttu-id="79adb-210">Formatage des enregistrements</span><span class="sxs-lookup"><span data-stu-id="79adb-210">Formatting records</span></span>

<span data-ttu-id="79adb-211">Les enregistrements courts peuvent être écrits en une seule ligne :</span><span class="sxs-lookup"><span data-stu-id="79adb-211">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="79adb-212">Les enregistrements plus longs devraient utiliser de nouvelles lignes pour les étiquettes :</span><span class="sxs-lookup"><span data-stu-id="79adb-212">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="79adb-213">Placer le jeton d’ouverture sur une nouvelle ligne, le contenu tabbed sur une portée, et le jeton de clôture sur une nouvelle ligne est préférable si vous êtes:</span><span class="sxs-lookup"><span data-stu-id="79adb-213">Placing the opening token on a new line, the contents tabbed over one scope, and the closing token on a new line is preferable if you are:</span></span>

* <span data-ttu-id="79adb-214">Déplacer les enregistrements dans le code avec différentes portées d’indentation</span><span class="sxs-lookup"><span data-stu-id="79adb-214">Moving records around in code with different indentation scopes</span></span>
* <span data-ttu-id="79adb-215">Les jeter dans une fonction</span><span class="sxs-lookup"><span data-stu-id="79adb-215">Piping them into a function</span></span>

```fsharp
let rainbow =
    {
        Boss1 = "Jeffrey"
        Boss2 = "Jeffrey"
        Boss3 = "Jeffrey"
        Boss4 = "Jeffrey"
        Boss5 = "Jeffrey"
        Boss6 = "Jeffrey"
        Boss7 = "Jeffrey"
        Boss8 = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"]
    }

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface

let foo a =
    a
    |> Option.map (fun x ->
        {
            MyField = x
        })
```

<span data-ttu-id="79adb-216">Les mêmes règles s’appliquent pour les éléments de liste et de tableau.</span><span class="sxs-lookup"><span data-stu-id="79adb-216">The same rules apply for list and array elements.</span></span>

## <a name="formatting-copy-and-update-record-expressions"></a><span data-ttu-id="79adb-217">Formater les expressions d’enregistrement de copie et de mise à jour</span><span class="sxs-lookup"><span data-stu-id="79adb-217">Formatting copy-and-update record expressions</span></span>

<span data-ttu-id="79adb-218">Une expression d’enregistrement de copie et de mise à jour est toujours un enregistrement, de sorte que des lignes directrices similaires s’appliquent.</span><span class="sxs-lookup"><span data-stu-id="79adb-218">A copy-and-update record expression is still a record, so similar guidelines apply.</span></span>

<span data-ttu-id="79adb-219">Les expressions courtes peuvent s’adapter sur une seule ligne :</span><span class="sxs-lookup"><span data-stu-id="79adb-219">Short expressions can fit on one line:</span></span>

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

<span data-ttu-id="79adb-220">Les expressions plus longues devraient utiliser de nouvelles lignes :</span><span class="sxs-lookup"><span data-stu-id="79adb-220">Longer expressions should use new lines:</span></span>

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="79adb-221">Et comme avec les conseils d’enregistrement, vous pouvez consacrer des lignes séparées pour les accolades et en retrait une portée à droite avec l’expression.</span><span class="sxs-lookup"><span data-stu-id="79adb-221">And as with the record guidance, you may want to dedicate separate lines for the braces and indent one scope to the right with the expression.</span></span> <span data-ttu-id="79adb-222">Dans certains cas particuliers, comme l’emballage d’une valeur avec une option sans parenthèses, vous devrez peut-être garder une accolade sur une seule ligne :</span><span class="sxs-lookup"><span data-stu-id="79adb-222">In some special cases, such as wrapping a value with an optional without parentheses, you may need to keep a brace on one line:</span></span>

```fsharp
type S = { F1: int; F2: string }
type State = { F:  S option }

let state = { F = Some { F1 = 1; F2 = "Hello" } }
let newState =
    {
        state with
            F = Some {
                    F1 = 0
                    F2 = ""
                }
    }
```

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="79adb-223">Classement des listes et des tableaux</span><span class="sxs-lookup"><span data-stu-id="79adb-223">Formatting lists and arrays</span></span>

<span data-ttu-id="79adb-224">Écrivez `x :: l` avec `::` des`::` espaces autour de l’opérateur (est un opérateur infix, donc entouré d’espaces).</span><span class="sxs-lookup"><span data-stu-id="79adb-224">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces).</span></span>

<span data-ttu-id="79adb-225">Liste et tableaux déclarés sur une seule ligne doivent avoir un espace après le support d’ouverture et avant le support de clôture:</span><span class="sxs-lookup"><span data-stu-id="79adb-225">List and arrays declared on a single line should have a space after the opening bracket and before the closing bracket:</span></span>

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

<span data-ttu-id="79adb-226">Utilisez toujours au moins un espace entre deux opérateurs distincts ressemblant à des accolades.</span><span class="sxs-lookup"><span data-stu-id="79adb-226">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="79adb-227">Par exemple, laissez un `[` espace `{`entre un et un .</span><span class="sxs-lookup"><span data-stu-id="79adb-227">For example, leave a space between a `[` and a `{`.</span></span>

```fsharp
// OK
[ { IngredientName = "Green beans"; Quantity = 250 }
  { IngredientName = "Pine nuts"; Quantity = 250 }
  { IngredientName = "Feta cheese"; Quantity = 250 }
  { IngredientName = "Olive oil"; Quantity = 10 }
  { IngredientName = "Lemon"; Quantity = 1 } ]

// Not OK
[{ IngredientName = "Green beans"; Quantity = 250 }
 { IngredientName = "Pine nuts"; Quantity = 250 }
 { IngredientName = "Feta cheese"; Quantity = 250 }
 { IngredientName = "Olive oil"; Quantity = 10 }
 { IngredientName = "Lemon"; Quantity = 1 }]
```

<span data-ttu-id="79adb-228">La même ligne directrice s’applique aux listes ou aux tableaux de tuples.</span><span class="sxs-lookup"><span data-stu-id="79adb-228">The same guideline applies for lists or arrays of tuples.</span></span>

<span data-ttu-id="79adb-229">Les listes et les tableaux qui se divisent entre plusieurs lignes suivent une règle similaire comme le font les enregistrements :</span><span class="sxs-lookup"><span data-stu-id="79adb-229">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

```fsharp
let pascalsTriangle =
    [|
        [| 1 |]
        [| 1; 1 |]
        [| 1; 2; 1 |]
        [| 1; 3; 3; 1 |]
        [| 1; 4; 6; 4; 1 |]
        [| 1; 5; 10; 10; 5; 1 |]
        [| 1; 6; 15; 20; 15; 6; 1 |]
        [| 1; 7; 21; 35; 35; 21; 7; 1 |]
        [| 1; 8; 28; 56; 70; 56; 28; 8; 1 |]
    |]
```

<span data-ttu-id="79adb-230">Et comme avec les dossiers, déclarer les supports d’ouverture et de fermeture sur leur propre ligne rendra le code de déplacement autour et la tuyauterie dans les fonctions plus facile.</span><span class="sxs-lookup"><span data-stu-id="79adb-230">And as with records, declaring the opening and closing brackets on their own line will make moving code around and piping into functions easier.</span></span>

<span data-ttu-id="79adb-231">Lorsque vous généez des tableaux `->` `do ... yield` et des listes programmatiquement, préférez-vous lorsque une valeur est toujours générée :</span><span class="sxs-lookup"><span data-stu-id="79adb-231">When generating arrays and lists programmatically, prefer `->` over `do ... yield` when a value is always generated:</span></span>

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x*x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x*x ]
```

<span data-ttu-id="79adb-232">Les anciennes versions de la `yield` langue F requises spécifiant dans les situations où les données peuvent être générées sous condition, ou il peut y avoir des expressions consécutives à évaluer.</span><span class="sxs-lookup"><span data-stu-id="79adb-232">Older versions of the F# language required specifying `yield` in situations where data may be generated conditionally, or there may be consecutive expressions to be evaluated.</span></span> <span data-ttu-id="79adb-233">Préférez omettre `yield` ces mots clés à moins que vous ne devez compiler avec une ancienne version linguistique de F :</span><span class="sxs-lookup"><span data-stu-id="79adb-233">Prefer omitting these `yield` keywords unless you must compile with an older F# language version:</span></span>

```fsharp
// Preferred
let daysOfWeek includeWeekend =
    [
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    ]

// Not preferred
let daysOfWeek' includeWeekend =
    [
        yield "Monday"
        yield "Tuesday"
        yield "Wednesday"
        yield "Thursday"
        yield "Friday"
        if includeWeekend then
            yield "Saturday"
            yield "Sunday"
    ]
```

<span data-ttu-id="79adb-234">Dans certains `do...yield` cas, peut aider à la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="79adb-234">In some cases, `do...yield` may aid in readability.</span></span> <span data-ttu-id="79adb-235">Ces cas, bien que subjectifs, doivent être pris en considération.</span><span class="sxs-lookup"><span data-stu-id="79adb-235">These cases, though subjective, should be taken into consideration.</span></span>

## <a name="formatting-if-expressions"></a><span data-ttu-id="79adb-236">Formatage si expressions</span><span class="sxs-lookup"><span data-stu-id="79adb-236">Formatting if expressions</span></span>

<span data-ttu-id="79adb-237">L’indentation des conditionnels dépend de la taille des expressions qui les composent.</span><span class="sxs-lookup"><span data-stu-id="79adb-237">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="79adb-238">Si `cond` `e1` , `e2` et sont courts, il suffit de les écrire sur une ligne:</span><span class="sxs-lookup"><span data-stu-id="79adb-238">If `cond`, `e1` and `e2` are short, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="79adb-239">Si `cond`l’un ou l’autre, `e1` ou `e2` sont plus longs, mais pas multi-lignes:</span><span class="sxs-lookup"><span data-stu-id="79adb-239">If either `cond`, `e1` or `e2` are longer, but not multi-line:</span></span>

```fsharp
if cond
then e1
else e2
```

<span data-ttu-id="79adb-240">Si l’une des expressions sont multi-lignes:</span><span class="sxs-lookup"><span data-stu-id="79adb-240">If any of the expressions are multi-line:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="79adb-241">Plusieurs conditionnels avec `elif` et `else` sont en retrait `if`à la même portée que le :</span><span class="sxs-lookup"><span data-stu-id="79adb-241">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="79adb-242">Constructions assorties de modèles</span><span class="sxs-lookup"><span data-stu-id="79adb-242">Pattern matching constructs</span></span>

<span data-ttu-id="79adb-243">Utilisez `|` un pour chaque clause d’un match sans indentation.</span><span class="sxs-lookup"><span data-stu-id="79adb-243">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="79adb-244">Si l’expression est courte, vous pouvez envisager d’utiliser une seule ligne si chaque sous-expression est également simple.</span><span class="sxs-lookup"><span data-stu-id="79adb-244">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> x
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> x
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

<span data-ttu-id="79adb-245">Si l’expression à droite de la flèche assortie du motif est trop grande, `match` / `|`déplacez-la à la ligne suivante, en retrait à un pas de la .</span><span class="sxs-lookup"><span data-stu-id="79adb-245">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="79adb-246">L’appariement des motifs des fonctions anonymes, à partir `function`de , ne devrait généralement pas s’en prendre trop loin.</span><span class="sxs-lookup"><span data-stu-id="79adb-246">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="79adb-247">Par exemple, l’indentage d’une portée comme suit est très bien :</span><span class="sxs-lookup"><span data-stu-id="79adb-247">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="79adb-248">L’appariement des `let` `let rec` motifs dans les fonctions `let`définies `function` par ou doit être en retrait quatre espaces après le début de , même si le mot clé est utilisé:</span><span class="sxs-lookup"><span data-stu-id="79adb-248">Pattern matching in functions defined by `let` or `let rec` should be indented four spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="79adb-249">Nous ne recommandons pas d’aligner les flèches.</span><span class="sxs-lookup"><span data-stu-id="79adb-249">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="79adb-250">Formater l’essai/avec des expressions</span><span class="sxs-lookup"><span data-stu-id="79adb-250">Formatting try/with expressions</span></span>

<span data-ttu-id="79adb-251">L’appariement des modèles sur le type `with`d’exception doit être en retrait au même niveau que .</span><span class="sxs-lookup"><span data-stu-id="79adb-251">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

```fsharp
try
    if System.DateTime.Now.Second % 3 = 0 then
        raise (new System.Exception())
    else
        raise (new System.ApplicationException())
with
| :? System.ApplicationException ->
    printfn "A second that was not a multiple of 3"
| _ ->
    printfn "A second that was a multiple of 3"
```

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="79adb-252">Application de paramètre de fonction de formatage</span><span class="sxs-lookup"><span data-stu-id="79adb-252">Formatting function parameter application</span></span>

<span data-ttu-id="79adb-253">En général, la plupart des applications de paramètres de fonction se font sur la même ligne.</span><span class="sxs-lookup"><span data-stu-id="79adb-253">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="79adb-254">Si vous souhaitez appliquer des paramètres à une fonction sur une nouvelle ligne, en indent par une portée.</span><span class="sxs-lookup"><span data-stu-id="79adb-254">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

```fsharp
// OK
sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
sprintf
     "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
let printVolumes x =
    printf "Volume in liters = %f, in us pints = %f, in imperial = %f"
        (convertVolumeToLiter x)
        (convertVolumeUSPint x)
        (convertVolumeImperialPint x)
```

<span data-ttu-id="79adb-255">Les mêmes lignes directrices s’appliquent pour les expressions lambda que les arguments de fonction.</span><span class="sxs-lookup"><span data-stu-id="79adb-255">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="79adb-256">Si le corps d’une expression lambda, le corps peut avoir une autre ligne, en retrait par une portée</span><span class="sxs-lookup"><span data-stu-id="79adb-256">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

```fsharp
let printListWithOffset a list1 =
    List.iter
        (fun elem -> printfn "%d" (a + elem))
        list1

// OK if lambda body is long enough
let printListWithOffset a list1 =
    List.iter
        (fun elem ->
            printfn "%d" (a + elem))
        list1
```

<span data-ttu-id="79adb-257">Cependant, si le corps d’une expression lambda est plus d’une ligne, envisager de l’affacturage dans une fonction distincte plutôt que d’avoir une construction multi-lignes appliquée comme un seul argument à une fonction.</span><span class="sxs-lookup"><span data-stu-id="79adb-257">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="79adb-258">Formater les opérateurs d’infixe</span><span class="sxs-lookup"><span data-stu-id="79adb-258">Formatting infix operators</span></span>

<span data-ttu-id="79adb-259">Séparer les opérateurs par espaces.</span><span class="sxs-lookup"><span data-stu-id="79adb-259">Separate operators by spaces.</span></span> <span data-ttu-id="79adb-260">Les exceptions évidentes `!` à `.` cette règle sont les opérateurs et les opérateurs.</span><span class="sxs-lookup"><span data-stu-id="79adb-260">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="79adb-261">Les expressions Infix sont OK pour lineup sur la même colonne:</span><span class="sxs-lookup"><span data-stu-id="79adb-261">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="79adb-262">Formater les exploitants de pipelines</span><span class="sxs-lookup"><span data-stu-id="79adb-262">Formatting pipeline operators</span></span>

<span data-ttu-id="79adb-263">Les `|>` exploitants de pipelines devraient passer sous les expressions sur laquelle ils opèrent.</span><span class="sxs-lookup"><span data-stu-id="79adb-263">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

```fsharp
// Preferred approach
let methods2 =
    System.AppDomain.CurrentDomain.GetAssemblies()
    |> List.ofArray
    |> List.map (fun assm -> assm.GetTypes())
    |> Array.concat
    |> List.ofArray
    |> List.map (fun t -> t.GetMethods())
    |> Array.concat

// Not OK
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
            |> List.ofArray
            |> List.map (fun assm -> assm.GetTypes())
            |> Array.concat
            |> List.ofArray
            |> List.map (fun t -> t.GetMethods())
            |> Array.concat
```

### <a name="formatting-modules"></a><span data-ttu-id="79adb-264">Modules de formatage</span><span class="sxs-lookup"><span data-stu-id="79adb-264">Formatting modules</span></span>

<span data-ttu-id="79adb-265">Le code d’un module local doit être en retrait par rapport au module, mais le code d’un module de haut niveau ne doit pas être en retrait.</span><span class="sxs-lookup"><span data-stu-id="79adb-265">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="79adb-266">Les éléments de l’espace de nom n’ont pas besoin d’être en retrait.</span><span class="sxs-lookup"><span data-stu-id="79adb-266">Namespace elements do not have to be indented.</span></span>

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a*a + b*b

module A2 =
    let function2 a b = a*a - b*b
```

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="79adb-267">Formater les expressions et les interfaces d’objets</span><span class="sxs-lookup"><span data-stu-id="79adb-267">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="79adb-268">Les expressions et interfaces d’objet doivent `member` être alignées de la même manière avec l’en retrait après quatre espaces.</span><span class="sxs-lookup"><span data-stu-id="79adb-268">Object expressions and interfaces should be aligned in the same way with `member` being indented after four spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="79adb-269">Formater l’espace blanc dans les expressions</span><span class="sxs-lookup"><span data-stu-id="79adb-269">Formatting white space in expressions</span></span>

<span data-ttu-id="79adb-270">Évitez l’espace blanc extra-nant dans les expressions F.</span><span class="sxs-lookup"><span data-stu-id="79adb-270">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="79adb-271">Les arguments nommés ne `=`devraient pas non plus avoir d’espace autour de la :</span><span class="sxs-lookup"><span data-stu-id="79adb-271">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a><span data-ttu-id="79adb-272">Formatage des attributs</span><span class="sxs-lookup"><span data-stu-id="79adb-272">Formatting attributes</span></span>

<span data-ttu-id="79adb-273">[Les attributs](../language-reference/attributes.md) sont placés au-dessus d’une construction :</span><span class="sxs-lookup"><span data-stu-id="79adb-273">[Attributes](../language-reference/attributes.md) are placed above a construct:</span></span>

```fsharp
[<SomeAttribute>]
type MyClass() = ...

[<RequireQualifiedAccess>]
module M =
    let f x = x

[<Struct>]
type MyRecord =
    { Label1: int
      Label2: string }
```

### <a name="formatting-attributes-on-parameters"></a><span data-ttu-id="79adb-274">Formatage des attributs sur les paramètres</span><span class="sxs-lookup"><span data-stu-id="79adb-274">Formatting attributes on parameters</span></span>

<span data-ttu-id="79adb-275">Les attributs peuvent également être des endroits sur les paramètres.</span><span class="sxs-lookup"><span data-stu-id="79adb-275">Attributes can also be places on parameters.</span></span> <span data-ttu-id="79adb-276">Dans ce cas, placez-le alors sur la même ligne que le paramètre et avant le nom :</span><span class="sxs-lookup"><span data-stu-id="79adb-276">In this case, place then on the same line as the parameter and before the name:</span></span>

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a><span data-ttu-id="79adb-277">Formater plusieurs attributs</span><span class="sxs-lookup"><span data-stu-id="79adb-277">Formatting multiple attributes</span></span>

<span data-ttu-id="79adb-278">Lorsque plusieurs attributs sont appliqués à une construction qui n’est pas un paramètre, ils doivent être placés de telle sorte qu’il y ait un attribut par ligne :</span><span class="sxs-lookup"><span data-stu-id="79adb-278">When multiple attributes are applied to a construct that is not a parameter, they should be placed such that there is one attribute per line:</span></span>

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="79adb-279">Lorsqu’ils sont appliqués à un paramètre, `;` ils doivent être sur la même ligne et séparés par un séparateur.</span><span class="sxs-lookup"><span data-stu-id="79adb-279">When applied to a parameter, they must be on the same line and separated by a `;` separator.</span></span>

## <a name="formatting-literals"></a><span data-ttu-id="79adb-280">Formater les littérals</span><span class="sxs-lookup"><span data-stu-id="79adb-280">Formatting literals</span></span>

<span data-ttu-id="79adb-281">[Les littérals](../language-reference/literals.md) `Literal` de F à l’aide de l’attribut doivent placer l’attribut sur sa propre ligne et utiliser PascalCase nommant :</span><span class="sxs-lookup"><span data-stu-id="79adb-281">[F# literals](../language-reference/literals.md) using the `Literal` attribute should place the attribute on its own line and use PascalCase naming:</span></span>

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

<span data-ttu-id="79adb-282">Évitez de placer l’attribut sur la même ligne que la valeur.</span><span class="sxs-lookup"><span data-stu-id="79adb-282">Avoid placing the attribute on the same line as the value.</span></span>
