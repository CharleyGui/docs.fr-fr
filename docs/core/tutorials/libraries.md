---
title: Développer des bibliothèques avec le CLI .NET Core
description: Découvrez comment créer des bibliothèques .NET Core à l’aide de l’CLI .NET Core. Vous allez créer une bibliothèque prenant en charge plusieurs frameworks.
author: cartermp
ms.topic: how-to
ms.date: 05/01/2017
ms.openlocfilehash: e98ce9e08c8d92bb4c89348e21cece60de811848
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223707"
---
# <a name="develop-libraries-with-the-net-core-cli"></a><span data-ttu-id="ad7bb-104">Développer des bibliothèques avec le CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="ad7bb-104">Develop libraries with the .NET Core CLI</span></span>

<span data-ttu-id="ad7bb-105">Cet article explique comment écrire des bibliothèques pour .NET à l’aide de l’CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-105">This article covers how to write libraries for .NET using the .NET Core CLI.</span></span> <span data-ttu-id="ad7bb-106">L’interface CLI fournit une expérience efficace et de bas niveau qui fonctionne sur tous les systèmes d’exploitation pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="ad7bb-107">Vous pouvez toujours créer des bibliothèques avec Visual Studio, et si c’est ce que vous préférez, [consultez le guide Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="ad7bb-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](library-with-visual-studio.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ad7bb-108">Prérequis</span><span class="sxs-lookup"><span data-stu-id="ad7bb-108">Prerequisites</span></span>

<span data-ttu-id="ad7bb-109">[Le SDK .NET Core et l’interface CLI](https://dotnet.microsoft.com/download) doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-109">You need [the .NET Core SDK and CLI](https://dotnet.microsoft.com/download) installed on your machine.</span></span>

<span data-ttu-id="ad7bb-110">Pour accéder aux sections de ce document concernant les versions du .NET Framework, vous devez installer le [.NET Framework](https://dotnet.microsoft.com) sur un ordinateur Windows.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](https://dotnet.microsoft.com) installed on a Windows machine.</span></span>

<span data-ttu-id="ad7bb-111">En outre, si vous souhaitez prendre en charge des cibles de .NET Framework plus anciennes, vous devez installer des packs de ciblage ou des packs de développement à partir de la [page des Archives de téléchargement .net](https://dotnet.microsoft.com/download/archives).</span><span class="sxs-lookup"><span data-stu-id="ad7bb-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting packs or developer packs from the [.NET download archives page](https://dotnet.microsoft.com/download/archives).</span></span> <span data-ttu-id="ad7bb-112">Reportez-vous au tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="ad7bb-112">Refer to this table:</span></span>

| <span data-ttu-id="ad7bb-113">Version du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ad7bb-113">.NET Framework version</span></span> | <span data-ttu-id="ad7bb-114">À télécharger</span><span class="sxs-lookup"><span data-stu-id="ad7bb-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="ad7bb-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="ad7bb-115">4.6.1</span></span>                  | <span data-ttu-id="ad7bb-116">Pack de ciblage .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="ad7bb-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="ad7bb-117">4.6</span><span class="sxs-lookup"><span data-stu-id="ad7bb-117">4.6</span></span>                    | <span data-ttu-id="ad7bb-118">Pack de ciblage .NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="ad7bb-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="ad7bb-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="ad7bb-119">4.5.2</span></span>                  | <span data-ttu-id="ad7bb-120">Pack du développeur .NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="ad7bb-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="ad7bb-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="ad7bb-121">4.5.1</span></span>                  | <span data-ttu-id="ad7bb-122">Pack du développeur .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="ad7bb-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="ad7bb-123">4.5</span><span class="sxs-lookup"><span data-stu-id="ad7bb-123">4.5</span></span>                    | <span data-ttu-id="ad7bb-124">SDK Windows pour Windows 8</span><span class="sxs-lookup"><span data-stu-id="ad7bb-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="ad7bb-125">4.0</span><span class="sxs-lookup"><span data-stu-id="ad7bb-125">4.0</span></span>                    | <span data-ttu-id="ad7bb-126">SDK pour Windows 7 et .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="ad7bb-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="ad7bb-127">2.0, 3.0 et 3.5</span><span class="sxs-lookup"><span data-stu-id="ad7bb-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="ad7bb-128">Runtime .NET Framework 3.5 SP1 (ou version Windows 8+)</span><span class="sxs-lookup"><span data-stu-id="ad7bb-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-net-standard"></a><span data-ttu-id="ad7bb-129">Comment cibler .NET Standard</span><span class="sxs-lookup"><span data-stu-id="ad7bb-129">How to target .NET Standard</span></span>

<span data-ttu-id="ad7bb-130">Si vous n’êtes pas familiarisé avec .NET Standard, reportez-vous à [.NET standard](../../standard/net-standard.md) pour en savoir plus.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-130">If you're not familiar with .NET Standard, refer to [.NET Standard](../../standard/net-standard.md) to learn more.</span></span>

<span data-ttu-id="ad7bb-131">Dans cet article, il existe un tableau qui mappe .NET Standard versions à différentes implémentations :</span><span class="sxs-lookup"><span data-stu-id="ad7bb-131">In that article, there is a table that maps .NET Standard versions to various implementations:</span></span>

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

<span data-ttu-id="ad7bb-132">Voici ce que signifie ce tableau dans le processus de création d’une bibliothèque :</span><span class="sxs-lookup"><span data-stu-id="ad7bb-132">Here's what this table means for the purposes of creating a library:</span></span>

<span data-ttu-id="ad7bb-133">La version de .NET Standard que vous choisissez est un compromis entre l’accès aux API les plus récentes et la possibilité de cibler davantage d’implémentations .NET et de versions de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-133">The version of .NET Standard you pick will be a tradeoff between access to the newest APIs and the ability to target more .NET implementations and .NET Standard versions.</span></span> <span data-ttu-id="ad7bb-134">Vous contrôlez la plage de versions et de plateformes ciblables en sélectionnant une version de `netstandardX.X` (où `X.X` est un numéro de version) et en l’ajoutant à votre fichier projet ( `.csproj` ou `.fsproj` ).</span><span class="sxs-lookup"><span data-stu-id="ad7bb-134">You control the range of targetable platforms and versions by picking a version of `netstandardX.X` (where `X.X` is a version number) and adding it to your project file (`.csproj` or `.fsproj`).</span></span>

<span data-ttu-id="ad7bb-135">Vous avez trois options principales pour cibler .NET Standard, en fonction de vos besoins.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-135">You have three primary options when targeting .NET Standard, depending on your needs.</span></span>

1. <span data-ttu-id="ad7bb-136">Vous pouvez utiliser la version par défaut de .NET Standard fournie par les modèles, `netstandard1.4` , qui vous permet d’accéder à la plupart des API sur .NET standard tout en étant toujours compatibles avec UWP, .NET Framework 4.6.1 et .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-136">You can use the default version of .NET Standard supplied by templates, `netstandard1.4`, which gives you access to most APIs on .NET Standard while still being compatible with UWP, .NET Framework 4.6.1, and .NET Standard 2.0.</span></span>

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. <span data-ttu-id="ad7bb-137">Vous pouvez utiliser une version inférieure ou supérieure de .NET Standard en modifiant la valeur dans le `TargetFramework` nœud de votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-137">You can use a lower or higher version of .NET Standard by modifying the value in the `TargetFramework` node of your project file.</span></span>

    <span data-ttu-id="ad7bb-138">Les versions .NET standard sont à compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-138">.NET Standard versions are backward compatible.</span></span> <span data-ttu-id="ad7bb-139">Cela signifie que les bibliothèques `netstandard1.0` s’exécutent sur les plateformes `netstandard1.1` et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-139">That means that `netstandard1.0` libraries run on `netstandard1.1` platforms and higher.</span></span> <span data-ttu-id="ad7bb-140">Toutefois, il n’existe pas de compatibilité ascendante.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-140">However, there is no forward compatibility.</span></span> <span data-ttu-id="ad7bb-141">Les plateformes de .NET Standard inférieures ne peuvent pas faire référence à des plateformes supérieures.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-141">Lower .NET Standard platforms cannot reference higher ones.</span></span> <span data-ttu-id="ad7bb-142">Cela signifie que les bibliothèques `netstandard1.0` ne peuvent pas cibler des bibliothèques de référence ciblant `netstandard1.1` ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-142">This means that `netstandard1.0` libraries cannot reference libraries targeting `netstandard1.1` or higher.</span></span> <span data-ttu-id="ad7bb-143">Sélectionnez la version Standard qui offre une bonne combinaison entre les API et la prise en charge de plateformes pour vos besoins.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-143">Select the Standard version that has the right mix of APIs and platform support for your needs.</span></span> <span data-ttu-id="ad7bb-144">Nous vous recommandons d’utiliser `netstandard1.4` pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-144">We recommend `netstandard1.4` for now.</span></span>

3. <span data-ttu-id="ad7bb-145">Si vous souhaitez cibler .NET Framework versions 4,0 ou antérieures, ou si vous souhaitez utiliser une API disponible dans .NET Framework mais pas dans .NET Standard (par exemple, `System.Drawing` ), lisez les sections suivantes et découvrez comment effectuer une MULTICIBLAGE.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-145">If you want to target .NET Framework versions 4.0 or below, or you wish to use an API available in .NET Framework but not in .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-net-framework"></a><span data-ttu-id="ad7bb-146">Comment cibler .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ad7bb-146">How to target .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="ad7bb-147">Ces instructions supposent que vous avez .NET Framework installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-147">These instructions assume you have .NET Framework installed on your machine.</span></span> <span data-ttu-id="ad7bb-148">Reportez-vous aux [Prérequis](#prerequisites) pour installer les dépendances.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-148">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="ad7bb-149">N’oubliez pas que certaines des versions de .NET Framework utilisées ici ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-149">Keep in mind that some of the .NET Framework versions used here are no longer supported.</span></span> <span data-ttu-id="ad7bb-150">Reportez-vous au [Forum aux questions sur la politique de support de Microsoft .NET Framework](https://support.microsoft.com/gp/framework_faq/en-us) concernant les versions non prises en charge.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-150">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="ad7bb-151">Si vous voulez atteindre le nombre maximal de développeurs et de projets, utilisez .NET Framework 4,0 comme cible de référence.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-151">If you want to reach the maximum number of developers and projects, use .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="ad7bb-152">Pour cibler .NET Framework, commencez par utiliser le moniker du Framework cible (TFM) approprié qui correspond à la version .NET Framework que vous souhaitez prendre en charge.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-152">To target .NET Framework, begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

| <span data-ttu-id="ad7bb-153">Version du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ad7bb-153">.NET Framework version</span></span> | <span data-ttu-id="ad7bb-154">TFM</span><span class="sxs-lookup"><span data-stu-id="ad7bb-154">TFM</span></span>      |
| ---------------------- | -------- |
| <span data-ttu-id="ad7bb-155">.NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="ad7bb-155">.NET Framework 2.0</span></span>     | `net20`  |
| <span data-ttu-id="ad7bb-156">.NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="ad7bb-156">.NET Framework 3.0</span></span>     | `net30`  |
| <span data-ttu-id="ad7bb-157">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="ad7bb-157">.NET Framework 3.5</span></span>     | `net35`  |
| <span data-ttu-id="ad7bb-158">.NET Framework 4.0</span><span class="sxs-lookup"><span data-stu-id="ad7bb-158">.NET Framework 4.0</span></span>     | `net40`  |
| <span data-ttu-id="ad7bb-159">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="ad7bb-159">.NET Framework 4.5</span></span>     | `net45`  |
| <span data-ttu-id="ad7bb-160">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="ad7bb-160">.NET Framework 4.5.1</span></span>   | `net451` |
| <span data-ttu-id="ad7bb-161">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="ad7bb-161">.NET Framework 4.5.2</span></span>   | `net452` |
| <span data-ttu-id="ad7bb-162">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="ad7bb-162">.NET Framework 4.6</span></span>     | `net46`  |
| <span data-ttu-id="ad7bb-163">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="ad7bb-163">.NET Framework 4.6.1</span></span>   | `net461` |
| <span data-ttu-id="ad7bb-164">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="ad7bb-164">.NET Framework 4.6.2</span></span>   | `net462` |
| <span data-ttu-id="ad7bb-165">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="ad7bb-165">.NET Framework 4.7</span></span>     | `net47`  |
| <span data-ttu-id="ad7bb-166">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="ad7bb-166">.NET Framework 4.8</span></span>     | `net48`  |

<span data-ttu-id="ad7bb-167">Insérez ensuite ce Moniker du Framework cible dans la section `TargetFramework` de votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-167">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="ad7bb-168">Par exemple, voici comment écrire une bibliothèque qui cible .NET Framework 4,0 :</span><span class="sxs-lookup"><span data-stu-id="ad7bb-168">For example, here's how you would write a library that targets .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="ad7bb-169">C’est tout !</span><span class="sxs-lookup"><span data-stu-id="ad7bb-169">And that's it!</span></span> <span data-ttu-id="ad7bb-170">Bien que cela soit compilé uniquement pour .NET Framework 4, vous pouvez utiliser la bibliothèque sur des versions plus récentes de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-170">Although this compiled only for .NET Framework 4, you can use the library on newer versions of .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="ad7bb-171">Comment multicibler</span><span class="sxs-lookup"><span data-stu-id="ad7bb-171">How to multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="ad7bb-172">Les instructions suivantes supposent que le .NET Framework est installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-172">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="ad7bb-173">Reportez-vous à la section [Prérequis](#prerequisites) pour savoir quelles dépendances doivent être installées et à partir d’où les télécharger.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-173">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="ad7bb-174">Vous devrez peut-être cibler des versions antérieures du .NET Framework si votre projet prend en charge à la fois .NET Framework et .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-174">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET Core.</span></span> <span data-ttu-id="ad7bb-175">Dans ce scénario, si vous voulez utiliser des API et des constructions de langage plus récentes pour des cibles plus récentes, utilisez des directives `#if` dans votre code.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-175">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="ad7bb-176">Vous pouvez aussi avoir besoin d’ajouter différents packages et différentes dépendances pour chaque plateforme que vous ciblez pour inclure les différentes API nécessaires à chaque cas.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-176">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="ad7bb-177">Supposons, par exemple, que vous avez une bibliothèque qui effectue des opérations réseau sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-177">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="ad7bb-178">Pour .NET Standard et les versions .NET Framework 4.5 ou ultérieures, vous pouvez utiliser la classe `HttpClient` à partir de l’espace de noms `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-178">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="ad7bb-179">Toutefois, les versions antérieures du .NET Framework ne disposent pas de la classe `HttpClient`. Vous pourriez donc utiliser la classe `WebClient` à partir de l’espace de noms `System.Net` à la place.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-179">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="ad7bb-180">Voici à quoi peut ressembler votre fichier projet :</span><span class="sxs-lookup"><span data-stu-id="ad7bb-180">Your project file could look like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
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

<span data-ttu-id="ad7bb-181">Notez trois changements majeurs ici :</span><span class="sxs-lookup"><span data-stu-id="ad7bb-181">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="ad7bb-182">Le nœud `TargetFramework` a été remplacé par `TargetFrameworks`, et trois Monikers du Framework cible sont exprimés à l’intérieur.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-182">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="ad7bb-183">Un nœud `<ItemGroup>` est présent pour l’extraction de cible `net40` dans une référence .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-183">There is an `<ItemGroup>` node for the `net40` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="ad7bb-184">Un nœud `<ItemGroup>` est présent pour l’extraction de cible `net45` dans deux références .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-184">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="ad7bb-185">Le système de build est informé des symboles de préprocesseur suivants utilisés dans les directives `#if`:</span><span class="sxs-lookup"><span data-stu-id="ad7bb-185">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

<span data-ttu-id="ad7bb-186">Voici un exemple d’utilisation de la compilation conditionnelle par cible :</span><span class="sxs-lookup"><span data-stu-id="ad7bb-186">Here is an example making use of conditional compilation per-target:</span></span>

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
        // .NET 4.5+ can use async/await!
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

<span data-ttu-id="ad7bb-187">Si vous générez ce projet avec `dotnet build`, notez la présence de trois répertoires sous le dossier `bin/` :</span><span class="sxs-lookup"><span data-stu-id="ad7bb-187">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard1.4/
```

<span data-ttu-id="ad7bb-188">Chacun d’entre eux contient les fichiers `.dll` pour chaque cible.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-188">Each of these contain the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net-core"></a><span data-ttu-id="ad7bb-189">Comment tester les bibliothèques sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="ad7bb-189">How to test libraries on .NET Core</span></span>

<span data-ttu-id="ad7bb-190">Il est important de pouvoir effectuer des tests sur plusieurs plateformes.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-190">It's important to be able to test across platforms.</span></span> <span data-ttu-id="ad7bb-191">Vous pouvez utiliser [xUnit](https://xunit.github.io/) ou MSTest dans leur version d’origine.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-191">You can use either [xUnit](https://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="ad7bb-192">Les deux conviennent parfaitement à la réalisation de tests unitaires sur votre bibliothèque sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-192">Both are perfectly suitable for unit testing your library on .NET Core.</span></span> <span data-ttu-id="ad7bb-193">La façon dont vous configurez votre solution avec des projets de test dépend de la [structure de votre solution](#structuring-a-solution).</span><span class="sxs-lookup"><span data-stu-id="ad7bb-193">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="ad7bb-194">L’exemple suivant part du principe que les répertoires de test et source résident dans le même répertoire de premier niveau.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-194">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="ad7bb-195">Cela utilise certaines commandes [CLI .net Core](../tools/index.md) .</span><span class="sxs-lookup"><span data-stu-id="ad7bb-195">This uses some [.NET Core CLI](../tools/index.md) commands.</span></span> <span data-ttu-id="ad7bb-196">Pour plus d’informations, consultez [dotnet new](../tools/dotnet-new.md) et [dotnet sln](../tools/dotnet-sln.md).</span><span class="sxs-lookup"><span data-stu-id="ad7bb-196">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="ad7bb-197">Configurez votre solution.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-197">Set up your solution.</span></span> <span data-ttu-id="ad7bb-198">Pour cela, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ad7bb-198">You can do so with the following commands:</span></span>

   ```dotnetcli
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="ad7bb-199">Cette commande crée des projets et les relie dans une solution.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-199">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="ad7bb-200">Votre répertoire pour `SolutionWithSrcAndTest` doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="ad7bb-200">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="ad7bb-201">Accédez au répertoire du projet de test et ajoutez une référence à `MyProject.Test` à partir de `MyProject`.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-201">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```dotnetcli
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="ad7bb-202">Restaurez les packages et générez les projets :</span><span class="sxs-lookup"><span data-stu-id="ad7bb-202">Restore packages and build projects:</span></span>

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. <span data-ttu-id="ad7bb-203">Exécutez la commande `dotnet test` pour vérifier que xUnit s’exécute.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-203">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="ad7bb-204">Si vous avez choisi d’utiliser MSTest, le Test Runner de console MSTest doit s’exécuter à la place.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-204">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>

<span data-ttu-id="ad7bb-205">C’est tout !</span><span class="sxs-lookup"><span data-stu-id="ad7bb-205">And that's it!</span></span> <span data-ttu-id="ad7bb-206">Vous pouvez maintenant tester votre bibliothèque sur toutes les plateformes à l’aide d’outils en ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-206">You can now test your library across all platforms using command-line tools.</span></span> <span data-ttu-id="ad7bb-207">Maintenant que vous avez tout configuré, le test de votre bibliothèque est très simple :</span><span class="sxs-lookup"><span data-stu-id="ad7bb-207">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="ad7bb-208">Apportez des modifications à votre bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-208">Make changes to your library.</span></span>
1. <span data-ttu-id="ad7bb-209">Exécutez les tests à partir de la ligne de commande, dans votre répertoire de test, avec la commande `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-209">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="ad7bb-210">Votre code est automatiquement régénéré quand vous appelez la commande `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-210">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="ad7bb-211">Comment utiliser plusieurs projets</span><span class="sxs-lookup"><span data-stu-id="ad7bb-211">How to use multiple projects</span></span>

<span data-ttu-id="ad7bb-212">Les bibliothèques plus volumineuses ont souvent besoin de placer des fonctionnalités dans différents projets.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-212">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="ad7bb-213">Imaginez que vous vouliez créer une bibliothèque pouvant être utilisée dans idiomatique C# et F #.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-213">Imagine you want to build a library that could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="ad7bb-214">Cela signifierait que les consommateurs de votre bibliothèque le consomment de manière naturelle pour C# ou F #.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-214">That would mean that consumers of your library consume it in ways that are natural to C# or F#.</span></span> <span data-ttu-id="ad7bb-215">Par exemple, en C#, vous pouvez utiliser la bibliothèque de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="ad7bb-215">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="ad7bb-216">En F#, le code peut se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="ad7bb-216">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="ad7bb-217">Les scénarios de consommation tels que celui-ci signifient que les API auxquelles vous accédez ont une structure différente en C# et F#.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-217">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="ad7bb-218">Pour réaliser ceci, il est courant de factoriser toute la logique d’une bibliothèque dans un projet principal et d’avoir des projets C# et F# définissant les couches API qui effectuent des appels à ce projet principal.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-218">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="ad7bb-219">Le reste de la section utilise les noms suivants :</span><span class="sxs-lookup"><span data-stu-id="ad7bb-219">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="ad7bb-220">**AwesomeLibrary. Core** : projet principal qui contient toute la logique de la bibliothèque</span><span class="sxs-lookup"><span data-stu-id="ad7bb-220">**AwesomeLibrary.Core** - A core project that contains all logic for the library</span></span>
* <span data-ttu-id="ad7bb-221">**AwesomeLibrary.CSharp** : projet avec des API publiques destinées à être consommées en C#</span><span class="sxs-lookup"><span data-stu-id="ad7bb-221">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="ad7bb-222">**AwesomeLibrary.CSharp** : projet avec des API publiques destinées à être consommées en F#</span><span class="sxs-lookup"><span data-stu-id="ad7bb-222">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="ad7bb-223">Vous pouvez exécuter les commandes suivantes dans votre terminal pour produire la même structure que ce guide :</span><span class="sxs-lookup"><span data-stu-id="ad7bb-223">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

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

<span data-ttu-id="ad7bb-224">Cela permet d’ajouter les trois projets ci-dessus et un fichier solution qui les lie.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-224">This will add the three projects above and a solution file that links them together.</span></span> <span data-ttu-id="ad7bb-225">La création du fichier solution et la liaison de projets vous permettent de restaurer et de générer des projets à partir d’un niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-225">Creating the solution file and linking projects will allow you to restore and build projects from a top level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="ad7bb-226">Références entre projets</span><span class="sxs-lookup"><span data-stu-id="ad7bb-226">Project-to-project referencing</span></span>

<span data-ttu-id="ad7bb-227">La meilleure façon de référencer un projet consiste à utiliser l’interface CLI .NET Core pour ajouter une référence de projet.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-227">The best way to reference a project is to use the .NET Core CLI to add a project reference.</span></span> <span data-ttu-id="ad7bb-228">À partir des répertoires de projet **AwesomeLibrary.CSharp** et de **AwesomeLibrary.FSharp**, vous pouvez exécuter la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="ad7bb-228">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="ad7bb-229">Les fichiers projet pour **AwesomeLibrary.CSharp** et **AwesomeLibrary.FSharp** référencent désormais **AwesomeLibrary.Core** comme cible de `ProjectReference`.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-229">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="ad7bb-230">Pour le vérifier, confirmez la présence des éléments suivants dans les fichiers projet :</span><span class="sxs-lookup"><span data-stu-id="ad7bb-230">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="ad7bb-231">Vous pouvez ajouter manuellement cette section à chaque fichier projet si vous préférez ne pas utiliser l’interface CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-231">You can add this section to each project file manually if you prefer not to use the .NET Core CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="ad7bb-232">Structurer une solution</span><span class="sxs-lookup"><span data-stu-id="ad7bb-232">Structuring a solution</span></span>

<span data-ttu-id="ad7bb-233">Un autre aspect important des solutions à projets multiples est la mise en place d’une bonne structure de projet globale.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-233">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="ad7bb-234">Vous pouvez organiser le code comme vous le souhaitez, et tant que vous liez chaque projet à votre fichier solution avec `dotnet sln add`, vous pouvez exécuter `dotnet restore` et `dotnet build` au niveau de la solution.</span><span class="sxs-lookup"><span data-stu-id="ad7bb-234">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
