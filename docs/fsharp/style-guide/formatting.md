---
title: Indications de mise en forme du code F#
description: 'Découvrez les instructions de mise en forme du code F #.'
ms.date: 08/31/2020
ms.openlocfilehash: b4b70d86b36f2ba50318cb50e54d65cc6abff450
ms.sourcegitcommit: f8cd3ef517ee177c99feed944824c27d208cc0d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2021
ms.locfileid: "98570227"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="04d84-103">Indications de mise en forme du code F#</span><span class="sxs-lookup"><span data-stu-id="04d84-103">F# code formatting guidelines</span></span>

<span data-ttu-id="04d84-104">Cet article fournit des instructions sur la façon de mettre en forme votre code afin que votre code F # soit :</span><span class="sxs-lookup"><span data-stu-id="04d84-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="04d84-105">Plus lisible</span><span class="sxs-lookup"><span data-stu-id="04d84-105">More legible</span></span>
* <span data-ttu-id="04d84-106">Conformément aux conventions appliquées par les outils de mise en forme dans Visual Studio et d’autres éditeurs</span><span class="sxs-lookup"><span data-stu-id="04d84-106">In accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="04d84-107">Similaire à un autre code en ligne</span><span class="sxs-lookup"><span data-stu-id="04d84-107">Similar to other code online</span></span>

