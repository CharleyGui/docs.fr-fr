---
title: Conventions de codage F#
description: Découvrez des instructions générales et des idiomes F# lors de l’écriture de code.
ms.date: 01/15/2020
ms.openlocfilehash: ca86bcf714d2fb4ee5f173ee54ba12c317f9abe7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737825"
---
# <a name="f-coding-conventions"></a><span data-ttu-id="206f6-103">Conventions de codage F#</span><span class="sxs-lookup"><span data-stu-id="206f6-103">F# coding conventions</span></span>

<span data-ttu-id="206f6-104">Les conventions suivantes sont formulées à partir de l’expérience F# de l’utilisation des codes base volumineux.</span><span class="sxs-lookup"><span data-stu-id="206f6-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="206f6-105">Les [cinq principes de bonne F# code](index.md#five-principles-of-good-f-code) constituent la base de chaque recommandation.</span><span class="sxs-lookup"><span data-stu-id="206f6-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="206f6-106">Ils sont liés aux [ F# règles de conception de composants](component-design-guidelines.md), mais s’appliquent à n’importe quel F# code, pas seulement aux composants tels que les bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="206f6-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="206f6-107">Organisation du code</span><span class="sxs-lookup"><span data-stu-id="206f6-107">Organizing code</span></span>

<span data-ttu-id="206f6-108">F#propose deux méthodes principales pour organiser le code : les modules et les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="206f6-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="206f6-109">Celles-ci sont similaires, mais elles présentent les différences suivantes :</span><span class="sxs-lookup"><span data-stu-id="206f6-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="206f6-110">Les espaces de noms sont compilés en tant qu’espaces de noms .NET.</span><span class="sxs-lookup"><span data-stu-id="206f6-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="206f6-111">Les modules sont compilés en tant que classes statiques.</span><span class="sxs-lookup"><span data-stu-id="206f6-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="206f6-112">Les espaces de noms sont toujours de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="206f6-112">Namespaces are always top level.</span></span> <span data-ttu-id="206f6-113">Les modules peuvent être de niveau supérieur et imbriqués dans d’autres modules.</span><span class="sxs-lookup"><span data-stu-id="206f6-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="206f6-114">Les espaces de noms peuvent s’étendre sur plusieurs fichiers.</span><span class="sxs-lookup"><span data-stu-id="206f6-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="206f6-115">Les modules ne peuvent pas.</span><span class="sxs-lookup"><span data-stu-id="206f6-115">Modules cannot.</span></span>
* <span data-ttu-id="206f6-116">Les modules peuvent être décorés avec `[<RequireQualifiedAccess>]` et `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="206f6-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="206f6-117">Les instructions suivantes vous aideront à les utiliser pour organiser votre code.</span><span class="sxs-lookup"><span data-stu-id="206f6-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="206f6-118">Préférer les espaces de noms au niveau supérieur</span><span class="sxs-lookup"><span data-stu-id="206f6-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="206f6-119">Pour tout code consommateur public, les espaces de noms sont préférentiels aux modules au niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="206f6-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="206f6-120">Étant donné qu’ils sont compilés en tant qu’espaces de noms .NET C# , ils peuvent être consommés à partir de sans problème.</span><span class="sxs-lookup"><span data-stu-id="206f6-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="206f6-121">L’utilisation d’un module de niveau supérieur peut ne pas apparaître différente quand F#elle est appelée C# uniquement à partir de, mais pour les consommateurs, les appelants peuvent être surpris par le fait d’avoir à qualifier `MyClass` avec le module `MyCode`.</span><span class="sxs-lookup"><span data-stu-id="206f6-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="206f6-122">Appliquez avec précaution `[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="206f6-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="206f6-123">La construction `[<AutoOpen>]` peut polluer l’étendue de ce qui est disponible pour les appelants, et la réponse à l’origine d’un élément provient de « Magic ».</span><span class="sxs-lookup"><span data-stu-id="206f6-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="206f6-124">Ce n’est pas une bonne chose.</span><span class="sxs-lookup"><span data-stu-id="206f6-124">This is not a good thing.</span></span> <span data-ttu-id="206f6-125">La F# bibliothèque principale est une exception à cette règle (bien que ce fait soit également un peu controversé).</span><span class="sxs-lookup"><span data-stu-id="206f6-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="206f6-126">Toutefois, cela est pratique si vous disposez d’une fonctionnalité d’assistance pour une API publique que vous souhaitez organiser séparément de cette API publique.</span><span class="sxs-lookup"><span data-stu-id="206f6-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

```fsharp
module MyAPI =
    [<AutoOpen>]
    module private Helpers =
        let helper1 x y z =
            ...

    let myFunction1 x =
        let y = ...
        let z = ...

        helper1 x y z
```

<span data-ttu-id="206f6-127">Cela vous permet de séparer correctement les détails de l’implémentation de l’API publique d’une fonction sans avoir à qualifier complètement une application d’assistance chaque fois que vous l’appelez.</span><span class="sxs-lookup"><span data-stu-id="206f6-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="206f6-128">En outre, l’exposition des méthodes d’extension et des générateurs d’expressions au niveau de l’espace de noms peut être clairement exprimée avec `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="206f6-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="206f6-129">Utilisez `[<RequireQualifiedAccess>]` chaque fois que les noms peuvent entrer en conflit ou que vous estimez qu’il aide à la lisibilité</span><span class="sxs-lookup"><span data-stu-id="206f6-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="206f6-130">L’ajout de l’attribut `[<RequireQualifiedAccess>]` à un module indique que le module ne peut pas être ouvert et que les références aux éléments du module requièrent un accès qualifié explicite.</span><span class="sxs-lookup"><span data-stu-id="206f6-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="206f6-131">Par exemple, le module `Microsoft.FSharp.Collections.List` a cet attribut.</span><span class="sxs-lookup"><span data-stu-id="206f6-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="206f6-132">Cela est utile lorsque les fonctions et valeurs du module ont des noms qui sont susceptibles d’entrer en conflit avec des noms dans d’autres modules.</span><span class="sxs-lookup"><span data-stu-id="206f6-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="206f6-133">La nécessité d’un accès qualifié peut augmenter la maintenabilité à long terme et la évolutivité d’une bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="206f6-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="206f6-134">Trier les instructions `open` topologiquement</span><span class="sxs-lookup"><span data-stu-id="206f6-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="206f6-135">Dans F#, l’ordre des déclarations est important, y compris avec les instructions `open`.</span><span class="sxs-lookup"><span data-stu-id="206f6-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="206f6-136">Contrairement C#à, l’effet de `using` et `using static` est indépendant de l’ordre des instructions dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="206f6-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="206f6-137">Dans F#, les éléments ouverts dans une portée peuvent masquer d’autres personnes déjà présentes.</span><span class="sxs-lookup"><span data-stu-id="206f6-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="206f6-138">Cela signifie que la réorganisation des instructions `open` peut modifier la signification du code.</span><span class="sxs-lookup"><span data-stu-id="206f6-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="206f6-139">Par conséquent, n’importe quel tri arbitraire de toutes les instructions `open` (par exemple, au format alphanumérique) n’est pas recommandé, vous pouvez en effet créer un comportement différent de celui que vous attendez.</span><span class="sxs-lookup"><span data-stu-id="206f6-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="206f6-140">Au lieu de cela, nous vous recommandons de les trier [topologiquement](https://en.wikipedia.org/wiki/Topological_sorting). autrement dit, commandez vos instructions `open` dans l’ordre dans lequel les _couches_ de votre système sont définies.</span><span class="sxs-lookup"><span data-stu-id="206f6-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="206f6-141">Le tri alphanumérique au sein de différentes couches topologiques peut également être envisagé.</span><span class="sxs-lookup"><span data-stu-id="206f6-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="206f6-142">À titre d’exemple, voici le tri topologique du fichier F# d’API publique du service du compilateur :</span><span class="sxs-lookup"><span data-stu-id="206f6-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

```fsharp
namespace Microsoft.FSharp.Compiler.SourceCodeServices

open System
open System.Collections.Generic
open System.Collections.Concurrent
open System.Diagnostics
open System.IO
open System.Reflection
open System.Text

open Microsoft.FSharp.Compiler
open Microsoft.FSharp.Compiler.AbstractIL
open Microsoft.FSharp.Compiler.AbstractIL.Diagnostics
open Microsoft.FSharp.Compiler.AbstractIL.IL
open Microsoft.FSharp.Compiler.AbstractIL.ILBinaryReader
open Microsoft.FSharp.Compiler.AbstractIL.Internal
open Microsoft.FSharp.Compiler.AbstractIL.Internal.Library

open Microsoft.FSharp.Compiler.AccessibilityLogic
open Microsoft.FSharp.Compiler.Ast
open Microsoft.FSharp.Compiler.CompileOps
open Microsoft.FSharp.Compiler.CompileOptions
open Microsoft.FSharp.Compiler.Driver
open Microsoft.FSharp.Compiler.ErrorLogger
open Microsoft.FSharp.Compiler.Infos
open Microsoft.FSharp.Compiler.InfoReader
open Microsoft.FSharp.Compiler.Lexhelp
open Microsoft.FSharp.Compiler.Layout
open Microsoft.FSharp.Compiler.Lib
open Microsoft.FSharp.Compiler.NameResolution
open Microsoft.FSharp.Compiler.PrettyNaming
open Microsoft.FSharp.Compiler.Parser
open Microsoft.FSharp.Compiler.Range
open Microsoft.FSharp.Compiler.Tast
open Microsoft.FSharp.Compiler.Tastops
open Microsoft.FSharp.Compiler.TcGlobals
open Microsoft.FSharp.Compiler.TypeChecker
open Microsoft.FSharp.Compiler.SourceCodeServices.SymbolHelpers

open Internal.Utilities
open Internal.Utilities.Collections
```

<span data-ttu-id="206f6-143">Notez qu’un saut de ligne sépare les couches topologiques, chaque couche étant triée par ordre alphabétique par la suite.</span><span class="sxs-lookup"><span data-stu-id="206f6-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="206f6-144">Cette classe organise correctement le code sans occulter accidentellement des valeurs.</span><span class="sxs-lookup"><span data-stu-id="206f6-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="206f6-145">Utiliser des classes pour contenir des valeurs qui ont des effets secondaires</span><span class="sxs-lookup"><span data-stu-id="206f6-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="206f6-146">Il existe de nombreuses fois que l’initialisation d’une valeur peut avoir des effets secondaires, par exemple l’instanciation d’un contexte à une base de données ou à une autre ressource distante.</span><span class="sxs-lookup"><span data-stu-id="206f6-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="206f6-147">Il est tentant d’initialiser ces éléments dans un module et de les utiliser dans les fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="206f6-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

```fsharp
// This is bad!
module MyApi =
    let dep1 = File.ReadAllText "/Users/{your name}/connectionstring.txt"
    let dep2 = Environment.GetEnvironmentVariable "DEP_2"

    let private r = Random()
    let dep3() = r.Next() // Problematic if multiple threads use this

    let function1 arg = doStuffWith dep1 dep2 dep3 arg
    let function2 arg = doSutffWith dep1 dep2 dep3 arg
```

<span data-ttu-id="206f6-148">C’est souvent une mauvaise idée pour plusieurs raisons :</span><span class="sxs-lookup"><span data-stu-id="206f6-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="206f6-149">Tout d’abord, la configuration de l’application est envoyée au code base avec `dep1` et `dep2`.</span><span class="sxs-lookup"><span data-stu-id="206f6-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="206f6-150">Cela est difficile à maintenir dans les codes base plus volumineux.</span><span class="sxs-lookup"><span data-stu-id="206f6-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="206f6-151">Deuxièmement, les données initialisées statiquement ne doivent pas inclure de valeurs qui ne sont pas thread-safe si votre composant utilise lui-même plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="206f6-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="206f6-152">Cela est clairement violé par `dep3`.</span><span class="sxs-lookup"><span data-stu-id="206f6-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="206f6-153">Enfin, l’initialisation de module se compile en un constructeur statique pour l’ensemble de l’unité de compilation.</span><span class="sxs-lookup"><span data-stu-id="206f6-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="206f6-154">Si une erreur se produit dans l’initialisation de la valeur liée à Let dans ce module, elle se manifeste comme un `TypeInitializationException` qui est ensuite mis en cache pour toute la durée de vie de l’application.</span><span class="sxs-lookup"><span data-stu-id="206f6-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="206f6-155">Cela peut être difficile à diagnostiquer.</span><span class="sxs-lookup"><span data-stu-id="206f6-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="206f6-156">Il y a généralement une exception interne que vous pouvez essayer de créer, mais si ce n’est pas le cas, il n’y a pas d’objet indiquant la cause racine.</span><span class="sxs-lookup"><span data-stu-id="206f6-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="206f6-157">Au lieu de cela, il vous suffit d’utiliser une classe simple pour stocker les dépendances :</span><span class="sxs-lookup"><span data-stu-id="206f6-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="206f6-158">Cela permet d’activer les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="206f6-158">This enables the following:</span></span>

1. <span data-ttu-id="206f6-159">Envoi d’un État dépendant en dehors de l’API elle-même.</span><span class="sxs-lookup"><span data-stu-id="206f6-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="206f6-160">La configuration peut maintenant être effectuée en dehors de l’API.</span><span class="sxs-lookup"><span data-stu-id="206f6-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="206f6-161">Les erreurs dans l’initialisation des valeurs dépendantes ne sont pas susceptibles de se manifester en tant que `TypeInitializationException`.</span><span class="sxs-lookup"><span data-stu-id="206f6-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="206f6-162">L’API est désormais plus facile à tester.</span><span class="sxs-lookup"><span data-stu-id="206f6-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="206f6-163">Gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="206f6-163">Error management</span></span>

<span data-ttu-id="206f6-164">La gestion des erreurs dans les systèmes de grande taille est un effort complexe et en nuances de temps, et il n’y a pas de puce Silver pour s’assurer que vos systèmes sont tolérants aux pannes et se comportent correctement.</span><span class="sxs-lookup"><span data-stu-id="206f6-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="206f6-165">Les instructions suivantes doivent vous aider à naviguer dans cet espace difficile.</span><span class="sxs-lookup"><span data-stu-id="206f6-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="206f6-166">Représenter des cas d’erreur et un État non conforme dans des types intrinsèques à votre domaine</span><span class="sxs-lookup"><span data-stu-id="206f6-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="206f6-167">Avec les [unions discriminées](../language-reference/discriminated-unions.md), F# vous donne la possibilité de représenter un état de programme défectueux dans votre système de type.</span><span class="sxs-lookup"><span data-stu-id="206f6-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="206f6-168">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="206f6-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="206f6-169">Dans ce cas, il existe trois façons connues de retirer de l’argent d’un compte bancaire.</span><span class="sxs-lookup"><span data-stu-id="206f6-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="206f6-170">Chaque cas d’erreur est représenté dans le type et peut donc être traité en toute sécurité dans tout le programme.</span><span class="sxs-lookup"><span data-stu-id="206f6-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="206f6-171">En général, si vous pouvez modéliser les différentes façons dont un événement peut **échouer** dans votre domaine, le code de gestion des erreurs n’est plus traité comme un problème que vous devez traiter en plus du déroulement normal du programme.</span><span class="sxs-lookup"><span data-stu-id="206f6-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="206f6-172">Il s’agit simplement d’une partie du déroulement normal du programme et n’est pas considéré comme **exceptionnel**.</span><span class="sxs-lookup"><span data-stu-id="206f6-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="206f6-173">Cela présente deux avantages principaux :</span><span class="sxs-lookup"><span data-stu-id="206f6-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="206f6-174">Il est plus facile à gérer lorsque votre domaine évolue dans le temps.</span><span class="sxs-lookup"><span data-stu-id="206f6-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="206f6-175">Les cas d’erreur sont plus faciles à tester par unité.</span><span class="sxs-lookup"><span data-stu-id="206f6-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="206f6-176">Utiliser des exceptions lorsque des erreurs ne peuvent pas être représentées avec des types</span><span class="sxs-lookup"><span data-stu-id="206f6-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="206f6-177">Toutes les erreurs ne peuvent pas être représentées dans un domaine posant problème.</span><span class="sxs-lookup"><span data-stu-id="206f6-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="206f6-178">Ces types d’erreurs sont de nature *exceptionnelle* , par conséquent la possibilité de déclencher et d’intercepter des exceptions dans F#.</span><span class="sxs-lookup"><span data-stu-id="206f6-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="206f6-179">Tout d’abord, il est recommandé de lire les [règles de conception des exceptions](../../standard/design-guidelines/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="206f6-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="206f6-180">Elles s’appliquent également F#à.</span><span class="sxs-lookup"><span data-stu-id="206f6-180">These are also applicable to F#.</span></span>

<span data-ttu-id="206f6-181">Les constructions principales disponibles dans dans F# le but de lever des exceptions doivent être prises en compte dans l’ordre de préférence suivant :</span><span class="sxs-lookup"><span data-stu-id="206f6-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="206f6-182">Fonction</span><span class="sxs-lookup"><span data-stu-id="206f6-182">Function</span></span> | <span data-ttu-id="206f6-183">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="206f6-183">Syntax</span></span> | <span data-ttu-id="206f6-184">Fonction</span><span class="sxs-lookup"><span data-stu-id="206f6-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="206f6-185">Déclenche un `System.ArgumentNullException` avec le nom d’argument spécifié.</span><span class="sxs-lookup"><span data-stu-id="206f6-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="206f6-186">Déclenche un `System.ArgumentException` avec un nom d’argument et un message spécifiés.</span><span class="sxs-lookup"><span data-stu-id="206f6-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="206f6-187">Déclenche un `System.InvalidOperationException` avec le message spécifié.</span><span class="sxs-lookup"><span data-stu-id="206f6-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="206f6-188">Mécanisme à usage général pour lever des exceptions.</span><span class="sxs-lookup"><span data-stu-id="206f6-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="206f6-189">Déclenche un `System.Exception` avec le message spécifié.</span><span class="sxs-lookup"><span data-stu-id="206f6-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="206f6-190">Déclenche un `System.Exception` avec un message déterminé par la chaîne de format et ses entrées.</span><span class="sxs-lookup"><span data-stu-id="206f6-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="206f6-191">Utilisez `nullArg`, `invalidArg` et `invalidOp` comme mécanisme pour lever `ArgumentNullException`, `ArgumentException` et `InvalidOperationException`, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="206f6-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="206f6-192">Les fonctions `failwith` et `failwithf` doivent généralement être évitées, car elles déclenchent le type de `Exception` de base, et non une exception spécifique.</span><span class="sxs-lookup"><span data-stu-id="206f6-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="206f6-193">Conformément aux [règles de conception d’exception](../../standard/design-guidelines/exceptions.md), vous souhaitez déclencher des exceptions plus spécifiques lorsque vous le pouvez.</span><span class="sxs-lookup"><span data-stu-id="206f6-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="206f6-194">Utilisation de la syntaxe de gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="206f6-194">Using exception-handling syntax</span></span>

<span data-ttu-id="206f6-195">F#prend en charge les modèles d’exception via la syntaxe `try...with` :</span><span class="sxs-lookup"><span data-stu-id="206f6-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="206f6-196">Le rapprochement des fonctionnalités à effectuer en cas d’exception avec les critères spéciaux peut être un peu délicat si vous souhaitez que le code reste propre.</span><span class="sxs-lookup"><span data-stu-id="206f6-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="206f6-197">Pour ce faire, il est possible d’utiliser des [modèles actifs](../language-reference/active-patterns.md) comme moyen de regrouper les fonctionnalités entourant un cas d’erreur avec une exception.</span><span class="sxs-lookup"><span data-stu-id="206f6-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="206f6-198">Par exemple, vous pouvez consommer une API qui, lorsqu’elle lève une exception, englobe des informations précieuses dans les métadonnées d’exception.</span><span class="sxs-lookup"><span data-stu-id="206f6-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="206f6-199">La désencapsulation d’une valeur utile dans le corps de l’exception capturée à l’intérieur du modèle actif et le retour de cette valeur peut être utile dans certaines situations.</span><span class="sxs-lookup"><span data-stu-id="206f6-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="206f6-200">N’utilisez pas la gestion des erreurs monadic pour remplacer les exceptions</span><span class="sxs-lookup"><span data-stu-id="206f6-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="206f6-201">Les exceptions sont considérées comme un peu Taboo dans la programmation fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="206f6-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="206f6-202">En effet, les exceptions enfreignent la pureté, donc il est préférable de les considérer comme non très fonctionnelles.</span><span class="sxs-lookup"><span data-stu-id="206f6-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="206f6-203">Toutefois, cela ignore la réalité de l’emplacement où le code doit s’exécuter et les erreurs d’exécution peuvent se produire.</span><span class="sxs-lookup"><span data-stu-id="206f6-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="206f6-204">En général, écrivez du code sur l’hypothèse que la plupart des choses ne sont ni pures ni totales, afin de minimiser les surprises.</span><span class="sxs-lookup"><span data-stu-id="206f6-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="206f6-205">Il est important de prendre en compte les points forts/aspects d’exception suivants en ce qui concerne leur pertinence et leur adéquation dans le Runtime .NET et l’écosystème interlangage dans son ensemble :</span><span class="sxs-lookup"><span data-stu-id="206f6-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="206f6-206">Elles contiennent des informations de diagnostic détaillées, ce qui est très utile lors du débogage d’un problème.</span><span class="sxs-lookup"><span data-stu-id="206f6-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="206f6-207">Elles sont bien comprises par le runtime et d’autres langages .NET.</span><span class="sxs-lookup"><span data-stu-id="206f6-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="206f6-208">Ils peuvent réduire les réemplois importants par rapport au code qui *ne permet pas d’éviter* les exceptions en implémentant un sous-ensemble de leur sémantique sur une base ad hoc.</span><span class="sxs-lookup"><span data-stu-id="206f6-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="206f6-209">Ce troisième point est essentiel.</span><span class="sxs-lookup"><span data-stu-id="206f6-209">This third point is critical.</span></span> <span data-ttu-id="206f6-210">Pour les opérations complexes non triviales, l’échec de l’utilisation d’exceptions peut entraîner une gestion des structures comme suit :</span><span class="sxs-lookup"><span data-stu-id="206f6-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="206f6-211">Ce qui peut facilement entraîner un code fragile comme la mise en correspondance de modèle sur les erreurs de type « chaîne » :</span><span class="sxs-lookup"><span data-stu-id="206f6-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="206f6-212">En outre, il peut être tentant d’absorber une exception dans le désir d’une fonction « simple » qui retourne un type « plus attrayant » :</span><span class="sxs-lookup"><span data-stu-id="206f6-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="206f6-213">Malheureusement, `tryReadAllText` peut lever de nombreuses exceptions en fonction de la myriade de choses qui peuvent se produire sur un système de fichiers, et ce code rejette toutes les informations sur ce qui peut en fait être erroné dans votre environnement.</span><span class="sxs-lookup"><span data-stu-id="206f6-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="206f6-214">Si vous remplacez ce code par un type de résultat, vous revenez à l’analyse du message d’erreur « typé en chaîne » :</span><span class="sxs-lookup"><span data-stu-id="206f6-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Ok
    with e -> Error e.Message

let r = tryReadAllText "path-to-file"
match r with
| Ok text -> ...
| Error e ->
    if e.Contains "uh oh, here we go again..." then ...
    else ...
```

<span data-ttu-id="206f6-215">Et le placement de l’objet exception lui-même dans le constructeur `Error` vous oblige simplement à gérer correctement le type d’exception sur le site d’appel plutôt que dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="206f6-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="206f6-216">Cela permet de créer efficacement des exceptions vérifiées, qui sont notoirement unfun pour traiter en tant qu’appelant d’une API.</span><span class="sxs-lookup"><span data-stu-id="206f6-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="206f6-217">Une bonne alternative aux exemples ci-dessus consiste à intercepter *des exceptions spécifiques* et à retourner une valeur significative dans le contexte de cette exception.</span><span class="sxs-lookup"><span data-stu-id="206f6-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="206f6-218">Si vous modifiez la fonction `tryReadAllText` comme suit, `None` a plus de sens :</span><span class="sxs-lookup"><span data-stu-id="206f6-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="206f6-219">Au lieu de fonctionner comme un catch, cette fonction gère désormais correctement le cas lorsqu’un fichier est introuvable et assigne cette signification à un retour.</span><span class="sxs-lookup"><span data-stu-id="206f6-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="206f6-220">Cette valeur de retour peut être mappée à ce cas d’erreur, sans ignorer d’informations contextuelles ou obliger les appelants à traiter un cas qui peut ne pas être pertinent à ce stade du code.</span><span class="sxs-lookup"><span data-stu-id="206f6-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="206f6-221">Les types tels que `Result<'Success, 'Error>` sont appropriés pour les opérations de base où ils ne sont F# pas imbriqués, et les types facultatifs sont *parfaits*pour représenter quand une opération peut retourner *un élément* ou rien.</span><span class="sxs-lookup"><span data-stu-id="206f6-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="206f6-222">Toutefois, ils ne remplacent pas les exceptions et ne doivent pas être utilisés dans une tentative de remplacement des exceptions.</span><span class="sxs-lookup"><span data-stu-id="206f6-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="206f6-223">Au lieu de cela, elles doivent être appliquées judicieusement pour répondre à des aspects spécifiques de la stratégie de gestion des exceptions et des erreurs de manière ciblée.</span><span class="sxs-lookup"><span data-stu-id="206f6-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="206f6-224">Programmation partielle d’application et de point-Free</span><span class="sxs-lookup"><span data-stu-id="206f6-224">Partial application and point-free programming</span></span>

<span data-ttu-id="206f6-225">F#prend en charge l’application partielle et, par conséquent, les différentes façons de programmer dans un style point-to-free.</span><span class="sxs-lookup"><span data-stu-id="206f6-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="206f6-226">Cela peut être bénéfique pour la réutilisation de code dans un module ou pour l’implémentation d’un événement, mais il ne s’agit pas d’un point à exposer publiquement.</span><span class="sxs-lookup"><span data-stu-id="206f6-226">This can be beneficial for code reuse within a module or the implementation of something, but it is not something to expose publicly.</span></span> <span data-ttu-id="206f6-227">En général, la programmation sans point n’est pas un fait en soi et peut ajouter une barrière cognitive importante pour les personnes qui ne sont pas immergées dans le style.</span><span class="sxs-lookup"><span data-stu-id="206f6-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="206f6-228">N’utilisez pas d’application partielle et de curryfication dans les API publiques</span><span class="sxs-lookup"><span data-stu-id="206f6-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="206f6-229">Avec peu d’exceptions, l’utilisation d’une application partielle dans des API publiques peut prêter à confusion pour les consommateurs.</span><span class="sxs-lookup"><span data-stu-id="206f6-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="206f6-230">En règle générale, les valeurs liées F# à `let`dans le code sont des **valeurs**, et non des valeurs de **fonction**.</span><span class="sxs-lookup"><span data-stu-id="206f6-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="206f6-231">La combinaison de valeurs et de valeurs de fonction peut entraîner l’enregistrement d’un petit nombre de lignes de code dans Exchange pour une surcharge cognitive, en particulier si elle est associée à des opérateurs tels que `>>` pour composer des fonctions.</span><span class="sxs-lookup"><span data-stu-id="206f6-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="206f6-232">Tenez compte des implications des outils pour la programmation sans point</span><span class="sxs-lookup"><span data-stu-id="206f6-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="206f6-233">Les fonctions curryfiée n’étiquettent pas leurs arguments.</span><span class="sxs-lookup"><span data-stu-id="206f6-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="206f6-234">Cela a des implications en matière d’outils.</span><span class="sxs-lookup"><span data-stu-id="206f6-234">This has tooling implications.</span></span> <span data-ttu-id="206f6-235">Considérez les deux fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="206f6-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="206f6-236">Les deux sont des fonctions valides, mais `funcWithApplication` est une fonction curryfiée.</span><span class="sxs-lookup"><span data-stu-id="206f6-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="206f6-237">Lorsque vous pointez sur leurs types dans un éditeur, vous voyez ceci :</span><span class="sxs-lookup"><span data-stu-id="206f6-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="206f6-238">Sur le site d’appel, les info-bulles dans des outils tels que Visual Studio ne vous fournissent pas d’informations significatives sur les types d’entrées `string` et `int` réellement représentés.</span><span class="sxs-lookup"><span data-stu-id="206f6-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="206f6-239">Si vous rencontrez du code de point-Free comme `funcWithApplication` qui est publiquement utilisable, il est recommandé d’effectuer une expansion η complète afin que les outils puissent récupérer des noms significatifs pour les arguments.</span><span class="sxs-lookup"><span data-stu-id="206f6-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="206f6-240">En outre, le débogage du code de point-Free peut être difficile, voire impossible.</span><span class="sxs-lookup"><span data-stu-id="206f6-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="206f6-241">Les outils de débogage s’appuient sur des valeurs liées aux noms (par exemple, `let` des liaisons) afin que vous puissiez inspecter les valeurs intermédiaires au milieu de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="206f6-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="206f6-242">Lorsque votre code n’a pas de valeurs à inspecter, il n’y a rien à déboguer.</span><span class="sxs-lookup"><span data-stu-id="206f6-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="206f6-243">À l’avenir, les outils de débogage peuvent évoluer pour synthétiser ces valeurs en fonction des chemins d’accès exécutés précédemment, mais il n’est pas judicieux de couvrir vos résultats sur les fonctionnalités de débogage *potentielles* .</span><span class="sxs-lookup"><span data-stu-id="206f6-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="206f6-244">Envisagez l’application partielle comme une technique pour réduire la réutilisabilité interne</span><span class="sxs-lookup"><span data-stu-id="206f6-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="206f6-245">Contrairement au point précédent, l’application partielle est un outil formidable pour réduire la réutilisabilité dans une application ou les éléments internes plus approfondis d’une API.</span><span class="sxs-lookup"><span data-stu-id="206f6-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="206f6-246">Il peut être utile pour les tests unitaires de l’implémentation d’API plus compliquées, où les réutilisations sont souvent difficiles à gérer.</span><span class="sxs-lookup"><span data-stu-id="206f6-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="206f6-247">Par exemple, le code suivant montre comment vous pouvez accomplir ce que la plupart des frameworks factices vous procurent sans prendre de dépendance externe sur une telle infrastructure et avoir à apprendre une API de rôle associé.</span><span class="sxs-lookup"><span data-stu-id="206f6-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="206f6-248">Par exemple, considérez la topographie de solution suivante :</span><span class="sxs-lookup"><span data-stu-id="206f6-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="206f6-249">`ImplementationLogic.fsproj` peut exposer du code tel que :</span><span class="sxs-lookup"><span data-stu-id="206f6-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="206f6-250">Le test unitaire `Transactions.doTransaction` dans `ImplementationLogic.Tests.fsproj` est simple :</span><span class="sxs-lookup"><span data-stu-id="206f6-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fsproj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="206f6-251">L’application partielle de `doTransaction` avec un objet de contexte factice vous permet d’appeler la fonction dans tous vos tests unitaires sans avoir à construire un contexte simulé à chaque fois :</span><span class="sxs-lookup"><span data-stu-id="206f6-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

```fsharp
namespace TransactionTests

open Xunit
open TransactionTypes
open TransactionsTestingUtil
open TransactionsTestingUtil.TransactionsTestable

let testableContext =
    { new ITransactionContext with
        member _.TheFirstMember() = ...
        member _.TheSecondMember() = ... }

let transactionRoutine = getTestableTransactionRoutine testableContext

[<Fact>]
let ``Test withdrawal transaction with 0.0 for balance``() =
    let expected = ...
    let actual = transactionRoutine TransactionType.Withdraw 0.0
    Assert.Equal(expected, actual)
```

<span data-ttu-id="206f6-252">Cette technique ne doit pas être appliquée universellement à votre code base, mais il s’agit d’un bon moyen de réduire la réutilisabilité pour les éléments internes complexes et les tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="206f6-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="206f6-253">Contrôle d'accès</span><span class="sxs-lookup"><span data-stu-id="206f6-253">Access control</span></span>

<span data-ttu-id="206f6-254">F#offre plusieurs options pour le [contrôle d’accès](../language-reference/access-control.md), héritées de ce qui est disponible dans le Runtime .net.</span><span class="sxs-lookup"><span data-stu-id="206f6-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="206f6-255">Celles-ci ne sont pas uniquement utilisables pour les types. vous pouvez également les utiliser pour les fonctions.</span><span class="sxs-lookup"><span data-stu-id="206f6-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="206f6-256">Préférez les types et les membres non`public` jusqu’à ce que vous ayez besoin qu’ils soient consommables publiquement.</span><span class="sxs-lookup"><span data-stu-id="206f6-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="206f6-257">Cela réduit également ce que les consommateurs couplent à.</span><span class="sxs-lookup"><span data-stu-id="206f6-257">This also minimizes what consumers couple to.</span></span>
* <span data-ttu-id="206f6-258">Efforcez-vous de conserver toutes les fonctionnalités d’assistance `private`.</span><span class="sxs-lookup"><span data-stu-id="206f6-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="206f6-259">Envisagez l’utilisation de `[<AutoOpen>]` sur un module privé de fonctions d’assistance si elles deviennent nombreuses.</span><span class="sxs-lookup"><span data-stu-id="206f6-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="206f6-260">Inférence de type et génériques</span><span class="sxs-lookup"><span data-stu-id="206f6-260">Type inference and generics</span></span>

<span data-ttu-id="206f6-261">L’inférence de type peut vous éviter de saisir un grand nombre de réutilisables.</span><span class="sxs-lookup"><span data-stu-id="206f6-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="206f6-262">La généralisation automatique dans F# le compilateur peut vous aider à écrire du code plus générique sans pratiquement aucun effort supplémentaire de votre part.</span><span class="sxs-lookup"><span data-stu-id="206f6-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="206f6-263">Toutefois, ces fonctionnalités ne sont pas universellement bonnes.</span><span class="sxs-lookup"><span data-stu-id="206f6-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="206f6-264">Envisagez d’étiqueter les noms d’arguments avec des types explicites dans les API publiques et de ne pas compter sur l’inférence de type pour ce.</span><span class="sxs-lookup"><span data-stu-id="206f6-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="206f6-265">Cela est dû au fait que **vous** devez contrôler la forme de votre API, et non le compilateur.</span><span class="sxs-lookup"><span data-stu-id="206f6-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="206f6-266">Bien que le compilateur puisse faire un travail précis au niveau de l’inférence des types pour vous, il est possible de modifier la forme de votre API si les éléments internes sur lesquels elle repose ont des types modifiés.</span><span class="sxs-lookup"><span data-stu-id="206f6-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="206f6-267">C’est peut-être ce que vous souhaitez, mais il résultera certainement d’une modification de l’API avec rupture que les consommateurs en aval devront ensuite traiter.</span><span class="sxs-lookup"><span data-stu-id="206f6-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="206f6-268">Au lieu de cela, si vous contrôlez explicitement la forme de votre API publique, vous pouvez contrôler ces modifications avec rupture.</span><span class="sxs-lookup"><span data-stu-id="206f6-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="206f6-269">En termes de DDD, cela peut être considéré comme une couche de lutte contre la corruption.</span><span class="sxs-lookup"><span data-stu-id="206f6-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="206f6-270">Envisagez de donner un nom explicite à vos arguments génériques.</span><span class="sxs-lookup"><span data-stu-id="206f6-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="206f6-271">À moins que vous n’écriviez du code véritablement générique qui n’est pas spécifique à un domaine particulier, un nom explicite peut aider d’autres programmeurs à comprendre le domaine dans lequel ils travaillent.</span><span class="sxs-lookup"><span data-stu-id="206f6-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="206f6-272">Par exemple, un paramètre de type nommé `'Document` dans le contexte de l’interaction avec une base de données de documents rend plus clair que les types de documents génériques peuvent être acceptés par la fonction ou le membre que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="206f6-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="206f6-273">Envisagez de nommer des paramètres de type générique avec casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="206f6-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="206f6-274">C’est le moyen général de faire des choses dans .NET. il est donc recommandé d’utiliser casse Pascal au lieu de snake_case ou la casse mixte.</span><span class="sxs-lookup"><span data-stu-id="206f6-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="206f6-275">Enfin, la généralisation automatique n’est pas toujours une aubaine pour les personnes F# qui découvrent ou une base de code volumineuse.</span><span class="sxs-lookup"><span data-stu-id="206f6-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="206f6-276">L’utilisation de composants génériques implique une surcharge cognitive.</span><span class="sxs-lookup"><span data-stu-id="206f6-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="206f6-277">En outre, si des fonctions automatiquement généralisées ne sont pas utilisées avec des types d’entrée différents (qui peuvent être utilisés en tant que tels), il n’y a pas d’avantages réels pour eux, à ce moment précis.</span><span class="sxs-lookup"><span data-stu-id="206f6-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="206f6-278">Envisagez toujours d’être générique pour le code que vous écrivez.</span><span class="sxs-lookup"><span data-stu-id="206f6-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="206f6-279">Performances</span><span class="sxs-lookup"><span data-stu-id="206f6-279">Performance</span></span>

### <a name="prefer-structs-for-small-data-types"></a><span data-ttu-id="206f6-280">Préférer des structs pour les petits types de données</span><span class="sxs-lookup"><span data-stu-id="206f6-280">Prefer structs for small data types</span></span>

<span data-ttu-id="206f6-281">L’utilisation de structs (également appelés types valeur) peut souvent aboutir à des performances supérieures pour du code, car il évite généralement d’allouer des objets.</span><span class="sxs-lookup"><span data-stu-id="206f6-281">Using structs (also called Value Types) can often result in higher performance for some code because it typically avoids allocating objects.</span></span> <span data-ttu-id="206f6-282">Toutefois, les structs ne sont pas toujours un bouton « Go plus rapide » : si la taille des données d’un struct dépasse 16 octets, la copie des données peut souvent entraîner une réduction du temps processeur par rapport à l’utilisation d’un type référence.</span><span class="sxs-lookup"><span data-stu-id="206f6-282">However, structs are not always a "go faster" button: if the size of the data in a struct exceeds 16 bytes, copying the data can often result in more CPU time spend than using a reference type.</span></span>

<span data-ttu-id="206f6-283">Pour déterminer si vous devez utiliser un struct, tenez compte des conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="206f6-283">To determine if you should use a struct, consider the following conditions:</span></span>

- <span data-ttu-id="206f6-284">Si la taille de vos données est inférieure ou égal à 16 octets.</span><span class="sxs-lookup"><span data-stu-id="206f6-284">If the size of your data is 16 bytes or smaller.</span></span>
- <span data-ttu-id="206f6-285">Si vous avez probablement un grand nombre de ces types de données résidant en mémoire dans un programme en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="206f6-285">If you're likely to have many of these data types resident in memory in a running program.</span></span>

<span data-ttu-id="206f6-286">Si la première condition s’applique, vous devez généralement utiliser un struct.</span><span class="sxs-lookup"><span data-stu-id="206f6-286">If the first condition applies, you should generally use a struct.</span></span> <span data-ttu-id="206f6-287">Si les deux s’appliquent, vous devez presque toujours utiliser un struct.</span><span class="sxs-lookup"><span data-stu-id="206f6-287">If both apply, you should almost always use a struct.</span></span> <span data-ttu-id="206f6-288">Il peut y avoir des cas où les conditions précédentes s’appliquent, mais l’utilisation d’un struct n’est pas mieux ou pire que l’utilisation d’un type référence, mais elles sont susceptibles d’être rares.</span><span class="sxs-lookup"><span data-stu-id="206f6-288">There may be some cases where the previous conditions apply, but using a struct is no better or worse than using a reference type, but they are likely to be rare.</span></span> <span data-ttu-id="206f6-289">Toutefois, il est important de toujours mesurer le moment où les modifications sont apportées, et non pas en fonction de l’hypothèse ou de l’intuition.</span><span class="sxs-lookup"><span data-stu-id="206f6-289">It's important to always measure when making changes like this, though, and not operate on assumption or intuition.</span></span>

#### <a name="prefer-struct-tuples-when-grouping-small-value-types"></a><span data-ttu-id="206f6-290">Préférer les tuples de struct lors du regroupement de petits types de valeur</span><span class="sxs-lookup"><span data-stu-id="206f6-290">Prefer struct tuples when grouping small value types</span></span>

<span data-ttu-id="206f6-291">Considérez les deux fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="206f6-291">Consider the following two functions:</span></span>

```fsharp
let rec runWithTuple t offset times =
    let offsetValues x y z offset =
        (x + offset, y + offset, z + offset)

    if times <= 0 then
        t
    else
        let (x, y, z) = t
        let r = offsetValues x y z offset
        runWithTuple r offset (times - 1)

let rec runWithStructTuple t offset times =
    let offsetValues x y z offset =
        struct(x + offset, y + offset, z + offset)

    if times <= 0 then
        t
    else
        let struct(x, y, z) = t
        let r = offsetValues x y z offset
        runWithStructTuple r offset (times - 1)
```

<span data-ttu-id="206f6-292">Lorsque vous testez ces fonctions avec un outil d’évaluation statistique comme [BenchmarkDotNet](https://benchmarkdotnet.org/), vous constaterez que la fonction `runWithStructTuple` qui utilise des tuples de struct s’exécute 40% plus rapidement et n’alloue pas de mémoire.</span><span class="sxs-lookup"><span data-stu-id="206f6-292">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that the `runWithStructTuple` function that uses struct tuples runs 40% faster and allocates no memory.</span></span>

<span data-ttu-id="206f6-293">Toutefois, ces résultats ne seront pas toujours le cas dans votre propre code.</span><span class="sxs-lookup"><span data-stu-id="206f6-293">However, these results won't always be the case in your own code.</span></span> <span data-ttu-id="206f6-294">Si vous marquez une fonction comme `inline`, le code qui utilise des tuples de référence peut obtenir des optimisations supplémentaires, ou le code qui allouerait peut simplement être optimisé.</span><span class="sxs-lookup"><span data-stu-id="206f6-294">If you mark a function as `inline`, code that uses reference tuples may get some additional optimizations, or code that would allocate could simply be optimized away.</span></span> <span data-ttu-id="206f6-295">Vous devez toujours mesurer les résultats chaque fois que les performances le concernent et ne jamais travailler en fonction de l’hypothèse ou de l’intuition.</span><span class="sxs-lookup"><span data-stu-id="206f6-295">You should always measure results whenever performance is concerned, and never operate based on assumption or intuition.</span></span>

#### <a name="prefer-struct-records-when-the-data-type-is-small"></a><span data-ttu-id="206f6-296">Préférer les enregistrements de struct lorsque le type de données est petit</span><span class="sxs-lookup"><span data-stu-id="206f6-296">Prefer struct records when the data type is small</span></span>

<span data-ttu-id="206f6-297">La règle empirique décrite précédemment contient également les [ F# types d’enregistrements](../language-reference/records.md).</span><span class="sxs-lookup"><span data-stu-id="206f6-297">The rule of thumb described earlier also holds for [F# record types](../language-reference/records.md).</span></span> <span data-ttu-id="206f6-298">Tenez compte des types de données et des fonctions suivants qui les traitent :</span><span class="sxs-lookup"><span data-stu-id="206f6-298">Consider the following data types and functions that process them:</span></span>

```fsharp
type Point = { X: float; Y: float; Z: float }

[<Struct>]
type SPoint = { X: float; Y: float; Z: float }

let rec processPoint (p: Point) offset times =
    let inline offsetValues (p: Point) offset =
        { p with X = p.X + offset; Y = p.Y + offset; Z = p.Z + offset }

    if times <= 0 then
        p
    else
        let r = offsetValues p offset
        processPoint r offset (times - 1)

let rec processStructPoint (p: SPoint) offset times =
    let inline offsetValues (p: SPoint) offset =
        { p with X = p.X + offset; Y = p.Y + offset; Z = p.Z + offset }

    if times <= 0 then
        p
    else
        let r = offsetValues p offset
        processStructPoint r offset (times - 1)
```

<span data-ttu-id="206f6-299">Cela est similaire au code de tuple précédent, mais cette fois-ci, l’exemple utilise des enregistrements et une fonction interne Inline.</span><span class="sxs-lookup"><span data-stu-id="206f6-299">This is similar to the previous tuple code, but this time the example uses records and an inlined inner function.</span></span>

<span data-ttu-id="206f6-300">Lorsque vous testez ces fonctions avec un outil d’évaluation statistique comme [BenchmarkDotNet](https://benchmarkdotnet.org/), vous constaterez que `processStructPoint` s’exécute presque 60% plus rapidement et n’alloue rien sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="206f6-300">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that `processStructPoint` runs nearly 60% faster and allocates nothing on the managed heap.</span></span>

#### <a name="prefer-struct-discriminated-unions-when-the-data-type-is-small"></a><span data-ttu-id="206f6-301">Préférer les unions discriminées struct lorsque le type de données est petit</span><span class="sxs-lookup"><span data-stu-id="206f6-301">Prefer struct discriminated unions when the data type is small</span></span>

<span data-ttu-id="206f6-302">Les observations précédentes sur les performances avec les tuples de struct et les enregistrements contiennent également des [ F# unions discriminées](../language-reference/discriminated-unions.md).</span><span class="sxs-lookup"><span data-stu-id="206f6-302">The previous observations about performance with struct tuples and records also holds for [F# Discriminated Unions](../language-reference/discriminated-unions.md).</span></span> <span data-ttu-id="206f6-303">Examinons le code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="206f6-303">Consider the following code:</span></span>

```fsharp
    type Name = Name of string
    
    [<Struct>]
    type SName = SName of string

    let reverseName (Name s) =
        s.ToCharArray()
        |> Array.rev
        |> string
        |> Name

    let structReverseName (SName s) =
        s.ToCharArray()
        |> Array.rev
        |> string
        |> SName
```

<span data-ttu-id="206f6-304">Il est courant de définir des unions discriminées à cas unique comme celles-ci pour la modélisation de domaine.</span><span class="sxs-lookup"><span data-stu-id="206f6-304">It's common to define single-case Discriminated Unions like this for domain modeling.</span></span> <span data-ttu-id="206f6-305">Lorsque vous testez ces fonctions avec un outil d’évaluation statistique comme [BenchmarkDotNet](https://benchmarkdotnet.org/), vous constaterez que `structReverseName` s’exécute environ 25% plus rapidement que `reverseName` pour les chaînes de petite taille.</span><span class="sxs-lookup"><span data-stu-id="206f6-305">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that `structReverseName` runs about 25% faster than `reverseName` for small strings.</span></span> <span data-ttu-id="206f6-306">Pour les chaînes volumineuses, elles sont toutes deux identiques.</span><span class="sxs-lookup"><span data-stu-id="206f6-306">For large strings, both perform about the same.</span></span> <span data-ttu-id="206f6-307">Ainsi, dans ce cas, il est toujours préférable d’utiliser un struct.</span><span class="sxs-lookup"><span data-stu-id="206f6-307">So, in this case, it's always preferable to use a struct.</span></span> <span data-ttu-id="206f6-308">Comme mentionné précédemment, il est toujours possible de mesurer et de ne pas utiliser les hypothèses ou l’intuition.</span><span class="sxs-lookup"><span data-stu-id="206f6-308">As previously mentioned, always measure and do not operate on assumptions or intuition.</span></span>

<span data-ttu-id="206f6-309">Bien que l’exemple précédent indiquait qu’une union discriminée de struct produisait de meilleures performances, il est courant d’avoir des unions discriminées plus importantes lors de la modélisation d’un domaine.</span><span class="sxs-lookup"><span data-stu-id="206f6-309">Although the previous example showed that a struct Discriminated Union yielded better performance, it is common to have larger Discriminated Unions when modeling a domain.</span></span> <span data-ttu-id="206f6-310">Les types de données plus importants, tels que, peuvent ne pas s’exécuter également s’ils sont des structs en fonction des opérations qui leur sont associées, car une copie supplémentaire peut être impliquée.</span><span class="sxs-lookup"><span data-stu-id="206f6-310">Larger data types like that may not perform as well if they are structs depending on the operations on them, since more copying could be involved.</span></span>

### <a name="functional-programming-and-mutation"></a><span data-ttu-id="206f6-311">Programmation et mutation fonctionnelles</span><span class="sxs-lookup"><span data-stu-id="206f6-311">Functional programming and mutation</span></span>

<span data-ttu-id="206f6-312">F#les valeurs sont immuables par défaut, ce qui vous permet d’éviter certaines classes de bogues (en particulier celles qui impliquent la concurrence et le parallélisme).</span><span class="sxs-lookup"><span data-stu-id="206f6-312">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="206f6-313">Toutefois, dans certains cas, pour obtenir une efficacité optimale (voire raisonnable) du temps d’exécution ou des allocations de mémoire, il est préférable d’implémenter une étendue de travail à l’aide d’une mutation sur place de l’État.</span><span class="sxs-lookup"><span data-stu-id="206f6-313">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="206f6-314">Cela est possible dans une base d’abonnement avec F# le mot clé `mutable`.</span><span class="sxs-lookup"><span data-stu-id="206f6-314">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="206f6-315">L’utilisation de `mutable` F# dans peut avoir un sens pour une pureté fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="206f6-315">Use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="206f6-316">Cela est compréhensible, mais la pureté fonctionnelle partout peut être à la même des objectifs de performances.</span><span class="sxs-lookup"><span data-stu-id="206f6-316">This is understandable, but functional purity everywhere can be at odds with performance goals.</span></span> <span data-ttu-id="206f6-317">Un compromis consiste à encapsuler la mutation de manière à ce que les appelants n’aient pas à se soucier de ce qui se passe lorsqu’ils appellent une fonction.</span><span class="sxs-lookup"><span data-stu-id="206f6-317">A compromise is to encapsulate mutation such that callers need not care about what happens when they call a function.</span></span> <span data-ttu-id="206f6-318">Cela vous permet d’écrire une interface fonctionnelle sur une implémentation basée sur une mutation pour le code critique pour les performances.</span><span class="sxs-lookup"><span data-stu-id="206f6-318">This allows you to write a functional interface over a mutation-based implementation for performance-critical code.</span></span>

#### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="206f6-319">Encapsuler le code mutable dans des interfaces immuables</span><span class="sxs-lookup"><span data-stu-id="206f6-319">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="206f6-320">Avec la transparence référentielle comme objectif, il est essentiel d’écrire du code qui n’expose pas le Underbelly mutable des fonctions critiques pour les performances.</span><span class="sxs-lookup"><span data-stu-id="206f6-320">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="206f6-321">Par exemple, le code suivant implémente la fonction `Array.contains` dans la F# bibliothèque principale :</span><span class="sxs-lookup"><span data-stu-id="206f6-321">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

```fsharp
[<CompiledName("Contains")>]
let inline contains value (array:'T[]) =
    checkNonNull "array" array
    let mutable state = false
    let mutable i = 0
    while not state && i < array.Length do
        state <- value = array.[i]
        i <- i + 1
    state
```

<span data-ttu-id="206f6-322">L’appel de cette fonction plusieurs fois ne change pas le tableau sous-jacent, pas plus qu’il ne nécessite que vous mainteniez un État mutable dans l’utilisation de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="206f6-322">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="206f6-323">Elle est transparente de manière référentielle, même si presque chaque ligne de code qu’elle contient utilise la mutation.</span><span class="sxs-lookup"><span data-stu-id="206f6-323">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

#### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="206f6-324">Envisagez d’encapsuler des données mutables dans des classes</span><span class="sxs-lookup"><span data-stu-id="206f6-324">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="206f6-325">L’exemple précédent utilisait une fonction unique pour encapsuler des opérations à l’aide de données mutables.</span><span class="sxs-lookup"><span data-stu-id="206f6-325">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="206f6-326">Cela n’est pas toujours suffisant pour les ensembles de données plus complexes.</span><span class="sxs-lookup"><span data-stu-id="206f6-326">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="206f6-327">Prenez en compte les ensembles de fonctions suivants :</span><span class="sxs-lookup"><span data-stu-id="206f6-327">Consider the following sets of functions:</span></span>

```fsharp
open System.Collections.Generic

let addToClosureTable (key, value) (t: Dictionary<_,_>) =
    if not (t.ContainsKey(key)) then
        t.Add(key, value)
    else
        t.[key] <- value

let closureTableCount (t: Dictionary<_,_>) = t.Count

let closureTableContains (key, value) (t: Dictionary<_, HashSet<_>>) =
    match t.TryGetValue(key) with
    | (true, v) -> v.Equals(value)
    | (false, _) -> false
```

<span data-ttu-id="206f6-328">Ce code est performant, mais il expose la structure de données basée sur la mutation que les appelants sont responsables de la gestion.</span><span class="sxs-lookup"><span data-stu-id="206f6-328">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="206f6-329">Cela peut être encapsulé à l’intérieur d’une classe sans membres sous-jacents qui peuvent changer :</span><span class="sxs-lookup"><span data-stu-id="206f6-329">This can be wrapped inside of a class with no underlying members that can change:</span></span>

```fsharp
open System.Collections.Generic

/// The results of computing the LALR(1) closure of an LR(0) kernel
type Closure1Table() =
    let t = Dictionary<Item0, HashSet<TerminalIndex>>()

    member _.Add(key, value) =
        if not (t.ContainsKey(key)) then
            t.Add(key, value)
        else
            t.[key] <- value

    member _.Count = t.Count

    member _.Contains(key, value) =
        match t.TryGetValue(key) with
        | (true, v) -> v.Equals(value)
        | (false, _) -> false
```

<span data-ttu-id="206f6-330">`Closure1Table` encapsule la structure de données basée sur la mutation sous-jacente, ce qui ne force pas les appelants à gérer la structure de données sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="206f6-330">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="206f6-331">Les classes sont un moyen puissant d’encapsuler des données et des routines basées sur une mutation sans exposer les détails aux appelants.</span><span class="sxs-lookup"><span data-stu-id="206f6-331">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

#### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="206f6-332">Préférer `let mutable` pour référencer des cellules</span><span class="sxs-lookup"><span data-stu-id="206f6-332">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="206f6-333">Les cellules de référence sont un moyen de représenter la référence à une valeur plutôt que la valeur elle-même.</span><span class="sxs-lookup"><span data-stu-id="206f6-333">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="206f6-334">Bien qu’elles puissent être utilisées pour le code critique pour les performances, elles ne sont pas recommandées.</span><span class="sxs-lookup"><span data-stu-id="206f6-334">Although they can be used for performance-critical code, they are not recommended.</span></span> <span data-ttu-id="206f6-335">Prenons l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="206f6-335">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="206f6-336">L’utilisation d’une cellule de référence « pollue » tout le code suivant avec un déréférencement et une nouvelle référence aux données sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="206f6-336">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="206f6-337">Au lieu de cela, envisagez `let mutable`:</span><span class="sxs-lookup"><span data-stu-id="206f6-337">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="206f6-338">Hormis le point de mutation unique au milieu de l’expression lambda, tout autre code qui touche `acc` peut le faire d’une manière qui ne diffère pas de l’utilisation d’une valeur immuable liée à la `let`normale.</span><span class="sxs-lookup"><span data-stu-id="206f6-338">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="206f6-339">Cela facilitera la modification au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="206f6-339">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="206f6-340">Programmation d’objets</span><span class="sxs-lookup"><span data-stu-id="206f6-340">Object programming</span></span>

<span data-ttu-id="206f6-341">F#offre une prise en charge complète des objets et des concepts orientés objet.</span><span class="sxs-lookup"><span data-stu-id="206f6-341">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="206f6-342">Bien que de nombreux concepts OO soient puissants et utiles, ils ne sont pas tous idéaux pour être utilisés.</span><span class="sxs-lookup"><span data-stu-id="206f6-342">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="206f6-343">Les listes suivantes offrent des conseils sur les catégories de fonctionnalités OO à un niveau élevé.</span><span class="sxs-lookup"><span data-stu-id="206f6-343">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="206f6-344">**Envisagez d’utiliser ces fonctionnalités dans de nombreux cas :**</span><span class="sxs-lookup"><span data-stu-id="206f6-344">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="206f6-345">Notation par points (`x.Length`)</span><span class="sxs-lookup"><span data-stu-id="206f6-345">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="206f6-346">Membres d’instance</span><span class="sxs-lookup"><span data-stu-id="206f6-346">Instance members</span></span>
* <span data-ttu-id="206f6-347">Constructeurs implicites</span><span class="sxs-lookup"><span data-stu-id="206f6-347">Implicit constructors</span></span>
* <span data-ttu-id="206f6-348">Membres static</span><span class="sxs-lookup"><span data-stu-id="206f6-348">Static members</span></span>
* <span data-ttu-id="206f6-349">Notation de l’indexeur (`arr.[x]`)</span><span class="sxs-lookup"><span data-stu-id="206f6-349">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="206f6-350">Arguments nommés et facultatifs</span><span class="sxs-lookup"><span data-stu-id="206f6-350">Named and Optional arguments</span></span>
* <span data-ttu-id="206f6-351">Interfaces et implémentations d’interface</span><span class="sxs-lookup"><span data-stu-id="206f6-351">Interfaces and interface implementations</span></span>

<span data-ttu-id="206f6-352">**N’atteignez pas ces fonctionnalités en premier, mais appliquez-les judicieusement lorsqu’ils sont pratiques pour résoudre un problème :**</span><span class="sxs-lookup"><span data-stu-id="206f6-352">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="206f6-353">Surcharge de méthode</span><span class="sxs-lookup"><span data-stu-id="206f6-353">Method overloading</span></span>
* <span data-ttu-id="206f6-354">Données mutables encapsulées</span><span class="sxs-lookup"><span data-stu-id="206f6-354">Encapsulated mutable data</span></span>
* <span data-ttu-id="206f6-355">Opérateurs sur les types</span><span class="sxs-lookup"><span data-stu-id="206f6-355">Operators on types</span></span>
* <span data-ttu-id="206f6-356">Propriétés automatiques</span><span class="sxs-lookup"><span data-stu-id="206f6-356">Auto properties</span></span>
* <span data-ttu-id="206f6-357">Implémentation de `IDisposable` et `IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="206f6-357">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="206f6-358">Extensions de type</span><span class="sxs-lookup"><span data-stu-id="206f6-358">Type extensions</span></span>
* <span data-ttu-id="206f6-359">Events</span><span class="sxs-lookup"><span data-stu-id="206f6-359">Events</span></span>
* <span data-ttu-id="206f6-360">Structures</span><span class="sxs-lookup"><span data-stu-id="206f6-360">Structs</span></span>
* <span data-ttu-id="206f6-361">Délégués</span><span class="sxs-lookup"><span data-stu-id="206f6-361">Delegates</span></span>
* <span data-ttu-id="206f6-362">Énumérations</span><span class="sxs-lookup"><span data-stu-id="206f6-362">Enums</span></span>

<span data-ttu-id="206f6-363">**Évitez généralement ces fonctionnalités, sauf si vous devez les utiliser :**</span><span class="sxs-lookup"><span data-stu-id="206f6-363">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="206f6-364">Hiérarchies de types basées sur l’héritage et héritage d’implémentation</span><span class="sxs-lookup"><span data-stu-id="206f6-364">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="206f6-365">Valeurs NULL et `Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="206f6-365">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="206f6-366">Préférer la composition à l’héritage</span><span class="sxs-lookup"><span data-stu-id="206f6-366">Prefer composition over inheritance</span></span>

<span data-ttu-id="206f6-367">La [composition sur l’héritage](https://en.wikipedia.org/wiki/Composition_over_inheritance) est un idiome à long terme F# auquel un bon code peut adhérer.</span><span class="sxs-lookup"><span data-stu-id="206f6-367">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="206f6-368">Le principe fondamental est que vous ne devez pas exposer une classe de base et forcer les appelants à hériter de cette classe de base pour obtenir des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="206f6-368">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="206f6-369">Utiliser des expressions d’objet pour implémenter des interfaces si vous n’avez pas besoin d’une classe</span><span class="sxs-lookup"><span data-stu-id="206f6-369">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="206f6-370">Les [expressions d’objet](../language-reference/object-expressions.md) vous permettent d’implémenter des interfaces à la volée, en liant l’interface implémentée à une valeur sans avoir à le faire à l’intérieur d’une classe.</span><span class="sxs-lookup"><span data-stu-id="206f6-370">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="206f6-371">Cela est pratique, surtout si vous avez _uniquement_ besoin d’implémenter l’interface et que vous n’avez pas besoin d’une classe complète.</span><span class="sxs-lookup"><span data-stu-id="206f6-371">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="206f6-372">Par exemple, voici le code qui est exécuté dans [Ionide](http://ionide.io/) pour fournir une action de correction de code si vous avez ajouté un symbole pour lequel vous n’avez pas d’instruction `open` :</span><span class="sxs-lookup"><span data-stu-id="206f6-372">For example, here is the code that is run in [Ionide](http://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

```fsharp
    let private createProvider () =
        { new CodeActionProvider with
            member this.provideCodeActions(doc, range, context, ct) =
                let diagnostics = context.diagnostics
                let diagnostic = diagnostics |> Seq.tryFind (fun d -> d.message.Contains "Unused open statement")
                let res =
                    match diagnostic with
                    | None -> [||]
                    | Some d ->
                        let line = doc.lineAt d.range.start.line
                        let cmd = createEmpty<Command>
                        cmd.title <- "Remove unused open"
                        cmd.command <- "fsharp.unusedOpenFix"
                        cmd.arguments <- Some ([| doc |> unbox; line.range |> unbox; |] |> ResizeArray)
                        [|cmd |]
                res
                |> ResizeArray
                |> U2.Case1
        }
```

<span data-ttu-id="206f6-373">Étant donné qu’il n’est pas nécessaire d’utiliser une classe lors de l’interaction avec l’API Visual Studio Code, les expressions d’objet constituent un outil idéal pour cela.</span><span class="sxs-lookup"><span data-stu-id="206f6-373">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="206f6-374">Elles sont également utiles pour les tests unitaires, lorsque vous souhaitez insérer une interface avec des routines de test de manière ad hoc.</span><span class="sxs-lookup"><span data-stu-id="206f6-374">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="consider-type-abbreviations-to-shorten-signatures"></a><span data-ttu-id="206f6-375">Considérer les abréviations de type pour raccourcir les signatures</span><span class="sxs-lookup"><span data-stu-id="206f6-375">Consider Type Abbreviations to shorten signatures</span></span>

<span data-ttu-id="206f6-376">Les [abréviations de type](../language-reference/type-abbreviations.md) sont un moyen pratique d’assigner une étiquette à un autre type, tel qu’une signature de fonction ou un type plus complexe.</span><span class="sxs-lookup"><span data-stu-id="206f6-376">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="206f6-377">Par exemple, l’alias suivant affecte une étiquette à ce qui est nécessaire pour définir un calcul avec [CNTK](https://docs.microsoft.com/cognitive-toolkit/), une bibliothèque d’apprentissage approfondi :</span><span class="sxs-lookup"><span data-stu-id="206f6-377">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://docs.microsoft.com/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="206f6-378">Le nom de `Computation` est un moyen pratique de désigner une fonction qui correspond à la signature qu’elle utilise comme alias.</span><span class="sxs-lookup"><span data-stu-id="206f6-378">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="206f6-379">L’utilisation d’abréviations de type comme celle-ci est pratique et permet d’obtenir un code plus concis.</span><span class="sxs-lookup"><span data-stu-id="206f6-379">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="206f6-380">Évitez d’utiliser des abréviations de type pour représenter votre domaine</span><span class="sxs-lookup"><span data-stu-id="206f6-380">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="206f6-381">Bien que les abréviations de type soient pratiques pour donner un nom aux signatures de fonction, elles peuvent prêter à confusion lors de l’abréviation d’autres types.</span><span class="sxs-lookup"><span data-stu-id="206f6-381">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="206f6-382">Tenez compte de cette abréviation :</span><span class="sxs-lookup"><span data-stu-id="206f6-382">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="206f6-383">Cela peut prêter à confusion de plusieurs façons :</span><span class="sxs-lookup"><span data-stu-id="206f6-383">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="206f6-384">`BufferSize` n’est pas une abstraction ; Il s’agit simplement d’un autre nom pour un entier.</span><span class="sxs-lookup"><span data-stu-id="206f6-384">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="206f6-385">Si `BufferSize` est exposée dans une API publique, elle peut facilement être interprétée de manière erronée pour signifier plus qu' `int`.</span><span class="sxs-lookup"><span data-stu-id="206f6-385">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="206f6-386">En règle générale, les types de domaine ont plusieurs attributs et ne sont pas des types primitifs comme `int`.</span><span class="sxs-lookup"><span data-stu-id="206f6-386">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="206f6-387">Cette abréviation ne respecte pas cette hypothèse.</span><span class="sxs-lookup"><span data-stu-id="206f6-387">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="206f6-388">La casse de `BufferSize` (casse Pascal) implique que ce type contient plus de données.</span><span class="sxs-lookup"><span data-stu-id="206f6-388">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="206f6-389">Cet alias n’offre pas de clarté accrue par rapport à la fourniture d’un argument nommé à une fonction.</span><span class="sxs-lookup"><span data-stu-id="206f6-389">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="206f6-390">L’abréviation ne se manifeste pas dans le langage intermédiaire compilé. Il s’agit simplement d’un entier et cet alias est une construction au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="206f6-390">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

<span data-ttu-id="206f6-391">En résumé, le piège avec les abréviations de type est qu’il ne s’agit **pas** d’abstractions sur les types qu’ils abrégént.</span><span class="sxs-lookup"><span data-stu-id="206f6-391">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="206f6-392">Dans l’exemple précédent, `BufferSize` n’est qu’un `int` en coulisses, sans données supplémentaires, ni aucun avantage du système de type en dehors de ce que `int` déjà.</span><span class="sxs-lookup"><span data-stu-id="206f6-392">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>

<span data-ttu-id="206f6-393">Une autre approche de l’utilisation d’abréviations de type pour représenter un domaine consiste à utiliser des unions discriminées à cas unique.</span><span class="sxs-lookup"><span data-stu-id="206f6-393">An alternative approach to using type abbreviations to represent a domain is to use single-case discriminated unions.</span></span> <span data-ttu-id="206f6-394">L’exemple précédent peut être modélisé comme suit :</span><span class="sxs-lookup"><span data-stu-id="206f6-394">The previous sample can be modeled as follows:</span></span>

```fsharp
type BufferSize = BufferSize of int
```

<span data-ttu-id="206f6-395">Si vous écrivez du code qui fonctionne en termes de `BufferSize` et de sa valeur sous-jacente, vous devez construire un entier au lieu de passer un entier arbitraire :</span><span class="sxs-lookup"><span data-stu-id="206f6-395">If you write code that operates in terms of `BufferSize` and its underlying value, you need to construct one rather than pass in any arbitrary integer:</span></span>

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

<span data-ttu-id="206f6-396">Cela réduit la probabilité de passer par erreur un entier arbitraire dans la fonction `send`, car l’appelant doit construire un type `BufferSize` pour encapsuler une valeur avant d’appeler la fonction.</span><span class="sxs-lookup"><span data-stu-id="206f6-396">This reduces the likelihood of mistakenly passing an arbitrary integer into the `send` function, because the caller must construct a `BufferSize` type to wrap a value before calling the function.</span></span>
