---
title: Indications de mise en forme du code F#
description: Découvrez des instructions pour la mise en forme F# code.
ms.date: 02/08/2019
ms.openlocfilehash: 8be5337d3f593c7e5a2f32cb7231cb7f759fb509
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833904"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="d8435-103">Indications de mise en forme du code F#</span><span class="sxs-lookup"><span data-stu-id="d8435-103">F# code formatting guidelines</span></span>

<span data-ttu-id="d8435-104">Cet article propose des conseils pour savoir comment mettre en forme votre code afin que votre F# code est :</span><span class="sxs-lookup"><span data-stu-id="d8435-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="d8435-105">Généralement considérée comme plus lisibles</span><span class="sxs-lookup"><span data-stu-id="d8435-105">Generally viewed as more legible</span></span>
* <span data-ttu-id="d8435-106">Est conformément aux conventions appliquées par la mise en forme des outils dans Visual Studio et autres éditeurs</span><span class="sxs-lookup"><span data-stu-id="d8435-106">Is in accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="d8435-107">Similaire à un autre code en ligne</span><span class="sxs-lookup"><span data-stu-id="d8435-107">Similar to other code online</span></span>

<span data-ttu-id="d8435-108">Ces instructions sont basées sur [un guide complet sur F# Conventions de mise en forme](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) par [Anh-Dung Phan](https://github.com/dungpa).</span><span class="sxs-lookup"><span data-stu-id="d8435-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="d8435-109">Règles générales pour la mise en retrait</span><span class="sxs-lookup"><span data-stu-id="d8435-109">General rules for indentation</span></span>

<span data-ttu-id="d8435-110">F#par défaut, utilise un espace blanc significatif.</span><span class="sxs-lookup"><span data-stu-id="d8435-110">F# uses significant white space by default.</span></span> <span data-ttu-id="d8435-111">Les instructions suivantes sont destinées à fournir des conseils quant à jongler avec des défis que cela peut imposer.</span><span class="sxs-lookup"><span data-stu-id="d8435-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="d8435-112">L’utilisation des espaces</span><span class="sxs-lookup"><span data-stu-id="d8435-112">Using spaces</span></span>

<span data-ttu-id="d8435-113">Lors de la mise en retrait est requise, vous devez utiliser des espaces, tabulations pas.</span><span class="sxs-lookup"><span data-stu-id="d8435-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="d8435-114">Au moins un espace est requis.</span><span class="sxs-lookup"><span data-stu-id="d8435-114">At least one space is required.</span></span> <span data-ttu-id="d8435-115">Votre organisation peut créer des normes de codage pour spécifier le nombre d’espaces à utiliser pour la mise en retrait ; deux, trois ou quatre espaces de mise en retrait à chaque niveau de mise en retrait est typique.</span><span class="sxs-lookup"><span data-stu-id="d8435-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="d8435-116">**Nous vous recommandons 4 espaces par mise en retrait.**</span><span class="sxs-lookup"><span data-stu-id="d8435-116">**We recommend 4 spaces per indentation.**</span></span>

<span data-ttu-id="d8435-117">Ceci dit, la mise en retrait de programmes est très subjective.</span><span class="sxs-lookup"><span data-stu-id="d8435-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="d8435-118">Variations sont OK, mais la première règle, vous devez suivre est *la cohérence de la mise en retrait*.</span><span class="sxs-lookup"><span data-stu-id="d8435-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="d8435-119">Choisir un style généralement accepté de mise en retrait et l’utiliser systématiquement tout au long de votre base de code.</span><span class="sxs-lookup"><span data-stu-id="d8435-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-white-space"></a><span data-ttu-id="d8435-120">Mise en forme d’un espace blanc</span><span class="sxs-lookup"><span data-stu-id="d8435-120">Formatting white space</span></span>

<span data-ttu-id="d8435-121">F#est un espace blanc sensibles.</span><span class="sxs-lookup"><span data-stu-id="d8435-121">F# is white space sensitive.</span></span> <span data-ttu-id="d8435-122">Bien que la plupart des sémantiques à partir d’un espace blanc sont couverts par la mise en retrait appropriée, il existe quelques autres points à prendre en compte.</span><span class="sxs-lookup"><span data-stu-id="d8435-122">Although most semantics from white space are covered by proper indentation, there are some other things to consider.</span></span>

### <a name="formatting-operators-in-arithmetic-expressions"></a><span data-ttu-id="d8435-123">Mise en forme des opérateurs dans les expressions arithmétiques</span><span class="sxs-lookup"><span data-stu-id="d8435-123">Formatting operators in arithmetic expressions</span></span>

<span data-ttu-id="d8435-124">Utilisez toujours un espace blanc autour des expressions arithmétiques binaires :</span><span class="sxs-lookup"><span data-stu-id="d8435-124">Always use white space around binary arithmetic expressions:</span></span>

```fsharp
let subtractThenAdd x = x - 1 + 3
```

<span data-ttu-id="d8435-125">Unaire `-` opérateurs doivent avoir toujours la valeur qu’ils sont la négation suivent immédiatement :</span><span class="sxs-lookup"><span data-stu-id="d8435-125">Unary `-` operators should always have the value they are negating immediately follow:</span></span>

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

<span data-ttu-id="d8435-126">Ajout d’un espace après le `-` opérateur peut prêter à confusion pour les autres.</span><span class="sxs-lookup"><span data-stu-id="d8435-126">Adding a white-space character after the `-` operator can lead to confusion for others.</span></span>

<span data-ttu-id="d8435-127">En résumé, il est important de toujours :</span><span class="sxs-lookup"><span data-stu-id="d8435-127">In summary, it's important to always:</span></span>

* <span data-ttu-id="d8435-128">Entourez les opérateurs binaires par un espace blanc</span><span class="sxs-lookup"><span data-stu-id="d8435-128">Surround binary operators with white space</span></span>
* <span data-ttu-id="d8435-129">Espace blanc de fin n’ont jamais après un opérateur unaire</span><span class="sxs-lookup"><span data-stu-id="d8435-129">Never have trailing white space after a unary operator</span></span>

<span data-ttu-id="d8435-130">L’indication de l’opérateur arithmétique binaire est particulièrement importante.</span><span class="sxs-lookup"><span data-stu-id="d8435-130">The binary arithmetic operator guideline is especially important.</span></span> <span data-ttu-id="d8435-131">Échec de l’entourer d’un fichier binaire `-` opérateur, lorsqu’elles sont combinées avec certaines options de mise en forme, risque d’interpréter comme un opérateur unaire `-`.</span><span class="sxs-lookup"><span data-stu-id="d8435-131">Failing to surround a binary `-` operator, when combined with certain formatting choices, could lead to interpreting it as a unary `-`.</span></span>

### <a name="surround-a-custom-operator-definition-with-white-space"></a><span data-ttu-id="d8435-132">Une définition d’opérateur personnalisé avec un espace blanc à effet surround</span><span class="sxs-lookup"><span data-stu-id="d8435-132">Surround a custom operator definition with white space</span></span>

<span data-ttu-id="d8435-133">Utilisez toujours un espace blanc pour entourer une définition d’opérateur :</span><span class="sxs-lookup"><span data-stu-id="d8435-133">Always use white space to surround an operator definition:</span></span>

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

<span data-ttu-id="d8435-134">Pour n’importe quel opérateur personnalisé qui commence par `*` et qui a plusieurs caractères, vous devez ajouter un espace blanc au début de la définition afin d’éviter une ambiguïté du compilateur.</span><span class="sxs-lookup"><span data-stu-id="d8435-134">For any custom operator that starts with `*` and that has more than one character, you need to add a white space to the beginning of the definition to avoid a compiler ambiguity.</span></span> <span data-ttu-id="d8435-135">Pour cette raison, nous recommandons que vous devez simplement placer les définitions de tous les opérateurs avec un seul caractère espace blanc.</span><span class="sxs-lookup"><span data-stu-id="d8435-135">Because of this, we recommend that you simply surround the definitions of all operators with a single white-space character.</span></span>

### <a name="surround-function-parameter-arrows-with-white-space"></a><span data-ttu-id="d8435-136">Entourez les flèches de paramètre de fonction avec un espace blanc</span><span class="sxs-lookup"><span data-stu-id="d8435-136">Surround function parameter arrows with white space</span></span>

<span data-ttu-id="d8435-137">Lorsque vous définissez la signature d’une fonction, utilisez un espace blanc autour du `->` symbole :</span><span class="sxs-lookup"><span data-stu-id="d8435-137">When defining the signature of a function, use white space around the `->` symbol:</span></span>

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a><span data-ttu-id="d8435-138">Entourez les arguments de fonction avec un espace blanc</span><span class="sxs-lookup"><span data-stu-id="d8435-138">Surround function arguments with white space</span></span>

<span data-ttu-id="d8435-139">Lorsque vous définissez une fonction, utilisez un espace blanc autour de chaque argument.</span><span class="sxs-lookup"><span data-stu-id="d8435-139">When defining a function, use white space around each argument.</span></span>

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="type-annotations"></a><span data-ttu-id="d8435-140">Annotations de type</span><span class="sxs-lookup"><span data-stu-id="d8435-140">Type annotations</span></span>

#### <a name="right-pad-function-argument-type-annotations"></a><span data-ttu-id="d8435-141">Annotations de type d’argument droite (fonction)</span><span class="sxs-lookup"><span data-stu-id="d8435-141">Right-pad function argument type annotations</span></span>

<span data-ttu-id="d8435-142">Lorsque vous définissez les arguments avec des annotations de type, utilisez un espace blanc après le `:` symbole :</span><span class="sxs-lookup"><span data-stu-id="d8435-142">When defining arguments with type annotations, use white space after the `:` symbol:</span></span>

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a><span data-ttu-id="d8435-143">Annotations de type de retour à effet surround par un espace blanc</span><span class="sxs-lookup"><span data-stu-id="d8435-143">Surround return type annotations with white space</span></span>

<span data-ttu-id="d8435-144">Dans un lié aux permettent de fonction ou valeur annotation de type (type de retour dans le cas d’une fonction), utilisez un espace blanc avant et après le `:` symbole :</span><span class="sxs-lookup"><span data-stu-id="d8435-144">In a let-bound function or value type annotation (return type in the case of a function), use white space before and after the `:` symbol:</span></span>

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="d8435-145">Mise en forme des lignes vides</span><span class="sxs-lookup"><span data-stu-id="d8435-145">Formatting blank lines</span></span>

* <span data-ttu-id="d8435-146">Distinct niveau supérieur (fonction) et classe les définitions avec deux lignes vides.</span><span class="sxs-lookup"><span data-stu-id="d8435-146">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="d8435-147">Les définitions de méthode à l’intérieur d’une classe sont séparées par une ligne vierge.</span><span class="sxs-lookup"><span data-stu-id="d8435-147">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="d8435-148">Lignes vierges supplémentaires peuvent servir (avec parcimonie) pour séparer les groupes de fonctions associées.</span><span class="sxs-lookup"><span data-stu-id="d8435-148">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="d8435-149">Peuvent être omis des lignes vides entre un ensemble de commandes associées à une ligne (par exemple, un ensemble d’implémentations factices).</span><span class="sxs-lookup"><span data-stu-id="d8435-149">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="d8435-150">Utiliser avec parcimonie, des lignes vides dans les fonctions, pour indiquer les sections logiques.</span><span class="sxs-lookup"><span data-stu-id="d8435-150">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="d8435-151">Mise en forme de commentaires</span><span class="sxs-lookup"><span data-stu-id="d8435-151">Formatting comments</span></span>

<span data-ttu-id="d8435-152">Préférez généralement plusieurs commentaires double barre oblique sur les commentaires de bloc de style de ML.</span><span class="sxs-lookup"><span data-stu-id="d8435-152">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="d8435-153">Les commentaires incorporés doivent mettre en majuscule la première lettre.</span><span class="sxs-lookup"><span data-stu-id="d8435-153">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="d8435-154">Conventions d'attribution d'un nom</span><span class="sxs-lookup"><span data-stu-id="d8435-154">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="d8435-155">Utilisent une casse mixte pour les fonctions et les valeurs de limite de classe, expression-liées aux et modèle</span><span class="sxs-lookup"><span data-stu-id="d8435-155">Use camelCase for class-bound, expression-bound and pattern-bound values and functions</span></span>

<span data-ttu-id="d8435-156">Il est courant et acceptés F# style à utiliser une casse mixte pour tous les noms liée en tant que variables locales ou dans les correspondances de modèles et de définitions de fonctions.</span><span class="sxs-lookup"><span data-stu-id="d8435-156">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="d8435-157">Fonctions liées à localement dans les classes doivent également utiliser une casse mixte.</span><span class="sxs-lookup"><span data-stu-id="d8435-157">Locally-bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="d8435-158">Utilisent une casse mixte pour les fonctions publiques liées à un module</span><span class="sxs-lookup"><span data-stu-id="d8435-158">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="d8435-159">Quand une fonction liée au module fait partie d’une API publique, il doit utiliser une casse mixte :</span><span class="sxs-lookup"><span data-stu-id="d8435-159">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="d8435-160">Utilisent une casse mixte pour les fonctions et les valeurs de module dépendant internes et privés</span><span class="sxs-lookup"><span data-stu-id="d8435-160">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="d8435-161">Utilisez la casse mixte pour les valeurs liée aux module privées, y compris les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="d8435-161">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="d8435-162">Fonctions ad hoc dans les scripts</span><span class="sxs-lookup"><span data-stu-id="d8435-162">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="d8435-163">Valeurs constituant l’implémentation interne d’un module ou un type</span><span class="sxs-lookup"><span data-stu-id="d8435-163">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="d8435-164">Utilisez la casse mixte pour les paramètres</span><span class="sxs-lookup"><span data-stu-id="d8435-164">Use camelCase for parameters</span></span>

<span data-ttu-id="d8435-165">Tous les paramètres doivent utiliser une casse mixte conformément aux conventions d’affectation de noms .NET.</span><span class="sxs-lookup"><span data-stu-id="d8435-165">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="d8435-166">Utiliser la casse Pascal pour les modules</span><span class="sxs-lookup"><span data-stu-id="d8435-166">Use PascalCase for modules</span></span>

<span data-ttu-id="d8435-167">Tous les modules (niveau supérieur, internes, privés, imbriquées) doivent utiliser la casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="d8435-167">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="d8435-168">Utilisez la casse Pascal pour les déclarations de type, les membres et les étiquettes</span><span class="sxs-lookup"><span data-stu-id="d8435-168">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="d8435-169">Classes, interfaces, structures, énumérations, délégués, les enregistrements et les unions discriminées doivent être nommées avec la casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="d8435-169">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="d8435-170">Membres au sein des types et des étiquettes pour les enregistrements et les unions discriminées doivent également utiliser la casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="d8435-170">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="d8435-171">Utilisez la casse Pascal pour les constructions intrinsèques pour .NET</span><span class="sxs-lookup"><span data-stu-id="d8435-171">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="d8435-172">Espaces de noms, exceptions, événements et projet /`.dll` noms doivent également utiliser la casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="d8435-172">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="d8435-173">Non seulement est-ce que la consommation à partir d’autres langages .NET sembler plus naturelle pour les consommateurs, il est également cohérente avec les conventions d’affectation de noms .NET que vous êtes susceptible de rencontrer.</span><span class="sxs-lookup"><span data-stu-id="d8435-173">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="d8435-174">Éviter les traits de soulignement dans les noms</span><span class="sxs-lookup"><span data-stu-id="d8435-174">Avoid underscores in names</span></span>

<span data-ttu-id="d8435-175">Historiquement, certaines F# bibliothèques ont utilisé des traits de soulignement dans les noms.</span><span class="sxs-lookup"><span data-stu-id="d8435-175">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="d8435-176">Toutefois, cela est n’est plus largement acceptée, en partie parce qu’il est en conflit avec les conventions d’affectation de noms .NET.</span><span class="sxs-lookup"><span data-stu-id="d8435-176">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="d8435-177">Cela étant dit, certains F# les programmeurs utilisent des traits de soulignement fortement, en partie pour des raisons historiques, et la tolérance de panne et le respect important.</span><span class="sxs-lookup"><span data-stu-id="d8435-177">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="d8435-178">Toutefois, n’oubliez pas que le style n’est souvent pas satisfaisant par d’autres personnes qui ont la possibilité d’utiliser.</span><span class="sxs-lookup"><span data-stu-id="d8435-178">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="d8435-179">Certaines exceptions inclut l’interopérabilité avec les composants natifs, où des traits de soulignement sont très courantes.</span><span class="sxs-lookup"><span data-stu-id="d8435-179">Some exceptions includes interoperating with native components, where underscores are very common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="d8435-180">Standard d’utilisation F# opérateurs</span><span class="sxs-lookup"><span data-stu-id="d8435-180">Use standard F# operators</span></span>

<span data-ttu-id="d8435-181">Les opérateurs suivants sont définis dans le F# bibliothèque standard et doit être utilisé au lieu de définir des équivalents.</span><span class="sxs-lookup"><span data-stu-id="d8435-181">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="d8435-182">L’utilisation de ces opérateurs est recommandée car elle a tendance à rendre le code plus lisible et idiomatique.</span><span class="sxs-lookup"><span data-stu-id="d8435-182">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="d8435-183">Les développeurs avec un arrière-plan dans OCaml ou autre langage de programmation fonctionnel peut-être habitués à différents idiomes.</span><span class="sxs-lookup"><span data-stu-id="d8435-183">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="d8435-184">La liste suivante résume l’architecture recommandée F# opérateurs.</span><span class="sxs-lookup"><span data-stu-id="d8435-184">The following list summarizes the recommended F# operators.</span></span>

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="d8435-185">Utiliser la syntaxe du préfixe pour les génériques (`Foo<T>`) plutôt que de la syntaxe de suffixe (`T Foo`)</span><span class="sxs-lookup"><span data-stu-id="d8435-185">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="d8435-186">F#hérite à la fois le style de ML suffixe de nommage des types génériques (par exemple, `int list`), ainsi que le préfixe de style .NET (par exemple, `list<int>`).</span><span class="sxs-lookup"><span data-stu-id="d8435-186">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="d8435-187">Préférer le style de .NET, à l’exception des cinq types spécifiques :</span><span class="sxs-lookup"><span data-stu-id="d8435-187">Prefer the .NET style, except for five specific types:</span></span>

1. <span data-ttu-id="d8435-188">Pour F# listes, utilisez la forme suffixée : `int list` plutôt que `list<int>`.</span><span class="sxs-lookup"><span data-stu-id="d8435-188">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="d8435-189">Pour F# Options, utilisez la forme suffixée : `int option` plutôt que `option<int>`.</span><span class="sxs-lookup"><span data-stu-id="d8435-189">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="d8435-190">Pour F# Options de valeur, utilisez la forme suffixée : `int voption` plutôt que `voption<int>`.</span><span class="sxs-lookup"><span data-stu-id="d8435-190">For F# Value Options, use the postfix form: `int voption` rather than `voption<int>`.</span></span>
4. <span data-ttu-id="d8435-191">Pour F# tableaux, utilisez le nom syntaxique `int[]` plutôt que `int array` ou `array<int>`.</span><span class="sxs-lookup"><span data-stu-id="d8435-191">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
5. <span data-ttu-id="d8435-192">Pour les cellules de référence, utilisez `int ref` plutôt que `ref<int>` ou `Ref<int>`.</span><span class="sxs-lookup"><span data-stu-id="d8435-192">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="d8435-193">Pour tous les autres types, utilisez la forme de préfixe.</span><span class="sxs-lookup"><span data-stu-id="d8435-193">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="d8435-194">Mise en forme de tuples</span><span class="sxs-lookup"><span data-stu-id="d8435-194">Formatting tuples</span></span>

<span data-ttu-id="d8435-195">Une instanciation de tuple doit être entre parenthèses, et les virgules de délimitation dans doivent être suivies par un espace, par exemple : `(1, 2)`, `(x, y, z)`.</span><span class="sxs-lookup"><span data-stu-id="d8435-195">A tuple instantiation should be parenthesized, and the delimiting commas within should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="d8435-196">Il est généralement admis pour omettre les parenthèses dans les critères spéciaux de tuples :</span><span class="sxs-lookup"><span data-stu-id="d8435-196">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

<span data-ttu-id="d8435-197">Il est également couramment acceptée pour omettre les parenthèses si le tuple est la valeur de retour d’une fonction :</span><span class="sxs-lookup"><span data-stu-id="d8435-197">It is also commonly accepted to omit parentheses if the tuple is the return value of a function:</span></span>

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

<span data-ttu-id="d8435-198">En résumé, préférez les instanciations de tuple entre parenthèses, mais lorsque vous utilisez des tuples pour une valeur de retour ou de critères spéciaux, il est considéré comme acceptable d’éviter des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="d8435-198">In summary, prefer parenthesized tuple instantiations, but when using tuples for pattern matching or a return value, it is considered fine to avoid parentheses.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="d8435-199">Mise en forme discriminée des déclarations d’union</span><span class="sxs-lookup"><span data-stu-id="d8435-199">Formatting discriminated union declarations</span></span>

<span data-ttu-id="d8435-200">Mettre en retrait `|` dans la définition de type par des 4 espaces :</span><span class="sxs-lookup"><span data-stu-id="d8435-200">Indent `|` in type definition by 4 spaces:</span></span>

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

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="d8435-201">Mise en forme des unions discriminées</span><span class="sxs-lookup"><span data-stu-id="d8435-201">Formatting discriminated unions</span></span>

<span data-ttu-id="d8435-202">Instancié Unions discriminées qui réparties sur plusieurs lignes doit fournir des données qu’il contient une nouvelle étendue avec la mise en retrait :</span><span class="sxs-lookup"><span data-stu-id="d8435-202">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="d8435-203">La parenthèse fermante peut également être sur une nouvelle ligne :</span><span class="sxs-lookup"><span data-stu-id="d8435-203">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="d8435-204">Mise en forme de déclarations d’enregistrement</span><span class="sxs-lookup"><span data-stu-id="d8435-204">Formatting record declarations</span></span>

<span data-ttu-id="d8435-205">Mettre en retrait `{` dans le type de définition par 4 espaces et démarrer la liste de champs sur la même ligne :</span><span class="sxs-lookup"><span data-stu-id="d8435-205">Indent `{` in type definition by 4 spaces and start the field list on the same line:</span></span>

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

<span data-ttu-id="d8435-206">Il est préférable si vous déclarez des implémentations d’interface ou de membres sur l’enregistrement de placer le jeton d’ouverture sur une nouvelle ligne et le jeton de fermeture sur une nouvelle ligne :</span><span class="sxs-lookup"><span data-stu-id="d8435-206">Placing the opening token on a new line and the closing token on a new line is preferable if you are declaring interface implementations or members on the record:</span></span>

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

## <a name="formatting-records"></a><span data-ttu-id="d8435-207">Mise en forme d’enregistrements</span><span class="sxs-lookup"><span data-stu-id="d8435-207">Formatting records</span></span>

<span data-ttu-id="d8435-208">Enregistrements courts peuvent être écrite sur une seule ligne :</span><span class="sxs-lookup"><span data-stu-id="d8435-208">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="d8435-209">Les enregistrements qui sont plus longs doivent utiliser les nouvelles lignes pour les étiquettes :</span><span class="sxs-lookup"><span data-stu-id="d8435-209">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="d8435-210">Placer l’ouverture jeton sur une nouvelle ligne, le contenu avec onglets sur une étendue, et le jeton de fermeture sur une nouvelle ligne est préférable si vous êtes :</span><span class="sxs-lookup"><span data-stu-id="d8435-210">Placing the opening token on a new line, the contents tabbed over one scope, and the closing token on a new line is preferable if you are:</span></span>

* <span data-ttu-id="d8435-211">Déplacer les enregistrements dans le code avec des étendues de mise en retrait différente</span><span class="sxs-lookup"><span data-stu-id="d8435-211">Moving records around in code with different indentation scopes</span></span>
* <span data-ttu-id="d8435-212">Transférant dans une fonction</span><span class="sxs-lookup"><span data-stu-id="d8435-212">Piping them into a function</span></span>

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

<span data-ttu-id="d8435-213">Les mêmes règles s’appliquent pour les éléments de liste et tableau.</span><span class="sxs-lookup"><span data-stu-id="d8435-213">The same rules apply for list and array elements.</span></span>

## <a name="formatting-copy-and-update-record-expressions"></a><span data-ttu-id="d8435-214">Expressions d’enregistrement de copie--mise à jour et de mise en forme</span><span class="sxs-lookup"><span data-stu-id="d8435-214">Formatting copy-and-update record expressions</span></span>

<span data-ttu-id="d8435-215">Une expression d’enregistrement de copie--mise à jour et est toujours un enregistrement, des instructions similaires s’appliquent donc pas.</span><span class="sxs-lookup"><span data-stu-id="d8435-215">A copy-and-update record expression is still a record, so similar guidelines apply.</span></span>

<span data-ttu-id="d8435-216">Expressions courtes peuvent tenir sur une seule ligne :</span><span class="sxs-lookup"><span data-stu-id="d8435-216">Short expressions can fit on one line:</span></span>

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

<span data-ttu-id="d8435-217">De plus longues expressions doivent utiliser les nouvelles lignes :</span><span class="sxs-lookup"><span data-stu-id="d8435-217">Longer expressions should use new lines:</span></span>

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="d8435-218">Et comme avec les conseils d’enregistrement, vous souhaiterez dédier des lignes distinctes pour les accolades et mettre en retrait d’une étendue à droite avec l’expression.</span><span class="sxs-lookup"><span data-stu-id="d8435-218">And as with the record guidance, you may want to dedicate separate lines for the braces and indent one scope to the right with the expression.</span></span> <span data-ttu-id="d8435-219">Notez que dans certains cas spéciaux, tels que l’encapsulation d’une valeur avec une option sans parenthèses, vous devrez peut-être conserver une accolade sur une seule ligne :</span><span class="sxs-lookup"><span data-stu-id="d8435-219">Note that in some special cases, such as wrapping a value with an optional without parentheses, you may need to keep a brace on one line:</span></span>

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

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="d8435-220">Mise en forme des listes et des tableaux</span><span class="sxs-lookup"><span data-stu-id="d8435-220">Formatting lists and arrays</span></span>

<span data-ttu-id="d8435-221">Écrire `x :: l` avec des espaces autour de la `::` opérateur (`::` est un opérateur infixe, par conséquent, entouré d’espaces).</span><span class="sxs-lookup"><span data-stu-id="d8435-221">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces).</span></span>

