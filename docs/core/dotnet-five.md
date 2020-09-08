---
title: Évolution de .NET Core vers .NET 5
description: Découvrez .NET 5, une plateforme de développement multiplateforme et open source qui est la prochaine évolution de .NET Core.
ms.date: 09/02/2020
ms.topic: overview
ms.author: dapine
author: IEvangelist
ms.openlocfilehash: 5e8ed371173ff8b81909ceb071ed93c6b0e1eea5
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89515842"
---
# <a name="the-evolution-of-net-core-to-net-5"></a><span data-ttu-id="50018-103">Évolution de .NET Core vers .NET 5</span><span class="sxs-lookup"><span data-stu-id="50018-103">The evolution of .NET Core to .NET 5</span></span>

<span data-ttu-id="50018-104">Cet article détaille ce qui est inclus dans .NET 5, qui est la prochaine version de .NET Core suivant 3,1.</span><span class="sxs-lookup"><span data-stu-id="50018-104">This article details what is included in .NET 5, which is the next release of .NET Core following 3.1.</span></span> <span data-ttu-id="50018-105">Le numéro de version est 5,0 pour éviter toute confusion avec .NET Framework 4. x.</span><span class="sxs-lookup"><span data-stu-id="50018-105">The version number is 5.0 to avoid confusion with .NET Framework 4.x.</span></span> <span data-ttu-id="50018-106">« Core » est supprimé du nom, car il s’agit de l’implémentation principale de .NET à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="50018-106">And "Core" is dropped from the name because it is the main implementation of .NET going forward.</span></span> <span data-ttu-id="50018-107">ASP.NET Core conserve le nom « Core » pour éviter qu’il ne soit confus avec ASP.NET MVC 5.</span><span class="sxs-lookup"><span data-stu-id="50018-107">ASP.NET Core retains the name "Core" to avoid confusing it with ASP.NET MVC 5.</span></span> <span data-ttu-id="50018-108">En outre, Entity Framework Core conserve le nom « Core » pour éviter qu’il ne soit confus avec Entity Framework 5 et 6.</span><span class="sxs-lookup"><span data-stu-id="50018-108">Additionally, Entity Framework Core retains the name "Core" to avoid confusing it with Entity Framework 5 and 6.</span></span> <span data-ttu-id="50018-109">.NET 5 prend en charge davantage de types d’applications et de plateformes que .NET Core ou .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="50018-109">.NET 5 supports more types of apps and more platforms than .NET Core or .NET Framework.</span></span>

<span data-ttu-id="50018-110">L’avènement de .NET Core a évolué l’écosystème .NET de manière attrayante.</span><span class="sxs-lookup"><span data-stu-id="50018-110">The advent of .NET Core has evolved the .NET ecosystem in compelling ways.</span></span> <span data-ttu-id="50018-111">Il a évolué en tant que projet open source sur GitHub, célébrant les contributions de la communauté et remarquer amélioré au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="50018-111">It matured as an open-source project on GitHub, celebrating community contributions, and humbly improving over time.</span></span>

<span data-ttu-id="50018-112">.NET Core présente plusieurs caractéristiques principales :</span><span class="sxs-lookup"><span data-stu-id="50018-112">.NET Core has several primary characteristics:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="50018-113">Système multiplateforme</span><span class="sxs-lookup"><span data-stu-id="50018-113">Cross-platform</span></span>
> - <span data-ttu-id="50018-114">Open source</span><span class="sxs-lookup"><span data-stu-id="50018-114">Open-source</span></span>
> - <span data-ttu-id="50018-115">Installation côte à côte</span><span class="sxs-lookup"><span data-stu-id="50018-115">Side-by-side installation</span></span>
> - <span data-ttu-id="50018-116">Petits fichiers de projet (style SDK)</span><span class="sxs-lookup"><span data-stu-id="50018-116">Small project files (SDK-style)</span></span>
> - <span data-ttu-id="50018-117">Déploiement flexible</span><span class="sxs-lookup"><span data-stu-id="50018-117">Flexible deployment</span></span>

<span data-ttu-id="50018-118">.NET 5 étend ces caractéristiques, ce qui apporte des améliorations incrémentielles :</span><span class="sxs-lookup"><span data-stu-id="50018-118">.NET 5 extends these characteristics, making incremental improvements:</span></span>

