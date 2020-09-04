---
title: Évolution de .NET Core vers .NET 5
description: Découvrez .NET 5, une plateforme de développement multiplateforme et open source qui est la prochaine évolution de .NET Core.
ms.date: 09/02/2020
ms.topic: overview
ms.author: dapine
author: IEvangelist
ms.openlocfilehash: f9fd0d09dbb65c2367ac268ea4a7055a299a7586
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89471988"
---
# <a name="the-evolution-of-net-core-to-net-5"></a><span data-ttu-id="8dd05-103">Évolution de .NET Core vers .NET 5</span><span class="sxs-lookup"><span data-stu-id="8dd05-103">The evolution of .NET Core to .NET 5</span></span>

<span data-ttu-id="8dd05-104">Cet article détaille ce qui est inclus dans .NET 5, qui est la prochaine version de .NET Core suivant 3,1.</span><span class="sxs-lookup"><span data-stu-id="8dd05-104">This article details what is included in .NET 5, which is the next release of .NET Core following 3.1.</span></span> <span data-ttu-id="8dd05-105">Le numéro de version est 5,0 pour éviter toute confusion avec .NET Framework 4. x.</span><span class="sxs-lookup"><span data-stu-id="8dd05-105">The version number is 5.0 to avoid confusion with .NET Framework 4.x.</span></span> <span data-ttu-id="8dd05-106">« Core » est supprimé du nom, car il s’agit de l’implémentation principale de .NET à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="8dd05-106">And "Core" is dropped from the name because it is the main implementation of .NET going forward.</span></span> <span data-ttu-id="8dd05-107">.NET 5 prend en charge davantage de types d’applications et de plateformes que .NET Core ou .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8dd05-107">.NET 5 supports more types of apps and more platforms than .NET Core or .NET Framework.</span></span>

<span data-ttu-id="8dd05-108">L’avènement de .NET Core a évolué l’écosystème .NET de manière attrayante.</span><span class="sxs-lookup"><span data-stu-id="8dd05-108">The advent of .NET Core has evolved the .NET ecosystem in compelling ways.</span></span> <span data-ttu-id="8dd05-109">Il a évolué en tant que projet open source sur GitHub, célébrant les contributions de la communauté et remarquer amélioré au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="8dd05-109">It matured as an open-source project on GitHub, celebrating community contributions, and humbly improving over time.</span></span>

<span data-ttu-id="8dd05-110">.NET Core présente plusieurs caractéristiques principales :</span><span class="sxs-lookup"><span data-stu-id="8dd05-110">.NET Core has several primary characteristics:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="8dd05-111">Système multiplateforme</span><span class="sxs-lookup"><span data-stu-id="8dd05-111">Cross-platform</span></span>
> - <span data-ttu-id="8dd05-112">Open source</span><span class="sxs-lookup"><span data-stu-id="8dd05-112">Open-source</span></span>
> - <span data-ttu-id="8dd05-113">Installation côte à côte</span><span class="sxs-lookup"><span data-stu-id="8dd05-113">Side-by-side installation</span></span>
> - <span data-ttu-id="8dd05-114">Petits fichiers de projet (style SDK)</span><span class="sxs-lookup"><span data-stu-id="8dd05-114">Small project files (SDK-style)</span></span>
> - <span data-ttu-id="8dd05-115">Déploiement flexible</span><span class="sxs-lookup"><span data-stu-id="8dd05-115">Flexible deployment</span></span>

<span data-ttu-id="8dd05-116">.NET 5 étend ces caractéristiques, ce qui apporte des améliorations incrémentielles :</span><span class="sxs-lookup"><span data-stu-id="8dd05-116">.NET 5 extends these characteristics, making incremental improvements:</span></span>