<span data-ttu-id="d8435-222">Liste et les tableaux déclarés sur une seule ligne doivent contenir un espace après le crochet ouvrant et avant le crochet fermant :</span><span class="sxs-lookup"><span data-stu-id="d8435-222">List and arrays declared on a single line should have a space after the opening bracket and before the closing bracket:</span></span>

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

<span data-ttu-id="d8435-223">Utilisez toujours au moins un espace entre les deux opérateurs distincts de type accolade.</span><span class="sxs-lookup"><span data-stu-id="d8435-223">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="d8435-224">Par exemple, laissez un espace entre un `[` et un `{`.</span><span class="sxs-lookup"><span data-stu-id="d8435-224">For example, leave a space between a `[` and a `{`.</span></span>

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

<span data-ttu-id="d8435-225">La même règle s’applique pour les listes ou des tableaux de tuples.</span><span class="sxs-lookup"><span data-stu-id="d8435-225">The same guideline applies for lists or arrays of tuples.</span></span>

<span data-ttu-id="d8435-226">Listes et des tableaux réparties sur plusieurs lignes suivent une règle similaire comme enregistrements :</span><span class="sxs-lookup"><span data-stu-id="d8435-226">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

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

<span data-ttu-id="d8435-227">Et comme avec les enregistrements, déclaration de l’ouverture et crochet fermant sur leur propre ligne facilitera migration autour du code et tuyauterie dans des fonctions.</span><span class="sxs-lookup"><span data-stu-id="d8435-227">And as with records, declaring the opening and closing brackets on their own line will make moving code around and piping into functions easier.</span></span>

