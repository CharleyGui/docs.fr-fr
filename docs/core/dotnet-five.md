---
title: Nouveautés de .NET 5
description: Découvrez .NET 5, une plateforme de développement multiplateforme et open source qui est la prochaine évolution de .NET Core.
ms.date: 11/18/2020
ms.topic: overview
ms.author: dapine
author: IEvangelist
ms.openlocfilehash: 1101e218f225eed2a2013ed9e19b60f4ece57738
ms.sourcegitcommit: 6d1ae17e60384f3b5953ca7b45ac859ec6d4c3a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94982299"
---
# <a name="whats-new-in-net-5"></a><span data-ttu-id="77f1c-103">Nouveautés de .NET 5</span><span class="sxs-lookup"><span data-stu-id="77f1c-103">What's new in .NET 5</span></span>

<span data-ttu-id="77f1c-104">.NET 5,0 est la prochaine version majeure de .NET Core suivant 3,1.</span><span class="sxs-lookup"><span data-stu-id="77f1c-104">.NET 5.0 is the next major release of .NET Core following 3.1.</span></span> <span data-ttu-id="77f1c-105">Nous avons nommé cette nouvelle version .NET 5,0 au lieu de .NET Core 4,0 pour deux raisons :</span><span class="sxs-lookup"><span data-stu-id="77f1c-105">We named this new release .NET 5.0 instead of .NET Core 4.0 for two reasons:</span></span>

- <span data-ttu-id="77f1c-106">Nous avons ignoré les numéros de version 4. x pour éviter toute confusion avec .NET Framework 4. x.</span><span class="sxs-lookup"><span data-stu-id="77f1c-106">We skipped version numbers 4.x to avoid confusion with .NET Framework 4.x.</span></span>
- <span data-ttu-id="77f1c-107">Nous avons supprimé « Core » du nom pour insister sur le fait qu’il s’agit de la principale implémentation de .NET.</span><span class="sxs-lookup"><span data-stu-id="77f1c-107">We dropped "Core" from the name to emphasize that this is the main implementation of .NET going forward.</span></span> <span data-ttu-id="77f1c-108">.NET 5,0 prend en charge davantage de types d’applications et de plateformes que .NET Core ou .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="77f1c-108">.NET 5.0 supports more types of apps and more platforms than .NET Core or .NET Framework.</span></span>

<span data-ttu-id="77f1c-109">ASP.NET Core 5,0 est basé sur .NET 5,0, mais conserve le nom « Core » pour éviter qu’il ne soit confus avec ASP.NET MVC 5.</span><span class="sxs-lookup"><span data-stu-id="77f1c-109">ASP.NET Core 5.0 is based on .NET 5.0 but retains the name "Core" to avoid confusing it with ASP.NET MVC 5.</span></span> <span data-ttu-id="77f1c-110">De même, Entity Framework Core 5,0 conserve le nom « Core » pour éviter qu’il ne soit confus avec Entity Framework 5 et 6.</span><span class="sxs-lookup"><span data-stu-id="77f1c-110">Likewise, Entity Framework Core 5.0 retains the name "Core" to avoid confusing it with Entity Framework 5 and 6.</span></span>

<span data-ttu-id="77f1c-111">.NET 5,0 comprend les améliorations et les nouvelles fonctionnalités suivantes par rapport à .NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="77f1c-111">.NET 5.0 includes the following improvements and new features compared to .NET Core 3.1:</span></span>