<span data-ttu-id="04d84-108">Ces instructions sont basées sur [un guide exhaustif des conventions de mise en forme F #](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) par [Anh-fumier Phan](https://github.com/dungpa).</span><span class="sxs-lookup"><span data-stu-id="04d84-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="04d84-109">Règles générales pour la mise en retrait</span><span class="sxs-lookup"><span data-stu-id="04d84-109">General rules for indentation</span></span>

<span data-ttu-id="04d84-110">F # utilise des espaces blancs significatifs par défaut.</span><span class="sxs-lookup"><span data-stu-id="04d84-110">F# uses significant white space by default.</span></span> <span data-ttu-id="04d84-111">Les instructions suivantes sont destinées à vous aider à jongler avec les défis que cela peut imposer.</span><span class="sxs-lookup"><span data-stu-id="04d84-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="04d84-112">Utilisation des espaces</span><span class="sxs-lookup"><span data-stu-id="04d84-112">Using spaces</span></span>

<span data-ttu-id="04d84-113">Lorsque la mise en retrait est requise, vous devez utiliser des espaces, et non des tabulations.</span><span class="sxs-lookup"><span data-stu-id="04d84-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="04d84-114">Au moins un espace est requis.</span><span class="sxs-lookup"><span data-stu-id="04d84-114">At least one space is required.</span></span> <span data-ttu-id="04d84-115">Votre organisation peut créer des normes de codage pour spécifier le nombre d’espaces à utiliser pour la mise en retrait ; deux, trois ou quatre espaces de mise en retrait à chaque niveau de mise en retrait sont typiques.</span><span class="sxs-lookup"><span data-stu-id="04d84-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three, or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="04d84-116">**Nous vous recommandons quatre espaces par retrait.**</span><span class="sxs-lookup"><span data-stu-id="04d84-116">**We recommend four spaces per indentation.**</span></span>

<span data-ttu-id="04d84-117">Ceci dit, la mise en retrait des programmes est une question subjective.</span><span class="sxs-lookup"><span data-stu-id="04d84-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="04d84-118">Les variations sont OK, mais la première règle que vous devez suivre est la *cohérence de la mise en retrait*.</span><span class="sxs-lookup"><span data-stu-id="04d84-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="04d84-119">Choisissez un style de mise en retrait généralement accepté et utilisez-le systématiquement tout au long de votre code base.</span><span class="sxs-lookup"><span data-stu-id="04d84-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-white-space"></a><span data-ttu-id="04d84-120">Mise en forme des espaces blancs</span><span class="sxs-lookup"><span data-stu-id="04d84-120">Formatting white space</span></span>

<span data-ttu-id="04d84-121">F # est sensible à l’espace blanc.</span><span class="sxs-lookup"><span data-stu-id="04d84-121">F# is white space sensitive.</span></span> <span data-ttu-id="04d84-122">Bien que la plupart des sémantiques de l’espace blanc soient couvertes par une mise en retrait appropriée, il y a d’autres éléments à prendre en compte.</span><span class="sxs-lookup"><span data-stu-id="04d84-122">Although most semantics from white space are covered by proper indentation, there are some other things to consider.</span></span>

### <a name="formatting-operators-in-arithmetic-expressions"></a><span data-ttu-id="04d84-123">Mise en forme des opérateurs dans les expressions arithmétiques</span><span class="sxs-lookup"><span data-stu-id="04d84-123">Formatting operators in arithmetic expressions</span></span>

<span data-ttu-id="04d84-124">Utilisez toujours un espace blanc autour des expressions arithmétiques binaires :</span><span class="sxs-lookup"><span data-stu-id="04d84-124">Always use white space around binary arithmetic expressions:</span></span>

```fsharp
let subtractThenAdd x = x - 1 + 3
```

<span data-ttu-id="04d84-125">`-`Les opérateurs unaires doivent toujours être suivis immédiatement de la valeur qu’ils annulent :</span><span class="sxs-lookup"><span data-stu-id="04d84-125">Unary `-` operators should always be immediately followed by the value they are negating:</span></span>

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

<span data-ttu-id="04d84-126">L’ajout d’un espace blanc après l' `-` opérateur peut entraîner des confusions pour d’autres.</span><span class="sxs-lookup"><span data-stu-id="04d84-126">Adding a white-space character after the `-` operator can lead to confusion for others.</span></span>

<span data-ttu-id="04d84-127">En résumé, il est important de toujours :</span><span class="sxs-lookup"><span data-stu-id="04d84-127">In summary, it's important to always:</span></span>

* <span data-ttu-id="04d84-128">Entourer les opérateurs binaires avec un espace blanc</span><span class="sxs-lookup"><span data-stu-id="04d84-128">Surround binary operators with white space</span></span>
* <span data-ttu-id="04d84-129">Ne jamais avoir d’espace blanc de fin après un opérateur unaire</span><span class="sxs-lookup"><span data-stu-id="04d84-129">Never have trailing white space after a unary operator</span></span>

<span data-ttu-id="04d84-130">L’indication de l’opérateur arithmétique binaire est particulièrement importante.</span><span class="sxs-lookup"><span data-stu-id="04d84-130">The binary arithmetic operator guideline is especially important.</span></span> <span data-ttu-id="04d84-131">L’échec de l’entourage d’un `-` opérateur binaire, lorsqu’il est associé à certains choix de mise en forme, peut entraîner son interprétation comme unaire `-` .</span><span class="sxs-lookup"><span data-stu-id="04d84-131">Failing to surround a binary `-` operator, when combined with certain formatting choices, could lead to interpreting it as a unary `-`.</span></span>

### <a name="surround-a-custom-operator-definition-with-white-space"></a><span data-ttu-id="04d84-132">Entourer une définition d’opérateur personnalisée avec un espace blanc</span><span class="sxs-lookup"><span data-stu-id="04d84-132">Surround a custom operator definition with white space</span></span>

<span data-ttu-id="04d84-133">Utilisez toujours des espaces blancs pour entourer une définition d’opérateur :</span><span class="sxs-lookup"><span data-stu-id="04d84-133">Always use white space to surround an operator definition:</span></span>

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

<span data-ttu-id="04d84-134">Pour tout opérateur personnalisé qui commence par `*` et qui contient plusieurs caractères, vous devez ajouter un espace blanc au début de la définition pour éviter une ambiguïté du compilateur.</span><span class="sxs-lookup"><span data-stu-id="04d84-134">For any custom operator that starts with `*` and that has more than one character, you need to add a white space to the beginning of the definition to avoid a compiler ambiguity.</span></span> <span data-ttu-id="04d84-135">Pour cette raison, nous vous recommandons d’entourer simplement les définitions de tous les opérateurs avec un seul espace blanc.</span><span class="sxs-lookup"><span data-stu-id="04d84-135">Because of this, we recommend that you simply surround the definitions of all operators with a single white-space character.</span></span>

### <a name="surround-function-parameter-arrows-with-white-space"></a><span data-ttu-id="04d84-136">Placer les flèches de paramètre de fonction avec un espace blanc</span><span class="sxs-lookup"><span data-stu-id="04d84-136">Surround function parameter arrows with white space</span></span>

<span data-ttu-id="04d84-137">Lors de la définition de la signature d’une fonction, utilisez un espace blanc autour du `->` symbole :</span><span class="sxs-lookup"><span data-stu-id="04d84-137">When defining the signature of a function, use white space around the `->` symbol:</span></span>

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a><span data-ttu-id="04d84-138">Entourer les arguments de fonction avec un espace blanc</span><span class="sxs-lookup"><span data-stu-id="04d84-138">Surround function arguments with white space</span></span>

<span data-ttu-id="04d84-139">Lors de la définition d’une fonction, utilisez un espace blanc autour de chaque argument.</span><span class="sxs-lookup"><span data-stu-id="04d84-139">When defining a function, use white space around each argument.</span></span>

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="avoid-name-sensitive-alignments"></a><span data-ttu-id="04d84-140">Éviter les alignements respectant le nom</span><span class="sxs-lookup"><span data-stu-id="04d84-140">Avoid name-sensitive alignments</span></span>

<span data-ttu-id="04d84-141">En général, recherchez pour éviter la mise en retrait et l’alignement sensibles au nom :</span><span class="sxs-lookup"><span data-stu-id="04d84-141">In general, seek to avoid indentation and alignment that is sensitive to naming:</span></span>

```fsharp
// OK
let myLongValueName =
    someExpression
    |> anotherExpression


// Bad
let myLongValueName = someExpression
                      |> anotherExpression
```

<span data-ttu-id="04d84-142">Cela est parfois appelé « alignement personnel » ou « mise en retrait personnel ».</span><span class="sxs-lookup"><span data-stu-id="04d84-142">This is sometimes called “vanity alignment” or “vanity indentation”.</span></span> <span data-ttu-id="04d84-143">Les principales raisons de l’éviter sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="04d84-143">The primary reasons for avoiding this are:</span></span>

* <span data-ttu-id="04d84-144">Le code important est déplacé vers la droite</span><span class="sxs-lookup"><span data-stu-id="04d84-144">Important code is moved far to the right</span></span>
* <span data-ttu-id="04d84-145">Il reste moins de largeur pour le code réel</span><span class="sxs-lookup"><span data-stu-id="04d84-145">There is less width left for the actual code</span></span>
* <span data-ttu-id="04d84-146">L’attribution d’un nouveau nom peut rompre l’alignement</span><span class="sxs-lookup"><span data-stu-id="04d84-146">Renaming can break the alignment</span></span>

<span data-ttu-id="04d84-147">Procédez de la même façon pour que `do` / `do!` la mise en retrait reste cohérente avec `let` / `let!` .</span><span class="sxs-lookup"><span data-stu-id="04d84-147">Do the same for `do`/`do!` in order to keep the indentation consistent with `let`/`let!`.</span></span> <span data-ttu-id="04d84-148">Voici un exemple d’utilisation `do` de dans une classe :</span><span class="sxs-lookup"><span data-stu-id="04d84-148">Here is an example using `do` in a class:</span></span>

```fsharp
// OK
type Foo () =
    let foo =
        fooBarBaz
        |> loremIpsumDolorSitAmet
        |> theQuickBrownFoxJumpedOverTheLazyDog
    do
        fooBarBaz
        |> loremIpsumDolorSitAmet
        |> theQuickBrownFoxJumpedOverTheLazyDog

// Bad - notice the "do" expression is indented one space less than the `let` expression
type Foo () =
    let foo =
        fooBarBaz
        |> loremIpsumDolorSitAmet
        |> theQuickBrownFoxJumpedOverTheLazyDog
    do fooBarBaz
       |> loremIpsumDolorSitAmet
       |> theQuickBrownFoxJumpedOverTheLazyDog
```

<span data-ttu-id="04d84-149">Voici un exemple d' `do!` utilisation de deux espaces de mise en retrait (parce qu' `do!` il n’y a pas de différence entre les approches lors de l’utilisation de 4 espaces de mise en retrait) :</span><span class="sxs-lookup"><span data-stu-id="04d84-149">Here is an example with `do!` using 2 spaces of indentation (because with `do!` there is coincidentally no difference between the approaches when using 4 spaces of indentation):</span></span>

```fsharp
// OK
async {
  let! foo =
    fooBarBaz
    |> loremIpsumDolorSitAmet
    |> theQuickBrownFoxJumpedOverTheLazyDog
  do!
    fooBarBaz
    |> loremIpsumDolorSitAmet
    |> theQuickBrownFoxJumpedOverTheLazyDog
}

// Bad - notice the "do!" expression is indented two spaces more than the `let!` expression
async {
  let! foo =
    fooBarBaz
    |> loremIpsumDolorSitAmet
    |> theQuickBrownFoxJumpedOverTheLazyDog
  do! fooBarBaz
      |> loremIpsumDolorSitAmet
      |> theQuickBrownFoxJumpedOverTheLazyDog
}
```

### <a name="place-parameters-on-a-new-line-for-long-definitions"></a><span data-ttu-id="04d84-150">Placer des paramètres sur une nouvelle ligne pour les définitions longues</span><span class="sxs-lookup"><span data-stu-id="04d84-150">Place parameters on a new line for long definitions</span></span>