## <a name="formatting-if-expressions"></a><span data-ttu-id="d8435-228">Mise en forme if expressions</span><span class="sxs-lookup"><span data-stu-id="d8435-228">Formatting if expressions</span></span>

<span data-ttu-id="d8435-229">Mise en retrait des instructions conditionnelles varie selon les tailles des expressions qui les composent.</span><span class="sxs-lookup"><span data-stu-id="d8435-229">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="d8435-230">Si `cond`, `e1` et `e2` sont courtes, il vous suffit de les écrire sur une seule ligne :</span><span class="sxs-lookup"><span data-stu-id="d8435-230">If `cond`, `e1` and `e2` are short, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="d8435-231">Si `cond`, `e1` ou `e2` sont plus de temps, mais pas plusieurs lignes :</span><span class="sxs-lookup"><span data-stu-id="d8435-231">If either `cond`, `e1` or `e2` are longer, but not multi-line:</span></span>

```fsharp
if cond
then e1
else e2
```

<span data-ttu-id="d8435-232">Si une des expressions est multiligne :</span><span class="sxs-lookup"><span data-stu-id="d8435-232">If any of the expressions are multi-line:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="d8435-233">Plusieurs instructions conditionnelles avec `elif` et `else` sont mises en retrait dans la même étendue en tant que le `if`:</span><span class="sxs-lookup"><span data-stu-id="d8435-233">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="d8435-234">Constructions de correspondance de modèle</span><span class="sxs-lookup"><span data-stu-id="d8435-234">Pattern matching constructs</span></span>

