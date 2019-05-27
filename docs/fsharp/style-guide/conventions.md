---
title: Conventions de codage F#
description: Découvrez des instructions générales et des idiomes lors de l’écriture F# code.
ms.date: 05/14/2018
ms.openlocfilehash: 4b292d0a844a4d9efc79aa865b054b4af2cb68c4
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052796"
---
# <a name="f-coding-conventions"></a><span data-ttu-id="df3b9-103">Conventions de codage F#</span><span class="sxs-lookup"><span data-stu-id="df3b9-103">F# coding conventions</span></span>

<span data-ttu-id="df3b9-104">Les conventions suivantes sont formulées à partir de l’expérience d’utilisation avec de grandes F# codes base.</span><span class="sxs-lookup"><span data-stu-id="df3b9-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="df3b9-105">Le [cinq principes bonne F# code](index.md#five-principles-of-good-f-code) constituent la base de chaque recommandation.</span><span class="sxs-lookup"><span data-stu-id="df3b9-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="df3b9-106">Elles sont liées à la [ F# les instructions de conception de composant](component-design-guidelines.md), mais sont applicables pour toute F# de code, pas seulement les composants telles que les bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="df3b9-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="df3b9-107">Organisation du code</span><span class="sxs-lookup"><span data-stu-id="df3b9-107">Organizing code</span></span>