<span data-ttu-id="04d84-151">Si vous avez une définition de fonction longue, placez les paramètres sur de nouvelles lignes et mettez-les en retrait pour qu’ils correspondent au niveau de mise en retrait du paramètre suivant.</span><span class="sxs-lookup"><span data-stu-id="04d84-151">If you have a long function definition, place the parameters on new lines and indent them to match the indentation level of the subsequent parameter.</span></span>

```fsharp
module M =
    let longFunctionWithLotsOfParameters
        (aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        =
        // ... the body of the method follows

    let longFunctionWithLotsOfParametersAndReturnType
        (aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        : ReturnType =
        // ... the body of the method follows

    let longFunctionWithLongTupleParameter
        (
            aVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse
        ) =
        // ... the body of the method follows

    let longFunctionWithLongTupleParameterAndReturnType
        (
            aVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse
        ) : ReturnType =
        // ... the body of the method follows
```

<span data-ttu-id="04d84-152">Cela s’applique également aux membres, constructeurs et paramètres à l’aide de tuples :</span><span class="sxs-lookup"><span data-stu-id="04d84-152">This also applies to members, constructors, and parameters using tuples:</span></span>

```fsharp
type TM() =
    member _.LongMethodWithLotsOfParameters
        (
            aVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse
        ) =
        // ... the body of the method

type TC
    (
        aVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse,
        aSecondVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse,
        aThirdVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse
    ) =
    // ... the body of the class follows
```

<span data-ttu-id="04d84-153">Si les paramètres sont currified, placez le `=` caractère avec n’importe quel type de retour sur une nouvelle ligne :</span><span class="sxs-lookup"><span data-stu-id="04d84-153">If the parameters are currified, place the `=` character along with any return type on a new line:</span></span>

```fsharp
type C() =
    member _.LongMethodWithLotsOfCurrifiedParamsAndReturnType
        (aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        : ReturnType =
        // ... the body of the method
    member _.LongMethodWithLotsOfCurrifiedParams
        (aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        =
        // ... the body of the method
```

<span data-ttu-id="04d84-154">Il s’agit d’un moyen d’éviter des lignes trop longues (dans le cas où le type de retour peut avoir un nom long) et d’avoir moins de dommages lors de l’ajout de paramètres.</span><span class="sxs-lookup"><span data-stu-id="04d84-154">This is a way to avoid too long lines (in case return type might have long name) and have less line-damage when adding parameters.</span></span>

### <a name="type-annotations"></a><span data-ttu-id="04d84-155">Annotations de type</span><span class="sxs-lookup"><span data-stu-id="04d84-155">Type annotations</span></span>

#### <a name="right-pad-function-argument-type-annotations"></a><span data-ttu-id="04d84-156">Annotations de type d’argument de fonction de remplissage à droite</span><span class="sxs-lookup"><span data-stu-id="04d84-156">Right-pad function argument type annotations</span></span>

<span data-ttu-id="04d84-157">Quand vous définissez des arguments avec des annotations de type, utilisez un espace blanc après le `:` symbole :</span><span class="sxs-lookup"><span data-stu-id="04d84-157">When defining arguments with type annotations, use white space after the `:` symbol:</span></span>

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a><span data-ttu-id="04d84-158">Entourer les annotations de type de retour avec des espaces blancs</span><span class="sxs-lookup"><span data-stu-id="04d84-158">Surround return type annotations with white space</span></span>

<span data-ttu-id="04d84-159">Dans une fonction de liaison ou une annotation de type valeur (type de retour dans le cas d’une fonction), utilisez un espace blanc avant et après le `:` symbole :</span><span class="sxs-lookup"><span data-stu-id="04d84-159">In a let-bound function or value type annotation (return type in the case of a function), use white space before and after the `:` symbol:</span></span>

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="04d84-160">Mise en forme des lignes vides</span><span class="sxs-lookup"><span data-stu-id="04d84-160">Formatting blank lines</span></span>

* <span data-ttu-id="04d84-161">Séparez les définitions de fonction et de classe de niveau supérieur par deux lignes vides.</span><span class="sxs-lookup"><span data-stu-id="04d84-161">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="04d84-162">Les définitions de méthode à l’intérieur d’une classe sont séparées par une seule ligne vide.</span><span class="sxs-lookup"><span data-stu-id="04d84-162">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="04d84-163">Des lignes vides supplémentaires peuvent être utilisées (avec modération) pour séparer les groupes de fonctions associées.</span><span class="sxs-lookup"><span data-stu-id="04d84-163">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="04d84-164">Des lignes vides peuvent être omises entre une série de lignes associées (par exemple, un ensemble d’implémentations factices).</span><span class="sxs-lookup"><span data-stu-id="04d84-164">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="04d84-165">Utilisez des lignes vides dans les fonctions, avec modération, pour indiquer les sections logiques.</span><span class="sxs-lookup"><span data-stu-id="04d84-165">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="04d84-166">Mise en forme des commentaires</span><span class="sxs-lookup"><span data-stu-id="04d84-166">Formatting comments</span></span>

<span data-ttu-id="04d84-167">Préférez généralement plusieurs commentaires à deux barres obliques par rapport aux commentaires de bloc de type ML.</span><span class="sxs-lookup"><span data-stu-id="04d84-167">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="04d84-168">Les commentaires insérés doivent mettre en majuscule la première lettre.</span><span class="sxs-lookup"><span data-stu-id="04d84-168">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="04d84-169">Conventions d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="04d84-169">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="04d84-170">Utilisez la casse mixte pour les valeurs et les fonctions liées à la classe, à l’expression et liées aux modèles</span><span class="sxs-lookup"><span data-stu-id="04d84-170">Use camelCase for class-bound, expression-bound, and pattern-bound values and functions</span></span>

<span data-ttu-id="04d84-171">Il est courant et accepté le style F # pour utiliser la casse mixte pour tous les noms liés en tant que variables locales ou dans les définitions de fonctions et les correspondances de modèle.</span><span class="sxs-lookup"><span data-stu-id="04d84-171">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="04d84-172">Les fonctions liées localement dans les classes doivent également utiliser la casse mixte.</span><span class="sxs-lookup"><span data-stu-id="04d84-172">Locally bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="04d84-173">Utiliser la casse mixte pour les fonctions publiques liées aux modules</span><span class="sxs-lookup"><span data-stu-id="04d84-173">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="04d84-174">Quand une fonction liée à un module fait partie d’une API publique, elle doit utiliser la casse mixte :</span><span class="sxs-lookup"><span data-stu-id="04d84-174">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="04d84-175">Utilisez la casse mixte pour les valeurs et les fonctions liées aux modules internes et privés</span><span class="sxs-lookup"><span data-stu-id="04d84-175">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="04d84-176">Utilisez la casse mixte pour les valeurs à liaison de module privées, y compris les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="04d84-176">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="04d84-177">Fonctions ad hoc dans les scripts</span><span class="sxs-lookup"><span data-stu-id="04d84-177">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="04d84-178">Valeurs constituant l’implémentation interne d’un module ou d’un type</span><span class="sxs-lookup"><span data-stu-id="04d84-178">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="04d84-179">Utiliser la casse mixte pour les paramètres</span><span class="sxs-lookup"><span data-stu-id="04d84-179">Use camelCase for parameters</span></span>