<span data-ttu-id="d8435-235">Utilisez un `|` pour chaque clause d’une correspondance avec aucune mise en retrait.</span><span class="sxs-lookup"><span data-stu-id="d8435-235">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="d8435-236">Si l’expression est courte, vous pouvez envisager d’utiliser une seule ligne si chaque sous-expression est également simple.</span><span class="sxs-lookup"><span data-stu-id="d8435-236">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

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

<span data-ttu-id="d8435-237">Si l’expression à droite de la flèche de critères spéciaux est trop volumineuse, déplacez-le vers la ligne suivante, mis en retrait d’une seule étape à partir de la `match` / `|`.</span><span class="sxs-lookup"><span data-stu-id="d8435-237">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="d8435-238">Filtre de correspondance de fonctions anonymes, en commençant par `function`, doit généralement pas mettre en retrait trop loin.</span><span class="sxs-lookup"><span data-stu-id="d8435-238">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="d8435-239">Par exemple, il est bien de mise en retrait d’une étendue comme suit :</span><span class="sxs-lookup"><span data-stu-id="d8435-239">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="d8435-240">Critères spéciaux dans les fonctions définies par `let` ou `let rec` doit être mis en retrait 4 espaces après le démarrage de `let`, même si `function` mot clé est utilisé :</span><span class="sxs-lookup"><span data-stu-id="d8435-240">Pattern matching in functions defined by `let` or `let rec` should be indented 4 spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="d8435-241">Nous vous déconseillons d’alignement des flèches.</span><span class="sxs-lookup"><span data-stu-id="d8435-241">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="d8435-242">Mise en forme try / with expressions</span><span class="sxs-lookup"><span data-stu-id="d8435-242">Formatting try/with expressions</span></span>

