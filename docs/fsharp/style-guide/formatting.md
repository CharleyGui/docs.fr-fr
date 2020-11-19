---
title: Indications de mise en forme du code F#
description: 'Découvrez les instructions de mise en forme du code F #.'
ms.date: 08/31/2020
ms.openlocfilehash: 8f5e333c015f30ae8449c76a3075763370a98e4d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830517"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="3f280-103">Indications de mise en forme du code F#</span><span class="sxs-lookup"><span data-stu-id="3f280-103">F# code formatting guidelines</span></span>

<span data-ttu-id="3f280-104">Cet article fournit des instructions sur la façon de mettre en forme votre code afin que votre code F # soit :</span><span class="sxs-lookup"><span data-stu-id="3f280-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="3f280-105">Plus lisible</span><span class="sxs-lookup"><span data-stu-id="3f280-105">More legible</span></span>
* <span data-ttu-id="3f280-106">Conformément aux conventions appliquées par les outils de mise en forme dans Visual Studio et d’autres éditeurs</span><span class="sxs-lookup"><span data-stu-id="3f280-106">In accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="3f280-107">Similaire à un autre code en ligne</span><span class="sxs-lookup"><span data-stu-id="3f280-107">Similar to other code online</span></span>

<span data-ttu-id="3f280-108">Ces instructions sont basées sur [un guide exhaustif des conventions de mise en forme F #](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) par [Anh-fumier Phan](https://github.com/dungpa).</span><span class="sxs-lookup"><span data-stu-id="3f280-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="3f280-109">Règles générales pour la mise en retrait</span><span class="sxs-lookup"><span data-stu-id="3f280-109">General rules for indentation</span></span>

<span data-ttu-id="3f280-110">F # utilise des espaces blancs significatifs par défaut.</span><span class="sxs-lookup"><span data-stu-id="3f280-110">F# uses significant white space by default.</span></span> <span data-ttu-id="3f280-111">Les instructions suivantes sont destinées à vous aider à jongler avec les défis que cela peut imposer.</span><span class="sxs-lookup"><span data-stu-id="3f280-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="3f280-112">Utilisation des espaces</span><span class="sxs-lookup"><span data-stu-id="3f280-112">Using spaces</span></span>

<span data-ttu-id="3f280-113">Lorsque la mise en retrait est requise, vous devez utiliser des espaces, et non des tabulations.</span><span class="sxs-lookup"><span data-stu-id="3f280-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="3f280-114">Au moins un espace est requis.</span><span class="sxs-lookup"><span data-stu-id="3f280-114">At least one space is required.</span></span> <span data-ttu-id="3f280-115">Votre organisation peut créer des normes de codage pour spécifier le nombre d’espaces à utiliser pour la mise en retrait ; deux, trois ou quatre espaces de mise en retrait à chaque niveau de mise en retrait sont typiques.</span><span class="sxs-lookup"><span data-stu-id="3f280-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three, or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="3f280-116">**Nous vous recommandons quatre espaces par retrait.**</span><span class="sxs-lookup"><span data-stu-id="3f280-116">**We recommend four spaces per indentation.**</span></span>

<span data-ttu-id="3f280-117">Ceci dit, la mise en retrait des programmes est une question subjective.</span><span class="sxs-lookup"><span data-stu-id="3f280-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="3f280-118">Les variations sont OK, mais la première règle que vous devez suivre est la *cohérence de la mise en retrait*.</span><span class="sxs-lookup"><span data-stu-id="3f280-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="3f280-119">Choisissez un style de mise en retrait généralement accepté et utilisez-le systématiquement tout au long de votre code base.</span><span class="sxs-lookup"><span data-stu-id="3f280-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-white-space"></a><span data-ttu-id="3f280-120">Mise en forme des espaces blancs</span><span class="sxs-lookup"><span data-stu-id="3f280-120">Formatting white space</span></span>

<span data-ttu-id="3f280-121">F # est sensible à l’espace blanc.</span><span class="sxs-lookup"><span data-stu-id="3f280-121">F# is white space sensitive.</span></span> <span data-ttu-id="3f280-122">Bien que la plupart des sémantiques de l’espace blanc soient couvertes par une mise en retrait appropriée, il y a d’autres éléments à prendre en compte.</span><span class="sxs-lookup"><span data-stu-id="3f280-122">Although most semantics from white space are covered by proper indentation, there are some other things to consider.</span></span>

### <a name="formatting-operators-in-arithmetic-expressions"></a><span data-ttu-id="3f280-123">Mise en forme des opérateurs dans les expressions arithmétiques</span><span class="sxs-lookup"><span data-stu-id="3f280-123">Formatting operators in arithmetic expressions</span></span>

<span data-ttu-id="3f280-124">Utilisez toujours un espace blanc autour des expressions arithmétiques binaires :</span><span class="sxs-lookup"><span data-stu-id="3f280-124">Always use white space around binary arithmetic expressions:</span></span>

```fsharp
let subtractThenAdd x = x - 1 + 3
```

<span data-ttu-id="3f280-125">`-`Les opérateurs unaires doivent toujours être suivis immédiatement de la valeur qu’ils annulent :</span><span class="sxs-lookup"><span data-stu-id="3f280-125">Unary `-` operators should always be immediately followed by the value they are negating:</span></span>

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

<span data-ttu-id="3f280-126">L’ajout d’un espace blanc après l' `-` opérateur peut entraîner des confusions pour d’autres.</span><span class="sxs-lookup"><span data-stu-id="3f280-126">Adding a white-space character after the `-` operator can lead to confusion for others.</span></span>

<span data-ttu-id="3f280-127">En résumé, il est important de toujours :</span><span class="sxs-lookup"><span data-stu-id="3f280-127">In summary, it's important to always:</span></span>

* <span data-ttu-id="3f280-128">Entourer les opérateurs binaires avec un espace blanc</span><span class="sxs-lookup"><span data-stu-id="3f280-128">Surround binary operators with white space</span></span>
* <span data-ttu-id="3f280-129">Ne jamais avoir d’espace blanc de fin après un opérateur unaire</span><span class="sxs-lookup"><span data-stu-id="3f280-129">Never have trailing white space after a unary operator</span></span>

<span data-ttu-id="3f280-130">L’indication de l’opérateur arithmétique binaire est particulièrement importante.</span><span class="sxs-lookup"><span data-stu-id="3f280-130">The binary arithmetic operator guideline is especially important.</span></span> <span data-ttu-id="3f280-131">L’échec de l’entourage d’un `-` opérateur binaire, lorsqu’il est associé à certains choix de mise en forme, peut entraîner son interprétation comme unaire `-` .</span><span class="sxs-lookup"><span data-stu-id="3f280-131">Failing to surround a binary `-` operator, when combined with certain formatting choices, could lead to interpreting it as a unary `-`.</span></span>

### <a name="surround-a-custom-operator-definition-with-white-space"></a><span data-ttu-id="3f280-132">Entourer une définition d’opérateur personnalisée avec un espace blanc</span><span class="sxs-lookup"><span data-stu-id="3f280-132">Surround a custom operator definition with white space</span></span>

<span data-ttu-id="3f280-133">Utilisez toujours des espaces blancs pour entourer une définition d’opérateur :</span><span class="sxs-lookup"><span data-stu-id="3f280-133">Always use white space to surround an operator definition:</span></span>

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

<span data-ttu-id="3f280-134">Pour tout opérateur personnalisé qui commence par `*` et qui contient plusieurs caractères, vous devez ajouter un espace blanc au début de la définition pour éviter une ambiguïté du compilateur.</span><span class="sxs-lookup"><span data-stu-id="3f280-134">For any custom operator that starts with `*` and that has more than one character, you need to add a white space to the beginning of the definition to avoid a compiler ambiguity.</span></span> <span data-ttu-id="3f280-135">Pour cette raison, nous vous recommandons d’entourer simplement les définitions de tous les opérateurs avec un seul espace blanc.</span><span class="sxs-lookup"><span data-stu-id="3f280-135">Because of this, we recommend that you simply surround the definitions of all operators with a single white-space character.</span></span>

### <a name="surround-function-parameter-arrows-with-white-space"></a><span data-ttu-id="3f280-136">Placer les flèches de paramètre de fonction avec un espace blanc</span><span class="sxs-lookup"><span data-stu-id="3f280-136">Surround function parameter arrows with white space</span></span>

<span data-ttu-id="3f280-137">Lors de la définition de la signature d’une fonction, utilisez un espace blanc autour du `->` symbole :</span><span class="sxs-lookup"><span data-stu-id="3f280-137">When defining the signature of a function, use white space around the `->` symbol:</span></span>

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a><span data-ttu-id="3f280-138">Entourer les arguments de fonction avec un espace blanc</span><span class="sxs-lookup"><span data-stu-id="3f280-138">Surround function arguments with white space</span></span>

<span data-ttu-id="3f280-139">Lors de la définition d’une fonction, utilisez un espace blanc autour de chaque argument.</span><span class="sxs-lookup"><span data-stu-id="3f280-139">When defining a function, use white space around each argument.</span></span>

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="place-parameters-on-a-new-line-for-long-definitions"></a><span data-ttu-id="3f280-140">Placer des paramètres sur une nouvelle ligne pour les définitions longues</span><span class="sxs-lookup"><span data-stu-id="3f280-140">Place parameters on a new line for long definitions</span></span>

<span data-ttu-id="3f280-141">Si vous avez une définition de fonction longue, placez les paramètres sur de nouvelles lignes et mettez-les en retrait pour qu’ils correspondent au niveau de mise en retrait du paramètre suivant.</span><span class="sxs-lookup"><span data-stu-id="3f280-141">If you have a long function definition, place the parameters on new lines and indent them to match the indentation level of the subsequent parameter.</span></span>

```fsharp
module M =
    let LongFunctionWithLotsOfParameters(aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                        (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                        (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                        =
        // ... the body of the method follows
```

<span data-ttu-id="3f280-142">Cela s’applique également aux membres, constructeurs et paramètres à l’aide de tuples :</span><span class="sxs-lookup"><span data-stu-id="3f280-142">This also applies to members, constructors, and parameters using tuples:</span></span>

```fsharp
type TM() =
    member _.LongMethodWithLotsOfParameters(aVeryLongParam: AVeryLongTypeThatYouNeedToUse,
                                            aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse,
                                            aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse) =
        // ... the body of the method

type TC(aVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse,
        aSecondVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse,
        aThirdVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse) =
    // ... the body of the class follows
```

<span data-ttu-id="3f280-143">Si les paramètres sont currified ou s’il existe une annotation de type de retour explicite, il est préférable de placer le `=` caractère sur une nouvelle ligne :</span><span class="sxs-lookup"><span data-stu-id="3f280-143">If the parameters are currified or there's an explicit return type annotation, it is preferable to place the `=` character on a new line:</span></span>

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(aVeryLongParam: AVeryLongTypeThatYouNeedToUse,
                                            aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse,
                                            aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                            : AReturnType =
        // ... the body of the method
    member _.LongMethodWithLotsOfCurrifiedParams(aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                                (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                                (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
                                                =
        // ... the body of the method
```

<span data-ttu-id="3f280-144">Il s’agit d’un moyen d’éviter des lignes trop longues (dans le cas où le type de retour peut avoir un nom long) et d’avoir moins de dommages lors de l’ajout de paramètres.</span><span class="sxs-lookup"><span data-stu-id="3f280-144">This is a way to avoid too long lines (in case return type might have long name) and have less line-damage when adding parameters.</span></span>

### <a name="type-annotations"></a><span data-ttu-id="3f280-145">Annotations de type</span><span class="sxs-lookup"><span data-stu-id="3f280-145">Type annotations</span></span>

#### <a name="right-pad-function-argument-type-annotations"></a><span data-ttu-id="3f280-146">Annotations de type d’argument de fonction de remplissage à droite</span><span class="sxs-lookup"><span data-stu-id="3f280-146">Right-pad function argument type annotations</span></span>

<span data-ttu-id="3f280-147">Quand vous définissez des arguments avec des annotations de type, utilisez un espace blanc après le `:` symbole :</span><span class="sxs-lookup"><span data-stu-id="3f280-147">When defining arguments with type annotations, use white space after the `:` symbol:</span></span>

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a><span data-ttu-id="3f280-148">Entourer les annotations de type de retour avec des espaces blancs</span><span class="sxs-lookup"><span data-stu-id="3f280-148">Surround return type annotations with white space</span></span>

<span data-ttu-id="3f280-149">Dans une fonction de liaison ou une annotation de type valeur (type de retour dans le cas d’une fonction), utilisez un espace blanc avant et après le `:` symbole :</span><span class="sxs-lookup"><span data-stu-id="3f280-149">In a let-bound function or value type annotation (return type in the case of a function), use white space before and after the `:` symbol:</span></span>

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="3f280-150">Mise en forme des lignes vides</span><span class="sxs-lookup"><span data-stu-id="3f280-150">Formatting blank lines</span></span>

* <span data-ttu-id="3f280-151">Séparez les définitions de fonction et de classe de niveau supérieur par deux lignes vides.</span><span class="sxs-lookup"><span data-stu-id="3f280-151">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="3f280-152">Les définitions de méthode à l’intérieur d’une classe sont séparées par une seule ligne vide.</span><span class="sxs-lookup"><span data-stu-id="3f280-152">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="3f280-153">Des lignes vides supplémentaires peuvent être utilisées (avec modération) pour séparer les groupes de fonctions associées.</span><span class="sxs-lookup"><span data-stu-id="3f280-153">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="3f280-154">Des lignes vides peuvent être omises entre une série de lignes associées (par exemple, un ensemble d’implémentations factices).</span><span class="sxs-lookup"><span data-stu-id="3f280-154">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="3f280-155">Utilisez des lignes vides dans les fonctions, avec modération, pour indiquer les sections logiques.</span><span class="sxs-lookup"><span data-stu-id="3f280-155">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="3f280-156">Mise en forme des commentaires</span><span class="sxs-lookup"><span data-stu-id="3f280-156">Formatting comments</span></span>

<span data-ttu-id="3f280-157">Préférez généralement plusieurs commentaires à deux barres obliques par rapport aux commentaires de bloc de type ML.</span><span class="sxs-lookup"><span data-stu-id="3f280-157">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="3f280-158">Les commentaires insérés doivent mettre en majuscule la première lettre.</span><span class="sxs-lookup"><span data-stu-id="3f280-158">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="3f280-159">Conventions d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="3f280-159">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="3f280-160">Utilisez la casse mixte pour les valeurs et les fonctions liées à la classe, à l’expression et liées aux modèles</span><span class="sxs-lookup"><span data-stu-id="3f280-160">Use camelCase for class-bound, expression-bound, and pattern-bound values and functions</span></span>

<span data-ttu-id="3f280-161">Il est courant et accepté le style F # pour utiliser la casse mixte pour tous les noms liés en tant que variables locales ou dans les définitions de fonctions et les correspondances de modèle.</span><span class="sxs-lookup"><span data-stu-id="3f280-161">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="3f280-162">Les fonctions liées localement dans les classes doivent également utiliser la casse mixte.</span><span class="sxs-lookup"><span data-stu-id="3f280-162">Locally bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="3f280-163">Utiliser la casse mixte pour les fonctions publiques liées aux modules</span><span class="sxs-lookup"><span data-stu-id="3f280-163">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="3f280-164">Quand une fonction liée à un module fait partie d’une API publique, elle doit utiliser la casse mixte :</span><span class="sxs-lookup"><span data-stu-id="3f280-164">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="3f280-165">Utilisez la casse mixte pour les valeurs et les fonctions liées aux modules internes et privés</span><span class="sxs-lookup"><span data-stu-id="3f280-165">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="3f280-166">Utilisez la casse mixte pour les valeurs à liaison de module privées, y compris les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="3f280-166">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="3f280-167">Fonctions ad hoc dans les scripts</span><span class="sxs-lookup"><span data-stu-id="3f280-167">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="3f280-168">Valeurs constituant l’implémentation interne d’un module ou d’un type</span><span class="sxs-lookup"><span data-stu-id="3f280-168">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="3f280-169">Utiliser la casse mixte pour les paramètres</span><span class="sxs-lookup"><span data-stu-id="3f280-169">Use camelCase for parameters</span></span>

<span data-ttu-id="3f280-170">Tous les paramètres doivent utiliser la casse mixte conformément aux conventions d’affectation de noms .NET.</span><span class="sxs-lookup"><span data-stu-id="3f280-170">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="3f280-171">Utiliser casse Pascal pour les modules</span><span class="sxs-lookup"><span data-stu-id="3f280-171">Use PascalCase for modules</span></span>

<span data-ttu-id="3f280-172">Tous les modules (de niveau supérieur, interne, privé, imbriqué) doivent utiliser casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="3f280-172">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="3f280-173">Utiliser casse Pascal pour les déclarations de type, les membres et les étiquettes</span><span class="sxs-lookup"><span data-stu-id="3f280-173">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="3f280-174">Les classes, les interfaces, les structures, les énumérations, les délégués, les enregistrements et les unions discriminées doivent toutes être nommées avec casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="3f280-174">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="3f280-175">Les membres dans les types et les étiquettes pour les enregistrements et les unions discriminées doivent également utiliser casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="3f280-175">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="3f280-176">Utiliser casse Pascal pour les constructions intrinsèques à .NET</span><span class="sxs-lookup"><span data-stu-id="3f280-176">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="3f280-177">Les espaces de noms, les exceptions, les événements et les projets/ `.dll` noms doivent également utiliser casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="3f280-177">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="3f280-178">Non seulement cela rend la consommation des autres langages .NET plus naturelle pour les consommateurs, mais elle est également cohérente avec les conventions de nommage .NET que vous êtes susceptible de rencontrer.</span><span class="sxs-lookup"><span data-stu-id="3f280-178">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="3f280-179">Éviter les traits de soulignement dans les noms</span><span class="sxs-lookup"><span data-stu-id="3f280-179">Avoid underscores in names</span></span>

<span data-ttu-id="3f280-180">Historiquement, certaines bibliothèques F # ont utilisé des traits de soulignement dans les noms.</span><span class="sxs-lookup"><span data-stu-id="3f280-180">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="3f280-181">Toutefois, cela n’est plus largement accepté, en partie parce qu’il est en conflit avec les conventions de nommage .NET.</span><span class="sxs-lookup"><span data-stu-id="3f280-181">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="3f280-182">Cela dit, certains programmeurs F # utilisent des traits de soulignement très largement, en partie pour des raisons historiques, et la tolérance et le respect sont importants.</span><span class="sxs-lookup"><span data-stu-id="3f280-182">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="3f280-183">Toutefois, le style est souvent utilisé par d’autres personnes qui ont le choix de l’utiliser ou non.</span><span class="sxs-lookup"><span data-stu-id="3f280-183">However, the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="3f280-184">Une exception concerne l’interopérabilité avec les composants natifs, où les traits de soulignement sont courants.</span><span class="sxs-lookup"><span data-stu-id="3f280-184">One exception includes interoperating with native components, where underscores are common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="3f280-185">Utiliser les opérateurs F # standard</span><span class="sxs-lookup"><span data-stu-id="3f280-185">Use standard F# operators</span></span>

<span data-ttu-id="3f280-186">Les opérateurs suivants sont définis dans la bibliothèque standard F # et doivent être utilisés au lieu de définir des équivalents.</span><span class="sxs-lookup"><span data-stu-id="3f280-186">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="3f280-187">L’utilisation de ces opérateurs est recommandée, car elle tend à rendre le code plus lisible et idiomatique.</span><span class="sxs-lookup"><span data-stu-id="3f280-187">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="3f280-188">Les développeurs disposant d’un arrière-plan dans OCaml ou d’autres langages de programmation fonctionnelle peuvent être habitués à différents idiomes.</span><span class="sxs-lookup"><span data-stu-id="3f280-188">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="3f280-189">La liste suivante récapitule les opérateurs F # recommandés.</span><span class="sxs-lookup"><span data-stu-id="3f280-189">The following list summarizes the recommended F# operators.</span></span>

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="3f280-190">Utilisez la syntaxe de préfixe pour les génériques ( `Foo<T>` ) de préférence à la syntaxe postfix ( `T Foo` )</span><span class="sxs-lookup"><span data-stu-id="3f280-190">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="3f280-191">F # hérite à la fois du style postfix ML de l’attribution d’un nom aux types génériques (par exemple,), ainsi `int list` que du style .net du préfixe (par exemple, `list<int>` ).</span><span class="sxs-lookup"><span data-stu-id="3f280-191">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="3f280-192">Préférer le style .NET, à l’exception de cinq types spécifiques :</span><span class="sxs-lookup"><span data-stu-id="3f280-192">Prefer the .NET style, except for five specific types:</span></span>

1. <span data-ttu-id="3f280-193">Pour les listes F #, utilisez le formulaire de suffixe : `int list` plutôt que `list<int>` .</span><span class="sxs-lookup"><span data-stu-id="3f280-193">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="3f280-194">Pour les options F #, utilisez le formulaire de suffixe : `int option` plutôt que `option<int>` .</span><span class="sxs-lookup"><span data-stu-id="3f280-194">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="3f280-195">Pour les options de valeur F #, utilisez la forme postfixé : `int voption` plutôt que `voption<int>` .</span><span class="sxs-lookup"><span data-stu-id="3f280-195">For F# Value Options, use the postfix form: `int voption` rather than `voption<int>`.</span></span>
4. <span data-ttu-id="3f280-196">Pour les tableaux F #, utilisez le nom syntaxique `int[]` plutôt que `int array` ou `array<int>` .</span><span class="sxs-lookup"><span data-stu-id="3f280-196">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
5. <span data-ttu-id="3f280-197">Pour les cellules de référence, utilisez `int ref` plutôt que `ref<int>` ou `Ref<int>` .</span><span class="sxs-lookup"><span data-stu-id="3f280-197">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="3f280-198">Pour tous les autres types, utilisez le formulaire de préfixe.</span><span class="sxs-lookup"><span data-stu-id="3f280-198">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="3f280-199">Mise en forme des tuples</span><span class="sxs-lookup"><span data-stu-id="3f280-199">Formatting tuples</span></span>

<span data-ttu-id="3f280-200">Une instanciation de tuple doit être placée entre parenthèses et les virgules de délimitation doivent être suivies d’un seul espace, par exemple : `(1, 2)` , `(x, y, z)` .</span><span class="sxs-lookup"><span data-stu-id="3f280-200">A tuple instantiation should be parenthesized, and the delimiting commas within it should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="3f280-201">Il est généralement admis d’omettre les parenthèses dans les critères spéciaux des tuples :</span><span class="sxs-lookup"><span data-stu-id="3f280-201">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

<span data-ttu-id="3f280-202">Il est également généralement admis à omettre les parenthèses si le tuple est la valeur de retour d’une fonction :</span><span class="sxs-lookup"><span data-stu-id="3f280-202">It is also commonly accepted to omit parentheses if the tuple is the return value of a function:</span></span>

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

<span data-ttu-id="3f280-203">En résumé, préférez les instanciations de tuple entre parenthèses, mais lors de l’utilisation de tuples pour les critères spéciaux ou une valeur de retour, il est considéré comme correct pour éviter les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="3f280-203">In summary, prefer parenthesized tuple instantiations, but when using tuples for pattern matching or a return value, it is considered fine to avoid parentheses.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="3f280-204">Mise en forme des déclarations d’union discriminée</span><span class="sxs-lookup"><span data-stu-id="3f280-204">Formatting discriminated union declarations</span></span>

<span data-ttu-id="3f280-205">Mise en retrait `|` dans la définition de type par quatre espaces :</span><span class="sxs-lookup"><span data-stu-id="3f280-205">Indent `|` in type definition by four spaces:</span></span>

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

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="3f280-206">Mise en forme des unions discriminées</span><span class="sxs-lookup"><span data-stu-id="3f280-206">Formatting discriminated unions</span></span>

<span data-ttu-id="3f280-207">Les unions discriminées instanciées qui sont fractionnées sur plusieurs lignes doivent fournir aux données contenues une nouvelle étendue avec mise en retrait :</span><span class="sxs-lookup"><span data-stu-id="3f280-207">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="3f280-208">La parenthèse fermante peut également se trouver sur une nouvelle ligne :</span><span class="sxs-lookup"><span data-stu-id="3f280-208">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="3f280-209">Mise en forme des déclarations d’enregistrement</span><span class="sxs-lookup"><span data-stu-id="3f280-209">Formatting record declarations</span></span>

<span data-ttu-id="3f280-210">Mettre en retrait `{` dans la définition de type par quatre espaces et démarrer la liste de champs sur la même ligne :</span><span class="sxs-lookup"><span data-stu-id="3f280-210">Indent `{` in type definition by four spaces and start the field list on the same line:</span></span>

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

<span data-ttu-id="3f280-211">Il est préférable de placer le jeton d’ouverture sur une nouvelle ligne et le jeton de fermeture sur une nouvelle ligne si vous déclarez des implémentations d’interface ou des membres sur l’enregistrement :</span><span class="sxs-lookup"><span data-stu-id="3f280-211">Placing the opening token on a new line and the closing token on a new line is preferable if you are declaring interface implementations or members on the record:</span></span>

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

## <a name="formatting-records"></a><span data-ttu-id="3f280-212">Mise en forme des enregistrements</span><span class="sxs-lookup"><span data-stu-id="3f280-212">Formatting records</span></span>

<span data-ttu-id="3f280-213">Les enregistrements courts peuvent être écrits en une seule ligne :</span><span class="sxs-lookup"><span data-stu-id="3f280-213">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="3f280-214">Les enregistrements qui sont plus longs doivent utiliser de nouvelles lignes pour les étiquettes :</span><span class="sxs-lookup"><span data-stu-id="3f280-214">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="3f280-215">Le fait de placer le jeton d’ouverture sur une nouvelle ligne, le contenu tabulé sur une étendue et le jeton de fermeture sur une nouvelle ligne sont préférables si vous êtes :</span><span class="sxs-lookup"><span data-stu-id="3f280-215">Placing the opening token on a new line, the contents tabbed over one scope, and the closing token on a new line is preferable if you are:</span></span>

* <span data-ttu-id="3f280-216">Déplacement d’enregistrements dans du code avec différentes étendues de mise en retrait</span><span class="sxs-lookup"><span data-stu-id="3f280-216">Moving records around in code with different indentation scopes</span></span>
* <span data-ttu-id="3f280-217">Les rediriger dans une fonction</span><span class="sxs-lookup"><span data-stu-id="3f280-217">Piping them into a function</span></span>

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

<span data-ttu-id="3f280-218">Les mêmes règles s’appliquent aux éléments de liste et de tableau.</span><span class="sxs-lookup"><span data-stu-id="3f280-218">The same rules apply for list and array elements.</span></span>

## <a name="formatting-copy-and-update-record-expressions"></a><span data-ttu-id="3f280-219">Mise en forme des expressions d’enregistrement de copie et de mise à jour</span><span class="sxs-lookup"><span data-stu-id="3f280-219">Formatting copy-and-update record expressions</span></span>

<span data-ttu-id="3f280-220">Une expression d’enregistrement de copie et de mise à jour est toujours un enregistrement, donc des instructions similaires s’appliquent.</span><span class="sxs-lookup"><span data-stu-id="3f280-220">A copy-and-update record expression is still a record, so similar guidelines apply.</span></span>

<span data-ttu-id="3f280-221">Les expressions courtes peuvent tenir sur une seule ligne :</span><span class="sxs-lookup"><span data-stu-id="3f280-221">Short expressions can fit on one line:</span></span>

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

<span data-ttu-id="3f280-222">Les expressions plus longues doivent utiliser de nouvelles lignes :</span><span class="sxs-lookup"><span data-stu-id="3f280-222">Longer expressions should use new lines:</span></span>

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = [ "Zippy"; "George"; "Bungle" ] }
```

<span data-ttu-id="3f280-223">Comme avec les conseils d’enregistrement, vous souhaiterez peut-être dédier des lignes distinctes pour les accolades et mettre en retrait une étendue à droite avec l’expression.</span><span class="sxs-lookup"><span data-stu-id="3f280-223">And as with the record guidance, you may want to dedicate separate lines for the braces and indent one scope to the right with the expression.</span></span> <span data-ttu-id="3f280-224">Dans certains cas spéciaux, tels que l’encapsulation d’une valeur avec un facultatif sans parenthèses, vous devrez peut-être conserver une accolade sur une ligne :</span><span class="sxs-lookup"><span data-stu-id="3f280-224">In some special cases, such as wrapping a value with an optional without parentheses, you may need to keep a brace on one line:</span></span>

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

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="3f280-225">Mise en forme des listes et des tableaux</span><span class="sxs-lookup"><span data-stu-id="3f280-225">Formatting lists and arrays</span></span>

<span data-ttu-id="3f280-226">Écrire `x :: l` avec des espaces autour de l' `::` opérateur ( `::` est un opérateur infixe, par conséquent entouré d’espaces).</span><span class="sxs-lookup"><span data-stu-id="3f280-226">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces).</span></span>

<span data-ttu-id="3f280-227">La liste et les tableaux déclarés sur une seule ligne doivent avoir un espace après le crochet ouvrant et avant le crochet fermant :</span><span class="sxs-lookup"><span data-stu-id="3f280-227">List and arrays declared on a single line should have a space after the opening bracket and before the closing bracket:</span></span>

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

<span data-ttu-id="3f280-228">Utilisez toujours au moins un espace entre deux opérateurs similaires à des accolades.</span><span class="sxs-lookup"><span data-stu-id="3f280-228">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="3f280-229">Par exemple, laissez un espace entre un `[` et un `{` .</span><span class="sxs-lookup"><span data-stu-id="3f280-229">For example, leave a space between a `[` and a `{`.</span></span>

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

<span data-ttu-id="3f280-230">La même règle s’applique pour les listes ou les tableaux de tuples.</span><span class="sxs-lookup"><span data-stu-id="3f280-230">The same guideline applies for lists or arrays of tuples.</span></span>

<span data-ttu-id="3f280-231">Les listes et les tableaux répartis sur plusieurs lignes suivent une règle similaire, à l’instar des enregistrements :</span><span class="sxs-lookup"><span data-stu-id="3f280-231">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

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

<span data-ttu-id="3f280-232">Et comme avec les enregistrements, la déclaration de l’ouverture et des crochets fermants sur leur propre ligne permet de faciliter le déplacement du code et de rediriger les fonctions vers les fonctions.</span><span class="sxs-lookup"><span data-stu-id="3f280-232">And as with records, declaring the opening and closing brackets on their own line will make moving code around and piping into functions easier.</span></span>

<span data-ttu-id="3f280-233">Lors de la génération de tableaux et de listes par programmation, préférez `->` `do ... yield` quand une valeur est toujours générée :</span><span class="sxs-lookup"><span data-stu-id="3f280-233">When generating arrays and lists programmatically, prefer `->` over `do ... yield` when a value is always generated:</span></span>

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x * x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x * x ]
```

<span data-ttu-id="3f280-234">Les versions antérieures du langage F # nécessitaient `yield` de spécifier dans des situations où les données peuvent être générées de manière conditionnelle, ou il peut y avoir des expressions consécutives à évaluer.</span><span class="sxs-lookup"><span data-stu-id="3f280-234">Older versions of the F# language required specifying `yield` in situations where data may be generated conditionally, or there may be consecutive expressions to be evaluated.</span></span> <span data-ttu-id="3f280-235">Préférez omettre ces `yield` Mots clés sauf si vous devez compiler avec une version plus ancienne du langage F # :</span><span class="sxs-lookup"><span data-stu-id="3f280-235">Prefer omitting these `yield` keywords unless you must compile with an older F# language version:</span></span>

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

<span data-ttu-id="3f280-236">Dans certains cas, `do...yield` peut contribuer à la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="3f280-236">In some cases, `do...yield` may aid in readability.</span></span> <span data-ttu-id="3f280-237">Ces cas, bien que subjectives, doivent être pris en considération.</span><span class="sxs-lookup"><span data-stu-id="3f280-237">These cases, though subjective, should be taken into consideration.</span></span>

## <a name="formatting-if-expressions"></a><span data-ttu-id="3f280-238">Mettre en forme si des expressions</span><span class="sxs-lookup"><span data-stu-id="3f280-238">Formatting if expressions</span></span>

<span data-ttu-id="3f280-239">La mise en retrait des conditions dépend de la taille et de la complexité des expressions qui les composent.</span><span class="sxs-lookup"><span data-stu-id="3f280-239">Indentation of conditionals depends on the size and complexity of the expressions that make them up.</span></span>
<span data-ttu-id="3f280-240">Écrivez-les sur une seule ligne lorsque :</span><span class="sxs-lookup"><span data-stu-id="3f280-240">Write them on one line when:</span></span>

- <span data-ttu-id="3f280-241">`cond`, `e1` et `e2` sont courts</span><span class="sxs-lookup"><span data-stu-id="3f280-241">`cond`, `e1`, and `e2` are short</span></span>
- <span data-ttu-id="3f280-242">`e1` et ne `e2` sont pas des `if/then/else` expressions elles-mêmes.</span><span class="sxs-lookup"><span data-stu-id="3f280-242">`e1` and `e2` are not `if/then/else` expressions themselves.</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="3f280-243">Si l’une des expressions est multiligne ou `if/then/else` expressions.</span><span class="sxs-lookup"><span data-stu-id="3f280-243">If any of the expressions are multi-line or `if/then/else` expressions.</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="3f280-244">Plusieurs conditionnels avec `elif` et `else` sont mis en retrait à la même portée que le `if` lorsqu’ils suivent les règles des expressions d’une ligne `if/then/else` .</span><span class="sxs-lookup"><span data-stu-id="3f280-244">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if` when they follow the rules of the one line `if/then/else` expressions.</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

<span data-ttu-id="3f280-245">Si l’une des conditions ou les expressions est multiligne, l’expression entière `if/then/else` est multiligne :</span><span class="sxs-lookup"><span data-stu-id="3f280-245">If any of the conditions or expressions is multi-line, the entire `if/then/else` expression is multi-line:</span></span>

```fsharp
if cond1 then
    e1
elif cond2 then
    e2
elif cond3 then
    e3
else
    e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="3f280-246">Constructions de critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="3f280-246">Pattern matching constructs</span></span>

<span data-ttu-id="3f280-247">Utilisez une `|` clause for each d’une correspondance sans mise en retrait.</span><span class="sxs-lookup"><span data-stu-id="3f280-247">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="3f280-248">Si l’expression est brève, vous pouvez envisager d’utiliser une seule ligne si chaque sous-expression est également simple.</span><span class="sxs-lookup"><span data-stu-id="3f280-248">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

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

<span data-ttu-id="3f280-249">Si l’expression à droite de la flèche de critères spéciaux est trop grande, déplacez-la vers la ligne suivante, en mettant en retrait une étape de la `match` / `|` .</span><span class="sxs-lookup"><span data-stu-id="3f280-249">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="3f280-250">Les critères spéciaux des fonctions anonymes, à partir de `function` , ne doivent généralement pas être mis en retrait trop loin.</span><span class="sxs-lookup"><span data-stu-id="3f280-250">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="3f280-251">Par exemple, la mise en retrait d’une étendue comme suit est correcte :</span><span class="sxs-lookup"><span data-stu-id="3f280-251">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="3f280-252">Les critères spéciaux dans les fonctions définies par `let` ou `let rec` doivent être mis en retrait à quatre espaces après le démarrage de `let` , même si le `function` mot clé est utilisé :</span><span class="sxs-lookup"><span data-stu-id="3f280-252">Pattern matching in functions defined by `let` or `let rec` should be indented four spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="3f280-253">Nous vous déconseillons d’aligner les flèches.</span><span class="sxs-lookup"><span data-stu-id="3f280-253">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="3f280-254">Mise en forme des expressions try/with</span><span class="sxs-lookup"><span data-stu-id="3f280-254">Formatting try/with expressions</span></span>

<span data-ttu-id="3f280-255">Les critères spéciaux sur le type d’exception doivent être mis en retrait au même niveau que `with` .</span><span class="sxs-lookup"><span data-stu-id="3f280-255">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

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

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="3f280-256">Mise en forme de l’application de paramètre de fonction</span><span class="sxs-lookup"><span data-stu-id="3f280-256">Formatting function parameter application</span></span>

<span data-ttu-id="3f280-257">En général, la plupart des paramètres de fonction sont exécutés sur la même ligne.</span><span class="sxs-lookup"><span data-stu-id="3f280-257">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="3f280-258">Si vous souhaitez appliquer des paramètres à une fonction sur une nouvelle ligne, mettez-les en retrait d’une seule étendue.</span><span class="sxs-lookup"><span data-stu-id="3f280-258">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

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

<span data-ttu-id="3f280-259">Les mêmes instructions s’appliquent aux expressions lambda comme arguments de fonction.</span><span class="sxs-lookup"><span data-stu-id="3f280-259">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="3f280-260">Si le corps d’une expression lambda, le corps peut avoir une autre ligne, mise en retrait d’une étendue</span><span class="sxs-lookup"><span data-stu-id="3f280-260">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

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

<span data-ttu-id="3f280-261">Toutefois, si le corps d’une expression lambda est plus d’une ligne, envisagez de le factoriser dans une fonction distincte plutôt que d’avoir une construction multiligne appliquée comme argument unique à une fonction.</span><span class="sxs-lookup"><span data-stu-id="3f280-261">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="3f280-262">Mise en forme des opérateurs infixes</span><span class="sxs-lookup"><span data-stu-id="3f280-262">Formatting infix operators</span></span>

<span data-ttu-id="3f280-263">Séparez les opérateurs par des espaces.</span><span class="sxs-lookup"><span data-stu-id="3f280-263">Separate operators by spaces.</span></span> <span data-ttu-id="3f280-264">Les opérateurs et sont des exceptions évidentes à cette règle `!` `.` .</span><span class="sxs-lookup"><span data-stu-id="3f280-264">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="3f280-265">Les expressions infixes sont correctes pour la programmation sur la même colonne :</span><span class="sxs-lookup"><span data-stu-id="3f280-265">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="3f280-266">Mise en forme des opérateurs de pipeline</span><span class="sxs-lookup"><span data-stu-id="3f280-266">Formatting pipeline operators</span></span>

<span data-ttu-id="3f280-267">`|>`Les opérateurs de pipeline doivent se trouver sous les expressions sur lesquelles ils opèrent.</span><span class="sxs-lookup"><span data-stu-id="3f280-267">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

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

### <a name="formatting-modules"></a><span data-ttu-id="3f280-268">Mise en forme des modules</span><span class="sxs-lookup"><span data-stu-id="3f280-268">Formatting modules</span></span>

<span data-ttu-id="3f280-269">Le code d’un module local doit être mis en retrait par rapport au module, mais le code d’un module de niveau supérieur ne doit pas être mis en retrait.</span><span class="sxs-lookup"><span data-stu-id="3f280-269">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="3f280-270">Les éléments d’espace de noms n’ont pas besoin d’être mis en retrait.</span><span class="sxs-lookup"><span data-stu-id="3f280-270">Namespace elements do not have to be indented.</span></span>

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a * a + b * b

module A2 =
    let function2 a b = a * a - b * b
```

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="3f280-271">Mise en forme des expressions et des interfaces d’objet</span><span class="sxs-lookup"><span data-stu-id="3f280-271">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="3f280-272">Les interfaces et les expressions d’objet doivent être alignées de la même façon avec `member` une mise en retrait après quatre espaces.</span><span class="sxs-lookup"><span data-stu-id="3f280-272">Object expressions and interfaces should be aligned in the same way with `member` being indented after four spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="3f280-273">Mise en forme des espaces blancs dans les expressions</span><span class="sxs-lookup"><span data-stu-id="3f280-273">Formatting white space in expressions</span></span>

<span data-ttu-id="3f280-274">Évitez les espaces superflus dans les expressions F #.</span><span class="sxs-lookup"><span data-stu-id="3f280-274">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="3f280-275">Les arguments nommés ne doivent pas non plus avoir d’espace autour de `=` :</span><span class="sxs-lookup"><span data-stu-id="3f280-275">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

### <a name="formatting-constructors-static-members-and-member-invocations"></a><span data-ttu-id="3f280-276">Mise en forme des constructeurs, des membres statiques et des appels de membres</span><span class="sxs-lookup"><span data-stu-id="3f280-276">Formatting constructors, static members, and member invocations</span></span>

<span data-ttu-id="3f280-277">Si l’expression est de type short, séparez les arguments par des espaces et conservez-les en une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="3f280-277">If the expression is short, separate arguments with spaces and keep it in one line.</span></span>

```fsharp
let person = new Person(a1, a2)

let myRegexMatch = Regex.Match(input, regex)

let untypedRes = checker.ParseFile(file, source, opts)
```

<span data-ttu-id="3f280-278">Si l’expression est longue, utilisez les nouvelles lignes et mettez en retrait une étendue, plutôt que de mettre en retrait le crochet.</span><span class="sxs-lookup"><span data-stu-id="3f280-278">If the expression is long, use newlines and indent one scope, rather than indenting to the bracket.</span></span>

```fsharp
let person =
    new Person(
        argument1,
        argument2
    )

let myRegexMatch =
    Regex.Match(
        "my longer input string with some interesting content in it",
        "myRegexPattern"
    )

let untypedRes =
    checker.ParseFile(
        fileName,
        sourceText,
        parsingOptionsWithDefines
    )
```

## <a name="formatting-attributes"></a><span data-ttu-id="3f280-279">Attributs de mise en forme</span><span class="sxs-lookup"><span data-stu-id="3f280-279">Formatting attributes</span></span>

<span data-ttu-id="3f280-280">Les [attributs](../language-reference/attributes.md) sont placés au-dessus d’une construction :</span><span class="sxs-lookup"><span data-stu-id="3f280-280">[Attributes](../language-reference/attributes.md) are placed above a construct:</span></span>

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

<span data-ttu-id="3f280-281">Ils doivent être placés après toute documentation XML :</span><span class="sxs-lookup"><span data-stu-id="3f280-281">They should go after any XML documentation:</span></span>

```fsharp
/// Module with some things in it.
[<RequireQualifiedAccess>]
module M =
    let f x = x
```

### <a name="formatting-attributes-on-parameters"></a><span data-ttu-id="3f280-282">Mise en forme des attributs sur les paramètres</span><span class="sxs-lookup"><span data-stu-id="3f280-282">Formatting attributes on parameters</span></span>

<span data-ttu-id="3f280-283">Les attributs peuvent également être placés sur des paramètres.</span><span class="sxs-lookup"><span data-stu-id="3f280-283">Attributes can also be placed on parameters.</span></span> <span data-ttu-id="3f280-284">Dans ce cas, placez ensuite sur la même ligne que le paramètre et avant le nom :</span><span class="sxs-lookup"><span data-stu-id="3f280-284">In this case, place then on the same line as the parameter and before the name:</span></span>

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a><span data-ttu-id="3f280-285">Mise en forme de plusieurs attributs</span><span class="sxs-lookup"><span data-stu-id="3f280-285">Formatting multiple attributes</span></span>

<span data-ttu-id="3f280-286">Quand plusieurs attributs sont appliqués à une construction qui n’est pas un paramètre, ils doivent être placés de façon à ce qu’il y ait un attribut par ligne :</span><span class="sxs-lookup"><span data-stu-id="3f280-286">When multiple attributes are applied to a construct that is not a parameter, they should be placed such that there is one attribute per line:</span></span>

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="3f280-287">Lorsqu’ils sont appliqués à un paramètre, ils doivent se trouver sur la même ligne et être séparés par un `;` séparateur.</span><span class="sxs-lookup"><span data-stu-id="3f280-287">When applied to a parameter, they must be on the same line and separated by a `;` separator.</span></span>

## <a name="formatting-literals"></a><span data-ttu-id="3f280-288">Mise en forme des littéraux</span><span class="sxs-lookup"><span data-stu-id="3f280-288">Formatting literals</span></span>

<span data-ttu-id="3f280-289">Les [littéraux F #](../language-reference/literals.md) utilisant l' `Literal` attribut doivent placer l’attribut sur sa propre ligne et utiliser la dénomination casse Pascal :</span><span class="sxs-lookup"><span data-stu-id="3f280-289">[F# literals](../language-reference/literals.md) using the `Literal` attribute should place the attribute on its own line and use PascalCase naming:</span></span>

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

<span data-ttu-id="3f280-290">Évitez de placer l’attribut sur la même ligne que la valeur.</span><span class="sxs-lookup"><span data-stu-id="3f280-290">Avoid placing the attribute on the same line as the value.</span></span>

## <a name="formatting-computation-expression-operations"></a><span data-ttu-id="3f280-291">Mise en forme des opérations d’expression de calcul</span><span class="sxs-lookup"><span data-stu-id="3f280-291">Formatting computation expression operations</span></span>

<span data-ttu-id="3f280-292">Lors de la création d’opérations personnalisées pour des [expressions de calcul](../language-reference/computation-expressions.md), il est recommandé d’utiliser l’affectation de noms la casse mixte :</span><span class="sxs-lookup"><span data-stu-id="3f280-292">When creating custom operations for [computation expressions](../language-reference/computation-expressions.md), it is recommended to use camelCase naming:</span></span>

```fsharp
type MathBuilder () =
    member _.Yield _ = 0

    [<CustomOperation("addOne")>]
    member _.AddOne (state: int) =
        state + 1

    [<CustomOperation("subtractOne")>]
    member _.SubtractOne (state: int) =
        state - 1

    [<CustomOperation("divideBy")>]
    member _.DivideBy (state: int, divisor: int) =
        state / divisor

    [<CustomOperation("multiplyBy")>]
    member _.MultiplyBy (state: int, factor: int) =
        state * factor

let math = MathBuilder()

// 10
let myNumber =
    math {
        addOne
        addOne
        addOne

        subtractOne

        divideBy 2

        multiplyBy 10
    }
```

<span data-ttu-id="3f280-293">Le domaine qui est modélisé doit finalement conduire la Convention d’affectation de noms.</span><span class="sxs-lookup"><span data-stu-id="3f280-293">The domain that's being modeled should ultimately drive the naming convention.</span></span>
<span data-ttu-id="3f280-294">S’il est idiomatique d’utiliser une convention différente, cette convention doit être utilisée à la place.</span><span class="sxs-lookup"><span data-stu-id="3f280-294">If it is idiomatic to use a different convention, that convention should be used instead.</span></span>