<span data-ttu-id="04d84-180">Tous les paramètres doivent utiliser la casse mixte conformément aux conventions d’affectation de noms .NET.</span><span class="sxs-lookup"><span data-stu-id="04d84-180">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="04d84-181">Utiliser casse Pascal pour les modules</span><span class="sxs-lookup"><span data-stu-id="04d84-181">Use PascalCase for modules</span></span>

<span data-ttu-id="04d84-182">Tous les modules (de niveau supérieur, interne, privé, imbriqué) doivent utiliser casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="04d84-182">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="04d84-183">Utiliser casse Pascal pour les déclarations de type, les membres et les étiquettes</span><span class="sxs-lookup"><span data-stu-id="04d84-183">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="04d84-184">Les classes, les interfaces, les structures, les énumérations, les délégués, les enregistrements et les unions discriminées doivent toutes être nommées avec casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="04d84-184">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="04d84-185">Les membres dans les types et les étiquettes pour les enregistrements et les unions discriminées doivent également utiliser casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="04d84-185">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="04d84-186">Utiliser casse Pascal pour les constructions intrinsèques à .NET</span><span class="sxs-lookup"><span data-stu-id="04d84-186">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="04d84-187">Les espaces de noms, les exceptions, les événements et les projets/ `.dll` noms doivent également utiliser casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="04d84-187">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="04d84-188">Non seulement cela rend la consommation des autres langages .NET plus naturelle pour les consommateurs, mais elle est également cohérente avec les conventions de nommage .NET que vous êtes susceptible de rencontrer.</span><span class="sxs-lookup"><span data-stu-id="04d84-188">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="04d84-189">Éviter les traits de soulignement dans les noms</span><span class="sxs-lookup"><span data-stu-id="04d84-189">Avoid underscores in names</span></span>

<span data-ttu-id="04d84-190">Historiquement, certaines bibliothèques F # ont utilisé des traits de soulignement dans les noms.</span><span class="sxs-lookup"><span data-stu-id="04d84-190">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="04d84-191">Toutefois, cela n’est plus largement accepté, en partie parce qu’il est en conflit avec les conventions de nommage .NET.</span><span class="sxs-lookup"><span data-stu-id="04d84-191">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="04d84-192">Cela dit, certains programmeurs F # utilisent des traits de soulignement très largement, en partie pour des raisons historiques, et la tolérance et le respect sont importants.</span><span class="sxs-lookup"><span data-stu-id="04d84-192">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="04d84-193">Toutefois, le style est souvent utilisé par d’autres personnes qui ont le choix de l’utiliser ou non.</span><span class="sxs-lookup"><span data-stu-id="04d84-193">However, the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="04d84-194">Une exception concerne l’interopérabilité avec les composants natifs, où les traits de soulignement sont courants.</span><span class="sxs-lookup"><span data-stu-id="04d84-194">One exception includes interoperating with native components, where underscores are common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="04d84-195">Utiliser les opérateurs F # standard</span><span class="sxs-lookup"><span data-stu-id="04d84-195">Use standard F# operators</span></span>

<span data-ttu-id="04d84-196">Les opérateurs suivants sont définis dans la bibliothèque standard F # et doivent être utilisés au lieu de définir des équivalents.</span><span class="sxs-lookup"><span data-stu-id="04d84-196">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="04d84-197">L’utilisation de ces opérateurs est recommandée, car elle tend à rendre le code plus lisible et idiomatique.</span><span class="sxs-lookup"><span data-stu-id="04d84-197">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="04d84-198">Les développeurs disposant d’un arrière-plan dans OCaml ou d’autres langages de programmation fonctionnelle peuvent être habitués à différents idiomes.</span><span class="sxs-lookup"><span data-stu-id="04d84-198">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="04d84-199">La liste suivante récapitule les opérateurs F # recommandés.</span><span class="sxs-lookup"><span data-stu-id="04d84-199">The following list summarizes the recommended F# operators.</span></span>

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="04d84-200">Utilisez la syntaxe de préfixe pour les génériques ( `Foo<T>` ) de préférence à la syntaxe postfix ( `T Foo` )</span><span class="sxs-lookup"><span data-stu-id="04d84-200">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="04d84-201">F # hérite à la fois du style postfix ML de l’attribution d’un nom aux types génériques (par exemple,), ainsi `int list` que du style .net du préfixe (par exemple, `list<int>` ).</span><span class="sxs-lookup"><span data-stu-id="04d84-201">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="04d84-202">Préférer le style .NET, à l’exception de cinq types spécifiques :</span><span class="sxs-lookup"><span data-stu-id="04d84-202">Prefer the .NET style, except for five specific types:</span></span>

1. <span data-ttu-id="04d84-203">Pour les listes F #, utilisez le formulaire de suffixe : `int list` plutôt que `list<int>` .</span><span class="sxs-lookup"><span data-stu-id="04d84-203">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="04d84-204">Pour les options F #, utilisez le formulaire de suffixe : `int option` plutôt que `option<int>` .</span><span class="sxs-lookup"><span data-stu-id="04d84-204">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="04d84-205">Pour les options de valeur F #, utilisez la forme postfixé : `int voption` plutôt que `voption<int>` .</span><span class="sxs-lookup"><span data-stu-id="04d84-205">For F# Value Options, use the postfix form: `int voption` rather than `voption<int>`.</span></span>
4. <span data-ttu-id="04d84-206">Pour les tableaux F #, utilisez le nom syntaxique `int[]` plutôt que `int array` ou `array<int>` .</span><span class="sxs-lookup"><span data-stu-id="04d84-206">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
5. <span data-ttu-id="04d84-207">Pour les cellules de référence, utilisez `int ref` plutôt que `ref<int>` ou `Ref<int>` .</span><span class="sxs-lookup"><span data-stu-id="04d84-207">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="04d84-208">Pour tous les autres types, utilisez le formulaire de préfixe.</span><span class="sxs-lookup"><span data-stu-id="04d84-208">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="04d84-209">Mise en forme des tuples</span><span class="sxs-lookup"><span data-stu-id="04d84-209">Formatting tuples</span></span>