<span data-ttu-id="d8435-243">Critères spéciaux sur le type d’exception doit être mis en retrait au même niveau que `with`.</span><span class="sxs-lookup"><span data-stu-id="d8435-243">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

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

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="d8435-244">Mise en forme d’application de paramètre de fonction</span><span class="sxs-lookup"><span data-stu-id="d8435-244">Formatting function parameter application</span></span>

<span data-ttu-id="d8435-245">En règle générale, la plupart des applications de paramètre de fonction sont effectuée sur la même ligne.</span><span class="sxs-lookup"><span data-stu-id="d8435-245">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="d8435-246">Si vous souhaitez appliquer des paramètres à une fonction sur une nouvelle ligne, mettre en retrait les par une étendue.</span><span class="sxs-lookup"><span data-stu-id="d8435-246">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

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

<span data-ttu-id="d8435-247">Les mêmes règles s’appliquent pour les expressions lambda en tant qu’arguments de fonction.</span><span class="sxs-lookup"><span data-stu-id="d8435-247">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="d8435-248">Si le corps d’une expression lambda, le corps peut avoir une autre ligne, la mise en retrait par une étendue</span><span class="sxs-lookup"><span data-stu-id="d8435-248">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

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

<span data-ttu-id="d8435-249">Toutefois, si le corps d’une expression lambda est plusieurs lignes, envisagez factorisant dans une fonction distincte plutôt que d’avoir une construction multiligne appliquée en tant qu’un seul argument à une fonction.</span><span class="sxs-lookup"><span data-stu-id="d8435-249">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="d8435-250">Opérateurs infixes mise en forme</span><span class="sxs-lookup"><span data-stu-id="d8435-250">Formatting infix operators</span></span>

