---
title: Indications de mise en forme du code F#
description: Découvrez les instructions de mise F# en forme du code.
ms.date: 11/04/2019
ms.openlocfilehash: 895c8211731b47bd4c59d762d5806cfc1bfe232d
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089319"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="41eb4-103">Indications de mise en forme du code F#</span><span class="sxs-lookup"><span data-stu-id="41eb4-103">F# code formatting guidelines</span></span>

<span data-ttu-id="41eb4-104">Cet article fournit des instructions sur la façon de mettre en forme votre F# code afin que votre code soit :</span><span class="sxs-lookup"><span data-stu-id="41eb4-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="41eb4-105">Généralement affichées comme plus lisibles</span><span class="sxs-lookup"><span data-stu-id="41eb4-105">Generally viewed as more legible</span></span>
* <span data-ttu-id="41eb4-106">Est conforme aux conventions appliquées par les outils de mise en forme dans Visual Studio et d’autres éditeurs</span><span class="sxs-lookup"><span data-stu-id="41eb4-106">Is in accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="41eb4-107">Similaire à un autre code en ligne</span><span class="sxs-lookup"><span data-stu-id="41eb4-107">Similar to other code online</span></span>

<span data-ttu-id="41eb4-108">Ces instructions sont basées sur [un guide complet sur F# la mise en forme des conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) par [Anh-fumier Phan](https://github.com/dungpa).</span><span class="sxs-lookup"><span data-stu-id="41eb4-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="41eb4-109">Règles générales pour la mise en retrait</span><span class="sxs-lookup"><span data-stu-id="41eb4-109">General rules for indentation</span></span>

<span data-ttu-id="41eb4-110">F#utilise l’espace blanc significatif par défaut.</span><span class="sxs-lookup"><span data-stu-id="41eb4-110">F# uses significant white space by default.</span></span> <span data-ttu-id="41eb4-111">Les instructions suivantes sont destinées à vous aider à jongler avec les défis que cela peut imposer.</span><span class="sxs-lookup"><span data-stu-id="41eb4-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="41eb4-112">Utilisation des espaces</span><span class="sxs-lookup"><span data-stu-id="41eb4-112">Using spaces</span></span>

<span data-ttu-id="41eb4-113">Lorsque la mise en retrait est requise, vous devez utiliser des espaces, et non des tabulations.</span><span class="sxs-lookup"><span data-stu-id="41eb4-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="41eb4-114">Au moins un espace est requis.</span><span class="sxs-lookup"><span data-stu-id="41eb4-114">At least one space is required.</span></span> <span data-ttu-id="41eb4-115">Votre organisation peut créer des normes de codage pour spécifier le nombre d’espaces à utiliser pour la mise en retrait ; deux, trois ou quatre espaces de mise en retrait à chaque niveau où la mise en retrait se produit est typique.</span><span class="sxs-lookup"><span data-stu-id="41eb4-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="41eb4-116">**Nous vous recommandons 4 espaces par retrait.**</span><span class="sxs-lookup"><span data-stu-id="41eb4-116">**We recommend 4 spaces per indentation.**</span></span>

<span data-ttu-id="41eb4-117">Ceci dit, la mise en retrait des programmes est une question subjective.</span><span class="sxs-lookup"><span data-stu-id="41eb4-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="41eb4-118">Les variations sont OK, mais la première règle que vous devez suivre est la *cohérence de la mise en retrait*.</span><span class="sxs-lookup"><span data-stu-id="41eb4-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="41eb4-119">Choisissez un style de mise en retrait généralement accepté et utilisez-le systématiquement tout au long de votre code base.</span><span class="sxs-lookup"><span data-stu-id="41eb4-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-white-space"></a><span data-ttu-id="41eb4-120">Mise en forme des espaces blancs</span><span class="sxs-lookup"><span data-stu-id="41eb4-120">Formatting white space</span></span>

<span data-ttu-id="41eb4-121">F#est sensible à l’espace blanc.</span><span class="sxs-lookup"><span data-stu-id="41eb4-121">F# is white space sensitive.</span></span> <span data-ttu-id="41eb4-122">Bien que la plupart des sémantiques de l’espace blanc soient couvertes par une mise en retrait appropriée, il y a d’autres éléments à prendre en compte.</span><span class="sxs-lookup"><span data-stu-id="41eb4-122">Although most semantics from white space are covered by proper indentation, there are some other things to consider.</span></span>

### <a name="formatting-operators-in-arithmetic-expressions"></a><span data-ttu-id="41eb4-123">Mise en forme des opérateurs dans les expressions arithmétiques</span><span class="sxs-lookup"><span data-stu-id="41eb4-123">Formatting operators in arithmetic expressions</span></span>

<span data-ttu-id="41eb4-124">Utilisez toujours un espace blanc autour des expressions arithmétiques binaires :</span><span class="sxs-lookup"><span data-stu-id="41eb4-124">Always use white space around binary arithmetic expressions:</span></span>

```fsharp
let subtractThenAdd x = x - 1 + 3
```

<span data-ttu-id="41eb4-125">Les opérateurs de `-` unaires doivent toujours avoir la valeur à laquelle ils sont opposés immédiatement :</span><span class="sxs-lookup"><span data-stu-id="41eb4-125">Unary `-` operators should always have the value they are negating immediately follow:</span></span>

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

<span data-ttu-id="41eb4-126">L’ajout d’un espace blanc après l’opérateur `-` peut entraîner des confusions pour d’autres.</span><span class="sxs-lookup"><span data-stu-id="41eb4-126">Adding a white-space character after the `-` operator can lead to confusion for others.</span></span>

<span data-ttu-id="41eb4-127">En résumé, il est important de toujours :</span><span class="sxs-lookup"><span data-stu-id="41eb4-127">In summary, it's important to always:</span></span>

* <span data-ttu-id="41eb4-128">Entourer les opérateurs binaires avec un espace blanc</span><span class="sxs-lookup"><span data-stu-id="41eb4-128">Surround binary operators with white space</span></span>
* <span data-ttu-id="41eb4-129">Ne jamais avoir d’espace blanc de fin après un opérateur unaire</span><span class="sxs-lookup"><span data-stu-id="41eb4-129">Never have trailing white space after a unary operator</span></span>

<span data-ttu-id="41eb4-130">L’indication de l’opérateur arithmétique binaire est particulièrement importante.</span><span class="sxs-lookup"><span data-stu-id="41eb4-130">The binary arithmetic operator guideline is especially important.</span></span> <span data-ttu-id="41eb4-131">L’échec de l’entourage d’un opérateur de `-` binaire, lorsqu’il est associé à certains choix de mise en forme, peut entraîner son interprétation en tant que `-`unaire.</span><span class="sxs-lookup"><span data-stu-id="41eb4-131">Failing to surround a binary `-` operator, when combined with certain formatting choices, could lead to interpreting it as a unary `-`.</span></span>

### <a name="surround-a-custom-operator-definition-with-white-space"></a><span data-ttu-id="41eb4-132">Entourer une définition d’opérateur personnalisée avec un espace blanc</span><span class="sxs-lookup"><span data-stu-id="41eb4-132">Surround a custom operator definition with white space</span></span>

<span data-ttu-id="41eb4-133">Utilisez toujours des espaces blancs pour entourer une définition d’opérateur :</span><span class="sxs-lookup"><span data-stu-id="41eb4-133">Always use white space to surround an operator definition:</span></span>

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

<span data-ttu-id="41eb4-134">Pour tout opérateur personnalisé qui commence par `*` et qui contient plusieurs caractères, vous devez ajouter un espace blanc au début de la définition pour éviter une ambiguïté du compilateur.</span><span class="sxs-lookup"><span data-stu-id="41eb4-134">For any custom operator that starts with `*` and that has more than one character, you need to add a white space to the beginning of the definition to avoid a compiler ambiguity.</span></span> <span data-ttu-id="41eb4-135">Pour cette raison, nous vous recommandons d’entourer simplement les définitions de tous les opérateurs avec un seul espace blanc.</span><span class="sxs-lookup"><span data-stu-id="41eb4-135">Because of this, we recommend that you simply surround the definitions of all operators with a single white-space character.</span></span>

### <a name="surround-function-parameter-arrows-with-white-space"></a><span data-ttu-id="41eb4-136">Placer les flèches de paramètre de fonction avec un espace blanc</span><span class="sxs-lookup"><span data-stu-id="41eb4-136">Surround function parameter arrows with white space</span></span>

<span data-ttu-id="41eb4-137">Lors de la définition de la signature d’une fonction, utilisez un espace blanc autour du symbole de `->` :</span><span class="sxs-lookup"><span data-stu-id="41eb4-137">When defining the signature of a function, use white space around the `->` symbol:</span></span>

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a><span data-ttu-id="41eb4-138">Entourer les arguments de fonction avec un espace blanc</span><span class="sxs-lookup"><span data-stu-id="41eb4-138">Surround function arguments with white space</span></span>

<span data-ttu-id="41eb4-139">Lors de la définition d’une fonction, utilisez un espace blanc autour de chaque argument.</span><span class="sxs-lookup"><span data-stu-id="41eb4-139">When defining a function, use white space around each argument.</span></span>

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="place-parameters-on-a-new-line-for-very-long-member-definitions"></a><span data-ttu-id="41eb4-140">Placer des paramètres sur une nouvelle ligne pour les définitions de membres très longues</span><span class="sxs-lookup"><span data-stu-id="41eb4-140">Place parameters on a new line for very long member definitions</span></span>

<span data-ttu-id="41eb4-141">Si vous avez une définition de membre très longue, placez les paramètres sur de nouvelles lignes et mettez-les en retrait d’une étendue.</span><span class="sxs-lookup"><span data-stu-id="41eb4-141">If you have a very long member definition, place the parameters on new lines and indent them one scope.</span></span>

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(
        aVeryLongType: AVeryLongTypeThatYouNeedToUse
        aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
        aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
        // ... the body of the method follows
```

<span data-ttu-id="41eb4-142">Cela s’applique également aux constructeurs :</span><span class="sxs-lookup"><span data-stu-id="41eb4-142">This also applies to constructors:</span></span>

```fsharp
type C(
    aVeryLongType: AVeryLongTypeThatYouNeedToUse
    aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
    aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
    // ... the body of the class follows
```

### <a name="type-annotations"></a><span data-ttu-id="41eb4-143">Annotations de type</span><span class="sxs-lookup"><span data-stu-id="41eb4-143">Type annotations</span></span>

#### <a name="right-pad-function-argument-type-annotations"></a><span data-ttu-id="41eb4-144">Annotations de type d’argument de fonction de remplissage à droite</span><span class="sxs-lookup"><span data-stu-id="41eb4-144">Right-pad function argument type annotations</span></span>

<span data-ttu-id="41eb4-145">Quand vous définissez des arguments avec des annotations de type, utilisez un espace blanc après le symbole `:` :</span><span class="sxs-lookup"><span data-stu-id="41eb4-145">When defining arguments with type annotations, use white space after the `:` symbol:</span></span>

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a><span data-ttu-id="41eb4-146">Entourer les annotations de type de retour avec des espaces blancs</span><span class="sxs-lookup"><span data-stu-id="41eb4-146">Surround return type annotations with white space</span></span>

<span data-ttu-id="41eb4-147">Dans une fonction ou une annotation de type valeur (type de retour dans le cas d’une fonction), utilisez un espace blanc avant et après le symbole `:` :</span><span class="sxs-lookup"><span data-stu-id="41eb4-147">In a let-bound function or value type annotation (return type in the case of a function), use white space before and after the `:` symbol:</span></span>

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="41eb4-148">Mise en forme des lignes vides</span><span class="sxs-lookup"><span data-stu-id="41eb4-148">Formatting blank lines</span></span>

* <span data-ttu-id="41eb4-149">Séparez les définitions de fonction et de classe de niveau supérieur par deux lignes vides.</span><span class="sxs-lookup"><span data-stu-id="41eb4-149">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="41eb4-150">Les définitions de méthode à l’intérieur d’une classe sont séparées par une seule ligne vide.</span><span class="sxs-lookup"><span data-stu-id="41eb4-150">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="41eb4-151">Des lignes vides supplémentaires peuvent être utilisées (avec modération) pour séparer les groupes de fonctions associées.</span><span class="sxs-lookup"><span data-stu-id="41eb4-151">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="41eb4-152">Des lignes vides peuvent être omises entre une série de lignes associées (par exemple, un ensemble d’implémentations factices).</span><span class="sxs-lookup"><span data-stu-id="41eb4-152">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="41eb4-153">Utilisez des lignes vides dans les fonctions, avec modération, pour indiquer les sections logiques.</span><span class="sxs-lookup"><span data-stu-id="41eb4-153">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="41eb4-154">Mise en forme des commentaires</span><span class="sxs-lookup"><span data-stu-id="41eb4-154">Formatting comments</span></span>

<span data-ttu-id="41eb4-155">Préférez généralement plusieurs commentaires à deux barres obliques par rapport aux commentaires de bloc de type ML.</span><span class="sxs-lookup"><span data-stu-id="41eb4-155">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="41eb4-156">Les commentaires insérés doivent mettre en majuscule la première lettre.</span><span class="sxs-lookup"><span data-stu-id="41eb4-156">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="41eb4-157">Conventions d'attribution d'un nom</span><span class="sxs-lookup"><span data-stu-id="41eb4-157">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="41eb4-158">Utiliser la casse mixte pour les valeurs et les fonctions liées à la classe, liées à une expression et liées à un modèle</span><span class="sxs-lookup"><span data-stu-id="41eb4-158">Use camelCase for class-bound, expression-bound and pattern-bound values and functions</span></span>

<span data-ttu-id="41eb4-159">Il est courant et accepté F# d’utiliser la casse mixte pour tous les noms liés en tant que variables locales ou dans les définitions de fonctions et les correspondances de modèle.</span><span class="sxs-lookup"><span data-stu-id="41eb4-159">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="41eb4-160">Les fonctions liées localement dans les classes doivent également utiliser la casse mixte.</span><span class="sxs-lookup"><span data-stu-id="41eb4-160">Locally-bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="41eb4-161">Utiliser la casse mixte pour les fonctions publiques liées aux modules</span><span class="sxs-lookup"><span data-stu-id="41eb4-161">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="41eb4-162">Quand une fonction liée à un module fait partie d’une API publique, elle doit utiliser la casse mixte :</span><span class="sxs-lookup"><span data-stu-id="41eb4-162">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="41eb4-163">Utilisez la casse mixte pour les valeurs et les fonctions liées aux modules internes et privés</span><span class="sxs-lookup"><span data-stu-id="41eb4-163">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="41eb4-164">Utilisez la casse mixte pour les valeurs à liaison de module privées, y compris les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="41eb4-164">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="41eb4-165">Fonctions ad hoc dans les scripts</span><span class="sxs-lookup"><span data-stu-id="41eb4-165">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="41eb4-166">Valeurs constituant l’implémentation interne d’un module ou d’un type</span><span class="sxs-lookup"><span data-stu-id="41eb4-166">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="41eb4-167">Utiliser la casse mixte pour les paramètres</span><span class="sxs-lookup"><span data-stu-id="41eb4-167">Use camelCase for parameters</span></span>

<span data-ttu-id="41eb4-168">Tous les paramètres doivent utiliser la casse mixte conformément aux conventions d’affectation de noms .NET.</span><span class="sxs-lookup"><span data-stu-id="41eb4-168">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="41eb4-169">Utiliser casse Pascal pour les modules</span><span class="sxs-lookup"><span data-stu-id="41eb4-169">Use PascalCase for modules</span></span>

<span data-ttu-id="41eb4-170">Tous les modules (de niveau supérieur, interne, privé, imbriqué) doivent utiliser casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="41eb4-170">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="41eb4-171">Utiliser casse Pascal pour les déclarations de type, les membres et les étiquettes</span><span class="sxs-lookup"><span data-stu-id="41eb4-171">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="41eb4-172">Les classes, les interfaces, les structures, les énumérations, les délégués, les enregistrements et les unions discriminées doivent toutes être nommées avec casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="41eb4-172">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="41eb4-173">Les membres dans les types et les étiquettes pour les enregistrements et les unions discriminées doivent également utiliser casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="41eb4-173">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="41eb4-174">Utiliser casse Pascal pour les constructions intrinsèques à .NET</span><span class="sxs-lookup"><span data-stu-id="41eb4-174">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="41eb4-175">Les espaces de noms, les exceptions, les événements et les noms de projet/`.dll` doivent également utiliser casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="41eb4-175">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="41eb4-176">Non seulement cela rend la consommation des autres langages .NET plus naturelle pour les consommateurs, mais elle est également cohérente avec les conventions de nommage .NET que vous êtes susceptible de rencontrer.</span><span class="sxs-lookup"><span data-stu-id="41eb4-176">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="41eb4-177">Éviter les traits de soulignement dans les noms</span><span class="sxs-lookup"><span data-stu-id="41eb4-177">Avoid underscores in names</span></span>

<span data-ttu-id="41eb4-178">Historiquement, certaines F# bibliothèques ont utilisé des traits de soulignement dans les noms.</span><span class="sxs-lookup"><span data-stu-id="41eb4-178">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="41eb4-179">Toutefois, cela n’est plus largement accepté, en partie parce qu’il est en conflit avec les conventions de nommage .NET.</span><span class="sxs-lookup"><span data-stu-id="41eb4-179">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="41eb4-180">Cela dit, certains F# programmeurs utilisent des traits de soulignement très largement, en partie pour des raisons historiques, et la tolérance et le respect sont importants.</span><span class="sxs-lookup"><span data-stu-id="41eb4-180">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="41eb4-181">Toutefois, n’oubliez pas que le style est souvent utilisé par d’autres personnes qui ont le choix de l’utiliser ou non.</span><span class="sxs-lookup"><span data-stu-id="41eb4-181">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="41eb4-182">Certaines exceptions incluent l’interopérabilité avec les composants natifs, où les traits de soulignement sont très courants.</span><span class="sxs-lookup"><span data-stu-id="41eb4-182">Some exceptions includes interoperating with native components, where underscores are very common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="41eb4-183">Utiliser des F# opérateurs standard</span><span class="sxs-lookup"><span data-stu-id="41eb4-183">Use standard F# operators</span></span>

<span data-ttu-id="41eb4-184">Les opérateurs suivants sont définis dans la F# bibliothèque standard et doivent être utilisés au lieu de définir des équivalents.</span><span class="sxs-lookup"><span data-stu-id="41eb4-184">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="41eb4-185">L’utilisation de ces opérateurs est recommandée, car elle tend à rendre le code plus lisible et idiomatique.</span><span class="sxs-lookup"><span data-stu-id="41eb4-185">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="41eb4-186">Les développeurs disposant d’un arrière-plan dans OCaml ou d’autres langages de programmation fonctionnelle peuvent être habitués à différents idiomes.</span><span class="sxs-lookup"><span data-stu-id="41eb4-186">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="41eb4-187">La liste suivante récapitule les opérateurs recommandés F# .</span><span class="sxs-lookup"><span data-stu-id="41eb4-187">The following list summarizes the recommended F# operators.</span></span>

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="41eb4-188">Utilisez la syntaxe de préfixe pour les génériques (`Foo<T>`) de préférence à la syntaxe postfixée (`T Foo`)</span><span class="sxs-lookup"><span data-stu-id="41eb4-188">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="41eb4-189">F#hérite à la fois du style d’affectation de noms de types génériques (par exemple, `int list`) et du style de préfixe .NET (par exemple, `list<int>`).</span><span class="sxs-lookup"><span data-stu-id="41eb4-189">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="41eb4-190">Préférer le style .NET, à l’exception de cinq types spécifiques :</span><span class="sxs-lookup"><span data-stu-id="41eb4-190">Prefer the .NET style, except for five specific types:</span></span>

1. <span data-ttu-id="41eb4-191">Pour F# les listes, utilisez le formulaire postfix : `int list` plutôt que `list<int>`.</span><span class="sxs-lookup"><span data-stu-id="41eb4-191">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="41eb4-192">Pour F# les options, utilisez le formulaire postfix : `int option` plutôt que `option<int>`.</span><span class="sxs-lookup"><span data-stu-id="41eb4-192">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="41eb4-193">Pour F# les options de valeur, utilisez la forme postfixer : `int voption` plutôt que `voption<int>`.</span><span class="sxs-lookup"><span data-stu-id="41eb4-193">For F# Value Options, use the postfix form: `int voption` rather than `voption<int>`.</span></span>
4. <span data-ttu-id="41eb4-194">Pour F# les tableaux, utilisez le nom syntaxique `int[]` plutôt que `int array` ou `array<int>`.</span><span class="sxs-lookup"><span data-stu-id="41eb4-194">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
5. <span data-ttu-id="41eb4-195">Pour les cellules de référence, utilisez `int ref` plutôt que `ref<int>` ou `Ref<int>`.</span><span class="sxs-lookup"><span data-stu-id="41eb4-195">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="41eb4-196">Pour tous les autres types, utilisez le formulaire de préfixe.</span><span class="sxs-lookup"><span data-stu-id="41eb4-196">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="41eb4-197">Mise en forme des tuples</span><span class="sxs-lookup"><span data-stu-id="41eb4-197">Formatting tuples</span></span>

<span data-ttu-id="41eb4-198">Une instanciation de tuple doit être placée entre parenthèses, et les virgules de délimitation dans doivent être suivies d’un seul espace, par exemple : `(1, 2)`, `(x, y, z)`.</span><span class="sxs-lookup"><span data-stu-id="41eb4-198">A tuple instantiation should be parenthesized, and the delimiting commas within should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="41eb4-199">Il est généralement admis d’omettre les parenthèses dans les critères spéciaux des tuples :</span><span class="sxs-lookup"><span data-stu-id="41eb4-199">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

<span data-ttu-id="41eb4-200">Il est également généralement admis à omettre les parenthèses si le tuple est la valeur de retour d’une fonction :</span><span class="sxs-lookup"><span data-stu-id="41eb4-200">It is also commonly accepted to omit parentheses if the tuple is the return value of a function:</span></span>

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

<span data-ttu-id="41eb4-201">En résumé, préférez les instanciations de tuple entre parenthèses, mais lors de l’utilisation de tuples pour les critères spéciaux ou une valeur de retour, il est considéré comme correct pour éviter les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="41eb4-201">In summary, prefer parenthesized tuple instantiations, but when using tuples for pattern matching or a return value, it is considered fine to avoid parentheses.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="41eb4-202">Mise en forme des déclarations d’union discriminée</span><span class="sxs-lookup"><span data-stu-id="41eb4-202">Formatting discriminated union declarations</span></span>

<span data-ttu-id="41eb4-203">Mettez en retrait `|` dans la définition de type par 4 espaces :</span><span class="sxs-lookup"><span data-stu-id="41eb4-203">Indent `|` in type definition by 4 spaces:</span></span>

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

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="41eb4-204">Mise en forme des unions discriminées</span><span class="sxs-lookup"><span data-stu-id="41eb4-204">Formatting discriminated unions</span></span>

<span data-ttu-id="41eb4-205">Les unions discriminées instanciées qui sont fractionnées sur plusieurs lignes doivent fournir aux données contenues une nouvelle étendue avec mise en retrait :</span><span class="sxs-lookup"><span data-stu-id="41eb4-205">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="41eb4-206">La parenthèse fermante peut également se trouver sur une nouvelle ligne :</span><span class="sxs-lookup"><span data-stu-id="41eb4-206">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="41eb4-207">Mise en forme des déclarations d’enregistrement</span><span class="sxs-lookup"><span data-stu-id="41eb4-207">Formatting record declarations</span></span>

<span data-ttu-id="41eb4-208">Mettez en retrait `{` dans la définition de type par 4 espaces et démarrez la liste de champs sur la même ligne :</span><span class="sxs-lookup"><span data-stu-id="41eb4-208">Indent `{` in type definition by 4 spaces and start the field list on the same line:</span></span>

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

<span data-ttu-id="41eb4-209">Il est préférable de placer le jeton d’ouverture sur une nouvelle ligne et le jeton de fermeture sur une nouvelle ligne si vous déclarez des implémentations d’interface ou des membres sur l’enregistrement :</span><span class="sxs-lookup"><span data-stu-id="41eb4-209">Placing the opening token on a new line and the closing token on a new line is preferable if you are declaring interface implementations or members on the record:</span></span>

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    } with
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a><span data-ttu-id="41eb4-210">Mise en forme des enregistrements</span><span class="sxs-lookup"><span data-stu-id="41eb4-210">Formatting records</span></span>

<span data-ttu-id="41eb4-211">Les enregistrements courts peuvent être écrits en une seule ligne :</span><span class="sxs-lookup"><span data-stu-id="41eb4-211">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="41eb4-212">Les enregistrements qui sont plus longs doivent utiliser de nouvelles lignes pour les étiquettes :</span><span class="sxs-lookup"><span data-stu-id="41eb4-212">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="41eb4-213">Le fait de placer le jeton d’ouverture sur une nouvelle ligne, le contenu tabulé sur une étendue et le jeton de fermeture sur une nouvelle ligne sont préférables si vous êtes :</span><span class="sxs-lookup"><span data-stu-id="41eb4-213">Placing the opening token on a new line, the contents tabbed over one scope, and the closing token on a new line is preferable if you are:</span></span>

* <span data-ttu-id="41eb4-214">Déplacement d’enregistrements dans du code avec différentes étendues de mise en retrait</span><span class="sxs-lookup"><span data-stu-id="41eb4-214">Moving records around in code with different indentation scopes</span></span>
* <span data-ttu-id="41eb4-215">Les rediriger dans une fonction</span><span class="sxs-lookup"><span data-stu-id="41eb4-215">Piping them into a function</span></span>

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

<span data-ttu-id="41eb4-216">Les mêmes règles s’appliquent aux éléments de liste et de tableau.</span><span class="sxs-lookup"><span data-stu-id="41eb4-216">The same rules apply for list and array elements.</span></span>

## <a name="formatting-copy-and-update-record-expressions"></a><span data-ttu-id="41eb4-217">Mise en forme des expressions d’enregistrement de copie et de mise à jour</span><span class="sxs-lookup"><span data-stu-id="41eb4-217">Formatting copy-and-update record expressions</span></span>

<span data-ttu-id="41eb4-218">Une expression d’enregistrement de copie et de mise à jour est toujours un enregistrement, donc des instructions similaires s’appliquent.</span><span class="sxs-lookup"><span data-stu-id="41eb4-218">A copy-and-update record expression is still a record, so similar guidelines apply.</span></span>

<span data-ttu-id="41eb4-219">Les expressions courtes peuvent tenir sur une seule ligne :</span><span class="sxs-lookup"><span data-stu-id="41eb4-219">Short expressions can fit on one line:</span></span>

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

<span data-ttu-id="41eb4-220">Les expressions plus longues doivent utiliser de nouvelles lignes :</span><span class="sxs-lookup"><span data-stu-id="41eb4-220">Longer expressions should use new lines:</span></span>

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="41eb4-221">Comme avec les conseils d’enregistrement, vous souhaiterez peut-être dédier des lignes distinctes pour les accolades et mettre en retrait une étendue à droite avec l’expression.</span><span class="sxs-lookup"><span data-stu-id="41eb4-221">And as with the record guidance, you may want to dedicate separate lines for the braces and indent one scope to the right with the expression.</span></span> <span data-ttu-id="41eb4-222">Notez que dans certains cas spéciaux, comme l’encapsulation d’une valeur avec un facultatif sans parenthèses, vous devrez peut-être conserver une accolade sur une ligne :</span><span class="sxs-lookup"><span data-stu-id="41eb4-222">Note that in some special cases, such as wrapping a value with an optional without parentheses, you may need to keep a brace on one line:</span></span>

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

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="41eb4-223">Mise en forme des listes et des tableaux</span><span class="sxs-lookup"><span data-stu-id="41eb4-223">Formatting lists and arrays</span></span>

<span data-ttu-id="41eb4-224">Écrire `x :: l` avec des espaces autour de l’opérateur `::` (`::` est un opérateur infix, entouré par des espaces).</span><span class="sxs-lookup"><span data-stu-id="41eb4-224">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces).</span></span>

<span data-ttu-id="41eb4-225">La liste et les tableaux déclarés sur une seule ligne doivent avoir un espace après le crochet ouvrant et avant le crochet fermant :</span><span class="sxs-lookup"><span data-stu-id="41eb4-225">List and arrays declared on a single line should have a space after the opening bracket and before the closing bracket:</span></span>

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

<span data-ttu-id="41eb4-226">Utilisez toujours au moins un espace entre deux opérateurs similaires à des accolades.</span><span class="sxs-lookup"><span data-stu-id="41eb4-226">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="41eb4-227">Par exemple, laissez un espace entre un `[` et un `{`.</span><span class="sxs-lookup"><span data-stu-id="41eb4-227">For example, leave a space between a `[` and a `{`.</span></span>

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

<span data-ttu-id="41eb4-228">La même règle s’applique pour les listes ou les tableaux de tuples.</span><span class="sxs-lookup"><span data-stu-id="41eb4-228">The same guideline applies for lists or arrays of tuples.</span></span>

<span data-ttu-id="41eb4-229">Les listes et les tableaux répartis sur plusieurs lignes suivent une règle similaire, à l’instar des enregistrements :</span><span class="sxs-lookup"><span data-stu-id="41eb4-229">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

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

<span data-ttu-id="41eb4-230">Et comme avec les enregistrements, la déclaration de l’ouverture et des crochets fermants sur leur propre ligne permet de faciliter le déplacement du code et de rediriger les fonctions vers les fonctions.</span><span class="sxs-lookup"><span data-stu-id="41eb4-230">And as with records, declaring the opening and closing brackets on their own line will make moving code around and piping into functions easier.</span></span>

<span data-ttu-id="41eb4-231">Lors de la génération de tableaux et de listes par programme, préférez `->` sur `do ... yield` lorsqu’une valeur est toujours générée :</span><span class="sxs-lookup"><span data-stu-id="41eb4-231">When generating arrays and lists programmatically, prefer `->` over `do ... yield` when a value is always generated:</span></span>

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x*x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x*x ]
```

<span data-ttu-id="41eb4-232">Les versions antérieures du F# langage nécessitaient la spécification d' `yield` dans les cas où des données peuvent être générées de manière conditionnelle, ou il peut y avoir des expressions consécutives à évaluer.</span><span class="sxs-lookup"><span data-stu-id="41eb4-232">Older versions of the F# language required specifying `yield` in situations where data may be generated conditionally, or there may be consecutive expressions to be evaluated.</span></span> <span data-ttu-id="41eb4-233">Préférez omettre ces mots clés `yield`, sauf si vous devez compiler avec F# une version de langage antérieure :</span><span class="sxs-lookup"><span data-stu-id="41eb4-233">Prefer omitting these `yield` keywords unless you must compile with an older F# language version:</span></span>

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

<span data-ttu-id="41eb4-234">Dans certains cas, `do...yield` peut contribuer à la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="41eb4-234">In some cases, `do...yield` may aid in readability.</span></span> <span data-ttu-id="41eb4-235">Ces cas, bien que subjectives, doivent être pris en considération.</span><span class="sxs-lookup"><span data-stu-id="41eb4-235">These cases, though subjective, should be taken into consideration.</span></span>

## <a name="formatting-if-expressions"></a><span data-ttu-id="41eb4-236">Mettre en forme si des expressions</span><span class="sxs-lookup"><span data-stu-id="41eb4-236">Formatting if expressions</span></span>

<span data-ttu-id="41eb4-237">La mise en retrait des conditions dépend de la taille des expressions qui les composent.</span><span class="sxs-lookup"><span data-stu-id="41eb4-237">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="41eb4-238">Si `cond`, `e1` et `e2` sont courts, il suffit de les écrire sur une seule ligne :</span><span class="sxs-lookup"><span data-stu-id="41eb4-238">If `cond`, `e1` and `e2` are short, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="41eb4-239">Si `cond`, `e1` ou `e2` sont plus longues, mais pas sur plusieurs lignes :</span><span class="sxs-lookup"><span data-stu-id="41eb4-239">If either `cond`, `e1` or `e2` are longer, but not multi-line:</span></span>

```fsharp
if cond
then e1
else e2
```

<span data-ttu-id="41eb4-240">Si l’une des expressions est multiligne :</span><span class="sxs-lookup"><span data-stu-id="41eb4-240">If any of the expressions are multi-line:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="41eb4-241">Plusieurs conditionnels avec `elif` et `else` sont mis en retrait dans la même portée que l' `if`:</span><span class="sxs-lookup"><span data-stu-id="41eb4-241">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="41eb4-242">Constructions de critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="41eb4-242">Pattern matching constructs</span></span>

<span data-ttu-id="41eb4-243">Utilisez une `|` pour chaque clause d’une correspondance sans mise en retrait.</span><span class="sxs-lookup"><span data-stu-id="41eb4-243">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="41eb4-244">Si l’expression est brève, vous pouvez envisager d’utiliser une seule ligne si chaque sous-expression est également simple.</span><span class="sxs-lookup"><span data-stu-id="41eb4-244">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

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

<span data-ttu-id="41eb4-245">Si l’expression située à droite de la flèche de critères spéciaux est trop grande, déplacez-la sur la ligne suivante, en mettant en retrait une étape du `match`/`|`.</span><span class="sxs-lookup"><span data-stu-id="41eb4-245">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="41eb4-246">Les critères spéciaux des fonctions anonymes, qui commencent par `function`, ne doivent généralement pas être trop mis en retrait.</span><span class="sxs-lookup"><span data-stu-id="41eb4-246">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="41eb4-247">Par exemple, la mise en retrait d’une étendue comme suit est correcte :</span><span class="sxs-lookup"><span data-stu-id="41eb4-247">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="41eb4-248">Les critères spéciaux dans les fonctions définies par `let` ou `let rec` doivent être mis en retrait de 4 espaces après le démarrage d' `let`, même si `function` mot clé est utilisé :</span><span class="sxs-lookup"><span data-stu-id="41eb4-248">Pattern matching in functions defined by `let` or `let rec` should be indented 4 spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="41eb4-249">Nous vous déconseillons d’aligner les flèches.</span><span class="sxs-lookup"><span data-stu-id="41eb4-249">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="41eb4-250">Mise en forme des expressions try/with</span><span class="sxs-lookup"><span data-stu-id="41eb4-250">Formatting try/with expressions</span></span>

<span data-ttu-id="41eb4-251">Les critères spéciaux sur le type d’exception doivent être mis en retrait au même niveau que `with`.</span><span class="sxs-lookup"><span data-stu-id="41eb4-251">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

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

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="41eb4-252">Mise en forme de l’application de paramètre de fonction</span><span class="sxs-lookup"><span data-stu-id="41eb4-252">Formatting function parameter application</span></span>

<span data-ttu-id="41eb4-253">En général, la plupart des paramètres de fonction sont exécutés sur la même ligne.</span><span class="sxs-lookup"><span data-stu-id="41eb4-253">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="41eb4-254">Si vous souhaitez appliquer des paramètres à une fonction sur une nouvelle ligne, mettez-les en retrait d’une seule étendue.</span><span class="sxs-lookup"><span data-stu-id="41eb4-254">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

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

<span data-ttu-id="41eb4-255">Les mêmes instructions s’appliquent aux expressions lambda comme arguments de fonction.</span><span class="sxs-lookup"><span data-stu-id="41eb4-255">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="41eb4-256">Si le corps d’une expression lambda, le corps peut avoir une autre ligne, mise en retrait d’une étendue</span><span class="sxs-lookup"><span data-stu-id="41eb4-256">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

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

<span data-ttu-id="41eb4-257">Toutefois, si le corps d’une expression lambda est plus d’une ligne, envisagez de le factoriser dans une fonction distincte plutôt que d’avoir une construction multiligne appliquée comme argument unique à une fonction.</span><span class="sxs-lookup"><span data-stu-id="41eb4-257">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="41eb4-258">Mise en forme des opérateurs infixes</span><span class="sxs-lookup"><span data-stu-id="41eb4-258">Formatting infix operators</span></span>

<span data-ttu-id="41eb4-259">Séparez les opérateurs par des espaces.</span><span class="sxs-lookup"><span data-stu-id="41eb4-259">Separate operators by spaces.</span></span> <span data-ttu-id="41eb4-260">Les opérateurs `!` et `.` sont des exceptions évidentes à cette règle.</span><span class="sxs-lookup"><span data-stu-id="41eb4-260">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="41eb4-261">Les expressions infixes sont correctes pour la programmation sur la même colonne :</span><span class="sxs-lookup"><span data-stu-id="41eb4-261">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="41eb4-262">Mise en forme des opérateurs de pipeline</span><span class="sxs-lookup"><span data-stu-id="41eb4-262">Formatting pipeline operators</span></span>

<span data-ttu-id="41eb4-263">Les opérateurs de `|>` de pipeline doivent se trouver sous les expressions sur lesquelles ils opèrent.</span><span class="sxs-lookup"><span data-stu-id="41eb4-263">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

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

### <a name="formatting-modules"></a><span data-ttu-id="41eb4-264">Mise en forme des modules</span><span class="sxs-lookup"><span data-stu-id="41eb4-264">Formatting modules</span></span>

<span data-ttu-id="41eb4-265">Le code d’un module local doit être mis en retrait par rapport au module, mais le code d’un module de niveau supérieur ne doit pas être mis en retrait.</span><span class="sxs-lookup"><span data-stu-id="41eb4-265">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="41eb4-266">Les éléments d’espace de noms n’ont pas besoin d’être mis en retrait.</span><span class="sxs-lookup"><span data-stu-id="41eb4-266">Namespace elements do not have to be indented.</span></span>

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

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="41eb4-267">Mise en forme des expressions et des interfaces d’objet</span><span class="sxs-lookup"><span data-stu-id="41eb4-267">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="41eb4-268">Les interfaces et les expressions d’objet doivent être alignées de la même façon avec `member` mis en retrait après 4 espaces.</span><span class="sxs-lookup"><span data-stu-id="41eb4-268">Object expressions and interfaces should be aligned in the same way with `member` being indented after 4 spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="41eb4-269">Mise en forme des espaces blancs dans les expressions</span><span class="sxs-lookup"><span data-stu-id="41eb4-269">Formatting white space in expressions</span></span>

<span data-ttu-id="41eb4-270">Évitez les espaces blancs superflus F# dans les expressions.</span><span class="sxs-lookup"><span data-stu-id="41eb4-270">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="41eb4-271">Les arguments nommés ne doivent pas avoir d’espace autour de l' `=`:</span><span class="sxs-lookup"><span data-stu-id="41eb4-271">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a><span data-ttu-id="41eb4-272">Attributs de mise en forme</span><span class="sxs-lookup"><span data-stu-id="41eb4-272">Formatting attributes</span></span>

<span data-ttu-id="41eb4-273">Les [attributs](../language-reference/attributes.md) sont placés au-dessus d’une construction :</span><span class="sxs-lookup"><span data-stu-id="41eb4-273">[Attributes](../language-reference/attributes.md) are placed above a construct:</span></span>

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

### <a name="formatting-attributes-on-parameters"></a><span data-ttu-id="41eb4-274">Mise en forme des attributs sur les paramètres</span><span class="sxs-lookup"><span data-stu-id="41eb4-274">Formatting attributes on parameters</span></span>

<span data-ttu-id="41eb4-275">Les attributs peuvent également être des emplacements de paramètres.</span><span class="sxs-lookup"><span data-stu-id="41eb4-275">Attributes can also be places on parameters.</span></span> <span data-ttu-id="41eb4-276">Dans ce cas, placez ensuite sur la même ligne que le paramètre et avant le nom :</span><span class="sxs-lookup"><span data-stu-id="41eb4-276">In this case, place then on the same line as the parameter and before the name:</span></span>

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a><span data-ttu-id="41eb4-277">Mise en forme de plusieurs attributs</span><span class="sxs-lookup"><span data-stu-id="41eb4-277">Formatting multiple attributes</span></span>

<span data-ttu-id="41eb4-278">Quand plusieurs attributs sont appliqués à une construction qui n’est pas un paramètre, ils doivent être placés de façon à ce qu’il y ait un attribut par ligne :</span><span class="sxs-lookup"><span data-stu-id="41eb4-278">When multiple attributes are applied to a construct that is not a parameter, they should be placed such that there is one attribute per line:</span></span>

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="41eb4-279">Lorsqu’ils sont appliqués à un paramètre, ils doivent se trouver sur la même ligne et être séparés par un séparateur de `;`.</span><span class="sxs-lookup"><span data-stu-id="41eb4-279">When applied to a parameter, they must be on the same line and separated by a `;` separator.</span></span>

## <a name="formatting-literals"></a><span data-ttu-id="41eb4-280">Mise en forme des littéraux</span><span class="sxs-lookup"><span data-stu-id="41eb4-280">Formatting literals</span></span>

<span data-ttu-id="41eb4-281">les littéraux utilisant l’attribut `Literal` doivent placer l’attribut sur sa propre ligne et utiliser la dénomination casse Pascal : [ F# ](../language-reference/literals.md)</span><span class="sxs-lookup"><span data-stu-id="41eb4-281">[F# literals](../language-reference/literals.md) using the `Literal` attribute should place the attribute on its own line and use PascalCase naming:</span></span>

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

<span data-ttu-id="41eb4-282">Évitez de placer l’attribut sur la même ligne que la valeur.</span><span class="sxs-lookup"><span data-stu-id="41eb4-282">Avoid placing the attribute on the same line as the value.</span></span>
