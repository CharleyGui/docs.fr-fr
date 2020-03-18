---
title: Développer des bibliothèques avec le CLI de base .NET
description: Apprenez à créer des bibliothèques de base .NET à l’aide de l’ICIC de base .NET. Vous allez créer une bibliothèque prenant en charge plusieurs frameworks.
author: cartermp
ms.date: 05/01/2017
ms.openlocfilehash: c23c1f027b4d6d09c50eb2257d34f72ec56302f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503510"
---
# <a name="develop-libraries-with-the-net-core-cli"></a><span data-ttu-id="c2371-104">Développer des bibliothèques avec le CLI de base .NET</span><span class="sxs-lookup"><span data-stu-id="c2371-104">Develop libraries with the .NET Core CLI</span></span>

<span data-ttu-id="c2371-105">Cet article couvre la façon d’écrire des bibliothèques pour .NET en utilisant le CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c2371-105">This article covers how to write libraries for .NET using the .NET Core CLI.</span></span> <span data-ttu-id="c2371-106">L’interface CLI fournit une expérience efficace et de bas niveau qui fonctionne sur tous les systèmes d’exploitation pris en charge.</span><span class="sxs-lookup"><span data-stu-id="c2371-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="c2371-107">Vous pouvez toujours créer des bibliothèques avec Visual Studio, et si c’est ce que vous préférez, [consultez le guide Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="c2371-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](library-with-visual-studio.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c2371-108">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="c2371-108">Prerequisites</span></span>

<span data-ttu-id="c2371-109">[Le SDK .NET Core et l’interface CLI](https://dotnet.microsoft.com/download) doivent être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c2371-109">You need [the .NET Core SDK and CLI](https://dotnet.microsoft.com/download) installed on your machine.</span></span>

<span data-ttu-id="c2371-110">Pour accéder aux sections de ce document concernant les versions du .NET Framework, vous devez installer le [.NET Framework](https://dotnet.microsoft.com) sur un ordinateur Windows.</span><span class="sxs-lookup"><span data-stu-id="c2371-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](https://dotnet.microsoft.com) installed on a Windows machine.</span></span>

<span data-ttu-id="c2371-111">En outre, si vous souhaitez prendre en charge les anciennes cibles cadre .NET, vous devez installer des packs de ciblage ou des packs de développeurs à partir de la [page d’archives de téléchargement .NET](https://dotnet.microsoft.com/download/archives).</span><span class="sxs-lookup"><span data-stu-id="c2371-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting packs or developer packs from the [.NET download archives page](https://dotnet.microsoft.com/download/archives).</span></span> <span data-ttu-id="c2371-112">Reportez-vous au tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="c2371-112">Refer to this table:</span></span>

| <span data-ttu-id="c2371-113">Version du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c2371-113">.NET Framework version</span></span> | <span data-ttu-id="c2371-114">À télécharger</span><span class="sxs-lookup"><span data-stu-id="c2371-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="c2371-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="c2371-115">4.6.1</span></span>                  | <span data-ttu-id="c2371-116">Pack de ciblage .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="c2371-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="c2371-117">4.6</span><span class="sxs-lookup"><span data-stu-id="c2371-117">4.6</span></span>                    | <span data-ttu-id="c2371-118">Pack de ciblage .NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="c2371-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="c2371-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="c2371-119">4.5.2</span></span>                  | <span data-ttu-id="c2371-120">Pack du développeur .NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="c2371-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="c2371-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="c2371-121">4.5.1</span></span>                  | <span data-ttu-id="c2371-122">Pack du développeur .NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="c2371-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="c2371-123">4.5</span><span class="sxs-lookup"><span data-stu-id="c2371-123">4.5</span></span>                    | <span data-ttu-id="c2371-124">SDK Windows pour Windows 8</span><span class="sxs-lookup"><span data-stu-id="c2371-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="c2371-125">4.0</span><span class="sxs-lookup"><span data-stu-id="c2371-125">4.0</span></span>                    | <span data-ttu-id="c2371-126">SDK pour Windows 7 et .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="c2371-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="c2371-127">2.0, 3.0 et 3.5</span><span class="sxs-lookup"><span data-stu-id="c2371-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="c2371-128">Runtime .NET Framework 3.5 SP1 (ou version Windows 8+)</span><span class="sxs-lookup"><span data-stu-id="c2371-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-the-net-standard"></a><span data-ttu-id="c2371-129">Comment cibler .NET Standard</span><span class="sxs-lookup"><span data-stu-id="c2371-129">How to target the .NET Standard</span></span>

<span data-ttu-id="c2371-130">Si vous n’êtes pas familier avec .NET Standard, faites référence à [.NET Standard](../../standard/net-standard.md) pour en savoir plus.</span><span class="sxs-lookup"><span data-stu-id="c2371-130">If you're not familiar with .NET Standard, refer to [.NET Standard](../../standard/net-standard.md) to learn more.</span></span>

<span data-ttu-id="c2371-131">Dans cet article, il existe un tableau qui cartographie les versions standard .NET à diverses implémentations :</span><span class="sxs-lookup"><span data-stu-id="c2371-131">In that article, there is a table that maps .NET Standard versions to various implementations:</span></span>

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

<span data-ttu-id="c2371-132">Voici ce que signifie ce tableau dans le processus de création d’une bibliothèque :</span><span class="sxs-lookup"><span data-stu-id="c2371-132">Here's what this table means for the purposes of creating a library:</span></span>

<span data-ttu-id="c2371-133">La version de .NET Standard que vous choisissez sera un compromis entre l’accès aux API les plus récents et la possibilité de cibler plus de implémentations .NET et .NET Versions Standard.</span><span class="sxs-lookup"><span data-stu-id="c2371-133">The version of .NET Standard you pick will be a tradeoff between access to the newest APIs and the ability to target more .NET implementations and .NET Standard versions.</span></span> <span data-ttu-id="c2371-134">Vous contrôlez la gamme de plates-formes et `netstandardX.X` de `X.X` versions ciblées en choisissant une`.csproj` version `.fsproj`de (où est un numéro de version) et en l’ajoutant à votre fichier de projet ( ou ).</span><span class="sxs-lookup"><span data-stu-id="c2371-134">You control the range of targetable platforms and versions by picking a version of `netstandardX.X` (where `X.X` is a version number) and adding it to your project file (`.csproj` or `.fsproj`).</span></span>

<span data-ttu-id="c2371-135">Vous avez trois options principales lors du ciblage .NET Standard, en fonction de vos besoins.</span><span class="sxs-lookup"><span data-stu-id="c2371-135">You have three primary options when targeting .NET Standard, depending on your needs.</span></span>

1. <span data-ttu-id="c2371-136">Vous pouvez utiliser la version par défaut de `netstandard1.4`.NET Standard fourni par des modèles, , qui vous donne accès à la plupart des API sur .NET Standard tout en étant compatible avec UWP, .NET Framework 4.6.1, et .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="c2371-136">You can use the default version of .NET Standard supplied by templates, `netstandard1.4`, which gives you access to most APIs on .NET Standard while still being compatible with UWP, .NET Framework 4.6.1, and .NET Standard 2.0.</span></span>

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. <span data-ttu-id="c2371-137">Vous pouvez utiliser une version inférieure ou supérieure de .NET Standard en modifiant la valeur dans le `TargetFramework` nœud de votre fichier de projet.</span><span class="sxs-lookup"><span data-stu-id="c2371-137">You can use a lower or higher version of .NET Standard by modifying the value in the `TargetFramework` node of your project file.</span></span>

    <span data-ttu-id="c2371-138">Les versions .NET standard sont à compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="c2371-138">.NET Standard versions are backward compatible.</span></span> <span data-ttu-id="c2371-139">Cela signifie que les bibliothèques `netstandard1.0` s’exécutent sur les plateformes `netstandard1.1` et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="c2371-139">That means that `netstandard1.0` libraries run on `netstandard1.1` platforms and higher.</span></span> <span data-ttu-id="c2371-140">Cependant, il n’y a pas de compatibilité vers l’avant.</span><span class="sxs-lookup"><span data-stu-id="c2371-140">However, there is no forward compatibility.</span></span> <span data-ttu-id="c2371-141">Les plates-formes standard inférieures .NET ne peuvent pas faire référence à des plates-formes supérieures.</span><span class="sxs-lookup"><span data-stu-id="c2371-141">Lower .NET Standard platforms cannot reference higher ones.</span></span> <span data-ttu-id="c2371-142">Cela signifie que les bibliothèques `netstandard1.0` ne peuvent pas cibler des bibliothèques de référence ciblant `netstandard1.1` ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="c2371-142">This means that `netstandard1.0` libraries cannot reference libraries targeting `netstandard1.1` or higher.</span></span> <span data-ttu-id="c2371-143">Sélectionnez la version Standard qui offre une bonne combinaison entre les API et la prise en charge de plateformes pour vos besoins.</span><span class="sxs-lookup"><span data-stu-id="c2371-143">Select the Standard version that has the right mix of APIs and platform support for your needs.</span></span> <span data-ttu-id="c2371-144">Nous vous recommandons d’utiliser `netstandard1.4` pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="c2371-144">We recommend `netstandard1.4` for now.</span></span>

3. <span data-ttu-id="c2371-145">Si vous souhaitez cibler les versions cadres .NET 4.0 ou moins, ou si vous souhaitez utiliser une `System.Drawing`API disponible dans .NET Framework mais pas en .NET Standard (par exemple, ), lisez les sections suivantes et apprenez à multitarget.</span><span class="sxs-lookup"><span data-stu-id="c2371-145">If you want to target .NET Framework versions 4.0 or below, or you wish to use an API available in .NET Framework but not in .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-net-framework"></a><span data-ttu-id="c2371-146">Comment cibler .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c2371-146">How to target .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="c2371-147">Ces instructions supposent que vous avez .NET Framework installé sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="c2371-147">These instructions assume you have .NET Framework installed on your machine.</span></span> <span data-ttu-id="c2371-148">Reportez-vous aux [Prérequis](#prerequisites) pour installer les dépendances.</span><span class="sxs-lookup"><span data-stu-id="c2371-148">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="c2371-149">Gardez à l’esprit que certaines des versions .NET Framework utilisées ici ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="c2371-149">Keep in mind that some of the .NET Framework versions used here are no longer supported.</span></span> <span data-ttu-id="c2371-150">Reportez-vous au [Forum aux questions sur la politique de support de Microsoft .NET Framework](https://support.microsoft.com/gp/framework_faq/en-us) concernant les versions non prises en charge.</span><span class="sxs-lookup"><span data-stu-id="c2371-150">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="c2371-151">Si vous souhaitez atteindre le nombre maximum de développeurs et de projets, utilisez .NET Framework 4.0 comme cible de référence.</span><span class="sxs-lookup"><span data-stu-id="c2371-151">If you want to reach the maximum number of developers and projects, use .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="c2371-152">Pour cibler .NET Framework, commencez par utiliser le bon accord-cadre cible (TFM) qui correspond à la version cadre .NET que vous souhaitez prendre en charge.</span><span class="sxs-lookup"><span data-stu-id="c2371-152">To target .NET Framework, begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

| <span data-ttu-id="c2371-153">Version du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c2371-153">.NET Framework version</span></span> | <span data-ttu-id="c2371-154">TFM</span><span class="sxs-lookup"><span data-stu-id="c2371-154">TFM</span></span>      |
| ---------------------- | -------- |
| <span data-ttu-id="c2371-155">.NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="c2371-155">.NET Framework 2.0</span></span>     | `net20`  |
| <span data-ttu-id="c2371-156">.NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="c2371-156">.NET Framework 3.0</span></span>     | `net30`  |
| <span data-ttu-id="c2371-157">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="c2371-157">.NET Framework 3.5</span></span>     | `net35`  |
| <span data-ttu-id="c2371-158">.NET Framework 4.0</span><span class="sxs-lookup"><span data-stu-id="c2371-158">.NET Framework 4.0</span></span>     | `net40`  |
| <span data-ttu-id="c2371-159">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="c2371-159">.NET Framework 4.5</span></span>     | `net45`  |
| <span data-ttu-id="c2371-160">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="c2371-160">.NET Framework 4.5.1</span></span>   | `net451` |
| <span data-ttu-id="c2371-161">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="c2371-161">.NET Framework 4.5.2</span></span>   | `net452` |
| <span data-ttu-id="c2371-162">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="c2371-162">.NET Framework 4.6</span></span>     | `net46`  |
| <span data-ttu-id="c2371-163">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="c2371-163">.NET Framework 4.6.1</span></span>   | `net461` |
| <span data-ttu-id="c2371-164">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="c2371-164">.NET Framework 4.6.2</span></span>   | `net462` |
| <span data-ttu-id="c2371-165">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="c2371-165">.NET Framework 4.7</span></span>     | `net47`  |
| <span data-ttu-id="c2371-166">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="c2371-166">.NET Framework 4.8</span></span>     | `net48`  |

<span data-ttu-id="c2371-167">Insérez ensuite ce Moniker du Framework cible dans la section `TargetFramework` de votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="c2371-167">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="c2371-168">Par exemple, voici comment vous écririez une bibliothèque qui cible .NET Framework 4.0 :</span><span class="sxs-lookup"><span data-stu-id="c2371-168">For example, here's how you would write a library that targets .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="c2371-169">Et le tour est joué !</span><span class="sxs-lookup"><span data-stu-id="c2371-169">And that's it!</span></span> <span data-ttu-id="c2371-170">Bien que cela n’ait été compilé que pour .NET Framework 4, vous pouvez utiliser la bibliothèque sur de nouvelles versions de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c2371-170">Although this compiled only for .NET Framework 4, you can use the library on newer versions of .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="c2371-171">Comment multitarget</span><span class="sxs-lookup"><span data-stu-id="c2371-171">How to multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="c2371-172">Les instructions suivantes supposent que le .NET Framework est installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c2371-172">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="c2371-173">Reportez-vous à la section [Prérequis](#prerequisites) pour savoir quelles dépendances doivent être installées et à partir d’où les télécharger.</span><span class="sxs-lookup"><span data-stu-id="c2371-173">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="c2371-174">Vous devrez peut-être cibler des versions antérieures du .NET Framework si votre projet prend en charge à la fois .NET Framework et .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c2371-174">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET Core.</span></span> <span data-ttu-id="c2371-175">Dans ce scénario, si vous voulez utiliser des API et des constructions de langage plus récentes pour des cibles plus récentes, utilisez des directives `#if` dans votre code.</span><span class="sxs-lookup"><span data-stu-id="c2371-175">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="c2371-176">Vous pouvez aussi avoir besoin d’ajouter différents packages et différentes dépendances pour chaque plateforme que vous ciblez pour inclure les différentes API nécessaires à chaque cas.</span><span class="sxs-lookup"><span data-stu-id="c2371-176">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="c2371-177">Supposons, par exemple, que vous avez une bibliothèque qui effectue des opérations réseau sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="c2371-177">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="c2371-178">Pour .NET Standard et les versions .NET Framework 4.5 ou ultérieures, vous pouvez utiliser la classe `HttpClient` à partir de l’espace de noms `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="c2371-178">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="c2371-179">Toutefois, les versions antérieures du .NET Framework ne disposent pas de la classe `HttpClient`. Vous pourriez donc utiliser la classe `WebClient` à partir de l’espace de noms `System.Net` à la place.</span><span class="sxs-lookup"><span data-stu-id="c2371-179">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="c2371-180">Voici à quoi peut ressembler votre fichier projet :</span><span class="sxs-lookup"><span data-stu-id="c2371-180">Your project file could look like this:</span></span>

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

<span data-ttu-id="c2371-181">Notez trois changements majeurs ici :</span><span class="sxs-lookup"><span data-stu-id="c2371-181">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="c2371-182">Le nœud `TargetFramework` a été remplacé par `TargetFrameworks`, et trois Monikers du Framework cible sont exprimés à l’intérieur.</span><span class="sxs-lookup"><span data-stu-id="c2371-182">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="c2371-183">Un nœud `<ItemGroup>` est présent pour l’extraction de cible `net40` dans une référence .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c2371-183">There is an `<ItemGroup>` node for the `net40` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="c2371-184">Un nœud `<ItemGroup>` est présent pour l’extraction de cible `net45` dans deux références .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c2371-184">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="c2371-185">Le système de build est informé des symboles de préprocesseur suivants utilisés dans les directives `#if`:</span><span class="sxs-lookup"><span data-stu-id="c2371-185">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

<span data-ttu-id="c2371-186">Voici un exemple d’utilisation de la compilation conditionnelle par cible :</span><span class="sxs-lookup"><span data-stu-id="c2371-186">Here is an example making use of conditional compilation per-target:</span></span>

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

<span data-ttu-id="c2371-187">Si vous générez ce projet avec `dotnet build`, notez la présence de trois répertoires sous le dossier `bin/` :</span><span class="sxs-lookup"><span data-stu-id="c2371-187">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard1.4/
```

<span data-ttu-id="c2371-188">Chacun d’entre eux contient les fichiers `.dll` pour chaque cible.</span><span class="sxs-lookup"><span data-stu-id="c2371-188">Each of these contain the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net-core"></a><span data-ttu-id="c2371-189">Comment tester les bibliothèques sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="c2371-189">How to test libraries on .NET Core</span></span>

<span data-ttu-id="c2371-190">Il est important de pouvoir effectuer des tests sur plusieurs plateformes.</span><span class="sxs-lookup"><span data-stu-id="c2371-190">It's important to be able to test across platforms.</span></span> <span data-ttu-id="c2371-191">Vous pouvez utiliser [xUnit](https://xunit.github.io/) ou MSTest dans leur version d’origine.</span><span class="sxs-lookup"><span data-stu-id="c2371-191">You can use either [xUnit](https://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="c2371-192">Les deux conviennent parfaitement à la réalisation de tests unitaires sur votre bibliothèque sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c2371-192">Both are perfectly suitable for unit testing your library on .NET Core.</span></span> <span data-ttu-id="c2371-193">La façon dont vous configurez votre solution avec des projets de test dépend de la [structure de votre solution](#structuring-a-solution).</span><span class="sxs-lookup"><span data-stu-id="c2371-193">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="c2371-194">L’exemple suivant part du principe que les répertoires de test et source résident dans le même répertoire de premier niveau.</span><span class="sxs-lookup"><span data-stu-id="c2371-194">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="c2371-195">Cela utilise quelques commandes [CLI .NET Core.](../tools/index.md)</span><span class="sxs-lookup"><span data-stu-id="c2371-195">This uses some [.NET Core CLI](../tools/index.md) commands.</span></span> <span data-ttu-id="c2371-196">Pour plus d’informations, consultez [dotnet new](../tools/dotnet-new.md) et [dotnet sln](../tools/dotnet-sln.md).</span><span class="sxs-lookup"><span data-stu-id="c2371-196">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="c2371-197">Configurez votre solution.</span><span class="sxs-lookup"><span data-stu-id="c2371-197">Set up your solution.</span></span> <span data-ttu-id="c2371-198">Pour cela, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="c2371-198">You can do so with the following commands:</span></span>

   ```dotnetcli
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="c2371-199">Cette commande crée des projets et les relie dans une solution.</span><span class="sxs-lookup"><span data-stu-id="c2371-199">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="c2371-200">Votre répertoire pour `SolutionWithSrcAndTest` doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="c2371-200">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="c2371-201">Accédez au répertoire du projet de test et ajoutez une référence à `MyProject.Test` à partir de `MyProject`.</span><span class="sxs-lookup"><span data-stu-id="c2371-201">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```dotnetcli
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="c2371-202">Restaurez les packages et générez les projets :</span><span class="sxs-lookup"><span data-stu-id="c2371-202">Restore packages and build projects:</span></span>

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. <span data-ttu-id="c2371-203">Exécutez la commande `dotnet test` pour vérifier que xUnit s’exécute.</span><span class="sxs-lookup"><span data-stu-id="c2371-203">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="c2371-204">Si vous avez choisi d’utiliser MSTest, le Test Runner de console MSTest doit s’exécuter à la place.</span><span class="sxs-lookup"><span data-stu-id="c2371-204">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>

<span data-ttu-id="c2371-205">Et le tour est joué !</span><span class="sxs-lookup"><span data-stu-id="c2371-205">And that's it!</span></span> <span data-ttu-id="c2371-206">Vous pouvez maintenant tester votre bibliothèque sur toutes les plateformes à l’aide d’outils de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c2371-206">You can now test your library across all platforms using command-line tools.</span></span> <span data-ttu-id="c2371-207">Maintenant que vous avez tout configuré, le test de votre bibliothèque est très simple :</span><span class="sxs-lookup"><span data-stu-id="c2371-207">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="c2371-208">Apportez des modifications à votre bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="c2371-208">Make changes to your library.</span></span>
1. <span data-ttu-id="c2371-209">Exécutez les tests à partir de la ligne de commande, dans votre répertoire de test, avec la commande `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="c2371-209">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="c2371-210">Votre code est automatiquement régénéré quand vous appelez la commande `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="c2371-210">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="c2371-211">Comment utiliser plusieurs projets</span><span class="sxs-lookup"><span data-stu-id="c2371-211">How to use multiple projects</span></span>

<span data-ttu-id="c2371-212">Les bibliothèques plus volumineuses ont souvent besoin de placer des fonctionnalités dans différents projets.</span><span class="sxs-lookup"><span data-stu-id="c2371-212">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="c2371-213">Imaginez que vous voulez construire une bibliothèque qui pourrait être consommée en C et F idiomatiques.</span><span class="sxs-lookup"><span data-stu-id="c2371-213">Imagine you want to build a library that could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="c2371-214">Cela signifierait que les consommateurs de votre bibliothèque le consomment d’une manière naturelle pour le C ou le F.</span><span class="sxs-lookup"><span data-stu-id="c2371-214">That would mean that consumers of your library consume it in ways that are natural to C# or F#.</span></span> <span data-ttu-id="c2371-215">Par exemple, en C#, vous pouvez utiliser la bibliothèque de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="c2371-215">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="c2371-216">En F#, le code peut se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="c2371-216">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="c2371-217">Les scénarios de consommation tels que celui-ci signifient que les API auxquelles vous accédez ont une structure différente en C# et F#.</span><span class="sxs-lookup"><span data-stu-id="c2371-217">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="c2371-218">Pour réaliser ceci, il est courant de factoriser toute la logique d’une bibliothèque dans un projet principal et d’avoir des projets C# et F# définissant les couches API qui effectuent des appels à ce projet principal.</span><span class="sxs-lookup"><span data-stu-id="c2371-218">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="c2371-219">Le reste de la section utilise les noms suivants :</span><span class="sxs-lookup"><span data-stu-id="c2371-219">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="c2371-220">**AwesomeLibrary.Core** - Un projet de base qui contient toute la logique pour la bibliothèque</span><span class="sxs-lookup"><span data-stu-id="c2371-220">**AwesomeLibrary.Core** - A core project that contains all logic for the library</span></span>
* <span data-ttu-id="c2371-221">**AwesomeLibrary.CSharp** : projet avec des API publiques destinées à être consommées en C#</span><span class="sxs-lookup"><span data-stu-id="c2371-221">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="c2371-222">**AwesomeLibrary.CSharp** : projet avec des API publiques destinées à être consommées en F#</span><span class="sxs-lookup"><span data-stu-id="c2371-222">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="c2371-223">Vous pouvez exécuter les commandes suivantes dans votre terminal pour produire la même structure que ce guide :</span><span class="sxs-lookup"><span data-stu-id="c2371-223">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

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

<span data-ttu-id="c2371-224">Cela ajoutera les trois projets ci-dessus et un fichier de solution qui les relie.</span><span class="sxs-lookup"><span data-stu-id="c2371-224">This will add the three projects above and a solution file that links them together.</span></span> <span data-ttu-id="c2371-225">La création du fichier de solutions et les projets de liaison vous permettront de restaurer et de construire des projets de haut niveau.</span><span class="sxs-lookup"><span data-stu-id="c2371-225">Creating the solution file and linking projects will allow you to restore and build projects from a top level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="c2371-226">Références entre projets</span><span class="sxs-lookup"><span data-stu-id="c2371-226">Project-to-project referencing</span></span>

<span data-ttu-id="c2371-227">La meilleure façon de référencer un projet consiste à utiliser l’interface CLI .NET Core pour ajouter une référence de projet.</span><span class="sxs-lookup"><span data-stu-id="c2371-227">The best way to reference a project is to use the .NET Core CLI to add a project reference.</span></span> <span data-ttu-id="c2371-228">À partir des répertoires de projet **AwesomeLibrary.CSharp** et de **AwesomeLibrary.FSharp**, vous pouvez exécuter la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="c2371-228">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="c2371-229">Les fichiers projet pour **AwesomeLibrary.CSharp** et **AwesomeLibrary.FSharp** référencent désormais **AwesomeLibrary.Core** comme cible de `ProjectReference`.</span><span class="sxs-lookup"><span data-stu-id="c2371-229">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="c2371-230">Pour le vérifier, confirmez la présence des éléments suivants dans les fichiers projet :</span><span class="sxs-lookup"><span data-stu-id="c2371-230">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="c2371-231">Vous pouvez ajouter manuellement cette section à chaque fichier projet si vous préférez ne pas utiliser l’interface CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c2371-231">You can add this section to each project file manually if you prefer not to use the .NET Core CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="c2371-232">Structurer une solution</span><span class="sxs-lookup"><span data-stu-id="c2371-232">Structuring a solution</span></span>

<span data-ttu-id="c2371-233">Un autre aspect important des solutions à projets multiples est la mise en place d’une bonne structure de projet globale.</span><span class="sxs-lookup"><span data-stu-id="c2371-233">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="c2371-234">Vous pouvez organiser le code comme vous le souhaitez, et tant que vous liez chaque projet à votre fichier solution avec `dotnet sln add`, vous pouvez exécuter `dotnet restore` et `dotnet build` au niveau de la solution.</span><span class="sxs-lookup"><span data-stu-id="c2371-234">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