<span data-ttu-id="d8435-251">Opérateurs distincts par des espaces.</span><span class="sxs-lookup"><span data-stu-id="d8435-251">Separate operators by spaces.</span></span> <span data-ttu-id="d8435-252">Exceptions évident à cette règle sont les `!` et `.` opérateurs.</span><span class="sxs-lookup"><span data-stu-id="d8435-252">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="d8435-253">Expressions de correspondance des infixes sont OK pour l’alignement sur la même colonne :</span><span class="sxs-lookup"><span data-stu-id="d8435-253">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="d8435-254">Mise en forme des opérateurs de pipeline</span><span class="sxs-lookup"><span data-stu-id="d8435-254">Formatting pipeline operators</span></span>

<span data-ttu-id="d8435-255">Pipeline `|>` opérateurs doivent figurer sous elles opèrent selon des expressions.</span><span class="sxs-lookup"><span data-stu-id="d8435-255">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

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

### <a name="formatting-modules"></a><span data-ttu-id="d8435-256">Mise en forme de modules</span><span class="sxs-lookup"><span data-stu-id="d8435-256">Formatting modules</span></span>

<span data-ttu-id="d8435-257">Code dans un module local doit être mis en retrait par rapport au module, mais le code dans un module de niveau supérieur ne doit pas être mis en retrait.</span><span class="sxs-lookup"><span data-stu-id="d8435-257">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="d8435-258">Les éléments Namespace n’ont pas à être mis en retrait.</span><span class="sxs-lookup"><span data-stu-id="d8435-258">Namespace elements do not have to be indented.</span></span>

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

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="d8435-259">Mise en forme d’expressions d’objet et des interfaces</span><span class="sxs-lookup"><span data-stu-id="d8435-259">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="d8435-260">Expressions d’objet et les interfaces doivent être alignées dans la même façon avec `member` en cours de mise en retrait après 4 espaces.</span><span class="sxs-lookup"><span data-stu-id="d8435-260">Object expressions and interfaces should be aligned in the same way with `member` being indented after 4 spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="d8435-261">Mise en forme des espaces blancs dans les expressions</span><span class="sxs-lookup"><span data-stu-id="d8435-261">Formatting white space in expressions</span></span>