- <span data-ttu-id="8dd05-117">Applications à fichier unique</span><span class="sxs-lookup"><span data-stu-id="8dd05-117">Single file apps</span></span>
- <span data-ttu-id="8dd05-118">Intrinsèques Windows ARM64 et ARM64</span><span class="sxs-lookup"><span data-stu-id="8dd05-118">Windows ARM64, and ARM64 intrinsics</span></span>
- <span data-ttu-id="8dd05-119">Amélioration des performances :</span><span class="sxs-lookup"><span data-stu-id="8dd05-119">Sweeping performance improvements to:</span></span>
  - [<span data-ttu-id="8dd05-120">Garbage collection (GC)</span><span class="sxs-lookup"><span data-stu-id="8dd05-120">Garbage Collection (GC)</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#gc)
  - [<span data-ttu-id="8dd05-121">System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="8dd05-121">System.Text.Json</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#json)
  - [<span data-ttu-id="8dd05-122">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="8dd05-122">System.Text.RegularExpressions</span></span>](https://devblogs.microsoft.com/dotnet/regex-performance-improvements-in-net-5)
  - [<span data-ttu-id="8dd05-123">Regroupement ValueTask asynchrone</span><span class="sxs-lookup"><span data-stu-id="8dd05-123">Async ValueTask pooling</span></span>](https://devblogs.microsoft.com/dotnet/async-valuetask-pooling-in-net-5)
  - [<span data-ttu-id="8dd05-124">Beaucoup plus de zones</span><span class="sxs-lookup"><span data-stu-id="8dd05-124">Many more areas</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
- <span data-ttu-id="8dd05-125">Optimisations de la taille du conteneur</span><span class="sxs-lookup"><span data-stu-id="8dd05-125">Container size optimizations</span></span>
- [<span data-ttu-id="8dd05-126">Suppression d’application</span><span class="sxs-lookup"><span data-stu-id="8dd05-126">App trimming</span></span>](https://devblogs.microsoft.com/dotnet/app-trimming-in-net-5)
- [<span data-ttu-id="8dd05-127">Améliorations du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="8dd05-127">C# compiler enhancements</span></span>](https://devblogs.microsoft.com/dotnet/automatically-find-latent-bugs-in-your-code-with-net-5)
- <span data-ttu-id="8dd05-128">Prise en charge des outils pour le débogage de vidage</span><span class="sxs-lookup"><span data-stu-id="8dd05-128">Tooling support for dump debugging</span></span>
- <span data-ttu-id="8dd05-129">La plateforme est 80% annotée pour les [types de référence Nullable](csharp/nullable-references.md)</span><span class="sxs-lookup"><span data-stu-id="8dd05-129">Platform is 80% annotated for [nullable reference types](csharp/nullable-references.md)</span></span>

### <a name="what-net-5-is-not"></a><span data-ttu-id="8dd05-130">Ce que .NET 5 n’est pas</span><span class="sxs-lookup"><span data-stu-id="8dd05-130">What .NET 5 is not</span></span>

<span data-ttu-id="8dd05-131">.NET 5 n’est pas un substitut pour .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8dd05-131">.NET 5 is not a replacement for .NET Framework.</span></span> <span data-ttu-id="8dd05-132">Il n’est pas prévu de porter les technologies suivantes de .NET Framework vers .NET 5, mais il existe des alternatives prises en charge incluses dans .NET 5 :</span><span class="sxs-lookup"><span data-stu-id="8dd05-132">There are no plans to port the following technologies from .NET Framework to .NET 5, but there are supported alternatives included in .NET 5:</span></span>

| <span data-ttu-id="8dd05-133">Technologie</span><span class="sxs-lookup"><span data-stu-id="8dd05-133">Technology</span></span>                             | <span data-ttu-id="8dd05-134">Recommandation</span><span class="sxs-lookup"><span data-stu-id="8dd05-134">Recommendation</span></span>                                              |
|----------------------------------------|-------------------------------------------------------------|
| <span data-ttu-id="8dd05-135">Web Forms</span><span class="sxs-lookup"><span data-stu-id="8dd05-135">Web Forms</span></span>                              | [<span data-ttu-id="8dd05-136">ASP.NET Core éblouissant</span><span class="sxs-lookup"><span data-stu-id="8dd05-136">ASP.NET Core Blazor</span></span>](/aspnet/core/blazor)                  |
| <span data-ttu-id="8dd05-137">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="8dd05-137">Windows Communication Foundation (WCF)</span></span> | [<span data-ttu-id="8dd05-138">gRPC</span><span class="sxs-lookup"><span data-stu-id="8dd05-138">gRPC</span></span>](/aspnet/core/grpc)                                   |
| <span data-ttu-id="8dd05-139">Windows Workflow (WF)</span><span class="sxs-lookup"><span data-stu-id="8dd05-139">Windows Workflow (WF)</span></span>                  | [<span data-ttu-id="8dd05-140">CoreWF Open source</span><span class="sxs-lookup"><span data-stu-id="8dd05-140">Open-source CoreWF</span></span>](https://github.com/UiPath-Open/corewf) |

## <a name="net-standard"></a><span data-ttu-id="8dd05-141">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="8dd05-141">.NET Standard</span></span>

<span data-ttu-id="8dd05-142">Le développement d’une nouvelle application peut spécifier le `net5.0` moniker du Framework cible (TFM) pour tous les types de projets, y compris les bibliothèques de classes.</span><span class="sxs-lookup"><span data-stu-id="8dd05-142">New application development can specify the `net5.0` target framework moniker (TFM) for all project types, including class libraries.</span></span> <span data-ttu-id="8dd05-143">Le partage de code entre les charges de travail .NET 5 est simplifié en ce que vous avez tout ce dont vous avez besoin `net5.0` TFM.</span><span class="sxs-lookup"><span data-stu-id="8dd05-143">Sharing code between .NET 5 workloads is simplified in that all you need is the `net5.0` TFM.</span></span>

<span data-ttu-id="8dd05-144">Le `net5.0` TFM combine et remplace `netcoreapp` les `netstandard` noms.</span><span class="sxs-lookup"><span data-stu-id="8dd05-144">The `net5.0` TFM combines and replaces `netcoreapp` and `netstandard` names.</span></span> <span data-ttu-id="8dd05-145">Ce TFM inclut généralement des technologies qui fonctionnent sur plusieurs plateformes, comme c’est le cas avec .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="8dd05-145">This TFM will generally only include technologies that work cross-platform, like was done with .NET Standard.</span></span> <span data-ttu-id="8dd05-146">Toutefois, si vous envisagez de partager du code entre des charges de travail de .NET Framework, .NET Core et .NET 5, vous pouvez le faire en spécifiant `netstandard2.0` comme TFM.</span><span class="sxs-lookup"><span data-stu-id="8dd05-146">However, if you're planning on sharing code between .NET Framework, .NET Core, and .NET 5 workloads - you can do so by specifying `netstandard2.0` as your TFM.</span></span> <span data-ttu-id="8dd05-147">Pour plus d’informations, consultez [comment spécifier des frameworks cibles](standard/frameworks.md#how-to-specify-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="8dd05-147">For more information, see [How to specify target frameworks](standard/frameworks.md#how-to-specify-target-frameworks).</span></span>

## <a name="language-updates"></a><span data-ttu-id="8dd05-148">Mises à jour du langage</span><span class="sxs-lookup"><span data-stu-id="8dd05-148">Language updates</span></span>

<span data-ttu-id="8dd05-149">Avec .NET 5, les langages de programmation .NET continuent à s’améliorer.</span><span class="sxs-lookup"><span data-stu-id="8dd05-149">With .NET 5, the .NET programming languages are continuing to improve.</span></span>

### <a name="c-updates"></a><span data-ttu-id="8dd05-150">Mises à jour C#</span><span class="sxs-lookup"><span data-stu-id="8dd05-150">C# updates</span></span>

<span data-ttu-id="8dd05-151">Les développeurs qui écrivent des applications .NET 5 auront accès à la version et aux fonctionnalités C# les plus récentes.</span><span class="sxs-lookup"><span data-stu-id="8dd05-151">Developers writing .NET 5 apps will have access to the latest C# version and features.</span></span> <span data-ttu-id="8dd05-152">.NET 5 est associé à C# 9.</span><span class="sxs-lookup"><span data-stu-id="8dd05-152">.NET 5 is paired with C# 9.</span></span> <span data-ttu-id="8dd05-153">C# 9 apporte de nombreuses nouvelles fonctionnalités au langage. Voici quelques points importants :</span><span class="sxs-lookup"><span data-stu-id="8dd05-153">C# 9 brings many new features to the language, here are a few highlights:</span></span>

- <span data-ttu-id="8dd05-154">Enregistrements : types référence immuables qui se comportent comme des types valeur et introduisent le nouveau `with` mot clé dans le langage.</span><span class="sxs-lookup"><span data-stu-id="8dd05-154">Records: Immutable reference types that behave like value types, and introduce the new `with` keyword into the language.</span></span>
- <span data-ttu-id="8dd05-155">Critères spéciaux relationnels : étend les fonctionnalités de critères spéciaux aux opérateurs relationnels pour les évaluations comparatives et les expressions, y compris les modèles logiques, les nouveaux mots clés `and` , `or` et `not` .</span><span class="sxs-lookup"><span data-stu-id="8dd05-155">Relational pattern matching: Extends pattern matching capabilities to relational operators for comparative evaluations and expressions, including logical patterns - new keywords `and`, `or`, and `not`.</span></span>
- <span data-ttu-id="8dd05-156">Instructions de niveau supérieur : comme un moyen d’accélérer l’adoption et l’apprentissage de C#, la `Main` méthode peut être omise et l’application est aussi simple que les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="8dd05-156">Top-level statements: As a means for accelerating adoption and learning of C#, the `Main` method can be omitted and application as simple as the following is valid:</span></span>

   ```csharp
   System.Console.Write("Hello world!");
   ```

- <span data-ttu-id="8dd05-157">Pointeurs fonctionnels : constructions de langage qui exposent le langage intermédiaire (IL) les OpCodes `ldftn` et `calli` .</span><span class="sxs-lookup"><span data-stu-id="8dd05-157">Functional pointers: Language constructs that expose intermediate language (IL) the following opcodes `ldftn` and `calli`.</span></span>

<span data-ttu-id="8dd05-158">Pour plus d’informations sur les fonctionnalités C# 9 disponibles, consultez [Nouveautés de c# 9](csharp/whats-new/csharp-9.md).</span><span class="sxs-lookup"><span data-stu-id="8dd05-158">For more information on the available C# 9 features, see [What's new in C# 9](csharp/whats-new/csharp-9.md).</span></span>

#### <a name="source-generators"></a><span data-ttu-id="8dd05-159">Générateurs de sources</span><span class="sxs-lookup"><span data-stu-id="8dd05-159">Source generators</span></span>

<span data-ttu-id="8dd05-160">En plus de certaines des nouvelles fonctionnalités en C#, les générateurs de code source s’intègrent dans des projets de développement.</span><span class="sxs-lookup"><span data-stu-id="8dd05-160">In addition to some of the highlighted new C# features, source generators are making their way into developer projects.</span></span> <span data-ttu-id="8dd05-161">Les générateurs de source autorisent le code qui s’exécute pendant la compilation à inspecter votre programme et à produire des fichiers supplémentaires qui sont compilés avec le reste de votre code.</span><span class="sxs-lookup"><span data-stu-id="8dd05-161">Source generators allow code that runs during compilation to inspect your program and produce additional files that are compiled together with the rest of your code.</span></span>

<span data-ttu-id="8dd05-162">Pour plus d’informations sur les générateurs de source, consultez [Présentation des générateurs de source c#](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) et [exemples de générateur de source c#](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples).</span><span class="sxs-lookup"><span data-stu-id="8dd05-162">For more information on source generators, see [Introducing C# source generators](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) and [C# source generator samples](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples).</span></span>

### <a name="f-updates"></a><span data-ttu-id="8dd05-163">Mises à jour de F #</span><span class="sxs-lookup"><span data-stu-id="8dd05-163">F# updates</span></span>

<span data-ttu-id="8dd05-164">F # est le langage de programmation fonctionnel .NET et, avec .NET 5, les développeurs ont accès à F # 5.</span><span class="sxs-lookup"><span data-stu-id="8dd05-164">F# is the .NET functional programming language, and with .NET 5, developers have access to F# 5.</span></span> <span data-ttu-id="8dd05-165">Voici plusieurs nouvelles fonctionnalités de F # 5 :</span><span class="sxs-lookup"><span data-stu-id="8dd05-165">Here are several new features of F# 5:</span></span>

#### <a name="interpolated-strings"></a><span data-ttu-id="8dd05-166">Chaînes interpolées</span><span class="sxs-lookup"><span data-stu-id="8dd05-166">Interpolated strings</span></span>

<span data-ttu-id="8dd05-167">Semblable à la chaîne interpolée en C#, et même JavaScript-F # prend en charge l’interpolation de chaîne de base.</span><span class="sxs-lookup"><span data-stu-id="8dd05-167">Similar to interpolated string in C#, and even JavaScript - F# supports basic string interpolation.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"{name} is {age} years old."
```

<span data-ttu-id="8dd05-168">Outre l’interpolation de chaîne de base, il existe une interpolation typée.</span><span class="sxs-lookup"><span data-stu-id="8dd05-168">In addition to basic string interpolation, there is typed interpolation.</span></span> <span data-ttu-id="8dd05-169">Avec l’interpolation typée, un type donné doit correspondre au spécificateur de format.</span><span class="sxs-lookup"><span data-stu-id="8dd05-169">With typed interpolation, a given type must match the format specifier.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"%s{name} is %d{age} years old."
```

<span data-ttu-id="8dd05-170">Cela est similaire à la [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) fonction qui met en forme une chaîne en fonction des entrées de type sécurisé.</span><span class="sxs-lookup"><span data-stu-id="8dd05-170">This is similar to the [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) function that formats a string based on type-safe inputs.</span></span> <span data-ttu-id="8dd05-171">Pour plus d’informations, consultez [what’s New in F # 5](fsharp/whats-new/fsharp-50.md) .</span><span class="sxs-lookup"><span data-stu-id="8dd05-171">For more information, see [What's new in F# 5](fsharp/whats-new/fsharp-50.md)</span></span>

### <a name="visual-basic-updates"></a><span data-ttu-id="8dd05-172">Mises à jour de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8dd05-172">Visual Basic updates</span></span>

<span data-ttu-id="8dd05-173">Il n’existe aucune nouvelle fonctionnalité de langage pour Visual Basic dans .NET 5.</span><span class="sxs-lookup"><span data-stu-id="8dd05-173">There are no new language features for Visual Basic in .NET 5.</span></span> <span data-ttu-id="8dd05-174">Toutefois, avec .NET 5, la prise en charge Visual Basic est étendue à :</span><span class="sxs-lookup"><span data-stu-id="8dd05-174">However, with .NET 5, Visual Basic support is extended to:</span></span>

| <span data-ttu-id="8dd05-175">Description</span><span class="sxs-lookup"><span data-stu-id="8dd05-175">Description</span></span>                            | <span data-ttu-id="8dd05-176">Paramètre `dotnet new`</span><span class="sxs-lookup"><span data-stu-id="8dd05-176">`dotnet new` parameter</span></span> |
|----------------------------------------|------------------------|
| <span data-ttu-id="8dd05-177">Application console</span><span class="sxs-lookup"><span data-stu-id="8dd05-177">Console Application</span></span>                    | `console`              |
| <span data-ttu-id="8dd05-178">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="8dd05-178">Class library</span></span>                          | `classlib`             |
| <span data-ttu-id="8dd05-179">Application WPF</span><span class="sxs-lookup"><span data-stu-id="8dd05-179">WPF Application</span></span>                        | `wpf`                  |
| <span data-ttu-id="8dd05-180">Bibliothèque de classes WPF</span><span class="sxs-lookup"><span data-stu-id="8dd05-180">WPF Class library</span></span>                      | `wpflib`               |
| <span data-ttu-id="8dd05-181">Bibliothèque de contrôles personnalisés WPF</span><span class="sxs-lookup"><span data-stu-id="8dd05-181">WPF Custom Control Library</span></span>             | `wpfcustomcontrollib`  |
| <span data-ttu-id="8dd05-182">Bibliothèque de contrôles utilisateur WPF</span><span class="sxs-lookup"><span data-stu-id="8dd05-182">WPF User Control Library</span></span>               | `wpfusercontrollib`    |
| <span data-ttu-id="8dd05-183">Application Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="8dd05-183">Windows Forms (WinForms) Application</span></span>   | `winforms`             |
| <span data-ttu-id="8dd05-184">Bibliothèque de classes Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="8dd05-184">Windows Forms (WinForms) Class library</span></span> | `winformslib`          |
| <span data-ttu-id="8dd05-185">Projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="8dd05-185">Unit Test Project</span></span>                      | `mstest`               |
| <span data-ttu-id="8dd05-186">Projet de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="8dd05-186">NUnit 3 Test Project</span></span>                   | `nunit`                |
| <span data-ttu-id="8dd05-187">Élément de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="8dd05-187">NUnit 3 Test Item</span></span>                      | `nunit-test`           |
| <span data-ttu-id="8dd05-188">Projet de test xUnit</span><span class="sxs-lookup"><span data-stu-id="8dd05-188">xUnit Test Project</span></span>                     | `xunit`                |

<span data-ttu-id="8dd05-189">Pour plus d’informations sur les modèles de projet à partir de l’interface CLI .NET, consultez [`dotnet new`](core/tools/dotnet-new.md) .</span><span class="sxs-lookup"><span data-stu-id="8dd05-189">For more information on project templates from the .NET CLI, see [`dotnet new`](core/tools/dotnet-new.md).</span></span>

## <a name="net-maui"></a><span data-ttu-id="8dd05-190">MAUI .NET</span><span class="sxs-lookup"><span data-stu-id="8dd05-190">.NET MAUI</span></span>

<span data-ttu-id="8dd05-191">.NET MAUI est une évolution du Xamarin. Forms Toolkit de plus en plus populaire et est open source sur GitHub à l’adresse [dotnet/Maui](https://github.com/dotnet/maui).</span><span class="sxs-lookup"><span data-stu-id="8dd05-191">.NET MAUI is an evolution of the increasingly popular Xamarin.Forms toolkit, and is open-source on GitHub at [dotnet/maui](https://github.com/dotnet/maui).</span></span> <span data-ttu-id="8dd05-192">Avec .NET MAUI, le choix pour les développeurs .NET est simplifié, fournissant une pile unique qui prend en charge toutes les charges de travail modernes : Android, iOS, macOS et Windows.</span><span class="sxs-lookup"><span data-stu-id="8dd05-192">With .NET MAUI, the choice for .NET developers is simplified, providing a single stack that supports all modern workloads: Android, iOS, macOS, and Windows.</span></span> <span data-ttu-id="8dd05-193">Avec .NET MAUI, vous bénéficiez d’une expérience de développement de projet unique qui cible plusieurs plateformes et appareils.</span><span class="sxs-lookup"><span data-stu-id="8dd05-193">With .NET MAUI, you get a single project developer experience that targets multiple platforms and devices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8dd05-194">.NET MAUI est en version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="8dd05-194">.NET MAUI is in early preview.</span></span> <span data-ttu-id="8dd05-195">Vous trouverez un exemple de code source sur [xamarin/net6-Samples](https://github.com/xamarin/net6-samples).</span><span class="sxs-lookup"><span data-stu-id="8dd05-195">Sample source code can be found at [xamarin/net6-samples](https://github.com/xamarin/net6-samples).</span></span>

### <a name="model-view-update-pattern"></a><span data-ttu-id="8dd05-196">Modèle Model-View-Update</span><span class="sxs-lookup"><span data-stu-id="8dd05-196">Model-View-Update pattern</span></span>

<span data-ttu-id="8dd05-197">Les développeurs aiment les modèles de développement modernes.</span><span class="sxs-lookup"><span data-stu-id="8dd05-197">Developers love modern development patterns.</span></span> <span data-ttu-id="8dd05-198">Une approche Fluent du développement de l’interface utilisateur, inspirée par « l’architecture Elm », est le modèle [Model-View-Update](https://elmprogramming.com/model-view-update-part-1.html) ou MVU.</span><span class="sxs-lookup"><span data-stu-id="8dd05-198">A fluent approach to UI development, inspired by "The Elm Architecture" is the [model-view-update](https://elmprogramming.com/model-view-update-part-1.html) or MVU pattern.</span></span> <span data-ttu-id="8dd05-199">MVU favorise un traitement unidirectionnel des données et de la gestion de l’État, ainsi qu’une expérience de développement Code First qui met à jour rapidement l’interface utilisateur en appliquant uniquement les modifications nécessaires.</span><span class="sxs-lookup"><span data-stu-id="8dd05-199">MVU promotes a one-way flow of data and state management, as well as a code-first development experience that rapidly updates the UI by applying only the changes necessary.</span></span>

<span data-ttu-id="8dd05-200">À titre d’exemple, considérez le compteur suivant écrit dans .NET MAUI à l’aide du modèle MVU :</span><span class="sxs-lookup"><span data-stu-id="8dd05-200">As an example, consider the following counter written in .NET MAUI using the MVU pattern:</span></span>

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

<span data-ttu-id="8dd05-201">Pour plus d’informations, consultez la feuille de [route .net Maui](https://github.com/dotnet/maui/wiki/Roadmap)et présentation de l’article [.net Maui](https://devblogs.microsoft.com/dotnet/introducing-net-multi-platform-app-ui) .</span><span class="sxs-lookup"><span data-stu-id="8dd05-201">For more information, see the [.NET MAUI roadmap](https://github.com/dotnet/maui/wiki/Roadmap), and [Introducing .NET MAUI](https://devblogs.microsoft.com/dotnet/introducing-net-multi-platform-app-ui) article.</span></span>

## <a name="see-also"></a><span data-ttu-id="8dd05-202">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8dd05-202">See also</span></span>

- [<span data-ttu-id="8dd05-203">Le trajet vers un .NET</span><span class="sxs-lookup"><span data-stu-id="8dd05-203">The Journey to one .NET</span></span>](https://channel9.msdn.com/Events/Build/2020/BOD106)
- [<span data-ttu-id="8dd05-204">Améliorations des performances dans .NET 5</span><span class="sxs-lookup"><span data-stu-id="8dd05-204">Performance improvements in .NET 5</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