<span data-ttu-id="04d84-210">Une instanciation de tuple doit être placée entre parenthèses et les virgules de délimitation doivent être suivies d’un seul espace, par exemple : `(1, 2)` , `(x, y, z)` .</span><span class="sxs-lookup"><span data-stu-id="04d84-210">A tuple instantiation should be parenthesized, and the delimiting commas within it should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="04d84-211">Il est généralement admis d’omettre les parenthèses dans les critères spéciaux des tuples :</span><span class="sxs-lookup"><span data-stu-id="04d84-211">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

<span data-ttu-id="04d84-212">Il est également généralement admis à omettre les parenthèses si le tuple est la valeur de retour d’une fonction :</span><span class="sxs-lookup"><span data-stu-id="04d84-212">It is also commonly accepted to omit parentheses if the tuple is the return value of a function:</span></span>

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

<span data-ttu-id="04d84-213">En résumé, préférez les instanciations de tuple entre parenthèses, mais lors de l’utilisation de tuples pour les critères spéciaux ou une valeur de retour, il est considéré comme correct pour éviter les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="04d84-213">In summary, prefer parenthesized tuple instantiations, but when using tuples for pattern matching or a return value, it is considered fine to avoid parentheses.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="04d84-214">Mise en forme des déclarations d’union discriminée</span><span class="sxs-lookup"><span data-stu-id="04d84-214">Formatting discriminated union declarations</span></span>

<span data-ttu-id="04d84-215">Mise en retrait `|` dans la définition de type par quatre espaces :</span><span class="sxs-lookup"><span data-stu-id="04d84-215">Indent `|` in type definition by four spaces:</span></span>

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

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="04d84-216">Mise en forme des unions discriminées</span><span class="sxs-lookup"><span data-stu-id="04d84-216">Formatting discriminated unions</span></span>

<span data-ttu-id="04d84-217">Les unions discriminées instanciées qui sont fractionnées sur plusieurs lignes doivent fournir aux données contenues une nouvelle étendue avec mise en retrait :</span><span class="sxs-lookup"><span data-stu-id="04d84-217">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="04d84-218">La parenthèse fermante peut également se trouver sur une nouvelle ligne :</span><span class="sxs-lookup"><span data-stu-id="04d84-218">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="04d84-219">Mise en forme des déclarations d’enregistrement</span><span class="sxs-lookup"><span data-stu-id="04d84-219">Formatting record declarations</span></span>

<span data-ttu-id="04d84-220">Mettre en retrait `{` dans la définition de type par quatre espaces et démarrer la liste de champs sur la même ligne :</span><span class="sxs-lookup"><span data-stu-id="04d84-220">Indent `{` in type definition by four spaces and start the field list on the same line:</span></span>

```fsharp
// OK
type PostalAddress =
    { Address: string
      City: string
      Zip: string }
    member x.ZipAndCity = $"{x.Zip} {x.City}"

// Not OK
type PostalAddress =
  { Address: string
    City: string
    Zip: string }
    member x.ZipAndCity = $"{x.Zip} {x.City}"

// Unusual in F#
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
```

<span data-ttu-id="04d84-221">Il est préférable de placer le jeton d’ouverture sur une nouvelle ligne et le jeton de fermeture sur une nouvelle ligne si vous déclarez des implémentations d’interface ou des membres sur l’enregistrement :</span><span class="sxs-lookup"><span data-stu-id="04d84-221">Placing the opening token on a new line and the closing token on a new line is preferable if you are declaring interface implementations or members on the record:</span></span>

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
    member x.ZipAndCity = $"{x.Zip} {x.City}"

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a><span data-ttu-id="04d84-222">Mise en forme des enregistrements</span><span class="sxs-lookup"><span data-stu-id="04d84-222">Formatting records</span></span>

<span data-ttu-id="04d84-223">Les enregistrements courts peuvent être écrits en une seule ligne :</span><span class="sxs-lookup"><span data-stu-id="04d84-223">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="04d84-224">Les enregistrements qui sont plus longs doivent utiliser de nouvelles lignes pour les étiquettes :</span><span class="sxs-lookup"><span data-stu-id="04d84-224">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="04d84-225">Le fait de placer le jeton d’ouverture sur une nouvelle ligne, le contenu tabulé sur une étendue et le jeton de fermeture sur une nouvelle ligne sont préférables si vous êtes :</span><span class="sxs-lookup"><span data-stu-id="04d84-225">Placing the opening token on a new line, the contents tabbed over one scope, and the closing token on a new line is preferable if you are:</span></span>

* <span data-ttu-id="04d84-226">Déplacement d’enregistrements dans du code avec différentes étendues de mise en retrait</span><span class="sxs-lookup"><span data-stu-id="04d84-226">Moving records around in code with different indentation scopes</span></span>
* <span data-ttu-id="04d84-227">Les rediriger dans une fonction</span><span class="sxs-lookup"><span data-stu-id="04d84-227">Piping them into a function</span></span>

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
    |> Option.map
        (fun x ->
            {
                MyField = x
            })
```

<span data-ttu-id="04d84-228">Les mêmes règles s’appliquent aux éléments de liste et de tableau.</span><span class="sxs-lookup"><span data-stu-id="04d84-228">The same rules apply for list and array elements.</span></span>

## <a name="formatting-copy-and-update-record-expressions"></a><span data-ttu-id="04d84-229">Mise en forme des expressions d’enregistrement de copie et de mise à jour</span><span class="sxs-lookup"><span data-stu-id="04d84-229">Formatting copy-and-update record expressions</span></span>

<span data-ttu-id="04d84-230">Une expression d’enregistrement de copie et de mise à jour est toujours un enregistrement, donc des instructions similaires s’appliquent.</span><span class="sxs-lookup"><span data-stu-id="04d84-230">A copy-and-update record expression is still a record, so similar guidelines apply.</span></span>

<span data-ttu-id="04d84-231">Les expressions courtes peuvent tenir sur une seule ligne :</span><span class="sxs-lookup"><span data-stu-id="04d84-231">Short expressions can fit on one line:</span></span>

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

<span data-ttu-id="04d84-232">Les expressions plus longues doivent utiliser de nouvelles lignes :</span><span class="sxs-lookup"><span data-stu-id="04d84-232">Longer expressions should use new lines:</span></span>

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = [ "Zippy"; "George"; "Bungle" ] }
```

<span data-ttu-id="04d84-233">Comme avec les conseils d’enregistrement, vous souhaiterez peut-être dédier des lignes distinctes pour les accolades et mettre en retrait une étendue à droite avec l’expression.</span><span class="sxs-lookup"><span data-stu-id="04d84-233">And as with the record guidance, you may want to dedicate separate lines for the braces and indent one scope to the right with the expression.</span></span> <span data-ttu-id="04d84-234">Dans certains cas spéciaux, tels que l’encapsulation d’une valeur avec un facultatif sans parenthèses, vous devrez peut-être conserver une accolade sur une ligne :</span><span class="sxs-lookup"><span data-stu-id="04d84-234">In some special cases, such as wrapping a value with an optional without parentheses, you may need to keep a brace on one line:</span></span>