<span data-ttu-id="d8435-262">Éviter les espaces superflus dans F# expressions.</span><span class="sxs-lookup"><span data-stu-id="d8435-262">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="d8435-263">Arguments nommés doivent avoir également pas espace entourant le `=`:</span><span class="sxs-lookup"><span data-stu-id="d8435-263">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a><span data-ttu-id="d8435-264">Attributs de mise en forme</span><span class="sxs-lookup"><span data-stu-id="d8435-264">Formatting attributes</span></span>

<span data-ttu-id="d8435-265">[Attributs](../language-reference/attributes.md) sont placés au-dessus d’une construction :</span><span class="sxs-lookup"><span data-stu-id="d8435-265">[Attributes](../language-reference/attributes.md) are placed above a construct:</span></span>

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

### <a name="formatting-attributes-on-parameters"></a><span data-ttu-id="d8435-266">Attributs sur les paramètres de mise en forme</span><span class="sxs-lookup"><span data-stu-id="d8435-266">Formatting attributes on parameters</span></span>

<span data-ttu-id="d8435-267">Attributs peuvent également être des emplacements sur les paramètres.</span><span class="sxs-lookup"><span data-stu-id="d8435-267">Attributes can also be places on parameters.</span></span> <span data-ttu-id="d8435-268">Placez dans ce cas, puis sur la même ligne que le paramètre et avant le nom :</span><span class="sxs-lookup"><span data-stu-id="d8435-268">In this case, place then on the same line as the parameter and before the name:</span></span>

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member __.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a><span data-ttu-id="d8435-269">Plusieurs attributs de mise en forme</span><span class="sxs-lookup"><span data-stu-id="d8435-269">Formatting multiple attributes</span></span>

