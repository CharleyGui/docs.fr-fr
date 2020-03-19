---
title: Conventions de codage F#
description: Apprenez les lignes directrices générales et les idiomes lors de la rédaction du code F.
ms.date: 01/15/2020
ms.openlocfilehash: 7266211e501bdb52564220781e2347d1aceaf296
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400308"
---
# <a name="f-coding-conventions"></a><span data-ttu-id="dfc18-103">Conventions de codage F#</span><span class="sxs-lookup"><span data-stu-id="dfc18-103">F# coding conventions</span></span>

<span data-ttu-id="dfc18-104">Les conventions suivantes sont formulées à partir de l’expérience de travail avec de grandes bases de code F.</span><span class="sxs-lookup"><span data-stu-id="dfc18-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="dfc18-105">Les [cinq principes d’un bon code F sont](index.md#five-principles-of-good-f-code) à la base de chaque recommandation.</span><span class="sxs-lookup"><span data-stu-id="dfc18-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="dfc18-106">Ils sont liés aux lignes directrices de [conception des composants F,](component-design-guidelines.md)mais s’appliquent à tout code F, et pas seulement aux composants tels que les bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="dfc18-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="dfc18-107">Code d’organisation</span><span class="sxs-lookup"><span data-stu-id="dfc18-107">Organizing code</span></span>

