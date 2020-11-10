---
title: Nouveautés de .NET 5
description: Découvrez .NET 5, une plateforme de développement multiplateforme et open source qui est la prochaine évolution de .NET Core.
ms.date: 11/06/2020
ms.topic: overview
ms.author: dapine
author: IEvangelist
ms.openlocfilehash: 43d7a2baa75f3d71de8bbbf1d0bff7d1beb3d7cd
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440533"
---
# <a name="whats-new-in-net-5"></a><span data-ttu-id="b7778-103">Nouveautés de .NET 5</span><span class="sxs-lookup"><span data-stu-id="b7778-103">What's new in .NET 5</span></span>

<span data-ttu-id="b7778-104">.NET 5,0 est la prochaine version majeure de .NET Core suivant 3,1.</span><span class="sxs-lookup"><span data-stu-id="b7778-104">.NET 5.0 is the next major release of .NET Core following 3.1.</span></span> <span data-ttu-id="b7778-105">Nous avons nommé cette nouvelle version .NET 5,0 au lieu de .NET Core 4,0 pour deux raisons :</span><span class="sxs-lookup"><span data-stu-id="b7778-105">We named this new release .NET 5.0 instead of .NET Core 4.0 for two reasons:</span></span>

- <span data-ttu-id="b7778-106">Nous avons ignoré les numéros de version 4. x pour éviter toute confusion avec .NET Framework 4. x.</span><span class="sxs-lookup"><span data-stu-id="b7778-106">We skipped version numbers 4.x to avoid confusion with .NET Framework 4.x.</span></span>
- <span data-ttu-id="b7778-107">Nous avons supprimé « Core » du nom pour insister sur le fait qu’il s’agit de la principale implémentation de .NET.</span><span class="sxs-lookup"><span data-stu-id="b7778-107">We dropped "Core" from the name to emphasize that this is the main implementation of .NET going forward.</span></span> <span data-ttu-id="b7778-108">.NET 5,0 prend en charge davantage de types d’applications et de plateformes que .NET Core ou .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b7778-108">.NET 5.0 supports more types of apps and more platforms than .NET Core or .NET Framework.</span></span>

<span data-ttu-id="b7778-109">ASP.NET Core 5,0 est basé sur .NET 5,0, mais conserve le nom « Core » pour éviter qu’il ne soit confus avec ASP.NET MVC 5.</span><span class="sxs-lookup"><span data-stu-id="b7778-109">ASP.NET Core 5.0 is based on .NET 5.0 but retains the name "Core" to avoid confusing it with ASP.NET MVC 5.</span></span> <span data-ttu-id="b7778-110">De même, Entity Framework Core 5,0 conserve le nom « Core » pour éviter qu’il ne soit confus avec Entity Framework 5 et 6.</span><span class="sxs-lookup"><span data-stu-id="b7778-110">Likewise, Entity Framework Core 5.0 retains the name "Core" to avoid confusing it with Entity Framework 5 and 6.</span></span>

<span data-ttu-id="b7778-111">.NET 5,0 comprend les améliorations et les nouvelles fonctionnalités suivantes par rapport à .NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="b7778-111">.NET 5.0 includes the following improvements and new features compared to .NET Core 3.1:</span></span>