<span data-ttu-id="d8435-270">Lorsque plusieurs attributs sont appliqués à une construction qui n’est pas un paramètre, ils doivent être placés qu’il y ait un seul attribut par ligne :</span><span class="sxs-lookup"><span data-stu-id="d8435-270">When multiple attributes are applied to a construct that is not a parameter, they should be placed such that there is one attribute per line:</span></span>

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="d8435-271">Lorsqu’il est appliqué à un paramètre, ils doivent se trouver sur la même ligne et séparés par un `;` séparateur.</span><span class="sxs-lookup"><span data-stu-id="d8435-271">When applied to a parameter, they must be on the same line and separated by a `;` separator.</span></span>

## <a name="formatting-literals"></a><span data-ttu-id="d8435-272">Mise en forme de littéraux</span><span class="sxs-lookup"><span data-stu-id="d8435-272">Formatting literals</span></span>

<span data-ttu-id="d8435-273">[F#littéraux](../language-reference/literals.md) à l’aide de la `Literal` attribut doit placer l’attribut sur sa propre ligne et utiliser la casse Pascal d’affectation de noms :</span><span class="sxs-lookup"><span data-stu-id="d8435-273">[F# literals](../language-reference/literals.md) using the `Literal` attribute should place the attribute on its own line and use PascalCase naming:</span></span>

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

<span data-ttu-id="d8435-274">Évitez de placer l’attribut sur la même ligne que la valeur.</span><span class="sxs-lookup"><span data-stu-id="d8435-274">Avoid placing the attribute on the same line as the value.</span></span>