<span data-ttu-id="df3b9-108">F#propose deux méthodes principales pour organiser le code : modules et les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="df3b9-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="df3b9-109">Ceux-ci sont similaires, mais que vous n’ont pas les différences suivantes :</span><span class="sxs-lookup"><span data-stu-id="df3b9-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="df3b9-110">Espaces de noms sont compilés en tant qu’espaces de noms .NET.</span><span class="sxs-lookup"><span data-stu-id="df3b9-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="df3b9-111">Les modules sont compilés en tant que classes statiques.</span><span class="sxs-lookup"><span data-stu-id="df3b9-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="df3b9-112">Espaces de noms sont toujours de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="df3b9-112">Namespaces are always top level.</span></span> <span data-ttu-id="df3b9-113">Modules peuvent être imbriqués dans d’autres modules et de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="df3b9-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="df3b9-114">Espaces de noms peut s’étendre sur plusieurs fichiers.</span><span class="sxs-lookup"><span data-stu-id="df3b9-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="df3b9-115">Les modules ne peuvent pas.</span><span class="sxs-lookup"><span data-stu-id="df3b9-115">Modules cannot.</span></span>
* <span data-ttu-id="df3b9-116">Les modules peuvent être décorées avec `[<RequireQualifiedAccess>]` et `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="df3b9-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="df3b9-117">Les instructions suivantes vous aideront à les utiliser pour organiser votre code.</span><span class="sxs-lookup"><span data-stu-id="df3b9-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="df3b9-118">Préférez les espaces de noms au niveau supérieur</span><span class="sxs-lookup"><span data-stu-id="df3b9-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="df3b9-119">Pour tout code utilisable publiquement, les espaces de noms sont préférentiels aux modules au niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="df3b9-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="df3b9-120">Car ils sont compilés en tant qu’espaces de noms .NET, ils sont consommables à partir de c# avec aucun problème.</span><span class="sxs-lookup"><span data-stu-id="df3b9-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="df3b9-121">À l’aide d’un module de niveau supérieur peuvent être absentes différent lorsqu’elle est appelée uniquement à partir de F#, mais pour C# consommateurs, les appelants peuvent être surpris par devoir qualifier `MyClass` avec la `MyCode` module.</span><span class="sxs-lookup"><span data-stu-id="df3b9-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="df3b9-122">Appliquer avec soin `[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="df3b9-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="df3b9-123">Le `[<AutoOpen>]` construction permettre polluent l’étendue de ce qui est disponible aux appelants, et la réponse à quelque chose de provenance est « magique ».</span><span class="sxs-lookup"><span data-stu-id="df3b9-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="df3b9-124">Cela n’est généralement pas une bonne chose.</span><span class="sxs-lookup"><span data-stu-id="df3b9-124">This is generally not a good thing.</span></span> <span data-ttu-id="df3b9-125">Une exception à cette règle est la F# bibliothèque principale elle-même (bien que cela n’existe également un peu controversé).</span><span class="sxs-lookup"><span data-stu-id="df3b9-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="df3b9-126">Toutefois, il est pratique si vous disposez des fonctionnalités d’assistance pour une API publique que vous souhaitez organiser séparément à partir de cette API publique.</span><span class="sxs-lookup"><span data-stu-id="df3b9-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

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

<span data-ttu-id="df3b9-127">Vous pouvez ainsi les détails d’implémentation de distinct correctement à partir de l’API publique d’une fonction sans avoir à qualifier complètement une assistance à chaque fois que vous l’appelez.</span><span class="sxs-lookup"><span data-stu-id="df3b9-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="df3b9-128">En outre, exposer des méthodes d’extension et de générateurs d’expressions au niveau de l’espace de noms peut être parfaitement exprimée avec `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="df3b9-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="df3b9-129">Utilisez `[<RequireQualifiedAccess>]` chaque fois que les noms peuvent entrer en conflit ou si vous pensez qui vous aideront à la lisibilité</span><span class="sxs-lookup"><span data-stu-id="df3b9-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="df3b9-130">Ajout de la `[<RequireQualifiedAccess>]` attribut à un module indique que le module ne peut-être pas être ouverts et des références aux éléments du module doivent explicite qualifié d’accès.</span><span class="sxs-lookup"><span data-stu-id="df3b9-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="df3b9-131">Par exemple, le `Microsoft.FSharp.Collections.List` module a cet attribut.</span><span class="sxs-lookup"><span data-stu-id="df3b9-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="df3b9-132">Cela est utile lorsque les valeurs dans le module et les fonctions ont des noms qui sont susceptibles d’entrer en conflit avec les noms dans d’autres modules.</span><span class="sxs-lookup"><span data-stu-id="df3b9-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="df3b9-133">Nécessitant un accès complet peut augmenter considérablement la facilité de maintenance à long terme et aspects d’une bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="df3b9-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="df3b9-134">Tri `open` instructions topologiquement</span><span class="sxs-lookup"><span data-stu-id="df3b9-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="df3b9-135">Dans F#, l’ordre des questions de déclarations, notamment avec `open` instructions.</span><span class="sxs-lookup"><span data-stu-id="df3b9-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="df3b9-136">Contrairement à c#, où l’effet de `using` et `using static` est indépendante de l’ordre de ces instructions dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="df3b9-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="df3b9-137">Dans F#, éléments ouverts dans une étendue peuvent masquer d’autres déjà présent.</span><span class="sxs-lookup"><span data-stu-id="df3b9-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="df3b9-138">Cela signifie que la réorganisation `open` instructions pourraient modifier la signification du code.</span><span class="sxs-lookup"><span data-stu-id="df3b9-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="df3b9-139">Par conséquent, toute arbitraire de tri de tous les `open` instructions (par exemple, dans l’ordre alphanumérique) n’est généralement pas recommandé, peur de vous générer un comportement différent que vous pourriez vous attendre.</span><span class="sxs-lookup"><span data-stu-id="df3b9-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is generally not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="df3b9-140">Au lieu de cela, nous vous recommandons de les trier [topologiquement](https://en.wikipedia.org/wiki/Topological_sorting); autrement dit, commander votre `open` instructions dans l’ordre dans lequel _couches_ de votre système sont définis.</span><span class="sxs-lookup"><span data-stu-id="df3b9-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="df3b9-141">Effectuant d’alphanumériques dans les différentes couches topologiques de tri peut également être considéré comme.</span><span class="sxs-lookup"><span data-stu-id="df3b9-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="df3b9-142">Par exemple, voici le tri topologique pour le F# fichier API publique de compilateur service :</span><span class="sxs-lookup"><span data-stu-id="df3b9-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

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

<span data-ttu-id="df3b9-143">Notez qu’un saut de ligne sépare les couches topologiques, avec chaque couche en cours de tri dans l’ordre alphanumérique par la suite.</span><span class="sxs-lookup"><span data-stu-id="df3b9-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="df3b9-144">Code sont correctement organisées sans occultation accidentellement des valeurs.</span><span class="sxs-lookup"><span data-stu-id="df3b9-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="df3b9-145">Utiliser des classes pour contenir des valeurs qui ont des effets secondaires</span><span class="sxs-lookup"><span data-stu-id="df3b9-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="df3b9-146">Il existe plusieurs fois lorsque l’initialisation d’une valeur peut avoir des effets secondaires, tels que l’instanciation d’un contexte à une base de données ou une autre ressource à distance.</span><span class="sxs-lookup"><span data-stu-id="df3b9-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="df3b9-147">Il est tentant de les initialiser des éléments dans un module et l’utiliser dans les fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="df3b9-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

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

<span data-ttu-id="df3b9-148">Il s’agit généralement une mauvaise idée pour plusieurs raisons :</span><span class="sxs-lookup"><span data-stu-id="df3b9-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="df3b9-149">Tout d’abord, configuration de l’application est placée dans la base de code avec `dep1` et `dep2`.</span><span class="sxs-lookup"><span data-stu-id="df3b9-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="df3b9-150">Il est difficile de maintenir dans des codes base supérieure.</span><span class="sxs-lookup"><span data-stu-id="df3b9-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="df3b9-151">Ensuite, initialisées de manière statique des données ne doivent pas inclure de valeurs qui ne sont pas thread-safe si votre composant lui-même utilise plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="df3b9-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="df3b9-152">Cela constitue une infraction clairement à `dep3`.</span><span class="sxs-lookup"><span data-stu-id="df3b9-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="df3b9-153">Enfin, l’initialisation du module compile dans un constructeur statique pour l’unité de compilation entière.</span><span class="sxs-lookup"><span data-stu-id="df3b9-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="df3b9-154">Si une erreur se produit dans l’initialisation de la valeur liée aux let dans ce module, il se manifeste comme un `TypeInitializationException` qui est ensuite mis en cache pour toute la durée de vie de l’application.</span><span class="sxs-lookup"><span data-stu-id="df3b9-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="df3b9-155">Cela peut être difficile à diagnostiquer.</span><span class="sxs-lookup"><span data-stu-id="df3b9-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="df3b9-156">Il existe généralement une exception interne que vous pouvez essayer d’analyser, mais s’il n’est pas, puis il est impossible de dire qu’est la cause racine.</span><span class="sxs-lookup"><span data-stu-id="df3b9-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="df3b9-157">Au lieu de cela, simplement utiliser une classe simple pour contenir les dépendances :</span><span class="sxs-lookup"><span data-stu-id="df3b9-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="df3b9-158">Ainsi, les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="df3b9-158">This enables the following:</span></span>

1. <span data-ttu-id="df3b9-159">Envoi de n’importe quel état dépendant en dehors de l’API elle-même.</span><span class="sxs-lookup"><span data-stu-id="df3b9-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="df3b9-160">Configuration peut maintenant être effectuée en dehors de l’API.</span><span class="sxs-lookup"><span data-stu-id="df3b9-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="df3b9-161">Erreurs dans l’initialisation de valeurs dépendantes ne sont pas susceptibles de se manifester par un `TypeInitializationException`.</span><span class="sxs-lookup"><span data-stu-id="df3b9-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="df3b9-162">L’API est maintenant plus facile à tester.</span><span class="sxs-lookup"><span data-stu-id="df3b9-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="df3b9-163">Gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="df3b9-163">Error management</span></span>

<span data-ttu-id="df3b9-164">Gestion des erreurs dans les systèmes volumineux s’avérer complexe et subtils, et il n’y a aucune silver puces garantir vos systèmes à tolérance de pannes et se comportent correctement.</span><span class="sxs-lookup"><span data-stu-id="df3b9-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="df3b9-165">Les instructions suivantes doivent offrir des conseils pour la navigation dans cet espace difficile.</span><span class="sxs-lookup"><span data-stu-id="df3b9-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="df3b9-166">Représentent les cas d’erreur et l’état non conforme dans les types intrinsèques à votre domaine</span><span class="sxs-lookup"><span data-stu-id="df3b9-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="df3b9-167">Avec [Unions discriminées](../language-reference/discriminated-unions.md), F# vous donne la possibilité pour représenter l’état du programme défectueux dans votre système de type.</span><span class="sxs-lookup"><span data-stu-id="df3b9-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="df3b9-168">Exemple :</span><span class="sxs-lookup"><span data-stu-id="df3b9-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="df3b9-169">Dans ce cas, il existe trois façons connus dont le retrait d’argent à partir d’un compte bancaire peut échouer.</span><span class="sxs-lookup"><span data-stu-id="df3b9-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="df3b9-170">Chaque cas d’erreur est représenté dans le type et peuvent donc être traitées en toute sécurité l’ensemble du programme.</span><span class="sxs-lookup"><span data-stu-id="df3b9-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="df3b9-171">En règle générale, si vous pouvez modéliser les différentes façons que quelque chose peut **échouer** dans votre domaine, puis gestion de code d’erreur n’est plus traité en tant que quelque chose que vous devez traiter en plus des flux de programme régulière.</span><span class="sxs-lookup"><span data-stu-id="df3b9-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="df3b9-172">Il est simplement une partie du flux de programme normal et pas considéré comme **exceptionnelles**.</span><span class="sxs-lookup"><span data-stu-id="df3b9-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="df3b9-173">Il existe deux grands avantages à cela :</span><span class="sxs-lookup"><span data-stu-id="df3b9-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="df3b9-174">Il est plus facile à maintenir votre domaine que les modifications apportées au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="df3b9-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="df3b9-175">Cas d’erreur sont plus faciles à test unitaire.</span><span class="sxs-lookup"><span data-stu-id="df3b9-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="df3b9-176">Utilisez les exceptions lorsque les erreurs ne peut pas être représentées avec des types</span><span class="sxs-lookup"><span data-stu-id="df3b9-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="df3b9-177">Pas toutes les erreurs peuvent être représentés dans un domaine qui pose problème.</span><span class="sxs-lookup"><span data-stu-id="df3b9-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="df3b9-178">Ces types d’erreurs sont *exceptionnelles* par nature, par conséquent, la possibilité de déclencher et intercepter des exceptions dans F#.</span><span class="sxs-lookup"><span data-stu-id="df3b9-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="df3b9-179">Tout d’abord, il est recommandé de lire le [instructions de conception d’Exception](../../standard/design-guidelines/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="df3b9-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="df3b9-180">Ceux-ci sont également applicables aux F#.</span><span class="sxs-lookup"><span data-stu-id="df3b9-180">These are also applicable to F#.</span></span>

<span data-ttu-id="df3b9-181">Les principales constructions disponibles dans F# pour les besoins de déclenchement d’exceptions doivent être considérés comme dans l’ordre de préférence suivant :</span><span class="sxs-lookup"><span data-stu-id="df3b9-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="df3b9-182">Fonction</span><span class="sxs-lookup"><span data-stu-id="df3b9-182">Function</span></span> | <span data-ttu-id="df3b9-183">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df3b9-183">Syntax</span></span> | <span data-ttu-id="df3b9-184">Objectif</span><span class="sxs-lookup"><span data-stu-id="df3b9-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="df3b9-185">Déclenche un `System.ArgumentNullException` portant le nom de l’argument spécifié.</span><span class="sxs-lookup"><span data-stu-id="df3b9-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="df3b9-186">Déclenche un `System.ArgumentException` avec un nom d’argument spécifié et le message.</span><span class="sxs-lookup"><span data-stu-id="df3b9-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="df3b9-187">Déclenche un `System.InvalidOperationException` avec le message spécifié.</span><span class="sxs-lookup"><span data-stu-id="df3b9-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="df3b9-188">Mécanisme à usage général pour lever des exceptions.</span><span class="sxs-lookup"><span data-stu-id="df3b9-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="df3b9-189">Déclenche un `System.Exception` avec le message spécifié.</span><span class="sxs-lookup"><span data-stu-id="df3b9-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="df3b9-190">Déclenche un `System.Exception` avec un message déterminé par la chaîne de format et de ses entrées.</span><span class="sxs-lookup"><span data-stu-id="df3b9-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="df3b9-191">Utilisez `nullArg`, `invalidArg` et `invalidOp` comme mécanisme pour lever `ArgumentNullException`, `ArgumentException` et `InvalidOperationException` quand cela est approprié.</span><span class="sxs-lookup"><span data-stu-id="df3b9-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="df3b9-192">Le `failwith` et `failwithf` fonctions doivent généralement être évitées, car elles déclenchent la base `Exception` type, pas une exception spécifique.</span><span class="sxs-lookup"><span data-stu-id="df3b9-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="df3b9-193">En tant que par le [instructions de conception d’Exception](../../standard/design-guidelines/exceptions.md), vous souhaitez déclencher des exceptions plus spécifiques lorsque vous pouvez.</span><span class="sxs-lookup"><span data-stu-id="df3b9-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="df3b9-194">À l’aide de la syntaxe de gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="df3b9-194">Using exception-handling syntax</span></span>

<span data-ttu-id="df3b9-195">F#prend en charge les modèles d’exception via la `try...with` syntaxe :</span><span class="sxs-lookup"><span data-stu-id="df3b9-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="df3b9-196">Réconciliation des fonctionnalités à effectuer en cas d’une exception avec les critères spéciaux peut être un peu délicate si vous souhaitez conserver le code propre.</span><span class="sxs-lookup"><span data-stu-id="df3b9-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="df3b9-197">Une d’elles consiste à gérer cette situation consiste à utiliser [modèles actifs](../language-reference/active-patterns.md) comme un moyen de la fonctionnalité de groupe qui entoure un cas d’erreur avec une exception lui-même.</span><span class="sxs-lookup"><span data-stu-id="df3b9-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="df3b9-198">Vous pouvez par exemple, qui utilise une API qui, lorsqu’elle lève une exception, englobe des informations précieuses dans les métadonnées d’exception.</span><span class="sxs-lookup"><span data-stu-id="df3b9-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="df3b9-199">Désencapsulage d’une valeur utile dans le corps de l’exception capturée à l’intérieur du modèle actif et en retournant que la valeur peut être utile dans certaines situations.</span><span class="sxs-lookup"><span data-stu-id="df3b9-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="df3b9-200">N’utilisez pas monadic gestion des erreurs pour remplacer des exceptions</span><span class="sxs-lookup"><span data-stu-id="df3b9-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="df3b9-201">Exceptions sont considérées comme un peu interdits dans la programmation fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="df3b9-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="df3b9-202">En effet, les exceptions violent pureté, qu’il s’agisse à prendre en compte non-tout à fait fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="df3b9-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="df3b9-203">Toutefois, il ignore la réalité du où le code doit s’exécuter et ce runtime erreurs peuvent se produire.</span><span class="sxs-lookup"><span data-stu-id="df3b9-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="df3b9-204">En règle générale, écrire du code sur l’hypothèse que la plupart des éléments sont pure ni total, afin de réduire les mauvaises surprises.</span><span class="sxs-lookup"><span data-stu-id="df3b9-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="df3b9-205">Il est important de considérer les principaux atouts/aspects suivants d’Exceptions en ce qui concerne leur pertinence et la pertinence dans le runtime .NET et l’écosystème d’interlangage dans son ensemble :</span><span class="sxs-lookup"><span data-stu-id="df3b9-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="df3b9-206">Elles contiennent des informations de diagnostic détaillées, ce qui est très utiles lors du débogage d’un problème.</span><span class="sxs-lookup"><span data-stu-id="df3b9-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="df3b9-207">Ils sont bien compris par le runtime et d’autres langages .NET.</span><span class="sxs-lookup"><span data-stu-id="df3b9-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="df3b9-208">Elles permettent une réduction significative réutilisable par rapport au code qui est hors de sa méthode pour *éviter* exceptions en implémentant un sous-ensemble de leur sémantique sur une base ad hoc.</span><span class="sxs-lookup"><span data-stu-id="df3b9-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="df3b9-209">Cet troisième point est essentiel.</span><span class="sxs-lookup"><span data-stu-id="df3b9-209">This third point is critical.</span></span> <span data-ttu-id="df3b9-210">Pour les opérations complexes non triviale, ne parvient pas à utiliser des exceptions peut entraîner dans le traitement des structures comme suit :</span><span class="sxs-lookup"><span data-stu-id="df3b9-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="df3b9-211">Qui peut facilement conduire à un code fragile comme critères spéciaux sur les erreurs « stringly typé » :</span><span class="sxs-lookup"><span data-stu-id="df3b9-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="df3b9-212">En outre, il peut être tentant d’AVALER toute exception dans la volonté de disposer d’une fonction « simple » qui retourne un type « mieux » :</span><span class="sxs-lookup"><span data-stu-id="df3b9-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="df3b9-213">Malheureusement, `tryReadAllText` peut lever de nombreuses exceptions selon la multitude de choses peuvent se produire sur un système de fichiers, et ce code annule immédiatement toutes les informations concernant ce qui peut réellement être fonctionner dans votre environnement.</span><span class="sxs-lookup"><span data-stu-id="df3b9-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="df3b9-214">Si vous remplacez ce code avec un type de résultat, vous êtes à l’analyse des messages d’erreur « stringly typé » :</span><span class="sxs-lookup"><span data-stu-id="df3b9-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

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

<span data-ttu-id="df3b9-215">Et en plaçant l’objet exception lui-même dans le `Error` constructeur simplement vous oblige à gérer correctement le type d’exception sur le site d’appel, plutôt que dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="df3b9-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="df3b9-216">Cette opération efficacement crée des exceptions vérifiées, qui sont notoirement unfun à gérer en tant qu’appelant d’une API.</span><span class="sxs-lookup"><span data-stu-id="df3b9-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="df3b9-217">Une bonne alternative aux exemples ci-dessus consiste à intercepter *spécifique* exceptions et retournent une valeur significative dans le contexte de cette exception.</span><span class="sxs-lookup"><span data-stu-id="df3b9-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="df3b9-218">Si vous modifiez le `tryReadAllText` fonctionnent comme suit, `None` a plus de sens :</span><span class="sxs-lookup"><span data-stu-id="df3b9-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="df3b9-219">Au lieu de fonctionner comme un fourre-tout, cette fonction désormais correctement gérera le cas lorsqu’un fichier est introuvable et affecter ce sens à un retour.</span><span class="sxs-lookup"><span data-stu-id="df3b9-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="df3b9-220">Cette valeur de retour peut mapper à ce cas d’erreur lors de pas en ignorant toutes les informations contextuelles ou forcer les appelants pour y faire face à un cas qui ne peuvent pas être pertinent à ce stade dans le code.</span><span class="sxs-lookup"><span data-stu-id="df3b9-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="df3b9-221">Types tels que `Result<'Success, 'Error>` conviennent pour les opérations de base où ils ne sont pas imbriqués, et F# types facultatifs sont parfaits pour représentant lorsque quelque chose peut retourner *quelque chose* ou *rien*.</span><span class="sxs-lookup"><span data-stu-id="df3b9-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="df3b9-222">Ils ne sont pas un substitut pour les exceptions, cependant et ne doivent pas être utilisés dans une tentative pour remplacer des exceptions.</span><span class="sxs-lookup"><span data-stu-id="df3b9-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="df3b9-223">Au lieu de cela, elles doivent être appliquées judicieusement à des aspects spécifiques d’adresse de stratégie de gestion des erreurs et des exceptions de manière ciblée.</span><span class="sxs-lookup"><span data-stu-id="df3b9-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="df3b9-224">Application partielle et libre de point de programmation</span><span class="sxs-lookup"><span data-stu-id="df3b9-224">Partial application and point-free programming</span></span>

<span data-ttu-id="df3b9-225">F#prend en charge d’application partielle et par conséquent, les différentes manières de programme dans un style libre de point.</span><span class="sxs-lookup"><span data-stu-id="df3b9-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="df3b9-226">Ceci peut être avantageux de réutilisation du code au sein d’un module ou de l’implémentation de quelque chose, mais il n’est généralement pas quelque chose pour exposer publiquement.</span><span class="sxs-lookup"><span data-stu-id="df3b9-226">This can be beneficial for code reuse within a module or the implementation of something, but it is generally not something to expose publicly.</span></span> <span data-ttu-id="df3b9-227">En général, libre de point de programmation n’est pas une raison elle-même et peut ajouter un frein COGNITIF pour les personnes qui ne sont pas plonge dans le style.</span><span class="sxs-lookup"><span data-stu-id="df3b9-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="df3b9-228">N’utilisez pas application partielle et des curryfication dans les API publiques</span><span class="sxs-lookup"><span data-stu-id="df3b9-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="df3b9-229">Avec peu d’exception, l’utilisation d’une application partielle dans les API publiques permettre prêter à confuse pour les consommateurs.</span><span class="sxs-lookup"><span data-stu-id="df3b9-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="df3b9-230">En règle générale, `let`-liée de valeurs dans F# code sont **valeurs**, et non **des valeurs de fonction**.</span><span class="sxs-lookup"><span data-stu-id="df3b9-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="df3b9-231">Combinaison de valeurs et les valeurs de fonction peut entraîner l’enregistrement d’un petit nombre de lignes de code en échange d’un peu de surcharge cognitive, en particulier si combinées avec des opérateurs tels que `>>` pour composer des fonctions.</span><span class="sxs-lookup"><span data-stu-id="df3b9-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="df3b9-232">Prendre en compte les implications en matière d’outils pour la programmation exempt de point</span><span class="sxs-lookup"><span data-stu-id="df3b9-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="df3b9-233">Fonctions curryfiées étiquette pas leurs arguments.</span><span class="sxs-lookup"><span data-stu-id="df3b9-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="df3b9-234">Cela a des implications des outils.</span><span class="sxs-lookup"><span data-stu-id="df3b9-234">This has tooling implications.</span></span> <span data-ttu-id="df3b9-235">Prenez en compte les deux fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="df3b9-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="df3b9-236">Les deux sont des fonctions valides, mais `funcWithApplication` est une fonction curryfiée.</span><span class="sxs-lookup"><span data-stu-id="df3b9-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="df3b9-237">Lorsque vous pointez sur leurs types dans un éditeur, vous voir ceci :</span><span class="sxs-lookup"><span data-stu-id="df3b9-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="df3b9-238">Sur le site d’appel, info-bulles dans les outils tels que Visual Studio ne vous donnera des informations significatives quant à ce que le `string` et `int` représentent les types d’entrée.</span><span class="sxs-lookup"><span data-stu-id="df3b9-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="df3b9-239">Si vous rencontrez le code sans point comme `funcWithApplication` qui est consommable publiquement, il est recommandé d’effectuer une expansion de η complète afin que les outils peuvent sélectionner en noms significatifs pour les arguments.</span><span class="sxs-lookup"><span data-stu-id="df3b9-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="df3b9-240">En outre, le débogage de code sans point peut être difficile, voire impossible.</span><span class="sxs-lookup"><span data-stu-id="df3b9-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="df3b9-241">Outils de débogage s’appuient sur les valeurs liées aux noms (par exemple, `let` liaisons) afin que vous puissiez inspecter au milieu des valeurs intermédiaires de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="df3b9-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="df3b9-242">Lorsque votre code n’a aucune valeur à inspecter, vous n’avez rien à déboguer.</span><span class="sxs-lookup"><span data-stu-id="df3b9-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="df3b9-243">À l’avenir, les outils de débogage peut évoluer pour synthétiser ces valeurs en fonction des chemins d’accès précédemment exécutées, mais il n’est pas une bonne idée pour couvrir vos meilleurs résultats sur *potentiels* fonctionnalités de débogage.</span><span class="sxs-lookup"><span data-stu-id="df3b9-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="df3b9-244">Considérez une application partielle comme une technique pour réduire réutilisable interne</span><span class="sxs-lookup"><span data-stu-id="df3b9-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="df3b9-245">Contrairement au point précédent, application partielle est un outil merveilleux pour réduire réutilisable à l’intérieur d’une application ou les mécanismes internes plus approfondies d’une API.</span><span class="sxs-lookup"><span data-stu-id="df3b9-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="df3b9-246">Il peut être utile pour l’implémentation des API plus complexes, où réutilisable est souvent un vrai calvaire s’occuper de tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="df3b9-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="df3b9-247">Par exemple, le code suivant montre comment vous pouvez réaliser les infrastructures factices plus vous donnent sans prendre une dépendance externe sur une telle infrastructure et devoir apprendre un connexes ad hoc des API.</span><span class="sxs-lookup"><span data-stu-id="df3b9-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="df3b9-248">Par exemple, considérez la topographie de solution suivants :</span><span class="sxs-lookup"><span data-stu-id="df3b9-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="df3b9-249">`ImplementationLogic.fsproj` peut exposer du code tel que :</span><span class="sxs-lookup"><span data-stu-id="df3b9-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="df3b9-250">Tests unitaires `Transactions.doTransaction` dans `ImplementationLogic.Tests.fspoj` est facile :</span><span class="sxs-lookup"><span data-stu-id="df3b9-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fspoj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="df3b9-251">Application partiellement `doTransaction` avec un contexte de simulation objet vous permet d’appeler la fonction dans tous vos tests unitaires sans avoir à construire un contexte factice chaque fois :</span><span class="sxs-lookup"><span data-stu-id="df3b9-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

```fsharp
namespace TransactionTests

open Xunit
open TransactionTypes
open TransactionsTestingUtil
open TransactionsTestingUtil.TransactionsTestable

let testableContext =
    { new ITransactionContext with
        member __.TheFirstMember() = ...
        member __.TheSecondMember() = ... }

let transactionRoutine = getTestableTransactionRoutine testableContext

[<Fact>]
let ``Test withdrawal transaction with 0.0 for balance``() =
    let expected = ...
    let actual = transactionRoutine TransactionType.Withdraw 0.0
    Assert.Equal(expected, actual)
```

<span data-ttu-id="df3b9-252">Cette technique ne doit pas être appliquée universellement à votre base de code entière, mais il est un bon moyen de réduire la réutilisation pour internals compliquée et ces éléments internes de tests unitaires.</span><span class="sxs-lookup"><span data-stu-id="df3b9-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="df3b9-253">Contrôle d'accès</span><span class="sxs-lookup"><span data-stu-id="df3b9-253">Access control</span></span>

<span data-ttu-id="df3b9-254">F#propose plusieurs options pour [contrôle d’accès](../language-reference/access-control.md), hérité de ce qui est disponible dans le runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="df3b9-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="df3b9-255">Ils ne sont pas simplement utilisables pour les types : vous pouvez les utiliser pour les fonctions, trop.</span><span class="sxs-lookup"><span data-stu-id="df3b9-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="df3b9-256">Préférez non -`public` types et membres jusqu'à ce que vous avez besoin pour être utilisable publiquement.</span><span class="sxs-lookup"><span data-stu-id="df3b9-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="df3b9-257">Cela réduit également les deux consommateurs à.</span><span class="sxs-lookup"><span data-stu-id="df3b9-257">This also minimizes what consumers couple to.</span></span>
* <span data-ttu-id="df3b9-258">Vous efforcer de garder toutes les fonctionnalités d’assistance `private`.</span><span class="sxs-lookup"><span data-stu-id="df3b9-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="df3b9-259">Envisagez d’utiliser `[<AutoOpen>]` sur un module privé de fonctions d’assistance si elles sont nombreuses.</span><span class="sxs-lookup"><span data-stu-id="df3b9-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="df3b9-260">Inférence de type et génériques</span><span class="sxs-lookup"><span data-stu-id="df3b9-260">Type inference and generics</span></span>

<span data-ttu-id="df3b9-261">Inférence de type peut vous faire gagner de la saisie d’un grand nombre de réutilisable.</span><span class="sxs-lookup"><span data-stu-id="df3b9-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="df3b9-262">Et la généralisation automatique dans le F# compilateur peut vous aider à écrire du code plus générique avec pratiquement aucun effort supplémentaire de votre part.</span><span class="sxs-lookup"><span data-stu-id="df3b9-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="df3b9-263">Toutefois, ces fonctionnalités ne sont pas universellement bonnes.</span><span class="sxs-lookup"><span data-stu-id="df3b9-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="df3b9-264">Envisagez d’étiqueter les noms des arguments avec des types explicites dans les API publiques et ne vous basez pas sur l’inférence de type pour cela.</span><span class="sxs-lookup"><span data-stu-id="df3b9-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="df3b9-265">La raison à cela est que **vous** doit se trouver dans le contrôle de la forme de votre API, pas le compilateur.</span><span class="sxs-lookup"><span data-stu-id="df3b9-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="df3b9-266">Bien que le compilateur peut effectuer un travail à l’inférence de types pour vous, il est possible d’avoir la forme de la modification de l’API si les données internes sur qu'il s’appuie ont été modifiés de types.</span><span class="sxs-lookup"><span data-stu-id="df3b9-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="df3b9-267">Il peut s’agir de ce que vous voulez, mais cela entraînerait certainement une modification d’API ayant des consommateurs en aval puis à gérer.</span><span class="sxs-lookup"><span data-stu-id="df3b9-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="df3b9-268">Au lieu de cela, si vous contrôlez explicitement la forme de votre API publique, vous pouvez contrôler ces modifications avec rupture.</span><span class="sxs-lookup"><span data-stu-id="df3b9-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="df3b9-269">En termes de conception pilotée par domaine, cela peut être représenté comme une couche de lutte contre la corruption.</span><span class="sxs-lookup"><span data-stu-id="df3b9-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="df3b9-270">Donnez un nom explicite pour vos arguments génériques.</span><span class="sxs-lookup"><span data-stu-id="df3b9-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="df3b9-271">Sauf si vous écrivez du code réellement générique qui n’est pas spécifique à un domaine particulier, un nom significatif peut aider d’autres programmeurs compréhension du domaine, qu'ils travaillent.</span><span class="sxs-lookup"><span data-stu-id="df3b9-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="df3b9-272">Par exemple, un paramètre de type nommé `'Document` dans le contexte de l’interaction avec un document de base de données plus clairement que les types de document générique peuvent être acceptés par la fonction ou le membre que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="df3b9-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="df3b9-273">Songez à nommer les paramètres de type générique avec la casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="df3b9-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="df3b9-274">Il s’agit du moyen général de faire des choses dans .NET, il est recommandé d’utiliser la casse Pascal plutôt que de snake_case ou de la casse mixte.</span><span class="sxs-lookup"><span data-stu-id="df3b9-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="df3b9-275">Enfin, la généralisation automatique n’est pas toujours une aubaine pour les personnes qui débutent avec F# ou un grand code base.</span><span class="sxs-lookup"><span data-stu-id="df3b9-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="df3b9-276">Il est nécessaire à l’aide de composants qui sont génériques.</span><span class="sxs-lookup"><span data-stu-id="df3b9-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="df3b9-277">En outre, si automatiquement généralisées fonctions ne sont pas utilisées avec différents types d’entrée (permettent uniquement si elles sont conçues pour être utilisé en tant que tel), alors il n’existe aucun avantage réel d’y être un générique à ce stade dans le temps.</span><span class="sxs-lookup"><span data-stu-id="df3b9-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="df3b9-278">Toujours prendre en compte si le code que vous écrivez est réellement avantage d’être générique.</span><span class="sxs-lookup"><span data-stu-id="df3b9-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="df3b9-279">Performances</span><span class="sxs-lookup"><span data-stu-id="df3b9-279">Performance</span></span>

<span data-ttu-id="df3b9-280">F#les valeurs sont immuables par défaut, ce qui vous permet d’éviter certaines catégories de bogues (en particulier les impliquant d’accès concurrentiel et parallélisme).</span><span class="sxs-lookup"><span data-stu-id="df3b9-280">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="df3b9-281">Toutefois, dans certains cas, afin d’obtenir une efficacité optimale (ou même raisonnable) de la durée d’exécution ou des allocations de mémoire, une étendue de travail peut-être mieux être implémentée à l’aide de mutation in situ d’état.</span><span class="sxs-lookup"><span data-stu-id="df3b9-281">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="df3b9-282">Cela est possible dans une base opt-in avec F# avec la `mutable` mot clé.</span><span class="sxs-lookup"><span data-stu-id="df3b9-282">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="df3b9-283">Toutefois, utiliser des `mutable` dans F# peuvent avoir l’impression ne correspond pas à pureté fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="df3b9-283">However, use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="df3b9-284">Ceci fonctionne bien, si vous ajustez les attentes à partir de la pureté [transparence référentielle](https://en.wikipedia.org/wiki/Referential_transparency).</span><span class="sxs-lookup"><span data-stu-id="df3b9-284">This is fine, if you adjust expectations from purity to [referential transparency](https://en.wikipedia.org/wiki/Referential_transparency).</span></span> <span data-ttu-id="df3b9-285">Transparence référentielle - pas pureté - est l’objectif final lors de l’écriture F# fonctions.</span><span class="sxs-lookup"><span data-stu-id="df3b9-285">Referential transparency - not purity - is the end goal when writing F# functions.</span></span> <span data-ttu-id="df3b9-286">Cela vous permet d’écrire une interface fonctionnelle par rapport à une implémentation basée sur une mutation pour le code critique de performances.</span><span class="sxs-lookup"><span data-stu-id="df3b9-286">This allows you to write a functional interface over a mutation-based implementation for performance critical code.</span></span>

### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="df3b9-287">Encapsuler le code mutable dans les interfaces immuables</span><span class="sxs-lookup"><span data-stu-id="df3b9-287">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="df3b9-288">Transparence référentielle en tant qu’objectif, il est essentiel d’écrire du code qui n’expose pas l’underbelly mutable de fonctions critiques pour les performances.</span><span class="sxs-lookup"><span data-stu-id="df3b9-288">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="df3b9-289">Par exemple, le code suivant implémente la `Array.contains` fonctionner dans le F# bibliothèque principale :</span><span class="sxs-lookup"><span data-stu-id="df3b9-289">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

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

<span data-ttu-id="df3b9-290">Appeler cette fonction plusieurs fois ne modifie pas le tableau sous-jacent, et il vous oblige à conserver un état mutable dans sa consommation.</span><span class="sxs-lookup"><span data-stu-id="df3b9-290">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="df3b9-291">Il est assortie transparent, même si presque à chaque ligne de code qu’il contient utilise mutation.</span><span class="sxs-lookup"><span data-stu-id="df3b9-291">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="df3b9-292">Envisagez d’encapsuler des données mutables dans les classes</span><span class="sxs-lookup"><span data-stu-id="df3b9-292">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="df3b9-293">L’exemple précédent utilisait une seule fonction pour encapsuler des opérations à l’aide de données mutables.</span><span class="sxs-lookup"><span data-stu-id="df3b9-293">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="df3b9-294">Cela n’est pas toujours suffisant pour les jeux de données plus complexes.</span><span class="sxs-lookup"><span data-stu-id="df3b9-294">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="df3b9-295">Tenez compte des ensembles de fonctions suivants :</span><span class="sxs-lookup"><span data-stu-id="df3b9-295">Consider the following sets of functions:</span></span>

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

<span data-ttu-id="df3b9-296">Ce code est performante, mais elle expose la structure de données basées sur une mutation que les appelants sont responsables de la maintenance.</span><span class="sxs-lookup"><span data-stu-id="df3b9-296">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="df3b9-297">Cela peut être encapsulée à l’intérieur d’une classe sans membres sous-jacentes qui peuvent changer :</span><span class="sxs-lookup"><span data-stu-id="df3b9-297">This can be wrapped inside of a class with no underlying members that can change:</span></span>

```fsharp
open System.Collections.Generic

/// The results of computing the LALR(1) closure of an LR(0) kernel
type Closure1Table() =
    let t = Dictionary<Item0, HashSet<TerminalIndex>>()

    member __.Add(key, value) =
        if not (t.ContainsKey(key)) then
            t.Add(key, value)
        else
            t.[key] <- value

    member __.Count = t.Count

    member __.Contains(key, value) =
        match t.TryGetValue(key) with
        | (true, v) -> v.Equals(value)
        | (false, _) -> false
```

<span data-ttu-id="df3b9-298">`Closure1Table` encapsule la structure de données basées sur une mutation sous-jacente, ce qui n’est ne pas forcé aux appelants de maintenir la structure de données sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="df3b9-298">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="df3b9-299">Les classes sont un moyen efficace d’encapsuler des données et les routines qui ne sont mutation sans exposer les détails aux appelants.</span><span class="sxs-lookup"><span data-stu-id="df3b9-299">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="df3b9-300">Préférez `let mutable` aux cellules de référence</span><span class="sxs-lookup"><span data-stu-id="df3b9-300">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="df3b9-301">Cellules de référence sont un moyen pour représenter la référence à une valeur plutôt que la valeur elle-même.</span><span class="sxs-lookup"><span data-stu-id="df3b9-301">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="df3b9-302">Même si elles peuvent servir pour le code critique pour les performances, ils sont généralement pas recommandés.</span><span class="sxs-lookup"><span data-stu-id="df3b9-302">Although they can be used for performance-critical code, they are generally not recommended.</span></span> <span data-ttu-id="df3b9-303">Prenons l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="df3b9-303">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="df3b9-304">L’utilisation d’une cellule de référence est maintenant « pollue « tout le code suivant à la déréférencer et re-référencer les données sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="df3b9-304">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="df3b9-305">Envisagez plutôt de `let mutable`:</span><span class="sxs-lookup"><span data-stu-id="df3b9-305">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="df3b9-306">Outre le point unique de mutation au milieu de l’expression lambda, tout autre code qui touche `acc` pouvez le faire d’une manière qui est similaire à l’utilisation d’un élément normal `let`-immuable valeur limite.</span><span class="sxs-lookup"><span data-stu-id="df3b9-306">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="df3b9-307">Cela rend plus facile à modifier au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="df3b9-307">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="df3b9-308">Programmation de l’objet</span><span class="sxs-lookup"><span data-stu-id="df3b9-308">Object programming</span></span>

<span data-ttu-id="df3b9-309">F#a une prise en charge complète pour les objets et concepts (OO) orientée objet.</span><span class="sxs-lookup"><span data-stu-id="df3b9-309">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="df3b9-310">Bien que de nombreux concepts OO sont puissants et utiles, certaines d'entre elles sont idéales à utiliser.</span><span class="sxs-lookup"><span data-stu-id="df3b9-310">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="df3b9-311">Les listes suivantes proposent des conseils sur les catégories de fonctionnalités OO à un niveau élevé.</span><span class="sxs-lookup"><span data-stu-id="df3b9-311">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="df3b9-312">**Envisagez d’utiliser ces fonctionnalités dans de nombreuses situations :**</span><span class="sxs-lookup"><span data-stu-id="df3b9-312">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="df3b9-313">Notation par points (`x.Length`)</span><span class="sxs-lookup"><span data-stu-id="df3b9-313">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="df3b9-314">Membres d’instance</span><span class="sxs-lookup"><span data-stu-id="df3b9-314">Instance members</span></span>
* <span data-ttu-id="df3b9-315">Constructeurs implicites</span><span class="sxs-lookup"><span data-stu-id="df3b9-315">Implicit constructors</span></span>
* <span data-ttu-id="df3b9-316">Membres static</span><span class="sxs-lookup"><span data-stu-id="df3b9-316">Static members</span></span>
* <span data-ttu-id="df3b9-317">Notation d’indexeur (`arr.[x]`)</span><span class="sxs-lookup"><span data-stu-id="df3b9-317">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="df3b9-318">Arguments nommés et facultatifs</span><span class="sxs-lookup"><span data-stu-id="df3b9-318">Named and Optional arguments</span></span>
* <span data-ttu-id="df3b9-319">Interfaces et implémentations d’interface</span><span class="sxs-lookup"><span data-stu-id="df3b9-319">Interfaces and interface implementations</span></span>

<span data-ttu-id="df3b9-320">**N’atteignent pas tout d’abord pour ces fonctionnalités, mais judicieusement appliquent les lorsqu’ils sont pratiques résoudre un problème :**</span><span class="sxs-lookup"><span data-stu-id="df3b9-320">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="df3b9-321">Surcharge de méthode</span><span class="sxs-lookup"><span data-stu-id="df3b9-321">Method overloading</span></span>
* <span data-ttu-id="df3b9-322">Données mutables encapsulées</span><span class="sxs-lookup"><span data-stu-id="df3b9-322">Encapsulated mutable data</span></span>
* <span data-ttu-id="df3b9-323">Opérateurs sur les types</span><span class="sxs-lookup"><span data-stu-id="df3b9-323">Operators on types</span></span>
* <span data-ttu-id="df3b9-324">Propriétés automatiques</span><span class="sxs-lookup"><span data-stu-id="df3b9-324">Auto properties</span></span>
* <span data-ttu-id="df3b9-325">Implémentation `IDisposable` et `IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="df3b9-325">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="df3b9-326">Extensions de type</span><span class="sxs-lookup"><span data-stu-id="df3b9-326">Type extensions</span></span>
* <span data-ttu-id="df3b9-327">Événements</span><span class="sxs-lookup"><span data-stu-id="df3b9-327">Events</span></span>
* <span data-ttu-id="df3b9-328">Structs</span><span class="sxs-lookup"><span data-stu-id="df3b9-328">Structs</span></span>
* <span data-ttu-id="df3b9-329">Délégués</span><span class="sxs-lookup"><span data-stu-id="df3b9-329">Delegates</span></span>
* <span data-ttu-id="df3b9-330">Enums</span><span class="sxs-lookup"><span data-stu-id="df3b9-330">Enums</span></span>

<span data-ttu-id="df3b9-331">**Généralement éviter ces fonctionnalités, sauf si vous devez les utiliser :**</span><span class="sxs-lookup"><span data-stu-id="df3b9-331">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="df3b9-332">Hiérarchies de type basé sur l’héritage et l’héritage d’implémentation</span><span class="sxs-lookup"><span data-stu-id="df3b9-332">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="df3b9-333">Les valeurs NULL et `Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="df3b9-333">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="df3b9-334">Préférer composition de l’héritage</span><span class="sxs-lookup"><span data-stu-id="df3b9-334">Prefer composition over inheritance</span></span>

<span data-ttu-id="df3b9-335">[Composition au fil de l’héritage](https://en.wikipedia.org/wiki/Composition_over_inheritance) est un idiome de longue date aussi simple que ça F# code peut respecter.</span><span class="sxs-lookup"><span data-stu-id="df3b9-335">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="df3b9-336">Le principe fondamental est que vous ne devez pas exposer une classe de base et forcer les appelants d’hériter de cette classe de base pour obtenir les fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="df3b9-336">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="df3b9-337">Utiliser des expressions d’objet pour implémenter les interfaces si vous n’avez pas besoin d’une classe</span><span class="sxs-lookup"><span data-stu-id="df3b9-337">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="df3b9-338">[Expressions d’objet](../language-reference/object-expressions.md) vous permettent d’implémenter des interfaces à la volée, liant l’interface implémentée à une valeur sans avoir à le faire à l’intérieur d’une classe.</span><span class="sxs-lookup"><span data-stu-id="df3b9-338">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="df3b9-339">C’est pratique, surtout si vous _uniquement_ devez implémenter l’interface et n’avez pas besoin d’une classe complète.</span><span class="sxs-lookup"><span data-stu-id="df3b9-339">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="df3b9-340">Par exemple, voici le code qui est exécuté dans [Ionide](http://ionide.io/) pour fournir une action de correction de code si vous avez ajouté un symbole que vous n’avez pas un `open` instruction pour :</span><span class="sxs-lookup"><span data-stu-id="df3b9-340">For example, here is the code that is run in [Ionide](http://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

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

<span data-ttu-id="df3b9-341">Car il n’est pas nécessaire pour une classe lors de l’interaction avec l’API de Code Visual Studio, les Expressions d’objet sont un outil idéal pour cela.</span><span class="sxs-lookup"><span data-stu-id="df3b9-341">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="df3b9-342">Ils sont également utiles pour tests unitaires, lorsque vous souhaitez remplacer une interface avec des routines de test de manière ad hoc.</span><span class="sxs-lookup"><span data-stu-id="df3b9-342">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="type-abbreviations"></a><span data-ttu-id="df3b9-343">Abréviations de types</span><span class="sxs-lookup"><span data-stu-id="df3b9-343">Type Abbreviations</span></span>

<span data-ttu-id="df3b9-344">[Abréviations de types](../language-reference/type-abbreviations.md) sont un moyen pratique d’attribuer une étiquette à un autre type, par exemple une signature de fonction ou un type plus complexe.</span><span class="sxs-lookup"><span data-stu-id="df3b9-344">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="df3b9-345">Par exemple, l’alias suivant attribue une étiquette pour ce qui est nécessaire pour définir un calcul avec [CNTK](https://docs.microsoft.com/cognitive-toolkit/), une bibliothèque d’apprentissage approfondi :</span><span class="sxs-lookup"><span data-stu-id="df3b9-345">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://docs.microsoft.com/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="df3b9-346">Le `Computation` nom est un moyen pratique pour désigner n’importe quelle fonction qui correspond à la signature sont les alias.</span><span class="sxs-lookup"><span data-stu-id="df3b9-346">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="df3b9-347">À l’aide des abréviations de types, comme cela est pratique et autorise le code plus concise.</span><span class="sxs-lookup"><span data-stu-id="df3b9-347">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="df3b9-348">Évitez d’utiliser des abréviations de Type pour représenter votre domaine</span><span class="sxs-lookup"><span data-stu-id="df3b9-348">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="df3b9-349">Bien que les abréviations de Type sont pratiques pour donner un nom pour les signatures de fonction, ils peuvent prêter à confus lors de l’abréviation d’autres types.</span><span class="sxs-lookup"><span data-stu-id="df3b9-349">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="df3b9-350">Prenez en compte cette abréviation :</span><span class="sxs-lookup"><span data-stu-id="df3b9-350">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="df3b9-351">Cela peut prêter à confusion de plusieurs façons :</span><span class="sxs-lookup"><span data-stu-id="df3b9-351">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="df3b9-352">`BufferSize` n’est pas une abstraction ; C’est juste un autre nom d’un entier.</span><span class="sxs-lookup"><span data-stu-id="df3b9-352">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="df3b9-353">Si `BufferSize` est exposé dans une API publique, il peut facilement être interprété à tort comme signifiant plus que `int`.</span><span class="sxs-lookup"><span data-stu-id="df3b9-353">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="df3b9-354">En règle générale, les types de domaine d’avoir plusieurs attributs leur et ne sont pas des types primitifs comme `int`.</span><span class="sxs-lookup"><span data-stu-id="df3b9-354">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="df3b9-355">Cette abréviation enfreint cette hypothèse.</span><span class="sxs-lookup"><span data-stu-id="df3b9-355">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="df3b9-356">La casse de `BufferSize` (la casse Pascal) implique que ce type conserve plus de données.</span><span class="sxs-lookup"><span data-stu-id="df3b9-356">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="df3b9-357">Cet alias n’offre pas de davantage de clarté par rapport à fournir un argument nommé à une fonction.</span><span class="sxs-lookup"><span data-stu-id="df3b9-357">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="df3b9-358">L’abréviation se manifeste pas dans le IL compilé ; Il s’agit simplement d’un entier, et cet alias est une construction de compilation.</span><span class="sxs-lookup"><span data-stu-id="df3b9-358">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

<span data-ttu-id="df3b9-359">En résumé, l’inconvénient avec les abréviations de Type est qu’ils sont **pas** abstractions sur les types qu’ils sont abréviation.</span><span class="sxs-lookup"><span data-stu-id="df3b9-359">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="df3b9-360">Dans l’exemple précédent, `BufferSize` est simplement un `int` en coulisses, avec des données supplémentaires, ni aucun avantage à partir du système de type en dehors de ce que `int` possède déjà.</span><span class="sxs-lookup"><span data-stu-id="df3b9-360">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>