```fsharp
type S = { F1: int; F2: string }
type State = { Foo: S option }

let state = { Foo = Some { F1 = 1; F2 = "Hello" } }
let newState =
    {
        state with
            Foo =
                Some {
                    F1 = 0
                    F2 = ""
                }
    }
```

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="04d84-235">Mise en forme des listes et des tableaux</span><span class="sxs-lookup"><span data-stu-id="04d84-235">Formatting lists and arrays</span></span>

<span data-ttu-id="04d84-236">Écrire `x :: l` avec des espaces autour de l' `::` opérateur ( `::` est un opérateur infixe, par conséquent entouré d’espaces).</span><span class="sxs-lookup"><span data-stu-id="04d84-236">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces).</span></span>

<span data-ttu-id="04d84-237">La liste et les tableaux déclarés sur une seule ligne doivent avoir un espace après le crochet ouvrant et avant le crochet fermant :</span><span class="sxs-lookup"><span data-stu-id="04d84-237">List and arrays declared on a single line should have a space after the opening bracket and before the closing bracket:</span></span>

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

<span data-ttu-id="04d84-238">Utilisez toujours au moins un espace entre deux opérateurs similaires à des accolades.</span><span class="sxs-lookup"><span data-stu-id="04d84-238">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="04d84-239">Par exemple, laissez un espace entre un `[` et un `{` .</span><span class="sxs-lookup"><span data-stu-id="04d84-239">For example, leave a space between a `[` and a `{`.</span></span>

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

<span data-ttu-id="04d84-240">La même règle s’applique pour les listes ou les tableaux de tuples.</span><span class="sxs-lookup"><span data-stu-id="04d84-240">The same guideline applies for lists or arrays of tuples.</span></span>

<span data-ttu-id="04d84-241">Les listes et les tableaux répartis sur plusieurs lignes suivent une règle similaire, à l’instar des enregistrements :</span><span class="sxs-lookup"><span data-stu-id="04d84-241">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

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

<span data-ttu-id="04d84-242">Et comme avec les enregistrements, la déclaration de l’ouverture et des crochets fermants sur leur propre ligne permet de faciliter le déplacement du code et de rediriger les fonctions vers les fonctions.</span><span class="sxs-lookup"><span data-stu-id="04d84-242">And as with records, declaring the opening and closing brackets on their own line will make moving code around and piping into functions easier.</span></span>

<span data-ttu-id="04d84-243">Lors de la génération de tableaux et de listes par programmation, préférez `->` `do ... yield` quand une valeur est toujours générée :</span><span class="sxs-lookup"><span data-stu-id="04d84-243">When generating arrays and lists programmatically, prefer `->` over `do ... yield` when a value is always generated:</span></span>

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x * x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x * x ]
```

<span data-ttu-id="04d84-244">Les versions antérieures du langage F # nécessitaient `yield` de spécifier dans des situations où les données peuvent être générées de manière conditionnelle, ou il peut y avoir des expressions consécutives à évaluer.</span><span class="sxs-lookup"><span data-stu-id="04d84-244">Older versions of the F# language required specifying `yield` in situations where data may be generated conditionally, or there may be consecutive expressions to be evaluated.</span></span> <span data-ttu-id="04d84-245">Préférez omettre ces `yield` Mots clés sauf si vous devez compiler avec une version plus ancienne du langage F # :</span><span class="sxs-lookup"><span data-stu-id="04d84-245">Prefer omitting these `yield` keywords unless you must compile with an older F# language version:</span></span>

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

<span data-ttu-id="04d84-246">Dans certains cas, `do...yield` peut contribuer à la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="04d84-246">In some cases, `do...yield` may aid in readability.</span></span> <span data-ttu-id="04d84-247">Ces cas, bien que subjectives, doivent être pris en considération.</span><span class="sxs-lookup"><span data-stu-id="04d84-247">These cases, though subjective, should be taken into consideration.</span></span>

## <a name="formatting-if-expressions"></a><span data-ttu-id="04d84-248">Mettre en forme si des expressions</span><span class="sxs-lookup"><span data-stu-id="04d84-248">Formatting if expressions</span></span>

<span data-ttu-id="04d84-249">La mise en retrait des conditions dépend de la taille et de la complexité des expressions qui les composent.</span><span class="sxs-lookup"><span data-stu-id="04d84-249">Indentation of conditionals depends on the size and complexity of the expressions that make them up.</span></span>
<span data-ttu-id="04d84-250">Écrivez-les sur une seule ligne lorsque :</span><span class="sxs-lookup"><span data-stu-id="04d84-250">Write them on one line when:</span></span>

- <span data-ttu-id="04d84-251">`cond`, `e1` et `e2` sont courts</span><span class="sxs-lookup"><span data-stu-id="04d84-251">`cond`, `e1`, and `e2` are short</span></span>
- <span data-ttu-id="04d84-252">`e1` et ne `e2` sont pas des `if/then/else` expressions elles-mêmes.</span><span class="sxs-lookup"><span data-stu-id="04d84-252">`e1` and `e2` are not `if/then/else` expressions themselves.</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="04d84-253">Si l’une des expressions est multiligne ou `if/then/else` expressions.</span><span class="sxs-lookup"><span data-stu-id="04d84-253">If any of the expressions are multi-line or `if/then/else` expressions.</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="04d84-254">Plusieurs conditionnels avec `elif` et `else` sont mis en retrait à la même portée que le `if` lorsqu’ils suivent les règles des expressions d’une ligne `if/then/else` .</span><span class="sxs-lookup"><span data-stu-id="04d84-254">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if` when they follow the rules of the one line `if/then/else` expressions.</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

<span data-ttu-id="04d84-255">Si l’une des conditions ou les expressions est multiligne, l’expression entière `if/then/else` est multiligne :</span><span class="sxs-lookup"><span data-stu-id="04d84-255">If any of the conditions or expressions is multi-line, the entire `if/then/else` expression is multi-line:</span></span>

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

### <a name="pattern-matching-constructs"></a><span data-ttu-id="04d84-256">Constructions de critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="04d84-256">Pattern matching constructs</span></span>

<span data-ttu-id="04d84-257">Utilisez une `|` clause for each d’une correspondance sans mise en retrait.</span><span class="sxs-lookup"><span data-stu-id="04d84-257">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="04d84-258">Si l’expression est brève, vous pouvez envisager d’utiliser une seule ligne si chaque sous-expression est également simple.</span><span class="sxs-lookup"><span data-stu-id="04d84-258">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

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

