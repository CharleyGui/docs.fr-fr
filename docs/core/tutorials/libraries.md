---
title: Développer des bibliothèques avec l’interface CLI .NET
description: Découvrez comment créer des bibliothèques .NET à l’aide de l’interface CLI .NET. Vous allez créer une bibliothèque prenant en charge plusieurs frameworks.
author: cartermp
ms.topic: how-to
ms.date: 12/14/2020
ms.openlocfilehash: 6f4c1feac7630a6a0250e4b0b39ef01152f5a400
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633674"
---
# <a name="develop-libraries-with-the-net-cli"></a><span data-ttu-id="b77ac-104">Développer des bibliothèques avec l’interface CLI .NET</span><span class="sxs-lookup"><span data-stu-id="b77ac-104">Develop libraries with the .NET CLI</span></span>

<span data-ttu-id="b77ac-105">Cet article explique comment écrire des bibliothèques pour .NET à l’aide de l’interface CLI .NET.</span><span class="sxs-lookup"><span data-stu-id="b77ac-105">This article covers how to write libraries for .NET using the .NET CLI.</span></span> <span data-ttu-id="b77ac-106">L’interface CLI fournit une expérience efficace et de bas niveau qui fonctionne sur tous les systèmes d’exploitation pris en charge.</span><span class="sxs-lookup"><span data-stu-id="b77ac-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="b77ac-107">Vous pouvez toujours créer des bibliothèques avec Visual Studio, et si c’est ce que vous préférez, [consultez le guide Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="b77ac-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](library-with-visual-studio.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b77ac-108">Prérequis</span><span class="sxs-lookup"><span data-stu-id="b77ac-108">Prerequisites</span></span>

<span data-ttu-id="b77ac-109">[Le kit de développement logiciel (SDK) .net et l’interface CLI](https://dotnet.microsoft.com/download) doivent être installés sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="b77ac-109">You need [the .NET SDK and CLI](https://dotnet.microsoft.com/download) installed on your machine.</span></span>

<span data-ttu-id="b77ac-110">Pour accéder aux sections de ce document concernant les versions du .NET Framework, vous devez installer le [.NET Framework](https://dotnet.microsoft.com) sur un ordinateur Windows.</span><span class="sxs-lookup"><span data-stu-id="b77ac-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](https://dotnet.microsoft.com) installed on a Windows machine.</span></span>

<span data-ttu-id="b77ac-111">En outre, si vous souhaitez prendre en charge des cibles de .NET Framework plus anciennes, vous devez installer des packs de ciblage ou des packs de développement à partir de la [page des Archives de téléchargement .net](https://dotnet.microsoft.com/download/archives).</span><span class="sxs-lookup"><span data-stu-id="b77ac-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting packs or developer packs from the [.NET download archives page](https://dotnet.microsoft.com/download/archives).</span></span> <span data-ttu-id="b77ac-112">Reportez-vous au tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="b77ac-112">Refer to this table:</span></span>

| <span data-ttu-id="b77ac-113">Version du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b77ac-113">.NET Framework version</span></span> | <span data-ttu-id="b77ac-114">À télécharger</span><span class="sxs-lookup"><span data-stu-id="b77ac-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="b77ac-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="b77ac-115">4.6.1</span></span>                  | <span data-ttu-id="b77ac-116">Pack de ciblage .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="b77ac-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="b77ac-117">4,6</span><span class="sxs-lookup"><span data-stu-id="b77ac-117">4.6</span></span>                    | <span data-ttu-id="b77ac-118">Pack de ciblage .NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="b77ac-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="b77ac-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="b77ac-119">4.5.2</span></span>                  | <span data-ttu-id="b77ac-120">Pack du développeur .NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="b77ac-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="b77ac-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="b77ac-121">4.5.1</span></span>                  | <span data-ttu-id="b77ac-122">Pack du développeur .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="b77ac-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="b77ac-123">4.5</span><span class="sxs-lookup"><span data-stu-id="b77ac-123">4.5</span></span>                    | <span data-ttu-id="b77ac-124">SDK Windows pour Windows 8</span><span class="sxs-lookup"><span data-stu-id="b77ac-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="b77ac-125">4.0</span><span class="sxs-lookup"><span data-stu-id="b77ac-125">4.0</span></span>                    | <span data-ttu-id="b77ac-126">SDK pour Windows 7 et .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="b77ac-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="b77ac-127">2.0, 3.0 et 3.5</span><span class="sxs-lookup"><span data-stu-id="b77ac-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="b77ac-128">Runtime .NET Framework 3.5 SP1 (ou version Windows 8+)</span><span class="sxs-lookup"><span data-stu-id="b77ac-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-net-50-or-net-standard"></a><span data-ttu-id="b77ac-129">Comment cibler .NET 5,0 ou .NET Standard</span><span class="sxs-lookup"><span data-stu-id="b77ac-129">How to target .NET 5.0 or .NET Standard</span></span>

<span data-ttu-id="b77ac-130">Vous contrôlez la version cible de .NET Framework de votre projet en l’ajoutant à votre fichier projet (*. csproj* ou *. fsproj*).</span><span class="sxs-lookup"><span data-stu-id="b77ac-130">You control your project's target framework by adding it to your project file (*.csproj* or *.fsproj*).</span></span> <span data-ttu-id="b77ac-131">Pour obtenir des conseils sur le choix entre le ciblage de .NET 5,0 ou de .NET Standard [, consultez .net 5 et .NET standard](../../standard/net-standard.md#net-5-and-net-standard).</span><span class="sxs-lookup"><span data-stu-id="b77ac-131">For guidance on how to choose between targeting .NET 5.0 or .NET Standard see [.NET 5 and .NET Standard](../../standard/net-standard.md#net-5-and-net-standard).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>
</Project>
```

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="b77ac-132">Si vous souhaitez cibler .NET Framework versions 4,0 ou antérieures, ou si vous souhaitez utiliser une API disponible dans .NET Framework mais pas dans .NET Standard (par exemple, `System.Drawing` ), lisez les sections suivantes et découvrez comment effectuer une MULTICIBLAGE.</span><span class="sxs-lookup"><span data-stu-id="b77ac-132">If you want to target .NET Framework versions 4.0 or below, or you wish to use an API available in .NET Framework but not in .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-net-framework"></a><span data-ttu-id="b77ac-133">Comment cibler .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b77ac-133">How to target .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="b77ac-134">Ces instructions supposent que vous avez .NET Framework installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b77ac-134">These instructions assume you have .NET Framework installed on your machine.</span></span> <span data-ttu-id="b77ac-135">Reportez-vous aux [Prérequis](#prerequisites) pour installer les dépendances.</span><span class="sxs-lookup"><span data-stu-id="b77ac-135">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="b77ac-136">N’oubliez pas que certaines des versions de .NET Framework utilisées ici ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="b77ac-136">Keep in mind that some of the .NET Framework versions used here are no longer supported.</span></span> <span data-ttu-id="b77ac-137">Reportez-vous au [Forum aux questions sur la politique de support de Microsoft .NET Framework](https://support.microsoft.com/gp/framework_faq/en-us) concernant les versions non prises en charge.</span><span class="sxs-lookup"><span data-stu-id="b77ac-137">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="b77ac-138">Si vous voulez atteindre le nombre maximal de développeurs et de projets, utilisez .NET Framework 4,0 comme cible de référence.</span><span class="sxs-lookup"><span data-stu-id="b77ac-138">If you want to reach the maximum number of developers and projects, use .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="b77ac-139">Pour cibler .NET Framework, commencez par utiliser le moniker du Framework cible (TFM) approprié qui correspond à la version .NET Framework que vous souhaitez prendre en charge.</span><span class="sxs-lookup"><span data-stu-id="b77ac-139">To target .NET Framework, begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

| <span data-ttu-id="b77ac-140">Version du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b77ac-140">.NET Framework version</span></span> | <span data-ttu-id="b77ac-141">TFM</span><span class="sxs-lookup"><span data-stu-id="b77ac-141">TFM</span></span>      |
| ---------------------- | -------- |
| <span data-ttu-id="b77ac-142">.NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="b77ac-142">.NET Framework 2.0</span></span>     | `net20`  |
| <span data-ttu-id="b77ac-143">.NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="b77ac-143">.NET Framework 3.0</span></span>     | `net30`  |
| <span data-ttu-id="b77ac-144">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="b77ac-144">.NET Framework 3.5</span></span>     | `net35`  |
| <span data-ttu-id="b77ac-145">.NET Framework 4.0</span><span class="sxs-lookup"><span data-stu-id="b77ac-145">.NET Framework 4.0</span></span>     | `net40`  |
| <span data-ttu-id="b77ac-146">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="b77ac-146">.NET Framework 4.5</span></span>     | `net45`  |
| <span data-ttu-id="b77ac-147">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="b77ac-147">.NET Framework 4.5.1</span></span>   | `net451` |
| <span data-ttu-id="b77ac-148">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="b77ac-148">.NET Framework 4.5.2</span></span>   | `net452` |
| <span data-ttu-id="b77ac-149">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="b77ac-149">.NET Framework 4.6</span></span>     | `net46`  |
| <span data-ttu-id="b77ac-150">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="b77ac-150">.NET Framework 4.6.1</span></span>   | `net461` |
| <span data-ttu-id="b77ac-151">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="b77ac-151">.NET Framework 4.6.2</span></span>   | `net462` |
| <span data-ttu-id="b77ac-152">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="b77ac-152">.NET Framework 4.7</span></span>     | `net47`  |
| <span data-ttu-id="b77ac-153">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="b77ac-153">.NET Framework 4.8</span></span>     | `net48`  |

<span data-ttu-id="b77ac-154">Insérez ensuite ce Moniker du Framework cible dans la section `TargetFramework` de votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="b77ac-154">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="b77ac-155">Par exemple, voici comment écrire une bibliothèque qui cible .NET Framework 4,0 :</span><span class="sxs-lookup"><span data-stu-id="b77ac-155">For example, here's how you would write a library that targets .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="b77ac-156">C’est tout !</span><span class="sxs-lookup"><span data-stu-id="b77ac-156">And that's it!</span></span> <span data-ttu-id="b77ac-157">Bien que cela soit compilé uniquement pour .NET Framework 4, vous pouvez utiliser la bibliothèque sur des versions plus récentes de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b77ac-157">Although this compiled only for .NET Framework 4, you can use the library on newer versions of .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="b77ac-158">Comment multicibler</span><span class="sxs-lookup"><span data-stu-id="b77ac-158">How to multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="b77ac-159">Les instructions suivantes supposent que le .NET Framework est installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b77ac-159">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="b77ac-160">Reportez-vous à la section [Prérequis](#prerequisites) pour savoir quelles dépendances doivent être installées et à partir d’où les télécharger.</span><span class="sxs-lookup"><span data-stu-id="b77ac-160">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="b77ac-161">Vous devrez peut-être cibler des versions antérieures du .NET Framework lorsque votre projet prend en charge les .NET Framework et .NET.</span><span class="sxs-lookup"><span data-stu-id="b77ac-161">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET.</span></span> <span data-ttu-id="b77ac-162">Dans ce scénario, si vous voulez utiliser des API et des constructions de langage plus récentes pour des cibles plus récentes, utilisez des directives `#if` dans votre code.</span><span class="sxs-lookup"><span data-stu-id="b77ac-162">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="b77ac-163">Vous pouvez aussi avoir besoin d’ajouter différents packages et différentes dépendances pour chaque plateforme que vous ciblez pour inclure les différentes API nécessaires à chaque cas.</span><span class="sxs-lookup"><span data-stu-id="b77ac-163">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="b77ac-164">Supposons, par exemple, que vous avez une bibliothèque qui effectue des opérations réseau sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="b77ac-164">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="b77ac-165">Pour .NET Standard et les versions .NET Framework 4.5 ou ultérieures, vous pouvez utiliser la classe `HttpClient` à partir de l’espace de noms `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="b77ac-165">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="b77ac-166">Toutefois, les versions antérieures du .NET Framework ne disposent pas de la classe `HttpClient`. Vous pourriez donc utiliser la classe `WebClient` à partir de l’espace de noms `System.Net` à la place.</span><span class="sxs-lookup"><span data-stu-id="b77ac-166">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="b77ac-167">Voici à quoi peut ressembler votre fichier projet :</span><span class="sxs-lookup"><span data-stu-id="b77ac-167">Your project file could look like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netstandard2.0;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.0 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net40'">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.5 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net45'">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="b77ac-168">Notez trois changements majeurs ici :</span><span class="sxs-lookup"><span data-stu-id="b77ac-168">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="b77ac-169">Le nœud `TargetFramework` a été remplacé par `TargetFrameworks`, et trois Monikers du Framework cible sont exprimés à l’intérieur.</span><span class="sxs-lookup"><span data-stu-id="b77ac-169">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="b77ac-170">Un nœud `<ItemGroup>` est présent pour l’extraction de cible `net40` dans une référence .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b77ac-170">There is an `<ItemGroup>` node for the `net40` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="b77ac-171">Un nœud `<ItemGroup>` est présent pour l’extraction de cible `net45` dans deux références .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b77ac-171">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="b77ac-172">Le système de build est informé des symboles de préprocesseur suivants utilisés dans les directives `#if`:</span><span class="sxs-lookup"><span data-stu-id="b77ac-172">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

<span data-ttu-id="b77ac-173">Voici un exemple d’utilisation de la compilation conditionnelle par cible :</span><span class="sxs-lookup"><span data-stu-id="b77ac-173">Here is an example making use of conditional compilation per-target:</span></span>

```csharp
using System;
using System.Text.RegularExpressions;
#if NET40
// This only compiles for the .NET Framework 4 targets
using System.Net;
#else
 // This compiles for all other targets
using System.Net.Http;
using System.Threading.Tasks;
#endif

namespace MultitargetLib
{
    public class Library
    {
#if NET40
        private readonly WebClient _client = new WebClient();
        private readonly object _locker = new object();
#else
        private readonly HttpClient _client = new HttpClient();
#endif

#if NET40
        // .NET Framework 4.0 does not have async/await
        public string GetDotNetCount()
        {
            string url = "https://www.dotnetfoundation.org/";

            var uri = new Uri(url);

            string result = "";

            // Lock here to provide thread-safety.
            lock(_locker)
            {
                result = _client.DownloadString(uri);
            }

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"Dotnet Foundation mentions .NET {dotNetCount} times!";
        }
#else
        // .NET Framework 4.5+ can use async/await!
        public async Task<string> GetDotNetCountAsync()
        {
            string url = "https://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

<span data-ttu-id="b77ac-174">Si vous générez ce projet avec `dotnet build`, notez la présence de trois répertoires sous le dossier `bin/` :</span><span class="sxs-lookup"><span data-stu-id="b77ac-174">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard2.0/
```

<span data-ttu-id="b77ac-175">Chacun d’eux contient les `.dll` fichiers de chaque cible.</span><span class="sxs-lookup"><span data-stu-id="b77ac-175">Each of these contains the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net"></a><span data-ttu-id="b77ac-176">Comment tester les bibliothèques sur .NET</span><span class="sxs-lookup"><span data-stu-id="b77ac-176">How to test libraries on .NET</span></span>

<span data-ttu-id="b77ac-177">Il est important de pouvoir effectuer des tests sur plusieurs plateformes.</span><span class="sxs-lookup"><span data-stu-id="b77ac-177">It's important to be able to test across platforms.</span></span> <span data-ttu-id="b77ac-178">Vous pouvez utiliser [xUnit](https://xunit.net/) ou MSTest dans leur version d’origine.</span><span class="sxs-lookup"><span data-stu-id="b77ac-178">You can use either [xUnit](https://xunit.net/) or MSTest out of the box.</span></span> <span data-ttu-id="b77ac-179">Les deux sont parfaitement adaptées au test unitaire de votre bibliothèque sur .NET.</span><span class="sxs-lookup"><span data-stu-id="b77ac-179">Both are perfectly suitable for unit testing your library on .NET.</span></span> <span data-ttu-id="b77ac-180">La façon dont vous configurez votre solution avec des projets de test dépend de la [structure de votre solution](#structuring-a-solution).</span><span class="sxs-lookup"><span data-stu-id="b77ac-180">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="b77ac-181">L’exemple suivant part du principe que les répertoires de test et source résident dans le même répertoire de premier niveau.</span><span class="sxs-lookup"><span data-stu-id="b77ac-181">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="b77ac-182">Cela utilise certaines commandes [CLI .net](../tools/index.md) .</span><span class="sxs-lookup"><span data-stu-id="b77ac-182">This uses some [.NET CLI](../tools/index.md) commands.</span></span> <span data-ttu-id="b77ac-183">Pour plus d’informations, consultez [dotnet new](../tools/dotnet-new.md) et [dotnet sln](../tools/dotnet-sln.md).</span><span class="sxs-lookup"><span data-stu-id="b77ac-183">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="b77ac-184">Configurez votre solution.</span><span class="sxs-lookup"><span data-stu-id="b77ac-184">Set up your solution.</span></span> <span data-ttu-id="b77ac-185">Pour cela, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="b77ac-185">You can do so with the following commands:</span></span>

   ```dotnetcli
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="b77ac-186">Cette commande crée des projets et les relie dans une solution.</span><span class="sxs-lookup"><span data-stu-id="b77ac-186">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="b77ac-187">Votre répertoire pour `SolutionWithSrcAndTest` doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="b77ac-187">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="b77ac-188">Accédez au répertoire du projet de test et ajoutez une référence à `MyProject.Test` à partir de `MyProject`.</span><span class="sxs-lookup"><span data-stu-id="b77ac-188">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```dotnetcli
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="b77ac-189">Restaurez les packages et générez les projets :</span><span class="sxs-lookup"><span data-stu-id="b77ac-189">Restore packages and build projects:</span></span>

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

1. <span data-ttu-id="b77ac-190">Exécutez la commande `dotnet test` pour vérifier que xUnit s’exécute.</span><span class="sxs-lookup"><span data-stu-id="b77ac-190">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="b77ac-191">Si vous avez choisi d’utiliser MSTest, le Test Runner de console MSTest doit s’exécuter à la place.</span><span class="sxs-lookup"><span data-stu-id="b77ac-191">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>

<span data-ttu-id="b77ac-192">C’est tout !</span><span class="sxs-lookup"><span data-stu-id="b77ac-192">And that's it!</span></span> <span data-ttu-id="b77ac-193">Vous pouvez maintenant tester votre bibliothèque sur toutes les plateformes à l’aide d’outils en ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b77ac-193">You can now test your library across all platforms using command-line tools.</span></span> <span data-ttu-id="b77ac-194">Maintenant que vous avez tout configuré, le test de votre bibliothèque est très simple :</span><span class="sxs-lookup"><span data-stu-id="b77ac-194">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="b77ac-195">Apportez des modifications à votre bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="b77ac-195">Make changes to your library.</span></span>
1. <span data-ttu-id="b77ac-196">Exécutez les tests à partir de la ligne de commande, dans votre répertoire de test, avec la commande `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="b77ac-196">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="b77ac-197">Votre code est automatiquement régénéré quand vous appelez la commande `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="b77ac-197">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="b77ac-198">Comment utiliser plusieurs projets</span><span class="sxs-lookup"><span data-stu-id="b77ac-198">How to use multiple projects</span></span>

<span data-ttu-id="b77ac-199">Les bibliothèques plus volumineuses ont souvent besoin de placer des fonctionnalités dans différents projets.</span><span class="sxs-lookup"><span data-stu-id="b77ac-199">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="b77ac-200">Imaginez que vous vouliez créer une bibliothèque pouvant être utilisée dans idiomatique C# et F #.</span><span class="sxs-lookup"><span data-stu-id="b77ac-200">Imagine you want to build a library that could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="b77ac-201">Cela signifierait que les consommateurs de votre bibliothèque le consomment de manière naturelle pour C# ou F #.</span><span class="sxs-lookup"><span data-stu-id="b77ac-201">That would mean that consumers of your library consume it in ways that are natural to C# or F#.</span></span> <span data-ttu-id="b77ac-202">Par exemple, en C#, vous pouvez utiliser la bibliothèque de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="b77ac-202">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="b77ac-203">En F#, le code peut se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="b77ac-203">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="b77ac-204">Les scénarios de consommation tels que celui-ci signifient que les API auxquelles vous accédez ont une structure différente en C# et F#.</span><span class="sxs-lookup"><span data-stu-id="b77ac-204">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="b77ac-205">Pour réaliser ceci, il est courant de factoriser toute la logique d’une bibliothèque dans un projet principal et d’avoir des projets C# et F# définissant les couches API qui effectuent des appels à ce projet principal.</span><span class="sxs-lookup"><span data-stu-id="b77ac-205">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="b77ac-206">Le reste de la section utilise les noms suivants :</span><span class="sxs-lookup"><span data-stu-id="b77ac-206">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="b77ac-207">**AwesomeLibrary. Core** : projet principal qui contient toute la logique de la bibliothèque</span><span class="sxs-lookup"><span data-stu-id="b77ac-207">**AwesomeLibrary.Core** - A core project that contains all logic for the library</span></span>
* <span data-ttu-id="b77ac-208">**AwesomeLibrary.CSharp** : projet avec des API publiques destinées à être consommées en C#</span><span class="sxs-lookup"><span data-stu-id="b77ac-208">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="b77ac-209">**AwesomeLibrary.CSharp** : projet avec des API publiques destinées à être consommées en F#</span><span class="sxs-lookup"><span data-stu-id="b77ac-209">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="b77ac-210">Vous pouvez exécuter les commandes suivantes dans votre terminal pour produire la même structure que ce guide :</span><span class="sxs-lookup"><span data-stu-id="b77ac-210">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

```dotnetcli
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang "F#"
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

<span data-ttu-id="b77ac-211">Cela permet d’ajouter les trois projets ci-dessus et un fichier solution qui les lie.</span><span class="sxs-lookup"><span data-stu-id="b77ac-211">This will add the three projects above and a solution file that links them together.</span></span> <span data-ttu-id="b77ac-212">La création du fichier solution et la liaison de projets vous permettent de restaurer et de générer des projets à partir d’un niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="b77ac-212">Creating the solution file and linking projects will allow you to restore and build projects from a top level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="b77ac-213">Références entre projets</span><span class="sxs-lookup"><span data-stu-id="b77ac-213">Project-to-project referencing</span></span>

<span data-ttu-id="b77ac-214">La meilleure façon de référencer un projet consiste à utiliser l’interface de ligne de commande .NET pour ajouter une référence de projet.</span><span class="sxs-lookup"><span data-stu-id="b77ac-214">The best way to reference a project is to use the .NET CLI to add a project reference.</span></span> <span data-ttu-id="b77ac-215">À partir des répertoires de projet **AwesomeLibrary.CSharp** et de **AwesomeLibrary.FSharp**, vous pouvez exécuter la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="b77ac-215">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="b77ac-216">Les fichiers projet pour **AwesomeLibrary.CSharp** et **AwesomeLibrary.FSharp** référencent désormais **AwesomeLibrary.Core** comme cible de `ProjectReference`.</span><span class="sxs-lookup"><span data-stu-id="b77ac-216">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="b77ac-217">Pour le vérifier, confirmez la présence des éléments suivants dans les fichiers projet :</span><span class="sxs-lookup"><span data-stu-id="b77ac-217">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="b77ac-218">Vous pouvez ajouter manuellement cette section à chaque fichier projet si vous préférez ne pas utiliser l’interface de ligne de commande .NET.</span><span class="sxs-lookup"><span data-stu-id="b77ac-218">You can add this section to each project file manually if you prefer not to use the .NET CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="b77ac-219">Structurer une solution</span><span class="sxs-lookup"><span data-stu-id="b77ac-219">Structuring a solution</span></span>

<span data-ttu-id="b77ac-220">Un autre aspect important des solutions à projets multiples est la mise en place d’une bonne structure de projet globale.</span><span class="sxs-lookup"><span data-stu-id="b77ac-220">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="b77ac-221">Vous pouvez organiser le code comme vous le souhaitez, et tant que vous liez chaque projet à votre fichier solution avec `dotnet sln add`, vous pouvez exécuter `dotnet restore` et `dotnet build` au niveau de la solution.</span><span class="sxs-lookup"><span data-stu-id="b77ac-221">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