<span data-ttu-id="dfc18-108">FMD dispose de deux façons principales d’organiser le code : les modules et les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="dfc18-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="dfc18-109">Ceux-ci sont similaires, mais ont les différences suivantes:</span><span class="sxs-lookup"><span data-stu-id="dfc18-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="dfc18-110">Les espaces de noms sont compilés sous forme d’espaces nominaux .NET.</span><span class="sxs-lookup"><span data-stu-id="dfc18-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="dfc18-111">Les modules sont compilés sous forme de classes statiques.</span><span class="sxs-lookup"><span data-stu-id="dfc18-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="dfc18-112">Les espaces de noms sont toujours de haut niveau.</span><span class="sxs-lookup"><span data-stu-id="dfc18-112">Namespaces are always top level.</span></span> <span data-ttu-id="dfc18-113">Les modules peuvent être de haut niveau et imbriqués dans d’autres modules.</span><span class="sxs-lookup"><span data-stu-id="dfc18-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="dfc18-114">Les espaces de noms peuvent s’étendre sur plusieurs fichiers.</span><span class="sxs-lookup"><span data-stu-id="dfc18-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="dfc18-115">Les modules ne peuvent pas.</span><span class="sxs-lookup"><span data-stu-id="dfc18-115">Modules cannot.</span></span>
* <span data-ttu-id="dfc18-116">Modules peuvent être `[<RequireQualifiedAccess>]` décorés avec et `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="dfc18-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="dfc18-117">Les lignes directrices suivantes vous aideront à les utiliser pour organiser votre code.</span><span class="sxs-lookup"><span data-stu-id="dfc18-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="dfc18-118">Préférez les espaces de nom au plus haut niveau</span><span class="sxs-lookup"><span data-stu-id="dfc18-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="dfc18-119">Pour tout code consommable publiquement, les espaces nominatifs sont préférentiels pour les modules au plus haut niveau.</span><span class="sxs-lookup"><span data-stu-id="dfc18-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="dfc18-120">Parce qu’ils sont compilés comme des espaces de nom .NET, ils sont consommables à partir de C ' sans aucun problème.</span><span class="sxs-lookup"><span data-stu-id="dfc18-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="dfc18-121">L’utilisation d’un module de haut niveau peut ne pas apparaître différente lorsqu’elle est `MyClass` appelée `MyCode` uniquement à partir de F, mais pour les consommateurs de C, les appelants peuvent être surpris d’avoir à se qualifier avec le module.</span><span class="sxs-lookup"><span data-stu-id="dfc18-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="dfc18-122">Appliquer soigneusement`[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="dfc18-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="dfc18-123">La `[<AutoOpen>]` construction peut polluer la portée de ce qui est disponible pour les appelants, et la réponse à l’endroit d’où quelque chose vient est «magique».</span><span class="sxs-lookup"><span data-stu-id="dfc18-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="dfc18-124">Ce n’est pas une bonne chose.</span><span class="sxs-lookup"><span data-stu-id="dfc18-124">This is not a good thing.</span></span> <span data-ttu-id="dfc18-125">Une exception à cette règle est la bibliothèque de base de F 'elle-même (bien que ce fait soit également un peu controversé).</span><span class="sxs-lookup"><span data-stu-id="dfc18-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="dfc18-126">Cependant, il est pratique si vous avez la fonctionnalité d’aide pour une API publique que vous souhaitez organiser séparément de cette API publique.</span><span class="sxs-lookup"><span data-stu-id="dfc18-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

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

<span data-ttu-id="dfc18-127">Cela vous permet de séparer proprement les détails de mise en œuvre de l’API publique d’une fonction sans avoir à qualifier pleinement une aide chaque fois que vous l’appelez.</span><span class="sxs-lookup"><span data-stu-id="dfc18-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="dfc18-128">En outre, exposer les méthodes d’extension et les constructeurs `[<AutoOpen>]`d’expression au niveau de l’espace de nom peut être soigneusement exprimé avec .</span><span class="sxs-lookup"><span data-stu-id="dfc18-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="dfc18-129">Utiliser `[<RequireQualifiedAccess>]` chaque fois que les noms peuvent entrer en conflit ou vous sentez qu’il aide à la lisibilité</span><span class="sxs-lookup"><span data-stu-id="dfc18-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="dfc18-130">L’ajout de l’attribut `[<RequireQualifiedAccess>]` à un module indique que le module peut ne pas être ouvert et que les références aux éléments du module nécessitent un accès explicite et qualifié.</span><span class="sxs-lookup"><span data-stu-id="dfc18-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="dfc18-131">Par exemple, `Microsoft.FSharp.Collections.List` le module a cet attribut.</span><span class="sxs-lookup"><span data-stu-id="dfc18-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="dfc18-132">Ceci est utile lorsque les fonctions et les valeurs du module ont des noms susceptibles d’entrer en conflit avec les noms d’autres modules.</span><span class="sxs-lookup"><span data-stu-id="dfc18-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="dfc18-133">Exiger un accès qualifié peut grandement accroître la maintenance à long terme et l’évocabilité d’une bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="dfc18-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="dfc18-134">Trier `open` les déclarations topologiquement</span><span class="sxs-lookup"><span data-stu-id="dfc18-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="dfc18-135">Dans l’ordre des déclarations, l’ordre des déclarations est important, y compris avec `open` les déclarations.</span><span class="sxs-lookup"><span data-stu-id="dfc18-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="dfc18-136">Cela est différent de C, `using` `using static` où l’effet de et est indépendant de la commande de ces déclarations dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="dfc18-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="dfc18-137">Dans le F, les éléments ouverts dans une portée peuvent faire l’ombre à d’autres personnes déjà présentes.</span><span class="sxs-lookup"><span data-stu-id="dfc18-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="dfc18-138">Cela signifie que `open` la réorganisation des déclarations pourrait modifier le sens du code.</span><span class="sxs-lookup"><span data-stu-id="dfc18-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="dfc18-139">En conséquence, tout tri arbitraire `open` de toutes les déclarations (par exemple, alphanumériquement) n’est pas recommandé, de peur que vous ne générez un comportement différent que vous pourriez vous attendre.</span><span class="sxs-lookup"><span data-stu-id="dfc18-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="dfc18-140">Au lieu de cela, nous vous recommandons de les trier [topologiquement](https://en.wikipedia.org/wiki/Topological_sorting); c’est-à-dire, commander vos `open` instructions dans l’ordre dans lequel les _couches_ de votre système sont définies.</span><span class="sxs-lookup"><span data-stu-id="dfc18-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="dfc18-141">Faire le tri alphanumérique dans différentes couches topologiques peut également être considéré.</span><span class="sxs-lookup"><span data-stu-id="dfc18-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="dfc18-142">À titre d’exemple, voici le tri topologique pour le fichier API public du service de compilateur F :</span><span class="sxs-lookup"><span data-stu-id="dfc18-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

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

<span data-ttu-id="dfc18-143">Notez qu’une rupture de ligne sépare les couches topologiques, chaque couche étant triée alphanumériquement par la suite.</span><span class="sxs-lookup"><span data-stu-id="dfc18-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="dfc18-144">Cela organise proprement le code sans ombrer accidentellement les valeurs.</span><span class="sxs-lookup"><span data-stu-id="dfc18-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="dfc18-145">Utiliser les classes pour contenir les valeurs qui ont des effets secondaires</span><span class="sxs-lookup"><span data-stu-id="dfc18-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="dfc18-146">Il y a plusieurs fois où l’initialisation d’une valeur peut avoir des effets secondaires, comme l’instantanéisation d’un contexte à une base de données ou à une autre ressource à distance.</span><span class="sxs-lookup"><span data-stu-id="dfc18-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="dfc18-147">Il est tentant d’initialiser de telles choses dans un module et de l’utiliser dans les fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="dfc18-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

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

<span data-ttu-id="dfc18-148">C’est souvent une mauvaise idée pour quelques raisons :</span><span class="sxs-lookup"><span data-stu-id="dfc18-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="dfc18-149">Tout d’abord, la configuration `dep1` de `dep2`l’application est poussée dans la base de code avec et .</span><span class="sxs-lookup"><span data-stu-id="dfc18-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="dfc18-150">Ceci est difficile à maintenir dans de plus grandes bases de code.</span><span class="sxs-lookup"><span data-stu-id="dfc18-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="dfc18-151">Deuxièmement, les données parasmineuses statiques ne doivent pas inclure de valeurs qui ne sont pas sans danger si votre composant utilisera lui-même plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="dfc18-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="dfc18-152">Cela est clairement `dep3`violé par .</span><span class="sxs-lookup"><span data-stu-id="dfc18-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="dfc18-153">Enfin, l’initialisation du module se transforme en un constructeur statique pour l’ensemble de l’unité de compilation.</span><span class="sxs-lookup"><span data-stu-id="dfc18-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="dfc18-154">Si une erreur se produit dans l’initialisation de valeur `TypeInitializationException` lisible dans ce module, elle se manifeste comme une qui est ensuite mise en cache pour toute la durée de vie de l’application.</span><span class="sxs-lookup"><span data-stu-id="dfc18-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="dfc18-155">Cela peut être difficile à diagnostiquer.</span><span class="sxs-lookup"><span data-stu-id="dfc18-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="dfc18-156">Il ya généralement une exception interne que vous pouvez essayer de raisonner, mais s’il n’y en a pas, alors il n’y a pas de dire quelle est la cause profonde.</span><span class="sxs-lookup"><span data-stu-id="dfc18-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="dfc18-157">Au lieu de cela, il suffit d’utiliser une classe simple pour tenir des dépendances:</span><span class="sxs-lookup"><span data-stu-id="dfc18-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="dfc18-158">Cela permet ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="dfc18-158">This enables the following:</span></span>

1. <span data-ttu-id="dfc18-159">Pousser tout état dépendant en dehors de l’API lui-même.</span><span class="sxs-lookup"><span data-stu-id="dfc18-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="dfc18-160">La configuration peut maintenant se faire en dehors de l’API.</span><span class="sxs-lookup"><span data-stu-id="dfc18-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="dfc18-161">Les erreurs dans l’initialisation des valeurs `TypeInitializationException`dépendantes ne sont pas susceptibles de se manifester comme un .</span><span class="sxs-lookup"><span data-stu-id="dfc18-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="dfc18-162">L’API est maintenant plus facile à tester.</span><span class="sxs-lookup"><span data-stu-id="dfc18-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="dfc18-163">Gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="dfc18-163">Error management</span></span>

<span data-ttu-id="dfc18-164">La gestion des erreurs dans les grands systèmes est une entreprise complexe et nuancée, et il n’y a pas de balles d’argent pour s’assurer que vos systèmes sont tolérants aux défauts et se comportent bien.</span><span class="sxs-lookup"><span data-stu-id="dfc18-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="dfc18-165">Les lignes directrices suivantes devraient offrir des conseils sur la navigation dans cet espace difficile.</span><span class="sxs-lookup"><span data-stu-id="dfc18-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="dfc18-166">Représentez les cas d’erreur et l’état illégal dans des types intrinsèques à votre domaine</span><span class="sxs-lookup"><span data-stu-id="dfc18-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="dfc18-167">Avec [Discriminated Unions](../language-reference/discriminated-unions.md), Fmd vous donne la possibilité de représenter l’état défectueux du programme dans votre système de type.</span><span class="sxs-lookup"><span data-stu-id="dfc18-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="dfc18-168">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="dfc18-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="dfc18-169">Dans ce cas, il existe trois façons connues que le retrait d’argent d’un compte bancaire peut échouer.</span><span class="sxs-lookup"><span data-stu-id="dfc18-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="dfc18-170">Chaque cas d’erreur est représenté dans le type, et peut donc être traité en toute sécurité tout au long du programme.</span><span class="sxs-lookup"><span data-stu-id="dfc18-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="dfc18-171">En général, si vous pouvez modéliser les différentes façons dont quelque chose peut **échouer** dans votre domaine, alors le code de traitement des erreurs n’est plus traité comme quelque chose que vous devez traiter en plus du flux régulier du programme.</span><span class="sxs-lookup"><span data-stu-id="dfc18-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="dfc18-172">Il s’agit simplement d’une partie du flux de programme normal, et non considéré comme **exceptionnel**.</span><span class="sxs-lookup"><span data-stu-id="dfc18-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="dfc18-173">Il y a deux avantages principaux à ceci :</span><span class="sxs-lookup"><span data-stu-id="dfc18-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="dfc18-174">Il est plus facile à maintenir que votre domaine change au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="dfc18-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="dfc18-175">Les cas d’erreur sont plus faciles à tester.</span><span class="sxs-lookup"><span data-stu-id="dfc18-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="dfc18-176">Utiliser des exceptions lorsque les erreurs ne peuvent pas être représentées avec des types</span><span class="sxs-lookup"><span data-stu-id="dfc18-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="dfc18-177">Toutes les erreurs ne peuvent pas être représentées dans un domaine problématique.</span><span class="sxs-lookup"><span data-stu-id="dfc18-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="dfc18-178">Ces types de défauts sont de nature *exceptionnelle,* d’où la capacité d’augmenter et d’attraper des exceptions dans le F.</span><span class="sxs-lookup"><span data-stu-id="dfc18-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="dfc18-179">Tout d’abord, il est recommandé que vous lisiez les [lignes directrices de conception d’exception](../../standard/design-guidelines/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="dfc18-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="dfc18-180">Celles-ci s’appliquent également à la F.</span><span class="sxs-lookup"><span data-stu-id="dfc18-180">These are also applicable to F#.</span></span>

<span data-ttu-id="dfc18-181">Les principales constructions disponibles en FMD aux fins de l’augmentation des exceptions devraient être prises en considération dans l’ordre de préférence suivant :</span><span class="sxs-lookup"><span data-stu-id="dfc18-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="dfc18-182">Fonction</span><span class="sxs-lookup"><span data-stu-id="dfc18-182">Function</span></span> | <span data-ttu-id="dfc18-183">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dfc18-183">Syntax</span></span> | <span data-ttu-id="dfc18-184">Objectif</span><span class="sxs-lookup"><span data-stu-id="dfc18-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="dfc18-185">Soulève `System.ArgumentNullException` un avec le nom d’argument spécifié.</span><span class="sxs-lookup"><span data-stu-id="dfc18-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="dfc18-186">Soulève `System.ArgumentException` un avec un nom d’argument spécifié et un message.</span><span class="sxs-lookup"><span data-stu-id="dfc18-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="dfc18-187">Soulève `System.InvalidOperationException` un avec le message spécifié.</span><span class="sxs-lookup"><span data-stu-id="dfc18-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="dfc18-188">Mécanisme à usage général pour jeter des exceptions.</span><span class="sxs-lookup"><span data-stu-id="dfc18-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="dfc18-189">Soulève `System.Exception` un avec le message spécifié.</span><span class="sxs-lookup"><span data-stu-id="dfc18-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="dfc18-190">Relance `System.Exception` un message déterminé par la chaîne de format et ses entrées.</span><span class="sxs-lookup"><span data-stu-id="dfc18-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="dfc18-191">`nullArg`Utilisez, `invalidArg` `invalidOp` et comme mécanisme `ArgumentNullException` `ArgumentException` à `InvalidOperationException` jeter, et le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="dfc18-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="dfc18-192">Les `failwith` `failwithf` fonctions et les fonctions doivent `Exception` généralement être évitées parce qu’elles soulèvent le type de base, et non une exception spécifique.</span><span class="sxs-lookup"><span data-stu-id="dfc18-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="dfc18-193">Conformément aux lignes directrices sur la [conception des exceptions,](../../standard/design-guidelines/exceptions.md)vous souhaitez soulever des exceptions plus précises lorsque vous le pouvez.</span><span class="sxs-lookup"><span data-stu-id="dfc18-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="dfc18-194">Utilisation de la syntaxe de manipulation d’exceptions</span><span class="sxs-lookup"><span data-stu-id="dfc18-194">Using exception-handling syntax</span></span>

<span data-ttu-id="dfc18-195">FMD prend en `try...with` charge les modèles d’exception via la syntaxe :</span><span class="sxs-lookup"><span data-stu-id="dfc18-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="dfc18-196">Concilier fonctionnalité à effectuer face à une exception avec l’appariement des motifs peut être un peu difficile si vous souhaitez garder le code propre.</span><span class="sxs-lookup"><span data-stu-id="dfc18-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="dfc18-197">Une telle façon de gérer cela est d’utiliser [des modèles actifs](../language-reference/active-patterns.md) comme un moyen de regrouper les fonctionnalités entourant un cas d’erreur à une exception elle-même.</span><span class="sxs-lookup"><span data-stu-id="dfc18-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="dfc18-198">Par exemple, vous pouvez consommer une API qui, lorsqu’elle fait une exception, contient des informations précieuses dans les métadonnées d’exception.</span><span class="sxs-lookup"><span data-stu-id="dfc18-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="dfc18-199">Déballer une valeur utile dans le corps de l’exception capturée à l’intérieur du modèle actif et le retour de cette valeur peut être utile dans certaines situations.</span><span class="sxs-lookup"><span data-stu-id="dfc18-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="dfc18-200">N’utilisez pas la manipulation d’erreur monadic pour remplacer les exceptions</span><span class="sxs-lookup"><span data-stu-id="dfc18-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="dfc18-201">Les exceptions sont considérées comme quelque peu taboues dans la programmation fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="dfc18-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="dfc18-202">En effet, les exceptions violent la pureté, il est donc sûr de les considérer pas tout à fait fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="dfc18-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="dfc18-203">Cependant, cela ignore la réalité de l’endroit où le code doit s’exécuter, et que des erreurs de temps d’exécution peuvent se produire.</span><span class="sxs-lookup"><span data-stu-id="dfc18-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="dfc18-204">En général, écrire du code sur l’hypothèse que la plupart des choses ne sont ni pures ni totales, pour minimiser les mauvaises surprises.</span><span class="sxs-lookup"><span data-stu-id="dfc18-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="dfc18-205">Il est important de tenir compte des forces/aspects fondamentaux suivants des exceptions en ce qui concerne leur pertinence et leur pertinence dans l’écosystème .NET runtime et cross-language dans son ensemble :</span><span class="sxs-lookup"><span data-stu-id="dfc18-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="dfc18-206">Ils contiennent des informations diagnostiques détaillées, ce qui est très utile lors de la débogage d’un problème.</span><span class="sxs-lookup"><span data-stu-id="dfc18-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="dfc18-207">Ils sont bien compris par le runtime et d’autres langues .NET.</span><span class="sxs-lookup"><span data-stu-id="dfc18-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="dfc18-208">Ils peuvent réduire la plaque chauffante importante par rapport au code qui fait des ravages pour *éviter* les exceptions en mettant en œuvre un sous-ensemble de leur sémantique sur une base ad hoc.</span><span class="sxs-lookup"><span data-stu-id="dfc18-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="dfc18-209">Ce troisième point est essentiel.</span><span class="sxs-lookup"><span data-stu-id="dfc18-209">This third point is critical.</span></span> <span data-ttu-id="dfc18-210">Pour les opérations non complexes non complexes, le défaut d’utiliser des exceptions peut entraîner des relations avec des structures comme celle-ci :</span><span class="sxs-lookup"><span data-stu-id="dfc18-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="dfc18-211">Ce qui peut facilement conduire à un code fragile comme l’appariement des motifs sur les erreurs de « stringly-typed » :</span><span class="sxs-lookup"><span data-stu-id="dfc18-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="dfc18-212">En outre, il peut être tentant d’avaler n’importe quelle exception dans le désir d’une fonction "simple" qui renvoie un type "plus agréable":</span><span class="sxs-lookup"><span data-stu-id="dfc18-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="dfc18-213">Malheureusement, `tryReadAllText` peut jeter de nombreuses exceptions basées sur la myriade de choses qui peuvent se produire sur un système de fichiers, et ce code écarte toute information sur ce qui pourrait réellement aller mal dans votre environnement.</span><span class="sxs-lookup"><span data-stu-id="dfc18-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="dfc18-214">Si vous remplacez ce code par un type de résultat, alors vous revenez à l’analyse de messages d’erreur « tapé » :</span><span class="sxs-lookup"><span data-stu-id="dfc18-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

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

<span data-ttu-id="dfc18-215">Et placer l’objet `Error` d’exception lui-même dans le constructeur vous oblige juste à traiter correctement avec le type d’exception au site d’appel plutôt que dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="dfc18-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="dfc18-216">Cela crée efficacement des exceptions vérifiées, qui sont notoirement non parfumés à traiter comme un appelant d’une API.</span><span class="sxs-lookup"><span data-stu-id="dfc18-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="dfc18-217">Une bonne alternative aux exemples ci-dessus est d’attraper des exceptions *précises* et de retourner une valeur significative dans le contexte de cette exception.</span><span class="sxs-lookup"><span data-stu-id="dfc18-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="dfc18-218">Si vous `tryReadAllText` modifiez la `None` fonction comme suit, a plus de sens:</span><span class="sxs-lookup"><span data-stu-id="dfc18-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="dfc18-219">Au lieu de fonctionner comme un fourre-tout, cette fonction va maintenant gérer correctement le cas quand un fichier n’a pas été trouvé et attribuer ce sens à une déclaration.</span><span class="sxs-lookup"><span data-stu-id="dfc18-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="dfc18-220">Cette valeur de retour peut être cartographe dans ce cas d’erreur, tout en ne rejetant aucune information contextuelle ou en forçant les appelants à traiter une affaire qui peut ne pas être pertinente à ce moment-là dans le code.</span><span class="sxs-lookup"><span data-stu-id="dfc18-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="dfc18-221">Les types `Result<'Success, 'Error>` tels que sont appropriés pour les opérations de base où ils ne sont pas imbriqués, et les types optionnels F sont parfaits pour représenter quand quelque chose pourrait soit retourner *quelque chose* ou *rien*.</span><span class="sxs-lookup"><span data-stu-id="dfc18-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="dfc18-222">Ils ne remplacent toutefois pas les exceptions et ne devraient pas être utilisés pour tenter de remplacer les exceptions.</span><span class="sxs-lookup"><span data-stu-id="dfc18-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="dfc18-223">Ils devraient plutôt être appliqués judicieusement pour aborder des aspects précis de la politique d’exception et de gestion des erreurs de façon ciblée.</span><span class="sxs-lookup"><span data-stu-id="dfc18-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="dfc18-224">Application partielle et programmation sans point</span><span class="sxs-lookup"><span data-stu-id="dfc18-224">Partial application and point-free programming</span></span>

<span data-ttu-id="dfc18-225">FMD prend en charge l’application partielle, et donc, de diverses façons de programmer dans un style sans point.</span><span class="sxs-lookup"><span data-stu-id="dfc18-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="dfc18-226">Cela peut être bénéfique pour la réutilisation du code dans un module ou la mise en œuvre de quelque chose, mais ce n’est pas quelque chose à exposer publiquement.</span><span class="sxs-lookup"><span data-stu-id="dfc18-226">This can be beneficial for code reuse within a module or the implementation of something, but it is not something to expose publicly.</span></span> <span data-ttu-id="dfc18-227">En général, la programmation sans point n’est pas une vertu en soi, et peut ajouter une barrière cognitive importante pour les personnes qui ne sont pas immergés dans le style.</span><span class="sxs-lookup"><span data-stu-id="dfc18-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="dfc18-228">N’utilisez pas l’application partielle et le curry dans les API publiques</span><span class="sxs-lookup"><span data-stu-id="dfc18-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="dfc18-229">À peu près d’exception, l’utilisation d’une application partielle dans les API publiques peut prêter à confusion pour les consommateurs.</span><span class="sxs-lookup"><span data-stu-id="dfc18-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="dfc18-230">Habituellement, `let`les valeurs liées dans le code F sont des **valeurs,** pas **des valeurs de fonction**.</span><span class="sxs-lookup"><span data-stu-id="dfc18-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="dfc18-231">Mélanger les valeurs et les valeurs de fonction peut permettre d’économiser un petit nombre de lignes `>>` de code en échange d’un certain nombre de frais généraux cognitifs, surtout s’ils sont combinés avec des opérateurs tels que pour composer des fonctions.</span><span class="sxs-lookup"><span data-stu-id="dfc18-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="dfc18-232">Tenir compte des implications en ce qui a eu pour la programmation sans point</span><span class="sxs-lookup"><span data-stu-id="dfc18-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="dfc18-233">Les fonctions au curry n’étiquetent pas leurs arguments.</span><span class="sxs-lookup"><span data-stu-id="dfc18-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="dfc18-234">Cela a des implications d’outillage.</span><span class="sxs-lookup"><span data-stu-id="dfc18-234">This has tooling implications.</span></span> <span data-ttu-id="dfc18-235">Considérez les deux fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="dfc18-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="dfc18-236">Les deux sont des `funcWithApplication` fonctions valides, mais est une fonction au curry.</span><span class="sxs-lookup"><span data-stu-id="dfc18-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="dfc18-237">Lorsque vous survolez leurs types dans un éditeur, vous voyez ceci:</span><span class="sxs-lookup"><span data-stu-id="dfc18-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="dfc18-238">Sur le site d’appel, les outils dans l’outillage tels que `string` `int` Visual Studio ne vous donneront pas d’informations significatives sur ce que les types et les types d’entrée représentent réellement.</span><span class="sxs-lookup"><span data-stu-id="dfc18-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="dfc18-239">Si vous rencontrez un `funcWithApplication` code sans point comme celui-ci est publiquement consommable, il est recommandé de faire une extension complète afin que l’outillage peut ramasser sur des noms significatifs pour les arguments.</span><span class="sxs-lookup"><span data-stu-id="dfc18-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="dfc18-240">En outre, débogage de code sans point peut être difficile, voire impossible.</span><span class="sxs-lookup"><span data-stu-id="dfc18-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="dfc18-241">Les outils de débogage s’appuient `let` sur des valeurs liées aux noms (par exemple, les fixations) afin que vous puissiez inspecter les valeurs intermédiaires à mi-parcours de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="dfc18-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="dfc18-242">Lorsque votre code n’a pas de valeurs à inspecter, il n’y a rien à déboiffer.</span><span class="sxs-lookup"><span data-stu-id="dfc18-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="dfc18-243">À l’avenir, des outils de débogage peuvent évoluer pour synthétiser ces valeurs en fonction de chemins précédemment exécutés, mais ce n’est pas une bonne idée de couvrir vos paris sur les fonctionnalités *potentielles* de débogage.</span><span class="sxs-lookup"><span data-stu-id="dfc18-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="dfc18-244">Considérez l’application partielle comme une technique pour réduire la plaque chauffante interne</span><span class="sxs-lookup"><span data-stu-id="dfc18-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="dfc18-245">Contrairement au point précédent, l’application partielle est un outil merveilleux pour réduire la plaque chauffante à l’intérieur d’une application ou les internes plus profonds d’une API.</span><span class="sxs-lookup"><span data-stu-id="dfc18-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="dfc18-246">Il peut être utile pour tester unitaire la mise en œuvre d’API plus compliquées, où la plaque chauffante est souvent une douleur à traiter.</span><span class="sxs-lookup"><span data-stu-id="dfc18-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="dfc18-247">Par exemple, le code suivant montre comment vous pouvez accomplir ce que la plupart des cadres moqueurs vous donnent sans prendre une dépendance externe à un tel cadre et d’avoir à apprendre une API sur mesure connexes.</span><span class="sxs-lookup"><span data-stu-id="dfc18-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="dfc18-248">Par exemple, considérez la topographie de solution suivante :</span><span class="sxs-lookup"><span data-stu-id="dfc18-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="dfc18-249">`ImplementationLogic.fsproj`pourrait exposer le code tel que :</span><span class="sxs-lookup"><span data-stu-id="dfc18-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="dfc18-250">Les `Transactions.doTransaction` tests `ImplementationLogic.Tests.fsproj` unitaires sont faciles :</span><span class="sxs-lookup"><span data-stu-id="dfc18-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fsproj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="dfc18-251">L’application `doTransaction` partielle avec un objet contextuelle vous permet d’appeler la fonction dans tous vos tests unitaires sans avoir besoin de construire un contexte simulé à chaque fois :</span><span class="sxs-lookup"><span data-stu-id="dfc18-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

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

<span data-ttu-id="dfc18-252">Cette technique ne doit pas être universellement appliquée à votre base de code entière, mais c’est un bon moyen de réduire la plaque chauffante pour les internes compliqués et les tests unitaires de ces internes.</span><span class="sxs-lookup"><span data-stu-id="dfc18-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="dfc18-253">Contrôle d’accès</span><span class="sxs-lookup"><span data-stu-id="dfc18-253">Access control</span></span>

<span data-ttu-id="dfc18-254">F a plusieurs options pour [le contrôle d’accès](../language-reference/access-control.md), hérité de ce qui est disponible dans le temps d’exécution .NET.</span><span class="sxs-lookup"><span data-stu-id="dfc18-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="dfc18-255">Ceux-ci ne sont pas seulement utilisables pour les types - vous pouvez les utiliser pour des fonctions, aussi.</span><span class="sxs-lookup"><span data-stu-id="dfc18-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="dfc18-256">Préférez les`public` non-types et les membres jusqu’à ce que vous en ayez besoin pour être consommables publiquement.</span><span class="sxs-lookup"><span data-stu-id="dfc18-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="dfc18-257">Cela minimise également ce que les consommateurs couple à.</span><span class="sxs-lookup"><span data-stu-id="dfc18-257">This also minimizes what consumers couple to.</span></span>
* <span data-ttu-id="dfc18-258">Efforcez-vous de conserver `private`toutes les fonctionnalités d’aide .</span><span class="sxs-lookup"><span data-stu-id="dfc18-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="dfc18-259">Considérez l’utilisation d’un `[<AutoOpen>]` module privé de fonctions d’aide si elles deviennent nombreuses.</span><span class="sxs-lookup"><span data-stu-id="dfc18-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="dfc18-260">Inférence de type et génériques</span><span class="sxs-lookup"><span data-stu-id="dfc18-260">Type inference and generics</span></span>

<span data-ttu-id="dfc18-261">L’inférence de type peut vous éviter de taper beaucoup de plaques chauffantes.</span><span class="sxs-lookup"><span data-stu-id="dfc18-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="dfc18-262">Et la généralisation automatique dans le compilateur de F peut vous aider à écrire plus de code générique sans aucun effort supplémentaire de votre part.</span><span class="sxs-lookup"><span data-stu-id="dfc18-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="dfc18-263">Cependant, ces caractéristiques ne sont pas universellement bonnes.</span><span class="sxs-lookup"><span data-stu-id="dfc18-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="dfc18-264">Envisagez d’étiqueter les noms d’arguments avec des types explicites dans les API publiques et ne vous fiez pas à l’inférence de type pour cela.</span><span class="sxs-lookup"><span data-stu-id="dfc18-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="dfc18-265">La raison en est que **vous** devriez être en contrôle de la forme de votre API, pas le compilateur.</span><span class="sxs-lookup"><span data-stu-id="dfc18-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="dfc18-266">Bien que le compilateur peut faire un excellent travail à déduire les types pour vous, il est possible d’avoir la forme de votre changement API si les internes qu’il s’appuie sur ont changé les types.</span><span class="sxs-lookup"><span data-stu-id="dfc18-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="dfc18-267">C’est peut-être ce que vous voulez, mais il en résultera presque certainement un changement d’API qui brisera que les consommateurs en aval devront alors faire face.</span><span class="sxs-lookup"><span data-stu-id="dfc18-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="dfc18-268">Au lieu de cela, si vous contrôlez explicitement la forme de votre API publique, alors vous pouvez contrôler ces changements de rupture.</span><span class="sxs-lookup"><span data-stu-id="dfc18-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="dfc18-269">En termes de DDD, cela peut être considéré comme une couche anti-corruption.</span><span class="sxs-lookup"><span data-stu-id="dfc18-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="dfc18-270">Envisagez de donner un nom significatif à vos arguments génériques.</span><span class="sxs-lookup"><span data-stu-id="dfc18-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="dfc18-271">Sauf si vous écrivez un code vraiment générique qui n’est pas spécifique à un domaine particulier, un nom significatif peut aider d’autres programmeurs à comprendre le domaine dans lequel ils travaillent.</span><span class="sxs-lookup"><span data-stu-id="dfc18-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="dfc18-272">Par exemple, un `'Document` paramètre type nommé dans le contexte de l’interaction avec une base de données de documents indique plus clairement que les types de documents génériques peuvent être acceptés par la fonction ou le membre avec lequel vous travaillez.</span><span class="sxs-lookup"><span data-stu-id="dfc18-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="dfc18-273">Envisagez de nommer des paramètres de type générique avec PascalCase.</span><span class="sxs-lookup"><span data-stu-id="dfc18-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="dfc18-274">C’est la façon générale de faire les choses en .NET, il est donc recommandé que vous utilisez PascalCase plutôt que snake_case ou camelCase.</span><span class="sxs-lookup"><span data-stu-id="dfc18-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="dfc18-275">Enfin, la généralisation automatique n’est pas toujours une aubaine pour les personnes qui sont nouvelles à F ou une grande base de code.</span><span class="sxs-lookup"><span data-stu-id="dfc18-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="dfc18-276">Il y a des frais généraux cognitifs dans l’utilisation des composants qui sont génériques.</span><span class="sxs-lookup"><span data-stu-id="dfc18-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="dfc18-277">En outre, si les fonctions automatiquement généralisées ne sont pas utilisées avec différents types d’entrées (et encore moins si elles sont destinées à être utilisées en tant que telles), alors il n’y a aucun avantage réel pour eux d’être générique à ce moment-là.</span><span class="sxs-lookup"><span data-stu-id="dfc18-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="dfc18-278">Considérez toujours si le code que vous écrivez bénéficiera réellement d’être générique.</span><span class="sxs-lookup"><span data-stu-id="dfc18-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="dfc18-279">Performances</span><span class="sxs-lookup"><span data-stu-id="dfc18-279">Performance</span></span>

### <a name="prefer-structs-for-small-data-types"></a><span data-ttu-id="dfc18-280">Préférez les structs pour les petits types de données</span><span class="sxs-lookup"><span data-stu-id="dfc18-280">Prefer structs for small data types</span></span>

<span data-ttu-id="dfc18-281">L’utilisation de structs (également appelées types de valeurs) peut souvent entraîner des performances plus élevées pour certains codes, car il évite généralement d’attribuer des objets.</span><span class="sxs-lookup"><span data-stu-id="dfc18-281">Using structs (also called Value Types) can often result in higher performance for some code because it typically avoids allocating objects.</span></span> <span data-ttu-id="dfc18-282">Cependant, les structs ne sont pas toujours un bouton « aller plus vite » : si la taille des données dans une struct dépasse 16 octets, la copie des données peut souvent entraîner plus de temps de processeur que d’utiliser un type de référence.</span><span class="sxs-lookup"><span data-stu-id="dfc18-282">However, structs are not always a "go faster" button: if the size of the data in a struct exceeds 16 bytes, copying the data can often result in more CPU time spend than using a reference type.</span></span>

<span data-ttu-id="dfc18-283">Pour déterminer si vous devez utiliser une struct, considérez les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="dfc18-283">To determine if you should use a struct, consider the following conditions:</span></span>

- <span data-ttu-id="dfc18-284">Si la taille de vos données est de 16 octets ou plus petit.</span><span class="sxs-lookup"><span data-stu-id="dfc18-284">If the size of your data is 16 bytes or smaller.</span></span>
- <span data-ttu-id="dfc18-285">Si vous êtes susceptible d’avoir beaucoup de ces types de données résident dans la mémoire dans un programme en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="dfc18-285">If you're likely to have many of these data types resident in memory in a running program.</span></span>

<span data-ttu-id="dfc18-286">Si la première condition s’applique, vous devriez généralement utiliser une struct.</span><span class="sxs-lookup"><span data-stu-id="dfc18-286">If the first condition applies, you should generally use a struct.</span></span> <span data-ttu-id="dfc18-287">Si les deux s’appliquent, vous devriez presque toujours utiliser une struct.</span><span class="sxs-lookup"><span data-stu-id="dfc18-287">If both apply, you should almost always use a struct.</span></span> <span data-ttu-id="dfc18-288">Il peut y avoir certains cas où les conditions précédentes s’appliquent, mais l’utilisation d’une struct n’est pas meilleure ou pire que l’utilisation d’un type de référence, mais ils sont susceptibles d’être rares.</span><span class="sxs-lookup"><span data-stu-id="dfc18-288">There may be some cases where the previous conditions apply, but using a struct is no better or worse than using a reference type, but they are likely to be rare.</span></span> <span data-ttu-id="dfc18-289">Il est important de toujours mesurer lors de faire des changements comme celui-ci, cependant, et ne pas fonctionner sur l’hypothèse ou l’intuition.</span><span class="sxs-lookup"><span data-stu-id="dfc18-289">It's important to always measure when making changes like this, though, and not operate on assumption or intuition.</span></span>

#### <a name="prefer-struct-tuples-when-grouping-small-value-types"></a><span data-ttu-id="dfc18-290">Préférez les tuples struct lors du regroupement de petits types de valeur</span><span class="sxs-lookup"><span data-stu-id="dfc18-290">Prefer struct tuples when grouping small value types</span></span>

<span data-ttu-id="dfc18-291">Considérez les deux fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="dfc18-291">Consider the following two functions:</span></span>

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

<span data-ttu-id="dfc18-292">Lorsque vous comparez ces fonctions avec un outil de benchmarking statistique `runWithStructTuple` comme [BenchmarkDotNet](https://benchmarkdotnet.org/), vous constaterez que la fonction qui utilise des tuples struct est 40% plus rapide et n’alloue aucune mémoire.</span><span class="sxs-lookup"><span data-stu-id="dfc18-292">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that the `runWithStructTuple` function that uses struct tuples runs 40% faster and allocates no memory.</span></span>

<span data-ttu-id="dfc18-293">Cependant, ces résultats ne seront pas toujours le cas dans votre propre code.</span><span class="sxs-lookup"><span data-stu-id="dfc18-293">However, these results won't always be the case in your own code.</span></span> <span data-ttu-id="dfc18-294">Si vous marquez `inline`une fonction comme , le code qui utilise des tuples de référence peut obtenir quelques optimisations supplémentaires, ou le code qui allouerait pourrait tout simplement être optimisé.</span><span class="sxs-lookup"><span data-stu-id="dfc18-294">If you mark a function as `inline`, code that uses reference tuples may get some additional optimizations, or code that would allocate could simply be optimized away.</span></span> <span data-ttu-id="dfc18-295">Vous devez toujours mesurer les résultats chaque fois que les performances sont concernées, et ne jamais fonctionner sur la base de l’hypothèse ou l’intuition.</span><span class="sxs-lookup"><span data-stu-id="dfc18-295">You should always measure results whenever performance is concerned, and never operate based on assumption or intuition.</span></span>

#### <a name="prefer-struct-records-when-the-data-type-is-small"></a><span data-ttu-id="dfc18-296">Préférez les enregistrements de struct lorsque le type de données est faible</span><span class="sxs-lookup"><span data-stu-id="dfc18-296">Prefer struct records when the data type is small</span></span>

<span data-ttu-id="dfc18-297">La règle de base décrite précédemment détient également pour [les types de disques F .](../language-reference/records.md)</span><span class="sxs-lookup"><span data-stu-id="dfc18-297">The rule of thumb described earlier also holds for [F# record types](../language-reference/records.md).</span></span> <span data-ttu-id="dfc18-298">Considérez les types et fonctions de données suivants qui les traitent :</span><span class="sxs-lookup"><span data-stu-id="dfc18-298">Consider the following data types and functions that process them:</span></span>

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

<span data-ttu-id="dfc18-299">Ceci est similaire au code de tuple précédent, mais cette fois l’exemple utilise des enregistrements et une fonction intérieure inlinisée.</span><span class="sxs-lookup"><span data-stu-id="dfc18-299">This is similar to the previous tuple code, but this time the example uses records and an inlined inner function.</span></span>

<span data-ttu-id="dfc18-300">Lorsque vous comparez ces fonctions avec un outil de benchmarking `processStructPoint` statistique comme [BenchmarkDotNet](https://benchmarkdotnet.org/), vous constaterez que fonctionne près de 60% plus rapidement et n’alloue rien sur le tas géré.</span><span class="sxs-lookup"><span data-stu-id="dfc18-300">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that `processStructPoint` runs nearly 60% faster and allocates nothing on the managed heap.</span></span>

#### <a name="prefer-struct-discriminated-unions-when-the-data-type-is-small"></a><span data-ttu-id="dfc18-301">Préférez les syndicats discriminés structurés lorsque le type de données est faible</span><span class="sxs-lookup"><span data-stu-id="dfc18-301">Prefer struct discriminated unions when the data type is small</span></span>

<span data-ttu-id="dfc18-302">Les observations précédentes sur la performance avec des tuples et des dossiers structurants sont également valables pour [les syndicats discriminés](../language-reference/discriminated-unions.md).</span><span class="sxs-lookup"><span data-stu-id="dfc18-302">The previous observations about performance with struct tuples and records also holds for [F# Discriminated Unions](../language-reference/discriminated-unions.md).</span></span> <span data-ttu-id="dfc18-303">Examinons le code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="dfc18-303">Consider the following code:</span></span>

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

<span data-ttu-id="dfc18-304">Il est courant de définir des unions discriminées à un seul cas comme celle-ci pour la modélisation de domaine.</span><span class="sxs-lookup"><span data-stu-id="dfc18-304">It's common to define single-case Discriminated Unions like this for domain modeling.</span></span> <span data-ttu-id="dfc18-305">Lorsque vous comparez ces fonctions avec un outil de benchmarking `structReverseName` statistique comme [BenchmarkDotNet](https://benchmarkdotnet.org/), vous trouverez que fonctionne environ 25% plus vite que `reverseName` pour les petites chaînes.</span><span class="sxs-lookup"><span data-stu-id="dfc18-305">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that `structReverseName` runs about 25% faster than `reverseName` for small strings.</span></span> <span data-ttu-id="dfc18-306">Pour les grosses cordes, les deux exécutent à peu près la même chose.</span><span class="sxs-lookup"><span data-stu-id="dfc18-306">For large strings, both perform about the same.</span></span> <span data-ttu-id="dfc18-307">Donc, dans ce cas, il est toujours préférable d’utiliser une struct.</span><span class="sxs-lookup"><span data-stu-id="dfc18-307">So, in this case, it's always preferable to use a struct.</span></span> <span data-ttu-id="dfc18-308">Comme mentionné précédemment, mesurez toujours et ne fonctionnent pas sur des hypothèses ou des intuitions.</span><span class="sxs-lookup"><span data-stu-id="dfc18-308">As previously mentioned, always measure and do not operate on assumptions or intuition.</span></span>

<span data-ttu-id="dfc18-309">Bien que l’exemple précédent ait montré qu’une union discriminée structed a donné de meilleurs résultats, il est courant d’avoir de plus grands unions discriminées lors de la modélisation d’un domaine.</span><span class="sxs-lookup"><span data-stu-id="dfc18-309">Although the previous example showed that a struct Discriminated Union yielded better performance, it is common to have larger Discriminated Unions when modeling a domain.</span></span> <span data-ttu-id="dfc18-310">Les types de données plus grands comme celui-ci peuvent ne pas fonctionner aussi bien s’ils sont structs en fonction des opérations sur eux, puisque plus de copie pourrait être impliquée.</span><span class="sxs-lookup"><span data-stu-id="dfc18-310">Larger data types like that may not perform as well if they are structs depending on the operations on them, since more copying could be involved.</span></span>

### <a name="functional-programming-and-mutation"></a><span data-ttu-id="dfc18-311">Programmation fonctionnelle et mutation</span><span class="sxs-lookup"><span data-stu-id="dfc18-311">Functional programming and mutation</span></span>

<span data-ttu-id="dfc18-312">Les valeurs F sont immuables par défaut, ce qui vous permet d’éviter certaines catégories de bogues (en particulier ceux impliquant la concurrence et le parallélisme).</span><span class="sxs-lookup"><span data-stu-id="dfc18-312">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="dfc18-313">Cependant, dans certains cas, afin d’atteindre une efficacité optimale (voire raisonnable) du temps d’exécution ou des allocations de mémoire, une durée de travail peut être mieux mise en œuvre en utilisant la mutation sur place de l’état.</span><span class="sxs-lookup"><span data-stu-id="dfc18-313">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="dfc18-314">Ceci est possible dans une base d’opt-in avec F avec le `mutable` mot clé.</span><span class="sxs-lookup"><span data-stu-id="dfc18-314">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="dfc18-315">L’utilisation de l’inF `mutable` peut se sentir en contradiction avec la pureté fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="dfc18-315">Use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="dfc18-316">C’est compréhensible, mais la pureté fonctionnelle partout peut être en contradiction avec les objectifs de performance.</span><span class="sxs-lookup"><span data-stu-id="dfc18-316">This is understandable, but functional purity everywhere can be at odds with performance goals.</span></span> <span data-ttu-id="dfc18-317">Un compromis est d’encapsuler la mutation de telle sorte que les appelants n’ont pas besoin de se soucier de ce qui se passe quand ils appellent une fonction.</span><span class="sxs-lookup"><span data-stu-id="dfc18-317">A compromise is to encapsulate mutation such that callers need not care about what happens when they call a function.</span></span> <span data-ttu-id="dfc18-318">Cela vous permet d’écrire une interface fonctionnelle sur une implémentation basée sur la mutation pour le code critique des performances.</span><span class="sxs-lookup"><span data-stu-id="dfc18-318">This allows you to write a functional interface over a mutation-based implementation for performance-critical code.</span></span>

#### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="dfc18-319">Enveloppez le code mutable dans des interfaces immuables</span><span class="sxs-lookup"><span data-stu-id="dfc18-319">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="dfc18-320">Avec la transparence référentielle comme objectif, il est essentiel d’écrire du code qui n’expose pas le ventre mutable des fonctions critiques de performance.</span><span class="sxs-lookup"><span data-stu-id="dfc18-320">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="dfc18-321">Par exemple, le code `Array.contains` suivant implémente la fonction dans la bibliothèque de base de FMD :</span><span class="sxs-lookup"><span data-stu-id="dfc18-321">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

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

<span data-ttu-id="dfc18-322">Appeler cette fonction plusieurs fois ne change pas le tableau sous-jacent, ni ne vous oblige à maintenir un état mutable en le consommant.</span><span class="sxs-lookup"><span data-stu-id="dfc18-322">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="dfc18-323">Il est référentiellement transparent, même si presque toutes les lignes de code en son sein utilisent la mutation.</span><span class="sxs-lookup"><span data-stu-id="dfc18-323">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

#### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="dfc18-324">Envisagez d’encapsulant des données mutables dans les classes</span><span class="sxs-lookup"><span data-stu-id="dfc18-324">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="dfc18-325">L’exemple précédent utilisait une seule fonction pour encapsuler les opérations à l’aide de données mutables.</span><span class="sxs-lookup"><span data-stu-id="dfc18-325">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="dfc18-326">Ce n’est pas toujours suffisant pour des ensembles de données plus complexes.</span><span class="sxs-lookup"><span data-stu-id="dfc18-326">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="dfc18-327">Considérez les ensembles de fonctions suivants :</span><span class="sxs-lookup"><span data-stu-id="dfc18-327">Consider the following sets of functions:</span></span>

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

<span data-ttu-id="dfc18-328">Ce code est performant, mais il expose la structure de données basée sur la mutation que les appelants sont responsables du maintien.</span><span class="sxs-lookup"><span data-stu-id="dfc18-328">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="dfc18-329">Ceci peut être enveloppé à l’intérieur d’une classe sans membres sous-jacents qui peuvent changer :</span><span class="sxs-lookup"><span data-stu-id="dfc18-329">This can be wrapped inside of a class with no underlying members that can change:</span></span>

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

<span data-ttu-id="dfc18-330">`Closure1Table`encapsule la structure de données sous-jacente basée sur la mutation, ce qui ne force pas les appelants à maintenir la structure de données sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="dfc18-330">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="dfc18-331">Les cours sont un moyen puissant d’encapsuler les données et les routines qui sont basées sur les mutations sans exposer les détails aux appelants.</span><span class="sxs-lookup"><span data-stu-id="dfc18-331">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

#### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="dfc18-332">Préférez `let mutable` les cellules de référence</span><span class="sxs-lookup"><span data-stu-id="dfc18-332">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="dfc18-333">Les cellules de référence sont un moyen de représenter la référence à une valeur plutôt qu’à la valeur elle-même.</span><span class="sxs-lookup"><span data-stu-id="dfc18-333">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="dfc18-334">Bien qu’ils puissent être utilisés pour le code critique des performances, ils ne sont pas recommandés.</span><span class="sxs-lookup"><span data-stu-id="dfc18-334">Although they can be used for performance-critical code, they are not recommended.</span></span> <span data-ttu-id="dfc18-335">Prenons l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="dfc18-335">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="dfc18-336">L’utilisation d’une cellule de référence « pollue » maintenant tout code subséquent en ayant à déreférencer et à recouper les données sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="dfc18-336">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="dfc18-337">Au lieu `let mutable`de cela, considérez :</span><span class="sxs-lookup"><span data-stu-id="dfc18-337">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="dfc18-338">Mis à part le seul point de mutation au milieu de `acc` l’expression lambda, tout autre code qui `let`touche peut le faire d’une manière qui n’est pas différente de l’utilisation d’une valeur immuable normale liée.</span><span class="sxs-lookup"><span data-stu-id="dfc18-338">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="dfc18-339">Cela facilitera le changement avec le temps.</span><span class="sxs-lookup"><span data-stu-id="dfc18-339">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="dfc18-340">Programmation d’objets</span><span class="sxs-lookup"><span data-stu-id="dfc18-340">Object programming</span></span>

<span data-ttu-id="dfc18-341">FMD bénéficie d’un support complet pour les objets et les concepts orientés objet (OO).</span><span class="sxs-lookup"><span data-stu-id="dfc18-341">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="dfc18-342">Bien que de nombreux concepts OO sont puissants et utiles, pas tous d’entre eux sont idéaux à utiliser.</span><span class="sxs-lookup"><span data-stu-id="dfc18-342">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="dfc18-343">Les listes suivantes offrent des conseils sur les catégories de fonctionnalités OO à un niveau élevé.</span><span class="sxs-lookup"><span data-stu-id="dfc18-343">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="dfc18-344">**Envisagez d’utiliser ces fonctionnalités dans de nombreuses situations :**</span><span class="sxs-lookup"><span data-stu-id="dfc18-344">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="dfc18-345">Notation par`x.Length`points ( )</span><span class="sxs-lookup"><span data-stu-id="dfc18-345">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="dfc18-346">Membres d’instance</span><span class="sxs-lookup"><span data-stu-id="dfc18-346">Instance members</span></span>
* <span data-ttu-id="dfc18-347">Constructeurs implicites</span><span class="sxs-lookup"><span data-stu-id="dfc18-347">Implicit constructors</span></span>
* <span data-ttu-id="dfc18-348">Membres static</span><span class="sxs-lookup"><span data-stu-id="dfc18-348">Static members</span></span>
* <span data-ttu-id="dfc18-349">Notation de`arr.[x]`l’indexeur ( )</span><span class="sxs-lookup"><span data-stu-id="dfc18-349">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="dfc18-350">Arguments nommés et facultatifs</span><span class="sxs-lookup"><span data-stu-id="dfc18-350">Named and Optional arguments</span></span>
* <span data-ttu-id="dfc18-351">Interfaces et implémentations d’interfaces</span><span class="sxs-lookup"><span data-stu-id="dfc18-351">Interfaces and interface implementations</span></span>

<span data-ttu-id="dfc18-352">**N’atteignez pas ces fonctionnalités d’abord, mais ne les appliquer judicieusement quand ils sont commodes pour résoudre un problème:**</span><span class="sxs-lookup"><span data-stu-id="dfc18-352">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="dfc18-353">Surcharge de méthode</span><span class="sxs-lookup"><span data-stu-id="dfc18-353">Method overloading</span></span>
* <span data-ttu-id="dfc18-354">Données mutables encapsulées</span><span class="sxs-lookup"><span data-stu-id="dfc18-354">Encapsulated mutable data</span></span>
* <span data-ttu-id="dfc18-355">Opérateurs sur les types</span><span class="sxs-lookup"><span data-stu-id="dfc18-355">Operators on types</span></span>
* <span data-ttu-id="dfc18-356">Propriétés automobiles</span><span class="sxs-lookup"><span data-stu-id="dfc18-356">Auto properties</span></span>
* <span data-ttu-id="dfc18-357">Mise `IDisposable` en œuvre et mise en œuvre`IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="dfc18-357">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="dfc18-358">Extensions de type</span><span class="sxs-lookup"><span data-stu-id="dfc18-358">Type extensions</span></span>
* <span data-ttu-id="dfc18-359">Événements</span><span class="sxs-lookup"><span data-stu-id="dfc18-359">Events</span></span>
* <span data-ttu-id="dfc18-360">Structs</span><span class="sxs-lookup"><span data-stu-id="dfc18-360">Structs</span></span>
* <span data-ttu-id="dfc18-361">Délégués</span><span class="sxs-lookup"><span data-stu-id="dfc18-361">Delegates</span></span>
* <span data-ttu-id="dfc18-362">Enums</span><span class="sxs-lookup"><span data-stu-id="dfc18-362">Enums</span></span>

<span data-ttu-id="dfc18-363">**Évitez généralement ces fonctionnalités à moins que vous ne les utilisiez :**</span><span class="sxs-lookup"><span data-stu-id="dfc18-363">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="dfc18-364">Hiérarchies de type fondées sur l’héritage et héritage de mise en œuvre</span><span class="sxs-lookup"><span data-stu-id="dfc18-364">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="dfc18-365">Nuls et`Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="dfc18-365">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="dfc18-366">Préférez la composition à l’héritage</span><span class="sxs-lookup"><span data-stu-id="dfc18-366">Prefer composition over inheritance</span></span>

<span data-ttu-id="dfc18-367">[La composition sur l’héritage](https://en.wikipedia.org/wiki/Composition_over_inheritance) est un idiome de longue date auquel un bon code F peut adhérer.</span><span class="sxs-lookup"><span data-stu-id="dfc18-367">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="dfc18-368">Le principe fondamental est que vous ne devriez pas exposer une classe de base et forcer les appelants à hériter de cette classe de base pour obtenir des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="dfc18-368">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="dfc18-369">Utilisez des expressions d’objets pour implémenter des interfaces si vous n’avez pas besoin d’une classe</span><span class="sxs-lookup"><span data-stu-id="dfc18-369">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="dfc18-370">[Les expressions d’objet](../language-reference/object-expressions.md) vous permettent d’implémenter des interfaces à la volée, liant l’interface implémentée à une valeur sans avoir besoin de le faire à l’intérieur d’une classe.</span><span class="sxs-lookup"><span data-stu-id="dfc18-370">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="dfc18-371">C’est pratique, surtout si vous _n’avez_ besoin que d’implémenter l’interface et n’avez pas besoin d’une classe complète.</span><span class="sxs-lookup"><span data-stu-id="dfc18-371">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="dfc18-372">Par exemple, voici le code qui est exécuté dans [Ionide](http://ionide.io/) pour fournir une action de correction `open` de code si vous avez ajouté un symbole que vous n’avez pas une déclaration pour :</span><span class="sxs-lookup"><span data-stu-id="dfc18-372">For example, here is the code that is run in [Ionide](http://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

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

<span data-ttu-id="dfc18-373">Parce qu’il n’est pas nécessaire d’avoir une classe lors de l’interaction avec l’API Visual Studio Code, Les expressions d’objets sont un outil idéal pour cela.</span><span class="sxs-lookup"><span data-stu-id="dfc18-373">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="dfc18-374">Ils sont également précieux pour les tests unitaires, lorsque vous voulez talon sur une interface avec des routines de test d’une manière ad hoc.</span><span class="sxs-lookup"><span data-stu-id="dfc18-374">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="consider-type-abbreviations-to-shorten-signatures"></a><span data-ttu-id="dfc18-375">Considérez les abréviations de type pour raccourcir les signatures</span><span class="sxs-lookup"><span data-stu-id="dfc18-375">Consider Type Abbreviations to shorten signatures</span></span>

<span data-ttu-id="dfc18-376">[Les abréviations de type](../language-reference/type-abbreviations.md) sont un moyen pratique d’attribuer une étiquette à un autre type, comme une signature de fonction ou un type plus complexe.</span><span class="sxs-lookup"><span data-stu-id="dfc18-376">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="dfc18-377">Par exemple, l’alias suivant attribue une étiquette à ce qui est nécessaire pour définir un calcul avec [CNTK](https://docs.microsoft.com/cognitive-toolkit/), une bibliothèque d’apprentissage profond :</span><span class="sxs-lookup"><span data-stu-id="dfc18-377">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://docs.microsoft.com/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="dfc18-378">Le `Computation` nom est un moyen pratique de désigner toute fonction qui correspond à la signature qu’il est aliasing.</span><span class="sxs-lookup"><span data-stu-id="dfc18-378">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="dfc18-379">L’utilisation d’abréviations de type comme celle-ci est pratique et permet un code plus succinct.</span><span class="sxs-lookup"><span data-stu-id="dfc18-379">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="dfc18-380">Évitez d’utiliser des abréviations de type pour représenter votre domaine</span><span class="sxs-lookup"><span data-stu-id="dfc18-380">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="dfc18-381">Bien que les abréviations de type soient pratiques pour donner un nom aux signatures de fonction, elles peuvent être confuses lors de l’abréviation d’autres types.</span><span class="sxs-lookup"><span data-stu-id="dfc18-381">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="dfc18-382">Considérez cette abréviation :</span><span class="sxs-lookup"><span data-stu-id="dfc18-382">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="dfc18-383">Cela peut être déroutant de multiples façons :</span><span class="sxs-lookup"><span data-stu-id="dfc18-383">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="dfc18-384">`BufferSize`n’est pas une abstraction; c’est juste un autre nom pour un integer.</span><span class="sxs-lookup"><span data-stu-id="dfc18-384">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="dfc18-385">Si `BufferSize` elle est exposée dans une API publique, elle peut `int`facilement être mal interprétée comme signifiant plus que simplement.</span><span class="sxs-lookup"><span data-stu-id="dfc18-385">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="dfc18-386">Généralement, les types de domaine ont plusieurs attributs pour eux et ne sont pas des types primitifs comme `int`.</span><span class="sxs-lookup"><span data-stu-id="dfc18-386">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="dfc18-387">Cette abréviation viole cette hypothèse.</span><span class="sxs-lookup"><span data-stu-id="dfc18-387">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="dfc18-388">Le boîtier `BufferSize` de (PascalCase) implique que ce type contient plus de données.</span><span class="sxs-lookup"><span data-stu-id="dfc18-388">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="dfc18-389">Ce pseudonyme n’offre pas une clarté accrue par rapport à la fourniture d’un argument nommé à une fonction.</span><span class="sxs-lookup"><span data-stu-id="dfc18-389">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="dfc18-390">L’abréviation ne se manifestera pas dans l’IL compilé; c’est juste un intégrant et ce alias est une construction de compile-temps.</span><span class="sxs-lookup"><span data-stu-id="dfc18-390">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

<span data-ttu-id="dfc18-391">En résumé, l’écueil avec les abréviations de type est qu’ils ne sont **pas** des abstractions sur les types qu’ils abrégé.</span><span class="sxs-lookup"><span data-stu-id="dfc18-391">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="dfc18-392">Dans l’exemple `BufferSize` précédent, `int` est juste un sous les couvertures, sans données `int` supplémentaires, ni aucun avantage du système de type en dehors de ce qui a déjà.</span><span class="sxs-lookup"><span data-stu-id="dfc18-392">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>

<span data-ttu-id="dfc18-393">Une autre approche de l’utilisation d’abréviations de type pour représenter un domaine consiste à utiliser des syndicats à cas unique et discriminés.</span><span class="sxs-lookup"><span data-stu-id="dfc18-393">An alternative approach to using type abbreviations to represent a domain is to use single-case discriminated unions.</span></span> <span data-ttu-id="dfc18-394">L’échantillon précédent peut être modélisé comme suit :</span><span class="sxs-lookup"><span data-stu-id="dfc18-394">The previous sample can be modeled as follows:</span></span>

```fsharp
type BufferSize = BufferSize of int
```

<span data-ttu-id="dfc18-395">Si vous écrivez du `BufferSize` code qui fonctionne en termes de et sa valeur sous-jacente, vous devez en construire un plutôt que de passer dans n’importe quel intégrant arbitraire :</span><span class="sxs-lookup"><span data-stu-id="dfc18-395">If you write code that operates in terms of `BufferSize` and its underlying value, you need to construct one rather than pass in any arbitrary integer:</span></span>

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

<span data-ttu-id="dfc18-396">Cela réduit la probabilité de passer par erreur un `send` integer arbitraire dans `BufferSize` la fonction, parce que l’appelant doit construire un type pour envelopper une valeur avant d’appeler la fonction.</span><span class="sxs-lookup"><span data-stu-id="dfc18-396">This reduces the likelihood of mistakenly passing an arbitrary integer into the `send` function, because the caller must construct a `BufferSize` type to wrap a value before calling the function.</span></span>