- [<span data-ttu-id="b7778-112">Mises à jour C#</span><span class="sxs-lookup"><span data-stu-id="b7778-112">C# updates</span></span>](#c-updates)
- [<span data-ttu-id="b7778-113">Mises à jour de F #</span><span class="sxs-lookup"><span data-stu-id="b7778-113">F# updates</span></span>](#f-updates)
- [<span data-ttu-id="b7778-114">Mises à jour de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b7778-114">Visual Basic updates</span></span>](#visual-basic-updates)
- [<span data-ttu-id="b7778-115">System.Text.Jssur les nouvelles fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="b7778-115">System.Text.Json new features</span></span>](#systemtextjson-new-features)
- [<span data-ttu-id="b7778-116">Applications à fichier unique</span><span class="sxs-lookup"><span data-stu-id="b7778-116">Single file apps</span></span>](deploying/single-file.md)
- [<span data-ttu-id="b7778-117">Suppression d’application</span><span class="sxs-lookup"><span data-stu-id="b7778-117">App trimming</span></span>](https://devblogs.microsoft.com/dotnet/app-trimming-in-net-5)
- <span data-ttu-id="b7778-118">Intrinsèques Windows ARM64 et ARM64</span><span class="sxs-lookup"><span data-stu-id="b7778-118">Windows ARM64 and ARM64 intrinsics</span></span>
- <span data-ttu-id="b7778-119">Prise en charge des outils pour le débogage de vidage</span><span class="sxs-lookup"><span data-stu-id="b7778-119">Tooling support for dump debugging</span></span>
- <span data-ttu-id="b7778-120">Les bibliothèques Runtime sont 80% annotées pour les [types référence Nullable](../csharp/nullable-references.md)</span><span class="sxs-lookup"><span data-stu-id="b7778-120">The runtime libraries are 80% annotated for [nullable reference types](../csharp/nullable-references.md)</span></span>
- <span data-ttu-id="b7778-121">Améliorations des performances :</span><span class="sxs-lookup"><span data-stu-id="b7778-121">Performance improvements:</span></span>
  - [<span data-ttu-id="b7778-122">Garbage collection (GC)</span><span class="sxs-lookup"><span data-stu-id="b7778-122">Garbage Collection (GC)</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#gc)
  - [<span data-ttu-id="b7778-123">System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="b7778-123">System.Text.Json</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#json)
  - [<span data-ttu-id="b7778-124">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="b7778-124">System.Text.RegularExpressions</span></span>](https://devblogs.microsoft.com/dotnet/regex-performance-improvements-in-net-5)
  - [<span data-ttu-id="b7778-125">Regroupement ValueTask asynchrone</span><span class="sxs-lookup"><span data-stu-id="b7778-125">Async ValueTask pooling</span></span>](https://devblogs.microsoft.com/dotnet/async-valuetask-pooling-in-net-5)
  - [<span data-ttu-id="b7778-126">Optimisations de la taille du conteneur</span><span class="sxs-lookup"><span data-stu-id="b7778-126">Container size optimizations</span></span>](https://github.com/dotnet/dotnet-docker/issues/1814#issuecomment-625294750)
  - [<span data-ttu-id="b7778-127">Beaucoup plus de zones</span><span class="sxs-lookup"><span data-stu-id="b7778-127">Many more areas</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)

## <a name="net-50-doesnt-replace-net-framework"></a><span data-ttu-id="b7778-128">.NET 5,0 ne remplace pas .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b7778-128">.NET 5.0 doesn't replace .NET Framework</span></span>

<span data-ttu-id="b7778-129">.NET 5,0 est la principale implémentation de .NET à l’avenir et .NET Framework 4. x est toujours pris en charge.</span><span class="sxs-lookup"><span data-stu-id="b7778-129">.NET 5.0 is the main implementation of .NET going forward and .NET Framework 4.x is still supported.</span></span>

<span data-ttu-id="b7778-130">Il n’est pas prévu de porter les technologies suivantes de .NET Framework vers .NET 5,0, mais il existe des alternatives dans .NET 5,0 :</span><span class="sxs-lookup"><span data-stu-id="b7778-130">There are no plans to port the following technologies from .NET Framework to .NET 5.0, but there are alternatives in .NET 5.0:</span></span>

| <span data-ttu-id="b7778-131">Technologie</span><span class="sxs-lookup"><span data-stu-id="b7778-131">Technology</span></span>                             | <span data-ttu-id="b7778-132">Alternative recommandée</span><span class="sxs-lookup"><span data-stu-id="b7778-132">Recommended alternative</span></span>                                                                         |
|----------------------------------------|-------------------------------------------------------------------------------------------------|
| <span data-ttu-id="b7778-133">Web Forms</span><span class="sxs-lookup"><span data-stu-id="b7778-133">Web Forms</span></span>                              | <span data-ttu-id="b7778-134">ASP.NET Core [éblouissant](/aspnet/core/blazor) ou [Razor pages](/aspnet/core/tutorials/razor-pages)</span><span class="sxs-lookup"><span data-stu-id="b7778-134">ASP.NET Core [Blazor](/aspnet/core/blazor) or [Razor Pages](/aspnet/core/tutorials/razor-pages)</span></span> |
| <span data-ttu-id="b7778-135">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="b7778-135">Windows Communication Foundation (WCF)</span></span> | [<span data-ttu-id="b7778-136">gRPC</span><span class="sxs-lookup"><span data-stu-id="b7778-136">gRPC</span></span>](/aspnet/core/grpc)                                                                       |
| <span data-ttu-id="b7778-137">Windows Workflow (WF)</span><span class="sxs-lookup"><span data-stu-id="b7778-137">Windows Workflow (WF)</span></span>                  | [<span data-ttu-id="b7778-138">CoreWF Open source</span><span class="sxs-lookup"><span data-stu-id="b7778-138">Open-source CoreWF</span></span>](https://github.com/UiPath-Open/corewf)                                     |

## <a name="net-50-doesnt-replace-net-standard"></a><span data-ttu-id="b7778-139">.NET 5,0 ne remplace pas .NET Standard</span><span class="sxs-lookup"><span data-stu-id="b7778-139">.NET 5.0 doesn't replace .NET Standard</span></span>

<span data-ttu-id="b7778-140">Le développement d’une nouvelle application peut spécifier le `net5.0` moniker du Framework cible (TFM) pour tous les types de projets, y compris les bibliothèques de classes.</span><span class="sxs-lookup"><span data-stu-id="b7778-140">New application development can specify the `net5.0` target framework moniker (TFM) for all project types, including class libraries.</span></span> <span data-ttu-id="b7778-141">Le partage de code entre les charges de travail .NET 5 est simplifié en ce que vous avez tout ce dont vous avez besoin `net5.0` TFM.</span><span class="sxs-lookup"><span data-stu-id="b7778-141">Sharing code between .NET 5 workloads is simplified in that all you need is the `net5.0` TFM.</span></span>

<span data-ttu-id="b7778-142">Pour les applications et les bibliothèques .NET 5,0, le `net5.0` moniker du Framework cible (TFM) combine et remplace les `netcoreapp` `netstandard` TFM.</span><span class="sxs-lookup"><span data-stu-id="b7778-142">For .NET 5.0 apps and libraries, the `net5.0` Target Framework Moniker (TFM) combines and replaces the `netcoreapp` and `netstandard` TFMs.</span></span> <span data-ttu-id="b7778-143">Toutefois, si vous envisagez de partager du code entre des charges de travail .NET Framework, .NET Core et .NET 5, vous pouvez le faire en spécifiant `netstandard2.0` comme TFM.</span><span class="sxs-lookup"><span data-stu-id="b7778-143">However, if you plan to share code between .NET Framework, .NET Core, and .NET 5 workloads, you can do so by specifying `netstandard2.0` as your TFM.</span></span> <span data-ttu-id="b7778-144">Pour plus d'informations, consultez [.NET Standard](../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="b7778-144">For more information, see [.NET Standard](../standard/net-standard.md).</span></span>

## <a name="c-updates"></a><span data-ttu-id="b7778-145">Mises à jour C#</span><span class="sxs-lookup"><span data-stu-id="b7778-145">C# updates</span></span>

<span data-ttu-id="b7778-146">Les développeurs qui écrivent des applications .NET 5 auront accès à la version et aux fonctionnalités C# les plus récentes.</span><span class="sxs-lookup"><span data-stu-id="b7778-146">Developers writing .NET 5 apps will have access to the latest C# version and features.</span></span> <span data-ttu-id="b7778-147">.NET 5 est associé à C# 9, qui offre de nombreuses nouvelles fonctionnalités au langage.</span><span class="sxs-lookup"><span data-stu-id="b7778-147">.NET 5 is paired with C# 9, which brings many new features to the language.</span></span> <span data-ttu-id="b7778-148">Voici quelques points importants :</span><span class="sxs-lookup"><span data-stu-id="b7778-148">Here are a few highlights:</span></span>

- <span data-ttu-id="b7778-149">Enregistrements : types référence immuables qui se comportent comme des types valeur et introduisent le nouveau `with` mot clé dans le langage.</span><span class="sxs-lookup"><span data-stu-id="b7778-149">Records: Immutable reference types that behave like value types, and introduce the new `with` keyword into the language.</span></span>
- <span data-ttu-id="b7778-150">Critères spéciaux relationnels : étend les fonctionnalités de critères spéciaux aux opérateurs relationnels pour les évaluations comparatives et les expressions, y compris les modèles logiques, les nouveaux mots clés `and` , `or` et `not` .</span><span class="sxs-lookup"><span data-stu-id="b7778-150">Relational pattern matching: Extends pattern matching capabilities to relational operators for comparative evaluations and expressions, including logical patterns - new keywords `and`, `or`, and `not`.</span></span>
- <span data-ttu-id="b7778-151">Instructions de niveau supérieur : comme un moyen d’accélérer l’adoption et l’apprentissage de C#, la `Main` méthode peut être omise et l’application est aussi simple que les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="b7778-151">Top-level statements: As a means for accelerating adoption and learning of C#, the `Main` method can be omitted and application as simple as the following is valid:</span></span>

   ```csharp
   System.Console.Write("Hello world!");
   ```

- <span data-ttu-id="b7778-152">Pointeurs fonction : constructions de langage qui exposent les OpCodes de langage intermédiaire (IL) suivants : `ldftn` et `calli` .</span><span class="sxs-lookup"><span data-stu-id="b7778-152">Function pointers: Language constructs that expose the following intermediate language (IL) opcodes: `ldftn` and `calli`.</span></span>

<span data-ttu-id="b7778-153">Pour plus d’informations sur les fonctionnalités C# 9 disponibles, consultez [Nouveautés de c# 9](../csharp/whats-new/csharp-9.md).</span><span class="sxs-lookup"><span data-stu-id="b7778-153">For more information on the available C# 9 features, see [What's new in C# 9](../csharp/whats-new/csharp-9.md).</span></span>

### <a name="source-generators"></a><span data-ttu-id="b7778-154">Générateurs de sources</span><span class="sxs-lookup"><span data-stu-id="b7778-154">Source generators</span></span>

<span data-ttu-id="b7778-155">En plus de certaines des nouvelles fonctionnalités en C#, les générateurs de code source s’intègrent dans des projets de développement.</span><span class="sxs-lookup"><span data-stu-id="b7778-155">In addition to some of the highlighted new C# features, source generators are making their way into developer projects.</span></span> <span data-ttu-id="b7778-156">Les générateurs de source autorisent le code qui s’exécute pendant la compilation à inspecter votre programme et à produire des fichiers supplémentaires qui sont compilés avec le reste de votre code.</span><span class="sxs-lookup"><span data-stu-id="b7778-156">Source generators allow code that runs during compilation to inspect your program and produce additional files that are compiled together with the rest of your code.</span></span>

<span data-ttu-id="b7778-157">Pour plus d’informations sur les générateurs de source, consultez [Présentation des générateurs de source c#](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) et [exemples de générateur de source c#](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples).</span><span class="sxs-lookup"><span data-stu-id="b7778-157">For more information on source generators, see [Introducing C# source generators](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) and [C# source generator samples](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples).</span></span>

## <a name="f-updates"></a><span data-ttu-id="b7778-158">Mises à jour de F #</span><span class="sxs-lookup"><span data-stu-id="b7778-158">F# updates</span></span>

<span data-ttu-id="b7778-159">F # est le langage de programmation fonctionnel .NET et, avec .NET 5, les développeurs ont accès à F # 5.</span><span class="sxs-lookup"><span data-stu-id="b7778-159">F# is the .NET functional programming language, and with .NET 5, developers have access to F# 5.</span></span> <span data-ttu-id="b7778-160">Voici plusieurs nouvelles fonctionnalités de F # 5 :</span><span class="sxs-lookup"><span data-stu-id="b7778-160">Here are several new features of F# 5:</span></span>

### <a name="interpolated-strings"></a><span data-ttu-id="b7778-161">Chaînes interpolées</span><span class="sxs-lookup"><span data-stu-id="b7778-161">Interpolated strings</span></span>

<span data-ttu-id="b7778-162">À l’instar de la chaîne interpolée en C#, et même de JavaScript, F # prend en charge l’interpolation de chaîne de base.</span><span class="sxs-lookup"><span data-stu-id="b7778-162">Similar to interpolated string in C#, and even JavaScript, F# supports basic string interpolation.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"{name} is {age} years old."
```

<span data-ttu-id="b7778-163">Outre l’interpolation de chaîne de base, il existe une interpolation typée.</span><span class="sxs-lookup"><span data-stu-id="b7778-163">In addition to basic string interpolation, there is typed interpolation.</span></span> <span data-ttu-id="b7778-164">Avec l’interpolation typée, un type donné doit correspondre au spécificateur de format.</span><span class="sxs-lookup"><span data-stu-id="b7778-164">With typed interpolation, a given type must match the format specifier.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"%s{name} is %d{age} years old."
```

<span data-ttu-id="b7778-165">Cela est similaire à la [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) fonction qui met en forme une chaîne en fonction des entrées de type sécurisé.</span><span class="sxs-lookup"><span data-stu-id="b7778-165">This is similar to the [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) function that formats a string based on type-safe inputs.</span></span> <!-- For more information, see [What's new in F# 5](fsharp/whats-new/fsharp-50.md). -->

## <a name="visual-basic-updates"></a><span data-ttu-id="b7778-166">Mises à jour de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b7778-166">Visual Basic updates</span></span>

<span data-ttu-id="b7778-167">Il n’existe aucune nouvelle fonctionnalité de langage pour Visual Basic dans .NET 5.</span><span class="sxs-lookup"><span data-stu-id="b7778-167">There are no new language features for Visual Basic in .NET 5.</span></span> <span data-ttu-id="b7778-168">Toutefois, avec .NET 5, la prise en charge Visual Basic est étendue à :</span><span class="sxs-lookup"><span data-stu-id="b7778-168">However, with .NET 5, Visual Basic support is extended to:</span></span>

| <span data-ttu-id="b7778-169">Description</span><span class="sxs-lookup"><span data-stu-id="b7778-169">Description</span></span>                            | <span data-ttu-id="b7778-170">Paramètre `dotnet new`</span><span class="sxs-lookup"><span data-stu-id="b7778-170">`dotnet new` parameter</span></span> |
|----------------------------------------|------------------------|
| <span data-ttu-id="b7778-171">Application console</span><span class="sxs-lookup"><span data-stu-id="b7778-171">Console Application</span></span>                    | `console`              |
| <span data-ttu-id="b7778-172">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="b7778-172">Class library</span></span>                          | `classlib`             |
| <span data-ttu-id="b7778-173">Application WPF</span><span class="sxs-lookup"><span data-stu-id="b7778-173">WPF Application</span></span>                        | `wpf`                  |
| <span data-ttu-id="b7778-174">Bibliothèque de classes WPF</span><span class="sxs-lookup"><span data-stu-id="b7778-174">WPF Class library</span></span>                      | `wpflib`               |
| <span data-ttu-id="b7778-175">Bibliothèque de contrôles personnalisés WPF</span><span class="sxs-lookup"><span data-stu-id="b7778-175">WPF Custom Control Library</span></span>             | `wpfcustomcontrollib`  |
| <span data-ttu-id="b7778-176">Bibliothèque de contrôles utilisateur WPF</span><span class="sxs-lookup"><span data-stu-id="b7778-176">WPF User Control Library</span></span>               | `wpfusercontrollib`    |
| <span data-ttu-id="b7778-177">Application Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="b7778-177">Windows Forms (WinForms) Application</span></span>   | `winforms`             |
| <span data-ttu-id="b7778-178">Bibliothèque de classes Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="b7778-178">Windows Forms (WinForms) Class library</span></span> | `winformslib`          |
| <span data-ttu-id="b7778-179">Projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="b7778-179">Unit Test Project</span></span>                      | `mstest`               |
| <span data-ttu-id="b7778-180">Projet de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="b7778-180">NUnit 3 Test Project</span></span>                   | `nunit`                |
| <span data-ttu-id="b7778-181">Élément de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="b7778-181">NUnit 3 Test Item</span></span>                      | `nunit-test`           |
| <span data-ttu-id="b7778-182">Projet de test xUnit</span><span class="sxs-lookup"><span data-stu-id="b7778-182">xUnit Test Project</span></span>                     | `xunit`                |

<span data-ttu-id="b7778-183">Pour plus d’informations sur les modèles de projet à partir de l’interface CLI .NET, consultez [`dotnet new`](tools/dotnet-new.md) .</span><span class="sxs-lookup"><span data-stu-id="b7778-183">For more information on project templates from the .NET CLI, see [`dotnet new`](tools/dotnet-new.md).</span></span>

## <a name="systemtextjson-new-features"></a><span data-ttu-id="b7778-184">System.Text.Jssur les nouvelles fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="b7778-184">System.Text.Json new features</span></span>

<span data-ttu-id="b7778-185">Il existe de nouvelles fonctionnalités dans et pour [System.Text.Jssur](../standard/serialization/system-text-json-overview.md):</span><span class="sxs-lookup"><span data-stu-id="b7778-185">There are new features in and for [System.Text.Json](../standard/serialization/system-text-json-overview.md):</span></span>

- [<span data-ttu-id="b7778-186">Conserver les références et gérer les références circulaires</span><span class="sxs-lookup"><span data-stu-id="b7778-186">Preserve references and handle circular references</span></span>](../standard/serialization/system-text-json-how-to.md#preserve-references-and-handle-circular-references)
- [<span data-ttu-id="b7778-187">Méthodes d’extension HttpClient et HttpContent</span><span class="sxs-lookup"><span data-stu-id="b7778-187">HttpClient and HttpContent extension methods</span></span>](../standard/serialization/system-text-json-how-to.md#httpclient-and-httpcontent-extension-methods)
- [<span data-ttu-id="b7778-188">Autoriser ou écrire des nombres entre guillemets</span><span class="sxs-lookup"><span data-stu-id="b7778-188">Allow or write numbers in quotes</span></span>](../standard/serialization/system-text-json-how-to.md#allow-or-write-numbers-in-quotes)
- [<span data-ttu-id="b7778-189">Prendre en charge les types immuables et les enregistrements C# 9</span><span class="sxs-lookup"><span data-stu-id="b7778-189">Support immutable types and C# 9 Records</span></span>](../standard/serialization/system-text-json-how-to.md#immutable-types-and-records)
- [<span data-ttu-id="b7778-190">Prendre en charge les accesseurs de propriété non publics</span><span class="sxs-lookup"><span data-stu-id="b7778-190">Support non-public property accessors</span></span>](../standard/serialization/system-text-json-how-to.md#non-public-property-accessors)
- [<span data-ttu-id="b7778-191">champs de support</span><span class="sxs-lookup"><span data-stu-id="b7778-191">support fields</span></span>](../standard/serialization/system-text-json-how-to.md#include-fields)
- [<span data-ttu-id="b7778-192">Ignorer conditionnellement les propriétés</span><span class="sxs-lookup"><span data-stu-id="b7778-192">Conditionally ignore properties</span></span>](../standard/serialization/system-text-json-how-to.md#ignore-properties)
- [<span data-ttu-id="b7778-193">Prise en charge des dictionnaires non-clés-chaîne</span><span class="sxs-lookup"><span data-stu-id="b7778-193">Support non-string-key dictionaries</span></span>](../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md#dictionary-with-non-string-key)
- [<span data-ttu-id="b7778-194">Prendre en charge les accesseurs de propriété non publics</span><span class="sxs-lookup"><span data-stu-id="b7778-194">Support non-public property accessors</span></span>](../standard/serialization/system-text-json-how-to.md#non-public-property-accessors)
- [<span data-ttu-id="b7778-195">Autoriser les convertisseurs personnalisés à gérer la valeur null</span><span class="sxs-lookup"><span data-stu-id="b7778-195">Allow custom converters to handle null</span></span>](../standard/serialization/system-text-json-converters-how-to.md#handle-null-values)
- [<span data-ttu-id="b7778-196">Copier JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="b7778-196">Copy JsonSerializerOptions</span></span>](../standard/serialization/system-text-json-how-to.md#copy-jsonserializeroptions)
- [<span data-ttu-id="b7778-197">Créer des JsonSerializerOptions avec des valeurs par défaut Web</span><span class="sxs-lookup"><span data-stu-id="b7778-197">Create JsonSerializerOptions with web defaults</span></span>](../standard/serialization/system-text-json-how-to.md#web-defaults-for-jsonserializeroptions)

## <a name="net-maui"></a><span data-ttu-id="b7778-198">MAUI .NET</span><span class="sxs-lookup"><span data-stu-id="b7778-198">.NET MAUI</span></span>

<span data-ttu-id="b7778-199">.NET MAUI est une évolution du Xamarin. Forms Toolkit de plus en plus populaire et est open source sur GitHub à l’adresse [dotnet/Maui](https://github.com/dotnet/maui).</span><span class="sxs-lookup"><span data-stu-id="b7778-199">.NET MAUI is an evolution of the increasingly popular Xamarin.Forms toolkit, and is open-source on GitHub at [dotnet/maui](https://github.com/dotnet/maui).</span></span> <span data-ttu-id="b7778-200">Avec .NET MAUI, le choix pour les développeurs .NET est simplifié, fournissant une pile unique qui prend en charge toutes les charges de travail modernes : Android, iOS, macOS et Windows.</span><span class="sxs-lookup"><span data-stu-id="b7778-200">With .NET MAUI, the choice for .NET developers is simplified, providing a single stack that supports all modern workloads: Android, iOS, macOS, and Windows.</span></span> <span data-ttu-id="b7778-201">Avec .NET MAUI, vous bénéficiez d’une expérience de développement de projet unique qui cible plusieurs plateformes et appareils.</span><span class="sxs-lookup"><span data-stu-id="b7778-201">With .NET MAUI, you get a single project developer experience that targets multiple platforms and devices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b7778-202">.NET MAUI est en version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="b7778-202">.NET MAUI is in early preview.</span></span> <span data-ttu-id="b7778-203">Vous trouverez un exemple de code source sur [xamarin/net6-Samples](https://github.com/xamarin/net6-samples).</span><span class="sxs-lookup"><span data-stu-id="b7778-203">Sample source code can be found at [xamarin/net6-samples](https://github.com/xamarin/net6-samples).</span></span>

### <a name="model-view-update-pattern"></a><span data-ttu-id="b7778-204">Modèle Model-View-Update</span><span class="sxs-lookup"><span data-stu-id="b7778-204">Model-View-Update pattern</span></span>

<span data-ttu-id="b7778-205">Les développeurs aiment les modèles de développement modernes.</span><span class="sxs-lookup"><span data-stu-id="b7778-205">Developers love modern development patterns.</span></span> <span data-ttu-id="b7778-206">Une approche Fluent du développement de l’interface utilisateur, inspirée par « l’architecture Elm », est le modèle [Model-View-Update](https://elmprogramming.com/model-view-update-part-1.html) ou MVU.</span><span class="sxs-lookup"><span data-stu-id="b7778-206">A fluent approach to UI development, inspired by "The Elm Architecture" is the [model-view-update](https://elmprogramming.com/model-view-update-part-1.html) or MVU pattern.</span></span> <span data-ttu-id="b7778-207">MVU favorise un traitement unidirectionnel des données et de la gestion de l’État, ainsi qu’une expérience de développement Code First qui met à jour rapidement l’interface utilisateur en appliquant uniquement les modifications nécessaires.</span><span class="sxs-lookup"><span data-stu-id="b7778-207">MVU promotes a one-way flow of data and state management, as well as a code-first development experience that rapidly updates the UI by applying only the changes necessary.</span></span>

<span data-ttu-id="b7778-208">À titre d’exemple, considérez le compteur suivant écrit dans .NET MAUI à l’aide du modèle MVU :</span><span class="sxs-lookup"><span data-stu-id="b7778-208">As an example, consider the following counter written in .NET MAUI using the MVU pattern:</span></span>

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

<span data-ttu-id="b7778-209">Pour plus d’informations, consultez la feuille de [route .net Maui](https://github.com/dotnet/maui/wiki/Roadmap)et présentation de l’article [.net Maui](https://devblogs.microsoft.com/dotnet/introducing-net-multi-platform-app-ui) .</span><span class="sxs-lookup"><span data-stu-id="b7778-209">For more information, see the [.NET MAUI roadmap](https://github.com/dotnet/maui/wiki/Roadmap), and [Introducing .NET MAUI](https://devblogs.microsoft.com/dotnet/introducing-net-multi-platform-app-ui) article.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7778-210">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7778-210">See also</span></span>

- [<span data-ttu-id="b7778-211">Le trajet vers un .NET</span><span class="sxs-lookup"><span data-stu-id="b7778-211">The Journey to one .NET</span></span>](https://channel9.msdn.com/Events/Build/2020/BOD106)
- [<span data-ttu-id="b7778-212">Améliorations des performances dans .NET 5</span><span class="sxs-lookup"><span data-stu-id="b7778-212">Performance improvements in .NET 5</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