<span data-ttu-id="04d84-259">Si l’expression à droite de la flèche de critères spéciaux est trop grande, déplacez-la vers la ligne suivante, en mettant en retrait une étape de la `match` / `|` .</span><span class="sxs-lookup"><span data-stu-id="04d84-259">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="04d84-260">Les critères spéciaux des fonctions anonymes, à partir de `function` , ne doivent généralement pas être mis en retrait trop loin.</span><span class="sxs-lookup"><span data-stu-id="04d84-260">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="04d84-261">Par exemple, la mise en retrait d’une étendue comme suit est correcte :</span><span class="sxs-lookup"><span data-stu-id="04d84-261">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map
    (function
        | Abs(x, body) -> 1 + sizeLambda 0 body
        | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
        | Var v -> 1)
```

<span data-ttu-id="04d84-262">Les critères spéciaux dans les fonctions définies par `let` ou `let rec` doivent être mis en retrait à quatre espaces après le démarrage de `let` , même si le `function` mot clé est utilisé :</span><span class="sxs-lookup"><span data-stu-id="04d84-262">Pattern matching in functions defined by `let` or `let rec` should be indented four spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="04d84-263">Nous vous déconseillons d’aligner les flèches.</span><span class="sxs-lookup"><span data-stu-id="04d84-263">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="04d84-264">Mise en forme des expressions try/with</span><span class="sxs-lookup"><span data-stu-id="04d84-264">Formatting try/with expressions</span></span>

<span data-ttu-id="04d84-265">Les critères spéciaux sur le type d’exception doivent être mis en retrait au même niveau que `with` .</span><span class="sxs-lookup"><span data-stu-id="04d84-265">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

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

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="04d84-266">Mise en forme de l’application de paramètre de fonction</span><span class="sxs-lookup"><span data-stu-id="04d84-266">Formatting function parameter application</span></span>

<span data-ttu-id="04d84-267">En général, la plupart des arguments sont fournis sur la même ligne :</span><span class="sxs-lookup"><span data-stu-id="04d84-267">In general, most arguments are provided on the same line:</span></span>

```fsharp
let x = sprintf "\t%s - %i\n\r" x.IngredientName x.Quantity

let printListWithOffset a list1 =
    List.iter (fun elem -> printfn $"%d{a + elem}") list1
```

<span data-ttu-id="04d84-268">Lorsqu’il s’agit de pipelines, il en est de même pour les pipelines, où une fonction curryfiée est appliquée en tant qu’argument sur la même ligne :</span><span class="sxs-lookup"><span data-stu-id="04d84-268">When pipelines are concerned, the same is typically also true, where a curried function is applied as an argument on the same line:</span></span>

```
let printListWithOffsetPiped a list1 =
    list1
    |> List.iter (fun elem -> printfn $"%d{a + elem}")
```

<span data-ttu-id="04d84-269">Toutefois, vous pouvez passer des arguments à une fonction sur une nouvelle ligne, pour des raisons de lisibilité ou parce que la liste d’arguments ou les noms d’arguments sont trop longs.</span><span class="sxs-lookup"><span data-stu-id="04d84-269">However, you may wish to pass arguments to a function on a new line, as a matter of readability or because the list of arguments or the argument names are too long.</span></span> <span data-ttu-id="04d84-270">Dans ce cas, mettez en retrait avec une étendue :</span><span class="sxs-lookup"><span data-stu-id="04d84-270">In that case, indent with one scope:</span></span>

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

<span data-ttu-id="04d84-271">Pour les expressions lambda, vous pouvez également envisager de placer le corps d’une expression lambda sur une nouvelle ligne, mise en retrait d’une étendue, si elle est suffisamment longue :</span><span class="sxs-lookup"><span data-stu-id="04d84-271">For lambda expressions, you may also want to consider placing the body of a lambda expression on a new line, indented by one scope, if it is long enough:</span></span>

```fsharp
let printListWithOffset a list1 =
    List.iter
        (fun elem ->
            printfn $"%d{a + elem}")
        list1

let printListWithOffsetPiped a list1 =
    list1
    |> List.iter
        (fun elem ->
            printfn $"%d{a + elem}")
```

<span data-ttu-id="04d84-272">Si le corps d’une expression lambda comporte plusieurs lignes, vous devez envisager de le refactoriser dans une fonction de portée locale.</span><span class="sxs-lookup"><span data-stu-id="04d84-272">If the body of a lambda expression is multiple lines long, you should consider refactoring it into a locally-scoped function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="04d84-273">Mise en forme des opérateurs infixes</span><span class="sxs-lookup"><span data-stu-id="04d84-273">Formatting infix operators</span></span>

<span data-ttu-id="04d84-274">Séparez les opérateurs par des espaces.</span><span class="sxs-lookup"><span data-stu-id="04d84-274">Separate operators by spaces.</span></span> <span data-ttu-id="04d84-275">Les opérateurs et sont des exceptions évidentes à cette règle `!` `.` .</span><span class="sxs-lookup"><span data-stu-id="04d84-275">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="04d84-276">Les expressions infixes sont correctes pour la programmation sur la même colonne :</span><span class="sxs-lookup"><span data-stu-id="04d84-276">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators-or-mutable-assignments"></a><span data-ttu-id="04d84-277">Mise en forme des opérateurs de pipeline ou des assignations mutables</span><span class="sxs-lookup"><span data-stu-id="04d84-277">Formatting pipeline operators or mutable assignments</span></span>

<span data-ttu-id="04d84-278">`|>`Les opérateurs de pipeline doivent se trouver sous les expressions sur lesquelles ils opèrent.</span><span class="sxs-lookup"><span data-stu-id="04d84-278">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

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

// Not OK either
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
               |> List.ofArray
               |> List.map (fun assm -> assm.GetTypes())
               |> Array.concat
               |> List.ofArray
               |> List.map (fun t -> t.GetMethods())
               |> Array.concat
```

<span data-ttu-id="04d84-279">Cela s’applique également aux accesseurs set mutables :</span><span class="sxs-lookup"><span data-stu-id="04d84-279">This also applies to mutable setters:</span></span>

```fsharp
// Preferred approach
ctx.Response.Headers.[HeaderNames.ContentType] <-
    Constants.jsonApiMediaType |> StringValues
ctx.Response.Headers.[HeaderNames.ContentLength] <-
    bytes.Length |> string |> StringValues

// Not OK
ctx.Response.Headers.[HeaderNames.ContentType] <- Constants.jsonApiMediaType
                                                  |> StringValues
ctx.Response.Headers.[HeaderNames.ContentLength] <- bytes.Length
                                                    |> string
                                                    |> StringValues
```

### <a name="formatting-modules"></a><span data-ttu-id="04d84-280">Mise en forme des modules</span><span class="sxs-lookup"><span data-stu-id="04d84-280">Formatting modules</span></span>