- [<span data-ttu-id="77f1c-112">Mises à jour C#</span><span class="sxs-lookup"><span data-stu-id="77f1c-112">C# updates</span></span>](#c-updates)
- [<span data-ttu-id="77f1c-113">Mises à jour de F #</span><span class="sxs-lookup"><span data-stu-id="77f1c-113">F# updates</span></span>](#f-updates)
- [<span data-ttu-id="77f1c-114">Mises à jour de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="77f1c-114">Visual Basic updates</span></span>](#visual-basic-updates)
- [<span data-ttu-id="77f1c-115">System.Text.Jssur les nouvelles fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="77f1c-115">System.Text.Json new features</span></span>](#systemtextjson-new-features)
- [<span data-ttu-id="77f1c-116">Applications à fichier unique</span><span class="sxs-lookup"><span data-stu-id="77f1c-116">Single file apps</span></span>](deploying/single-file.md)
- [<span data-ttu-id="77f1c-117">Suppression d’application</span><span class="sxs-lookup"><span data-stu-id="77f1c-117">App trimming</span></span>](https://devblogs.microsoft.com/dotnet/app-trimming-in-net-5)
- <span data-ttu-id="77f1c-118">Intrinsèques Windows ARM64 et ARM64</span><span class="sxs-lookup"><span data-stu-id="77f1c-118">Windows ARM64 and ARM64 intrinsics</span></span>
- <span data-ttu-id="77f1c-119">Prise en charge des outils pour le débogage de vidage</span><span class="sxs-lookup"><span data-stu-id="77f1c-119">Tooling support for dump debugging</span></span>
- <span data-ttu-id="77f1c-120">Les bibliothèques Runtime sont 80% annotées pour les [types référence Nullable](../csharp/nullable-references.md)</span><span class="sxs-lookup"><span data-stu-id="77f1c-120">The runtime libraries are 80% annotated for [nullable reference types](../csharp/nullable-references.md)</span></span>
- <span data-ttu-id="77f1c-121">Améliorations des performances :</span><span class="sxs-lookup"><span data-stu-id="77f1c-121">Performance improvements:</span></span>
  - [<span data-ttu-id="77f1c-122">Garbage collection (GC)</span><span class="sxs-lookup"><span data-stu-id="77f1c-122">Garbage Collection (GC)</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#gc)
  - [<span data-ttu-id="77f1c-123">System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="77f1c-123">System.Text.Json</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#json)
  - [<span data-ttu-id="77f1c-124">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="77f1c-124">System.Text.RegularExpressions</span></span>](https://devblogs.microsoft.com/dotnet/regex-performance-improvements-in-net-5)
  - [<span data-ttu-id="77f1c-125">Regroupement ValueTask asynchrone</span><span class="sxs-lookup"><span data-stu-id="77f1c-125">Async ValueTask pooling</span></span>](https://devblogs.microsoft.com/dotnet/async-valuetask-pooling-in-net-5)
  - [<span data-ttu-id="77f1c-126">Optimisations de la taille du conteneur</span><span class="sxs-lookup"><span data-stu-id="77f1c-126">Container size optimizations</span></span>](https://github.com/dotnet/dotnet-docker/issues/1814#issuecomment-625294750)
  - [<span data-ttu-id="77f1c-127">Beaucoup plus de zones</span><span class="sxs-lookup"><span data-stu-id="77f1c-127">Many more areas</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)

## <a name="net-50-doesnt-replace-net-framework"></a><span data-ttu-id="77f1c-128">.NET 5,0 ne remplace pas .NET Framework</span><span class="sxs-lookup"><span data-stu-id="77f1c-128">.NET 5.0 doesn't replace .NET Framework</span></span>

<span data-ttu-id="77f1c-129">.NET 5,0 est la principale implémentation de .NET à l’avenir et .NET Framework 4. x est toujours pris en charge.</span><span class="sxs-lookup"><span data-stu-id="77f1c-129">.NET 5.0 is the main implementation of .NET going forward and .NET Framework 4.x is still supported.</span></span>

<span data-ttu-id="77f1c-130">Il n’est pas prévu de porter les technologies suivantes de .NET Framework vers .NET 5,0, mais il existe des alternatives dans .NET 5,0 :</span><span class="sxs-lookup"><span data-stu-id="77f1c-130">There are no plans to port the following technologies from .NET Framework to .NET 5.0, but there are alternatives in .NET 5.0:</span></span>

| <span data-ttu-id="77f1c-131">Technology</span><span class="sxs-lookup"><span data-stu-id="77f1c-131">Technology</span></span>            | <span data-ttu-id="77f1c-132">Alternative recommandée</span><span class="sxs-lookup"><span data-stu-id="77f1c-132">Recommended alternative</span></span>                                                                         |
|-----------------------|-------------------------------------------------------------------------------------------------|
| <span data-ttu-id="77f1c-133">Web Forms</span><span class="sxs-lookup"><span data-stu-id="77f1c-133">Web Forms</span></span>             | <span data-ttu-id="77f1c-134">ASP.NET Core [éblouissant](/aspnet/core/blazor) ou [Razor pages](/aspnet/core/tutorials/razor-pages)</span><span class="sxs-lookup"><span data-stu-id="77f1c-134">ASP.NET Core [Blazor](/aspnet/core/blazor) or [Razor Pages](/aspnet/core/tutorials/razor-pages)</span></span> |
| <span data-ttu-id="77f1c-135">Windows Workflow (WF)</span><span class="sxs-lookup"><span data-stu-id="77f1c-135">Windows Workflow (WF)</span></span> | [<span data-ttu-id="77f1c-136">CoreWF Open source</span><span class="sxs-lookup"><span data-stu-id="77f1c-136">Open-source CoreWF</span></span>](https://github.com/UiPath-Open/corewf)                                     |

### <a name="windows-communication-foundation"></a><span data-ttu-id="77f1c-137">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="77f1c-137">Windows Communication Foundation</span></span>

<span data-ttu-id="77f1c-138">L’implémentation d’origine de [Windows Communication Foundation (WCF)](../framework/wcf/index.md) était uniquement prise en charge sur Windows.</span><span class="sxs-lookup"><span data-stu-id="77f1c-138">The original implementation of [Windows Communication Foundation (WCF)](../framework/wcf/index.md) was only supported on Windows.</span></span> <span data-ttu-id="77f1c-139">Toutefois, il existe un port client disponible à partir de .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="77f1c-139">However, there is a client port available from the .NET Foundation.</span></span> <span data-ttu-id="77f1c-140">Il est entièrement [Open source](https://github.com/dotnet/wcf), multiplateforme et pris en charge par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="77f1c-140">It is entirely [open source](https://github.com/dotnet/wcf), cross platform, and supported by Microsoft.</span></span> <span data-ttu-id="77f1c-141">Les packages NuGet principaux sont répertoriés ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="77f1c-141">The core NuGet packages are listed below:</span></span>

- [<span data-ttu-id="77f1c-142">System.ServiceModel.Duplex</span><span class="sxs-lookup"><span data-stu-id="77f1c-142">System.ServiceModel.Duplex</span></span>](https://www.nuget.org/packages/System.ServiceModel.Duplex)
- [<span data-ttu-id="77f1c-143">System. ServiceModel. Federation</span><span class="sxs-lookup"><span data-stu-id="77f1c-143">System.ServiceModel.Federation</span></span>](https://www.nuget.org/packages/System.ServiceModel.Federation)
- [<span data-ttu-id="77f1c-144">System.ServiceModel.Http</span><span class="sxs-lookup"><span data-stu-id="77f1c-144">System.ServiceModel.Http</span></span>](https://www.nuget.org/packages/System.ServiceModel.Http)
- [<span data-ttu-id="77f1c-145">System.ServiceModel.NetTcp</span><span class="sxs-lookup"><span data-stu-id="77f1c-145">System.ServiceModel.NetTcp</span></span>](https://www.nuget.org/packages/System.ServiceModel.NetTcp)
- [<span data-ttu-id="77f1c-146">System.ServiceModel.Primitives</span><span class="sxs-lookup"><span data-stu-id="77f1c-146">System.ServiceModel.Primitives</span></span>](https://www.nuget.org/packages/System.ServiceModel.Primitives)
- [<span data-ttu-id="77f1c-147">System. ServiceModel. Security</span><span class="sxs-lookup"><span data-stu-id="77f1c-147">System.ServiceModel.Security</span></span>](https://www.nuget.org/packages/System.ServiceModel.Security)

<span data-ttu-id="77f1c-148">La Communauté gère les composants serveur qui complètent les bibliothèques clientes mentionnées ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="77f1c-148">The community maintains the server components that complement the aforementioned client libraries.</span></span> <span data-ttu-id="77f1c-149">Le référentiel GitHub se trouve sur [CoreWCF](https://github.com/CoreWCF/CoreWCF).</span><span class="sxs-lookup"><span data-stu-id="77f1c-149">The GitHub repository can be found at [CoreWCF](https://github.com/CoreWCF/CoreWCF).</span></span> <span data-ttu-id="77f1c-150">Les composants serveur ne sont _pas_ officiellement pris en charge par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="77f1c-150">The server components are _not_ officially supported by Microsoft.</span></span> <span data-ttu-id="77f1c-151">Pour une alternative à WCF, pensez à [gRPC](/aspnet/core/grpc).</span><span class="sxs-lookup"><span data-stu-id="77f1c-151">For an alternative to WCF, consider [gRPC](/aspnet/core/grpc).</span></span>

## <a name="net-50-doesnt-replace-net-standard"></a><span data-ttu-id="77f1c-152">.NET 5,0 ne remplace pas .NET Standard</span><span class="sxs-lookup"><span data-stu-id="77f1c-152">.NET 5.0 doesn't replace .NET Standard</span></span>

<span data-ttu-id="77f1c-153">Le développement d’une nouvelle application peut spécifier le `net5.0` moniker du Framework cible (TFM) pour tous les types de projets, y compris les bibliothèques de classes.</span><span class="sxs-lookup"><span data-stu-id="77f1c-153">New application development can specify the `net5.0` target framework moniker (TFM) for all project types, including class libraries.</span></span> <span data-ttu-id="77f1c-154">Le partage de code entre les charges de travail .NET 5 est simplifié en ce que vous avez tout ce dont vous avez besoin `net5.0` TFM.</span><span class="sxs-lookup"><span data-stu-id="77f1c-154">Sharing code between .NET 5 workloads is simplified in that all you need is the `net5.0` TFM.</span></span>

<span data-ttu-id="77f1c-155">Pour les applications et les bibliothèques .NET 5,0, le `net5.0` moniker du Framework cible (TFM) combine et remplace les `netcoreapp` `netstandard` TFM.</span><span class="sxs-lookup"><span data-stu-id="77f1c-155">For .NET 5.0 apps and libraries, the `net5.0` Target Framework Moniker (TFM) combines and replaces the `netcoreapp` and `netstandard` TFMs.</span></span> <span data-ttu-id="77f1c-156">Toutefois, si vous envisagez de partager du code entre des charges de travail .NET Framework, .NET Core et .NET 5, vous pouvez le faire en spécifiant `netstandard2.0` comme TFM.</span><span class="sxs-lookup"><span data-stu-id="77f1c-156">However, if you plan to share code between .NET Framework, .NET Core, and .NET 5 workloads, you can do so by specifying `netstandard2.0` as your TFM.</span></span> <span data-ttu-id="77f1c-157">Pour plus d'informations, consultez [.NET Standard](../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="77f1c-157">For more information, see [.NET Standard](../standard/net-standard.md).</span></span>

## <a name="c-updates"></a><span data-ttu-id="77f1c-158">Mises à jour C#</span><span class="sxs-lookup"><span data-stu-id="77f1c-158">C# updates</span></span>

<span data-ttu-id="77f1c-159">Les développeurs qui écrivent des applications .NET 5 auront accès à la version et aux fonctionnalités C# les plus récentes.</span><span class="sxs-lookup"><span data-stu-id="77f1c-159">Developers writing .NET 5 apps will have access to the latest C# version and features.</span></span> <span data-ttu-id="77f1c-160">.NET 5 est associé à C# 9, qui offre de nombreuses nouvelles fonctionnalités au langage.</span><span class="sxs-lookup"><span data-stu-id="77f1c-160">.NET 5 is paired with C# 9, which brings many new features to the language.</span></span> <span data-ttu-id="77f1c-161">Voici quelques points importants :</span><span class="sxs-lookup"><span data-stu-id="77f1c-161">Here are a few highlights:</span></span>

- <span data-ttu-id="77f1c-162">Enregistrements : types référence avec une sémantique d’égalité basée sur des valeurs et une mutation non destructrice prise en charge par une nouvelle `with` expression.</span><span class="sxs-lookup"><span data-stu-id="77f1c-162">Records: reference types with value-based equality semantics and non-destructive mutation supported by a new `with` expression.</span></span>
- <span data-ttu-id="77f1c-163">Critères spéciaux relationnels : étend les fonctionnalités de critères spéciaux aux opérateurs relationnels pour les évaluations comparatives et les expressions, y compris les modèles logiques, les nouveaux mots clés `and` , `or` et `not` .</span><span class="sxs-lookup"><span data-stu-id="77f1c-163">Relational pattern matching: Extends pattern matching capabilities to relational operators for comparative evaluations and expressions, including logical patterns - new keywords `and`, `or`, and `not`.</span></span>
- <span data-ttu-id="77f1c-164">Instructions de niveau supérieur : comme un moyen d’accélérer l’adoption et l’apprentissage de C#, la `Main` méthode peut être omise et l’application est aussi simple que les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="77f1c-164">Top-level statements: As a means for accelerating adoption and learning of C#, the `Main` method can be omitted and application as simple as the following is valid:</span></span>

   ```csharp
   System.Console.Write("Hello world!");
   ```

- <span data-ttu-id="77f1c-165">Pointeurs fonction : constructions de langage qui exposent les OpCodes de langage intermédiaire (IL) suivants : `ldftn` et `calli` .</span><span class="sxs-lookup"><span data-stu-id="77f1c-165">Function pointers: Language constructs that expose the following intermediate language (IL) opcodes: `ldftn` and `calli`.</span></span>

<span data-ttu-id="77f1c-166">Pour plus d’informations sur les fonctionnalités C# 9 disponibles, consultez [Nouveautés de c# 9](../csharp/whats-new/csharp-9.md).</span><span class="sxs-lookup"><span data-stu-id="77f1c-166">For more information on the available C# 9 features, see [What's new in C# 9](../csharp/whats-new/csharp-9.md).</span></span>

### <a name="source-generators"></a><span data-ttu-id="77f1c-167">Générateurs de sources</span><span class="sxs-lookup"><span data-stu-id="77f1c-167">Source generators</span></span>

<span data-ttu-id="77f1c-168">En plus de certaines des nouvelles fonctionnalités en C#, les générateurs de code source s’intègrent dans des projets de développement.</span><span class="sxs-lookup"><span data-stu-id="77f1c-168">In addition to some of the highlighted new C# features, source generators are making their way into developer projects.</span></span> <span data-ttu-id="77f1c-169">Les générateurs de source autorisent le code qui s’exécute pendant la compilation à inspecter votre programme et à produire des fichiers supplémentaires qui sont compilés avec le reste de votre code.</span><span class="sxs-lookup"><span data-stu-id="77f1c-169">Source generators allow code that runs during compilation to inspect your program and produce additional files that are compiled together with the rest of your code.</span></span>

<span data-ttu-id="77f1c-170">Pour plus d’informations sur les générateurs de source, consultez [Présentation des générateurs de source c#](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) et [exemples de générateur de source c#](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples).</span><span class="sxs-lookup"><span data-stu-id="77f1c-170">For more information on source generators, see [Introducing C# source generators](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) and [C# source generator samples](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples).</span></span>

## <a name="f-updates"></a><span data-ttu-id="77f1c-171">Mises à jour de F #</span><span class="sxs-lookup"><span data-stu-id="77f1c-171">F# updates</span></span>

<span data-ttu-id="77f1c-172">F # est le langage de programmation fonctionnel .NET et, avec .NET 5, les développeurs ont accès à F # 5.</span><span class="sxs-lookup"><span data-stu-id="77f1c-172">F# is the .NET functional programming language, and with .NET 5, developers have access to F# 5.</span></span> <span data-ttu-id="77f1c-173">Voici plusieurs nouvelles fonctionnalités de F # 5 :</span><span class="sxs-lookup"><span data-stu-id="77f1c-173">Here are several new features of F# 5:</span></span>

### <a name="interpolated-strings"></a><span data-ttu-id="77f1c-174">Chaînes interpolées</span><span class="sxs-lookup"><span data-stu-id="77f1c-174">Interpolated strings</span></span>

<span data-ttu-id="77f1c-175">À l’instar de la chaîne interpolée en C#, et même de JavaScript, F # prend en charge l’interpolation de chaîne de base.</span><span class="sxs-lookup"><span data-stu-id="77f1c-175">Similar to interpolated string in C#, and even JavaScript, F# supports basic string interpolation.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"{name} is {age} years old."
```

<span data-ttu-id="77f1c-176">Outre l’interpolation de chaîne de base, il existe une interpolation typée.</span><span class="sxs-lookup"><span data-stu-id="77f1c-176">In addition to basic string interpolation, there is typed interpolation.</span></span> <span data-ttu-id="77f1c-177">Avec l’interpolation typée, un type donné doit correspondre au spécificateur de format.</span><span class="sxs-lookup"><span data-stu-id="77f1c-177">With typed interpolation, a given type must match the format specifier.</span></span>

```fsharp
let name = "David"
let age = 36
let message = $"%s{name} is %d{age} years old."
```

<span data-ttu-id="77f1c-178">Cela est similaire à la [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) fonction qui met en forme une chaîne en fonction des entrées de type sécurisé.</span><span class="sxs-lookup"><span data-stu-id="77f1c-178">This is similar to the [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) function that formats a string based on type-safe inputs.</span></span> <!-- For more information, see [What's new in F# 5](fsharp/whats-new/fsharp-50.md). -->

## <a name="visual-basic-updates"></a><span data-ttu-id="77f1c-179">Mises à jour de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="77f1c-179">Visual Basic updates</span></span>

<span data-ttu-id="77f1c-180">Il n’existe aucune nouvelle fonctionnalité de langage pour Visual Basic dans .NET 5.</span><span class="sxs-lookup"><span data-stu-id="77f1c-180">There are no new language features for Visual Basic in .NET 5.</span></span> <span data-ttu-id="77f1c-181">Toutefois, avec .NET 5, la prise en charge Visual Basic est étendue à :</span><span class="sxs-lookup"><span data-stu-id="77f1c-181">However, with .NET 5, Visual Basic support is extended to:</span></span>

| <span data-ttu-id="77f1c-182">Description</span><span class="sxs-lookup"><span data-stu-id="77f1c-182">Description</span></span>                            | <span data-ttu-id="77f1c-183">Paramètre `dotnet new`</span><span class="sxs-lookup"><span data-stu-id="77f1c-183">`dotnet new` parameter</span></span> |
|----------------------------------------|------------------------|
| <span data-ttu-id="77f1c-184">Application console</span><span class="sxs-lookup"><span data-stu-id="77f1c-184">Console Application</span></span>                    | `console`              |
| <span data-ttu-id="77f1c-185">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="77f1c-185">Class library</span></span>                          | `classlib`             |
| <span data-ttu-id="77f1c-186">Application WPF</span><span class="sxs-lookup"><span data-stu-id="77f1c-186">WPF Application</span></span>                        | `wpf`                  |
| <span data-ttu-id="77f1c-187">Bibliothèque de classes WPF</span><span class="sxs-lookup"><span data-stu-id="77f1c-187">WPF Class library</span></span>                      | `wpflib`               |
| <span data-ttu-id="77f1c-188">Bibliothèque de contrôles personnalisés WPF</span><span class="sxs-lookup"><span data-stu-id="77f1c-188">WPF Custom Control Library</span></span>             | `wpfcustomcontrollib`  |
| <span data-ttu-id="77f1c-189">Bibliothèque de contrôles utilisateur WPF</span><span class="sxs-lookup"><span data-stu-id="77f1c-189">WPF User Control Library</span></span>               | `wpfusercontrollib`    |
| <span data-ttu-id="77f1c-190">Application Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="77f1c-190">Windows Forms (WinForms) Application</span></span>   | `winforms`             |
| <span data-ttu-id="77f1c-191">Bibliothèque de classes Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="77f1c-191">Windows Forms (WinForms) Class library</span></span> | `winformslib`          |
| <span data-ttu-id="77f1c-192">Projet de test unitaire</span><span class="sxs-lookup"><span data-stu-id="77f1c-192">Unit Test Project</span></span>                      | `mstest`               |
| <span data-ttu-id="77f1c-193">Projet de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="77f1c-193">NUnit 3 Test Project</span></span>                   | `nunit`                |
| <span data-ttu-id="77f1c-194">Élément de test NUnit 3</span><span class="sxs-lookup"><span data-stu-id="77f1c-194">NUnit 3 Test Item</span></span>                      | `nunit-test`           |
| <span data-ttu-id="77f1c-195">Projet de test xUnit</span><span class="sxs-lookup"><span data-stu-id="77f1c-195">xUnit Test Project</span></span>                     | `xunit`                |

<span data-ttu-id="77f1c-196">Pour plus d’informations sur les modèles de projet à partir de l’interface CLI .NET, consultez [`dotnet new`](tools/dotnet-new.md) .</span><span class="sxs-lookup"><span data-stu-id="77f1c-196">For more information on project templates from the .NET CLI, see [`dotnet new`](tools/dotnet-new.md).</span></span>

## <a name="systemtextjson-new-features"></a><span data-ttu-id="77f1c-197">System.Text.Jssur les nouvelles fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="77f1c-197">System.Text.Json new features</span></span>

<span data-ttu-id="77f1c-198">Il existe de nouvelles fonctionnalités dans et pour [System.Text.Jssur](../standard/serialization/system-text-json-overview.md):</span><span class="sxs-lookup"><span data-stu-id="77f1c-198">There are new features in and for [System.Text.Json](../standard/serialization/system-text-json-overview.md):</span></span>

- [<span data-ttu-id="77f1c-199">Conserver les références et gérer les références circulaires</span><span class="sxs-lookup"><span data-stu-id="77f1c-199">Preserve references and handle circular references</span></span>](../standard/serialization/system-text-json-how-to.md#preserve-references-and-handle-circular-references)
- [<span data-ttu-id="77f1c-200">Méthodes d’extension HttpClient et HttpContent</span><span class="sxs-lookup"><span data-stu-id="77f1c-200">HttpClient and HttpContent extension methods</span></span>](../standard/serialization/system-text-json-how-to.md#httpclient-and-httpcontent-extension-methods)
- [<span data-ttu-id="77f1c-201">Autoriser ou écrire des nombres entre guillemets</span><span class="sxs-lookup"><span data-stu-id="77f1c-201">Allow or write numbers in quotes</span></span>](../standard/serialization/system-text-json-how-to.md#allow-or-write-numbers-in-quotes)
- [<span data-ttu-id="77f1c-202">Prendre en charge les types immuables et les enregistrements C# 9</span><span class="sxs-lookup"><span data-stu-id="77f1c-202">Support immutable types and C# 9 Records</span></span>](../standard/serialization/system-text-json-how-to.md#immutable-types-and-records)
- [<span data-ttu-id="77f1c-203">Prendre en charge les accesseurs de propriété non publics</span><span class="sxs-lookup"><span data-stu-id="77f1c-203">Support non-public property accessors</span></span>](../standard/serialization/system-text-json-how-to.md#non-public-property-accessors)
- [<span data-ttu-id="77f1c-204">champs de support</span><span class="sxs-lookup"><span data-stu-id="77f1c-204">support fields</span></span>](../standard/serialization/system-text-json-how-to.md#include-fields)
- [<span data-ttu-id="77f1c-205">Ignorer conditionnellement les propriétés</span><span class="sxs-lookup"><span data-stu-id="77f1c-205">Conditionally ignore properties</span></span>](../standard/serialization/system-text-json-how-to.md#ignore-properties)
- [<span data-ttu-id="77f1c-206">Prise en charge des dictionnaires non-clés-chaîne</span><span class="sxs-lookup"><span data-stu-id="77f1c-206">Support non-string-key dictionaries</span></span>](../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md#dictionary-with-non-string-key)
- [<span data-ttu-id="77f1c-207">Autoriser les convertisseurs personnalisés à gérer la valeur null</span><span class="sxs-lookup"><span data-stu-id="77f1c-207">Allow custom converters to handle null</span></span>](../standard/serialization/system-text-json-converters-how-to.md#handle-null-values)
- [<span data-ttu-id="77f1c-208">Copier JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="77f1c-208">Copy JsonSerializerOptions</span></span>](../standard/serialization/system-text-json-how-to.md#copy-jsonserializeroptions)
- [<span data-ttu-id="77f1c-209">Créer des JsonSerializerOptions avec des valeurs par défaut Web</span><span class="sxs-lookup"><span data-stu-id="77f1c-209">Create JsonSerializerOptions with web defaults</span></span>](../standard/serialization/system-text-json-how-to.md#web-defaults-for-jsonserializeroptions)

## <a name="see-also"></a><span data-ttu-id="77f1c-210">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77f1c-210">See also</span></span>

- [<span data-ttu-id="77f1c-211">Le trajet vers un .NET</span><span class="sxs-lookup"><span data-stu-id="77f1c-211">The Journey to one .NET</span></span>](https://channel9.msdn.com/Events/Build/2020/BOD106)
- [<span data-ttu-id="77f1c-212">Améliorations des performances dans .NET 5</span><span class="sxs-lookup"><span data-stu-id="77f1c-212">Performance improvements in .NET 5</span></span>](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
- [<span data-ttu-id="77f1c-213">Télécharger le Kit de développement logiciel (SDK) .NET</span><span class="sxs-lookup"><span data-stu-id="77f1c-213">Download the .NET SDK</span></span>](https://dotnet.microsoft.com/download)