- <span data-ttu-id="50018-119">Applications à fichier unique</span><span class="sxs-lookup"><span data-stu-id="50018-119">Single file apps</span></span>
- <span data-ttu-id="50018-120">Intrinsèques Windows ARM64 et ARM64</span><span class="sxs-lookup"><span data-stu-id="50018-120">Windows ARM64, and ARM64 intrinsics</span></span>
- <span data-ttu-id="50018-121">Amélioration des performances :</span><span class="sxs-lookup"><span data-stu-id="50018-121">Sweeping performance improvements to:</span></span>
  - [<span data-ttu-id="50018-122">Garbage collection (GC)</span><span class="sxs-lookup"><span data-stu-id="50018-122">Garbage Collection (GC)</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#gc)
  - [<span data-ttu-id="50018-123">System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="50018-123">System.Text.Json</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#json)
  - [<span data-ttu-id="50018-124">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="50018-124">System.Text.RegularExpressions</span></span>](https://devblogs.microsoft.com/dotnet/regex-performance-improvements-in-net-5)
  - [<span data-ttu-id="50018-125">Regroupement ValueTask asynchrone</span><span class="sxs-lookup"><span data-stu-id="50018-125">Async ValueTask pooling</span></span>](https://devblogs.microsoft.com/dotnet/async-valuetask-pooling-in-net-5)
  - [<span data-ttu-id="50018-126">Beaucoup plus de zones</span><span class="sxs-lookup"><span data-stu-id="50018-126">Many more areas</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
- <span data-ttu-id="50018-127">Optimisations de la taille du conteneur</span><span class="sxs-lookup"><span data-stu-id="50018-127">Container size optimizations</span></span>
- [<span data-ttu-id="50018-128">Suppression d’application</span><span class="sxs-lookup"><span data-stu-id="50018-128">App trimming</span></span>](https://devblogs.microsoft.com/dotnet/app-trimming-in-net-5)
- [<span data-ttu-id="50018-129">Améliorations du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="50018-129">C# compiler enhancements</span></span>](https://devblogs.microsoft.com/dotnet/automatically-find-latent-bugs-in-your-code-with-net-5)
- <span data-ttu-id="50018-130">Prise en charge des outils pour le débogage de vidage</span><span class="sxs-lookup"><span data-stu-id="50018-130">Tooling support for dump debugging</span></span>
- <span data-ttu-id="50018-131">La plateforme est 80% annotée pour les [types de référence Nullable](../csharp/nullable-references.md)</span><span class="sxs-lookup"><span data-stu-id="50018-131">Platform is 80% annotated for [nullable reference types](../csharp/nullable-references.md)</span></span>

### <a name="what-net-5-is-not"></a><span data-ttu-id="50018-132">Ce que .NET 5 n’est pas</span><span class="sxs-lookup"><span data-stu-id="50018-132">What .NET 5 is not</span></span>

<span data-ttu-id="50018-133">.NET 5 n’est pas un substitut pour .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="50018-133">.NET 5 is not a replacement for .NET Framework.</span></span> <span data-ttu-id="50018-134">Il n’est pas prévu de porter les technologies suivantes de .NET Framework vers .NET 5, mais il existe des alternatives prises en charge incluses dans .NET 5 :</span><span class="sxs-lookup"><span data-stu-id="50018-134">There are no plans to port the following technologies from .NET Framework to .NET 5, but there are supported alternatives included in .NET 5:</span></span>

| <span data-ttu-id="50018-135">Technologie</span><span class="sxs-lookup"><span data-stu-id="50018-135">Technology</span></span>                             | <span data-ttu-id="50018-136">Recommandation</span><span class="sxs-lookup"><span data-stu-id="50018-136">Recommendation</span></span>                                              |
|----------------------------------------|-------------------------------------------------------------|
| <span data-ttu-id="50018-137">Web Forms</span><span class="sxs-lookup"><span data-stu-id="50018-137">Web Forms</span></span>                              | [<span data-ttu-id="50018-138">ASP.NET Core éblouissant</span><span class="sxs-lookup"><span data-stu-id="50018-138">ASP.NET Core Blazor</span></span>](/aspnet/core/blazor)                  |
| <span data-ttu-id="50018-139">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="50018-139">Windows Communication Foundation (WCF)</span></span> | [<span data-ttu-id="50018-140">gRPC</span><span class="sxs-lookup"><span data-stu-id="50018-140">gRPC</span></span>](/aspnet/core/grpc)                                   |
| <span data-ttu-id="50018-141">Windows Workflow (WF)</span><span class="sxs-lookup"><span data-stu-id="50018-141">Windows Workflow (WF)</span></span>                  | [<span data-ttu-id="50018-142">CoreWF Open source</span><span class="sxs-lookup"><span data-stu-id="50018-142">Open-source CoreWF</span></span>](https://github.com/UiPath-Open/corewf) |

## <a name="net-standard"></a><span data-ttu-id="50018-143">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="50018-143">.NET Standard</span></span>

<span data-ttu-id="50018-144">Le développement d’une nouvelle application peut spécifier le `net5.0` moniker du Framework cible (TFM) pour tous les types de projets, y compris les bibliothèques de classes.</span><span class="sxs-lookup"><span data-stu-id="50018-144">New application development can specify the `net5.0` target framework moniker (TFM) for all project types, including class libraries.</span></span> <span data-ttu-id="50018-145">Le partage de code entre les charges de travail .NET 5 est simplifié en ce que vous avez tout ce dont vous avez besoin `net5.0` TFM.</span><span class="sxs-lookup"><span data-stu-id="50018-145">Sharing code between .NET 5 workloads is simplified in that all you need is the `net5.0` TFM.</span></span>

<span data-ttu-id="50018-146">Le `net5.0` TFM combine et remplace `netcoreapp` les `netstandard` noms.</span><span class="sxs-lookup"><span data-stu-id="50018-146">The `net5.0` TFM combines and replaces `netcoreapp` and `netstandard` names.</span></span> <span data-ttu-id="50018-147">Ce TFM inclut généralement des technologies qui fonctionnent sur plusieurs plateformes, comme c’est le cas avec .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="50018-147">This TFM will generally only include technologies that work cross-platform, like was done with .NET Standard.</span></span> <span data-ttu-id="50018-148">Toutefois, si vous envisagez de partager du code entre des charges de travail de .NET Framework, .NET Core et .NET 5, vous pouvez le faire en spécifiant `netstandard2.0` comme TFM.</span><span class="sxs-lookup"><span data-stu-id="50018-148">However, if you're planning on sharing code between .NET Framework, .NET Core, and .NET 5 workloads - you can do so by specifying `netstandard2.0` as your TFM.</span></span> <span data-ttu-id="50018-149">Pour plus d’informations, consultez [comment spécifier des frameworks cibles](../standard/frameworks.md#how-to-specify-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="50018-149">For more information, see [How to specify target frameworks](../standard/frameworks.md#how-to-specify-target-frameworks).</span></span>

## <a name="language-updates"></a><span data-ttu-id="50018-150">Mises à jour du langage</span><span class="sxs-lookup"><span data-stu-id="50018-150">Language updates</span></span>

<span data-ttu-id="50018-151">Avec .NET 5, les langages de programmation .NET continuent à s’améliorer.</span><span class="sxs-lookup"><span data-stu-id="50018-151">With .NET 5, the .NET programming languages are continuing to improve.</span></span>

### <a name="c-updates"></a><span data-ttu-id="50018-152">Mises à jour C#</span><span class="sxs-lookup"><span data-stu-id="50018-152">C# updates</span></span>

<span data-ttu-id="50018-153">Les développeurs qui écrivent des applications .NET 5 auront accès à la version et aux fonctionnalités C# les plus récentes.</span><span class="sxs-lookup"><span data-stu-id="50018-153">Developers writing .NET 5 apps will have access to the latest C# version and features.</span></span> <span data-ttu-id="50018-154">.NET 5 est associé à C# 9.</span><span class="sxs-lookup"><span data-stu-id="50018-154">.NET 5 is paired with C# 9.</span></span> <span data-ttu-id="50018-155">C# 9 apporte de nombreuses nouvelles fonctionnalités au langage. Voici quelques points importants :</span><span class="sxs-lookup"><span data-stu-id="50018-155">C# 9 brings many new features to the language, here are a few highlights:</span></span>

- <span data-ttu-id="50018-156">Enregistrements : types référence immuables qui se comportent comme des types valeur et introduisent le nouveau `with` mot clé dans le langage.</span><span class="sxs-lookup"><span data-stu-id="50018-156">Records: Immutable reference types that behave like value types, and introduce the new `with` keyword into the language.</span></span>
- <span data-ttu-id="50018-157">Critères spéciaux relationnels : étend les fonctionnalités de critères spéciaux aux opérateurs relationnels pour les évaluations comparatives et les expressions, y compris les modèles logiques, les nouveaux mots clés `and` , `or` et `not` .</span><span class="sxs-lookup"><span data-stu-id="50018-157">Relational pattern matching: Extends pattern matching capabilities to relational operators for comparative evaluations and expressions, including logical patterns - new keywords `and`, `or`, and `not`.</span></span>
- <span data-ttu-id="50018-158">Instructions de niveau supérieur : comme un moyen d’accélérer l’adoption et l’apprentissage de C#, la `Main` méthode peut être omise et l’application est aussi simple que les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="50018-158">Top-level statements: As a means for accelerating adoption and learning of C#, the `Main` method can be omitted and application as simple as the following is valid:</span></span>

   ```csharp
   System.Console.Write("Hello world!");
   ```

- <span data-ttu-id="50018-159">Pointeurs fonction : constructions de langage qui exposent les OpCodes de langage intermédiaire (IL) suivants : `ldftn` et `calli` .</span><span class="sxs-lookup"><span data-stu-id="50018-159">Function pointers: Language constructs that expose the following intermediate language (IL) opcodes: `ldftn` and `calli`.</span></span>

<span data-ttu-id="50018-160">Pour plus d’informations sur les fonctionnalités C# 9 disponibles, consultez [Nouveautés de c# 9](../csharp/whats-new/csharp-9.md).</span><span class="sxs-lookup"><span data-stu-id="50018-160">For more information on the available C# 9 features, see [What's new in C# 9](../csharp/whats-new/csharp-9.md).</span></span>

#### <a name="source-generators"></a><span data-ttu-id="50018-161">Générateurs de sources</span><span class="sxs-lookup"><span data-stu-id="50018-161">Source generators</span></span>

<span data-ttu-id="50018-162">En plus de certaines des nouvelles fonctionnalités en C#, les générateurs de code source s’intègrent dans des projets de développement.</span><span class="sxs-lookup"><span data-stu-id="50018-162">In addition to some of the highlighted new C# features, source generators are making their way into developer projects.</span></span> <span data-ttu-id="50018-163">Les générateurs de source autorisent le code qui s’exécute pendant la compilation à inspecter votre programme et à produire des fichiers supplémentaires qui sont compilés avec le reste de votre code.</span><span class="sxs-lookup"><span data-stu-id="50018-163">Source generators allow code that runs during compilation to inspect your program and produce additional files that are compiled together with the rest of your code.</span></span>

<span data-ttu-id="50018-164">Pour plus d’informations sur les générateurs de source, consultez [Présentation des générateurs de source c#](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) et [exemples de générateur de source c#](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples).</span><span class="sxs-lookup"><span data-stu-id="50018-164">For more information on source generators, see [Introducing C# source generators](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) and [C# source generator samples](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples).</span></span>

### <a name="f-updates"></a><span data-ttu-id="50018-165">Mises à jour de F #</span><span class="sxs-lookup"><span data-stu-id="50018-165">F# updates</span></span>

<span data-ttu-id="50018-166">F # est le langage de programmation fonctionnel .NET et, avec .NET 5, les développeurs ont accès à F # 5.</span><span class="sxs-lookup"><span data-stu-id="50018-166">F# is the .NET functional programming language, and with .NET 5, developers have access to F# 5.</span></span> <span data-ttu-id="50018-167">Voici plusieurs nouvelles fonctionnalités de F # 5 :</span><span class="sxs-lookup"><span data-stu-id="50018-167">Here are several new features of F# 5:</span></span>

#### <a name="interpolated-strings"></a><span data-ttu-id="50018-168">Chaînes interpolées</span><span class="sxs-lookup"><span data-stu-id="50018-168">Interpolated strings</span></span>

<span data-ttu-id="50018-169">Semblable à la chaîne interpolée en C#, et même JavaScript-F # prend en charge l’interpolation de chaîne de base.</span><span class="sxs-lookup"><span data-stu-id="50018-169">Similar to interpolated string in C#, and even JavaScript - F# supports basic string interpolation.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"{name} is {age} years old."
```

<span data-ttu-id="50018-170">Outre l’interpolation de chaîne de base, il existe une interpolation typée.</span><span class="sxs-lookup"><span data-stu-id="50018-170">In addition to basic string interpolation, there is typed interpolation.</span></span> <span data-ttu-id="50018-171">Avec l’interpolation typée, un type donné doit correspondre au spécificateur de format.</span><span class="sxs-lookup"><span data-stu-id="50018-171">With typed interpolation, a given type must match the format specifier.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"%s{name} is %d{age} years old."
```

<span data-ttu-id="50018-172">Cela est similaire à la [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) fonction qui met en forme une chaîne en fonction des entrées de type sécurisé.</span><span class="sxs-lookup"><span data-stu-id="50018-172">This is similar to the [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) function that formats a string based on type-safe inputs.</span></span> <!-- For more information, see [What's new in F# 5](fsharp/whats-new/fsharp-50.md). -->

### <a name="visual-basic-updates"></a><span data-ttu-id="50018-173">Mises à jour de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="50018-173">Visual Basic updates</span></span>

<span data-ttu-id="50018-174">Il n’existe aucune nouvelle fonctionnalité de langage pour Visual Basic dans .NET 5.</span><span class="sxs-lookup"><span data-stu-id="50018-174">There are no new language features for Visual Basic in .NET 5.</span></span> <span data-ttu-id="50018-175">Toutefois, avec .NET 5, la prise en charge Visual Basic est étendue à :</span><span class="sxs-lookup"><span data-stu-id="50018-175">However, with .NET 5, Visual Basic support is extended to:</span></span>

| <span data-ttu-id="50018-176">Description</span><span class="sxs-lookup"><span data-stu-id="50018-176">Description</span></span>                            | <span data-ttu-id="50018-177">Paramètre `dotnet new`</span><span class="sxs-lookup"><span data-stu-id="50018-177">`dotnet new` parameter</span></span> |
|----------------------------------------|------------------------|
| <span data-ttu-id="50018-178">Application console</span><span class="sxs-lookup"><span data-stu-id="50018-178">Console Application</span></span>                    | `console`              |
| <span data-ttu-id="50018-179">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="50018-179">Class library</span></span>                          | `classlib`             |
| <span data-ttu-id="50018-180">Application WPF</span><span class="sxs-lookup"><span data-stu-id="50018-180">WPF Application</span></span>                        | `wpf`                  |
| <span data-ttu-id="50018-181">Bibliothèque de classes WPF</span><span class="sxs-lookup"><span data-stu-id="50018-181">WPF Class library</span></span>                      | `wpflib`               |
| <span data-ttu-id="50018-182">Bibliothèque de contrôles personnalisés WPF</span><span class="sxs-lookup"><span data-stu-id="50018-182">WPF Custom Control Library</span></span>             | `wpfcustomcontrollib`  |
| <span data-ttu-id="50018-183">Bibliothèque de contrôles utilisateur WPF</span><span class="sxs-lookup"><span data-stu-id="50018-183">WPF User Control Library</span></span>               | `wpfusercontrollib`    |
| <span data-ttu-id="50018-184">Application Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="50018-184">Windows Forms (WinForms) Application</span></span>   | `winforms`             |
| <span data-ttu-id="50018-185">Bibliothèque de classes Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="50018-185">Windows Forms (WinForms) Class library</span></span> | `winformslib`          |
| <span data-ttu-id="50018-186">Projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="50018-186">Unit Test Project</span></span>                      | `mstest`               |
| <span data-ttu-id="50018-187">Projet de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="50018-187">NUnit 3 Test Project</span></span>                   | `nunit`                |
| <span data-ttu-id="50018-188">Élément de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="50018-188">NUnit 3 Test Item</span></span>                      | `nunit-test`           |
| <span data-ttu-id="50018-189">Projet de test xUnit</span><span class="sxs-lookup"><span data-stu-id="50018-189">xUnit Test Project</span></span>                     | `xunit`                |

<span data-ttu-id="50018-190">Pour plus d’informations sur les modèles de projet à partir de l’interface CLI .NET, consultez [`dotnet new`](tools/dotnet-new.md) .</span><span class="sxs-lookup"><span data-stu-id="50018-190">For more information on project templates from the .NET CLI, see [`dotnet new`](tools/dotnet-new.md).</span></span>

## <a name="net-maui"></a><span data-ttu-id="50018-191">MAUI .NET</span><span class="sxs-lookup"><span data-stu-id="50018-191">.NET MAUI</span></span>

<span data-ttu-id="50018-192">.NET MAUI est une évolution du Xamarin. Forms Toolkit de plus en plus populaire et est open source sur GitHub à l’adresse [dotnet/Maui](https://github.com/dotnet/maui).</span><span class="sxs-lookup"><span data-stu-id="50018-192">.NET MAUI is an evolution of the increasingly popular Xamarin.Forms toolkit, and is open-source on GitHub at [dotnet/maui](https://github.com/dotnet/maui).</span></span> <span data-ttu-id="50018-193">Avec .NET MAUI, le choix pour les développeurs .NET est simplifié, fournissant une pile unique qui prend en charge toutes les charges de travail modernes : Android, iOS, macOS et Windows.</span><span class="sxs-lookup"><span data-stu-id="50018-193">With .NET MAUI, the choice for .NET developers is simplified, providing a single stack that supports all modern workloads: Android, iOS, macOS, and Windows.</span></span> <span data-ttu-id="50018-194">Avec .NET MAUI, vous bénéficiez d’une expérience de développement de projet unique qui cible plusieurs plateformes et appareils.</span><span class="sxs-lookup"><span data-stu-id="50018-194">With .NET MAUI, you get a single project developer experience that targets multiple platforms and devices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="50018-195">.NET MAUI est en version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="50018-195">.NET MAUI is in early preview.</span></span> <span data-ttu-id="50018-196">Vous trouverez un exemple de code source sur [xamarin/net6-Samples](https://github.com/xamarin/net6-samples).</span><span class="sxs-lookup"><span data-stu-id="50018-196">Sample source code can be found at [xamarin/net6-samples](https://github.com/xamarin/net6-samples).</span></span>

### <a name="model-view-update-pattern"></a><span data-ttu-id="50018-197">Modèle Model-View-Update</span><span class="sxs-lookup"><span data-stu-id="50018-197">Model-View-Update pattern</span></span>

<span data-ttu-id="50018-198">Les développeurs aiment les modèles de développement modernes.</span><span class="sxs-lookup"><span data-stu-id="50018-198">Developers love modern development patterns.</span></span> <span data-ttu-id="50018-199">Une approche Fluent du développement de l’interface utilisateur, inspirée par « l’architecture Elm », est le modèle [Model-View-Update](https://elmprogramming.com/model-view-update-part-1.html) ou MVU.</span><span class="sxs-lookup"><span data-stu-id="50018-199">A fluent approach to UI development, inspired by "The Elm Architecture" is the [model-view-update](https://elmprogramming.com/model-view-update-part-1.html) or MVU pattern.</span></span> <span data-ttu-id="50018-200">MVU favorise un traitement unidirectionnel des données et de la gestion de l’État, ainsi qu’une expérience de développement Code First qui met à jour rapidement l’interface utilisateur en appliquant uniquement les modifications nécessaires.</span><span class="sxs-lookup"><span data-stu-id="50018-200">MVU promotes a one-way flow of data and state management, as well as a code-first development experience that rapidly updates the UI by applying only the changes necessary.</span></span>

<span data-ttu-id="50018-201">À titre d’exemple, considérez le compteur suivant écrit dans .NET MAUI à l’aide du modèle MVU :</span><span class="sxs-lookup"><span data-stu-id="50018-201">As an example, consider the following counter written in .NET MAUI using the MVU pattern:</span></span>

```csharp
readonly State<int> _count = 0;

[Body]
View body() => new StackLayout
{
    new Label("Welcome to .NET MAUI!"),
    new Button(
        () => $"You clicked {_count} times.",
        () => ++ _count.Value)
    )
};
```

<span data-ttu-id="50018-202">Pour plus d’informations, consultez la feuille de [route .net Maui](https://github.com/dotnet/maui/wiki/Roadmap)et présentation de l’article [.net Maui](https://devblogs.microsoft.com/dotnet/introducing-net-multi-platform-app-ui) .</span><span class="sxs-lookup"><span data-stu-id="50018-202">For more information, see the [.NET MAUI roadmap](https://github.com/dotnet/maui/wiki/Roadmap), and [Introducing .NET MAUI](https://devblogs.microsoft.com/dotnet/introducing-net-multi-platform-app-ui) article.</span></span>

## <a name="see-also"></a><span data-ttu-id="50018-203">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50018-203">See also</span></span>

- [<span data-ttu-id="50018-204">Le trajet vers un .NET</span><span class="sxs-lookup"><span data-stu-id="50018-204">The Journey to one .NET</span></span>](https://channel9.msdn.com/Events/Build/2020/BOD106)
- [<span data-ttu-id="50018-205">Améliorations des performances dans .NET 5</span><span class="sxs-lookup"><span data-stu-id="50018-205">Performance improvements in .NET 5</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