<span data-ttu-id="04d84-281">Le code d’un module local doit être mis en retrait par rapport au module, mais le code d’un module de niveau supérieur ne doit pas être mis en retrait.</span><span class="sxs-lookup"><span data-stu-id="04d84-281">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="04d84-282">Les éléments d’espace de noms n’ont pas besoin d’être mis en retrait.</span><span class="sxs-lookup"><span data-stu-id="04d84-282">Namespace elements do not have to be indented.</span></span>

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

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="04d84-283">Mise en forme des expressions et des interfaces d’objet</span><span class="sxs-lookup"><span data-stu-id="04d84-283">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="04d84-284">Les interfaces et les expressions d’objet doivent être alignées de la même façon avec `member` une mise en retrait après quatre espaces.</span><span class="sxs-lookup"><span data-stu-id="04d84-284">Object expressions and interfaces should be aligned in the same way with `member` being indented after four spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="04d84-285">Mise en forme des espaces blancs dans les expressions</span><span class="sxs-lookup"><span data-stu-id="04d84-285">Formatting white space in expressions</span></span>

<span data-ttu-id="04d84-286">Évitez les espaces superflus dans les expressions F #.</span><span class="sxs-lookup"><span data-stu-id="04d84-286">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="04d84-287">Les arguments nommés ne doivent pas non plus avoir d’espace autour de `=` :</span><span class="sxs-lookup"><span data-stu-id="04d84-287">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

### <a name="formatting-constructors-static-members-and-member-invocations"></a><span data-ttu-id="04d84-288">Mise en forme des constructeurs, des membres statiques et des appels de membres</span><span class="sxs-lookup"><span data-stu-id="04d84-288">Formatting constructors, static members, and member invocations</span></span>

<span data-ttu-id="04d84-289">Si l’expression est de type short, séparez les arguments par des espaces et conservez-les en une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="04d84-289">If the expression is short, separate arguments with spaces and keep it in one line.</span></span>

```fsharp
let person = new Person(a1, a2)

let myRegexMatch = Regex.Match(input, regex)

let untypedRes = checker.ParseFile(file, source, opts)
```

<span data-ttu-id="04d84-290">Si l’expression est longue, utilisez les nouvelles lignes et mettez en retrait une étendue, plutôt que de mettre en retrait le crochet.</span><span class="sxs-lookup"><span data-stu-id="04d84-290">If the expression is long, use newlines and indent one scope, rather than indenting to the bracket.</span></span>

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

## <a name="formatting-attributes"></a><span data-ttu-id="04d84-291">Attributs de mise en forme</span><span class="sxs-lookup"><span data-stu-id="04d84-291">Formatting attributes</span></span>

<span data-ttu-id="04d84-292">Les [attributs](../language-reference/attributes.md) sont placés au-dessus d’une construction :</span><span class="sxs-lookup"><span data-stu-id="04d84-292">[Attributes](../language-reference/attributes.md) are placed above a construct:</span></span>

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

<span data-ttu-id="04d84-293">Ils doivent être placés après toute documentation XML :</span><span class="sxs-lookup"><span data-stu-id="04d84-293">They should go after any XML documentation:</span></span>

```fsharp
/// Module with some things in it.
[<RequireQualifiedAccess>]
module M =
    let f x = x
```

### <a name="formatting-attributes-on-parameters"></a><span data-ttu-id="04d84-294">Mise en forme des attributs sur les paramètres</span><span class="sxs-lookup"><span data-stu-id="04d84-294">Formatting attributes on parameters</span></span>

<span data-ttu-id="04d84-295">Les attributs peuvent également être placés sur des paramètres.</span><span class="sxs-lookup"><span data-stu-id="04d84-295">Attributes can also be placed on parameters.</span></span> <span data-ttu-id="04d84-296">Dans ce cas, placez ensuite sur la même ligne que le paramètre et avant le nom :</span><span class="sxs-lookup"><span data-stu-id="04d84-296">In this case, place then on the same line as the parameter and before the name:</span></span>

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a><span data-ttu-id="04d84-297">Mise en forme de plusieurs attributs</span><span class="sxs-lookup"><span data-stu-id="04d84-297">Formatting multiple attributes</span></span>

<span data-ttu-id="04d84-298">Quand plusieurs attributs sont appliqués à une construction qui n’est pas un paramètre, ils doivent être placés de façon à ce qu’il y ait un attribut par ligne :</span><span class="sxs-lookup"><span data-stu-id="04d84-298">When multiple attributes are applied to a construct that is not a parameter, they should be placed such that there is one attribute per line:</span></span>

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="04d84-299">Lorsqu’ils sont appliqués à un paramètre, ils doivent se trouver sur la même ligne et être séparés par un `;` séparateur.</span><span class="sxs-lookup"><span data-stu-id="04d84-299">When applied to a parameter, they must be on the same line and separated by a `;` separator.</span></span>

## <a name="formatting-literals"></a><span data-ttu-id="04d84-300">Mise en forme des littéraux</span><span class="sxs-lookup"><span data-stu-id="04d84-300">Formatting literals</span></span>

<span data-ttu-id="04d84-301">Les [littéraux F #](../language-reference/literals.md) utilisant l' `Literal` attribut doivent placer l’attribut sur sa propre ligne et utiliser la dénomination casse Pascal :</span><span class="sxs-lookup"><span data-stu-id="04d84-301">[F# literals](../language-reference/literals.md) using the `Literal` attribute should place the attribute on its own line and use PascalCase naming:</span></span>

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

<span data-ttu-id="04d84-302">Évitez de placer l’attribut sur la même ligne que la valeur.</span><span class="sxs-lookup"><span data-stu-id="04d84-302">Avoid placing the attribute on the same line as the value.</span></span>

## <a name="formatting-computation-expression-operations"></a><span data-ttu-id="04d84-303">Mise en forme des opérations d’expression de calcul</span><span class="sxs-lookup"><span data-stu-id="04d84-303">Formatting computation expression operations</span></span>

<span data-ttu-id="04d84-304">Lors de la création d’opérations personnalisées pour des [expressions de calcul](../language-reference/computation-expressions.md), il est recommandé d’utiliser l’affectation de noms la casse mixte :</span><span class="sxs-lookup"><span data-stu-id="04d84-304">When creating custom operations for [computation expressions](../language-reference/computation-expressions.md), it is recommended to use camelCase naming:</span></span>

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

<span data-ttu-id="04d84-305">Le domaine qui est modélisé doit finalement conduire la Convention d’affectation de noms.</span><span class="sxs-lookup"><span data-stu-id="04d84-305">The domain that's being modeled should ultimately drive the naming convention.</span></span>
<span data-ttu-id="04d84-306">S’il est idiomatique d’utiliser une convention différente, cette convention doit être utilisée à la place.</span><span class="sxs-lookup"><span data-stu-id="04d84-306">If it is idiomatic to use a different convention, that convention should be used instead.</span></span>
