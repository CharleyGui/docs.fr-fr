---
title: Nouveautés de .NET Core 3.0
description: Découvrez les nouvelles fonctionnalités de .NET Core 3.0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 09/22/2019
ms.openlocfilehash: ddb758b942099657708e79b590c7817c309396d7
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216265"
---
# <a name="whats-new-in-net-core-30"></a><span data-ttu-id="16c2c-103">Nouveautés de .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="16c2c-103">What's new in .NET Core 3.0</span></span>

<span data-ttu-id="16c2c-104">Cet article décrit les nouveautés de .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="16c2c-104">This article describes what is new in .NET Core 3.0.</span></span> <span data-ttu-id="16c2c-105">Une des principales améliorations est la prise en charge des applications de bureau Windows (Windows uniquement).</span><span class="sxs-lookup"><span data-stu-id="16c2c-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="16c2c-106">En utilisant le composant du SDK .NET Core 3.0 Windows Desktop, vous pouvez porter vos applications Windows Forms et Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="16c2c-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="16c2c-107">Pour être clair, le composant Windows Desktop est pris en charge et inclus seulement sur Windows.</span><span class="sxs-lookup"><span data-stu-id="16c2c-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="16c2c-108">Pour plus d’informations, consultez la section [Bureau Windows](#windows-desktop) plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="16c2c-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="16c2c-109">.NET Core 3.0 prend en charge C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="16c2c-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="16c2c-110">Il est fortement recommandé d’utiliser [Visual Studio 2019 16.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), [Visual Studio pour Mac 8.3](/visualstudio/mac/install-preview)ou [Visual Studio code](https://code.visualstudio.com/) avec l'  **C# extension**.</span><span class="sxs-lookup"><span data-stu-id="16c2c-110">It's highly recommended that you use [Visual Studio 2019 16.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), [Visual Studio for Mac 8.3](/visualstudio/mac/install-preview), or [Visual Studio Code](https://code.visualstudio.com/) with the **C# extension**.</span></span>

<span data-ttu-id="16c2c-111">[Téléchargez et commencez à utiliser .NET Core 3.0](https://aka.ms/netcore3download) pour le moment sur Windows, MacOS ou Linux.</span><span class="sxs-lookup"><span data-stu-id="16c2c-111">[Download and get started with .NET Core 3.0](https://aka.ms/netcore3download) right now on Windows, macOS, or Linux.</span></span>

<span data-ttu-id="16c2c-112">Pour plus d’informations sur la version, consultez l' [annonce de .NET Core 3.0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="16c2c-112">For more information about the release, see the [.NET Core 3.0 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).</span></span>

<span data-ttu-id="16c2c-113">.NET Core RC1 a été considéré comme une production prête par Microsoft et a été entièrement pris en charge.</span><span class="sxs-lookup"><span data-stu-id="16c2c-113">.NET Core RC1 was considered production ready by Microsoft and was fully supported.</span></span> <span data-ttu-id="16c2c-114">Si vous utilisez une version préliminaire, vous devez passer à la version RTM pour une prise en charge continue.</span><span class="sxs-lookup"><span data-stu-id="16c2c-114">If you're using a preview release, you must move to the RTM version for continued support.</span></span>

## <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="16c2c-115">Windows Installer pour le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="16c2c-115">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="16c2c-116">Le programme d’installation MSI pour Windows a changé à compter de .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="16c2c-116">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="16c2c-117">Les programmes d’installation du SDK mettent désormais à niveau les versions des plages de fonctionnalités du SDK.</span><span class="sxs-lookup"><span data-stu-id="16c2c-117">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="16c2c-118">Les plages de fonctionnalités sont définies dans les groupes *hundreds* de la section *patch* du numéro de version.</span><span class="sxs-lookup"><span data-stu-id="16c2c-118">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="16c2c-119">Par exemple, **3.0._101_** et **3.0._201_** sont des versions dans deux plages de fonctionnalités différentes, tandis que **3.0._101_** et **3.0._199_** se trouvent dans la même plages de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="16c2c-119">For example, **3.0._101_** and **3.0._201_** are versions in two different feature bands while **3.0._101_** and **3.0._199_** are in the same feature band.</span></span> <span data-ttu-id="16c2c-120">En outre, quand le SDK .NET Core **3.0._101_** est installé, le SDK .NET Core **3.0._100_** est supprimé de la machine s’il existe.</span><span class="sxs-lookup"><span data-stu-id="16c2c-120">And, when .NET Core SDK **3.0._101_** is installed, .NET Core SDK **3.0._100_** will be removed from the machine if it exists.</span></span> <span data-ttu-id="16c2c-121">Quand le SDK .NET Core **3.0._200_** est installé sur la même machine, le SDK .NET Core **3.0._101_** n’est pas supprimé.</span><span class="sxs-lookup"><span data-stu-id="16c2c-121">When .NET Core SDK **3.0._200_** is installed on the same machine, .NET Core SDK **3.0._101_** won't be removed.</span></span>

<span data-ttu-id="16c2c-122">Pour plus d’informations sur la gestion des versions, consultez [Vue d’ensemble de la gestion des versions .NET Core](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="16c2c-122">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

## <a name="c-80"></a><span data-ttu-id="16c2c-123">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="16c2c-123">C# 8.0</span></span>

<span data-ttu-id="16c2c-124">C#8.0 fait également partie de cette version, qui comprend la fonctionnalité de types de référence Nullable, les flux asynchrones et plus de modèles.</span><span class="sxs-lookup"><span data-stu-id="16c2c-124">C# 8.0 is also part of this release, which includes the nullable reference types feature, async streams, and more patterns.</span></span> <span data-ttu-id="16c2c-125">Pour plus d’informations sur les fonctionnalités de C# 8.0, consultez [Nouveautés de C# 8.0](../../csharp/whats-new/csharp-8.md).</span><span class="sxs-lookup"><span data-stu-id="16c2c-125">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

## <a name="net-standard-21"></a><span data-ttu-id="16c2c-126">.NET Standard 2.1</span><span class="sxs-lookup"><span data-stu-id="16c2c-126">.NET Standard 2.1</span></span>

<span data-ttu-id="16c2c-127">Même si .NET Core 3.0 prend en charge **.NET standard 2.1**, `dotnet new classlib` le modèle par défaut génère un projet qui cible toujours **.NET standard 2.0**.</span><span class="sxs-lookup"><span data-stu-id="16c2c-127">Even though .NET Core 3.0 supports **.NET Standard 2.1**, the default `dotnet new classlib` template generates a project that still targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="16c2c-128">Pour cibler **.NET Standard 2.1**, modifiez votre fichier projet et définissez la propriété `TargetFramework` sur `netstandard2.1` :</span><span class="sxs-lookup"><span data-stu-id="16c2c-128">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="16c2c-129">Si vous utilisez Visual Studio, vous avez besoin de [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), car Visual Studio 2017 ne prend pas en charge **.NET Standard 2.1** ou **.NET Core 3.0**.</span><span class="sxs-lookup"><span data-stu-id="16c2c-129">If you're using Visual Studio, you need [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span>

## <a name="improved-net-core-version-apis"></a><span data-ttu-id="16c2c-130">API de version de .NET Core améliorées</span><span class="sxs-lookup"><span data-stu-id="16c2c-130">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="16c2c-131">À compter de .NET Core 3.0, les API de version fournies avec .NET Core retournent les informations souhaitées.</span><span class="sxs-lookup"><span data-stu-id="16c2c-131">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="16c2c-132">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="16c2c-132">For example:</span></span>

```csharp
System.Console.WriteLine($"Environment.Version: {System.Environment.Version}");

// Old result
//   Environment.Version: 4.0.30319.42000
//
// New result
//   Environment.Version: 3.0.0
```

```csharp
System.Console.WriteLine($"RuntimeInformation.FrameworkDescription: {System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription}");

// Old result
//   RuntimeInformation.FrameworkDescription: .NET Core 4.6.27415.71
//
// New result
//   RuntimeInformation.FrameworkDescription: .NET Core 3.0.0-preview4-27615-11
```

> [!WARNING]
> <span data-ttu-id="16c2c-133">Modification avec rupture.</span><span class="sxs-lookup"><span data-stu-id="16c2c-133">Breaking change.</span></span> <span data-ttu-id="16c2c-134">Il s’agit techniquement d’une modification avec rupture, car le schéma de gestion de version a changé.</span><span class="sxs-lookup"><span data-stu-id="16c2c-134">This is technically a breaking change because the versioning scheme has changed.</span></span>

## <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="16c2c-135">Intrinsèques dépendant de la plateforme .NET</span><span class="sxs-lookup"><span data-stu-id="16c2c-135">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="16c2c-136">Des API ont été ajoutées, qui permettent d’accéder à certaines instructions de l’UC orientées performances, comme les ensembles **SIMD** ou les ensembles d’**instructions de manipulation de bits**.</span><span class="sxs-lookup"><span data-stu-id="16c2c-136">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="16c2c-137">Ces instructions peuvent améliorer les performances dans certains scénarios de matière significative, comme le traitement efficace de données en parallèle.</span><span class="sxs-lookup"><span data-stu-id="16c2c-137">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span>

<span data-ttu-id="16c2c-138">Le cas échéant, les bibliothèques .NET ont commencé à utiliser ces instructions pour améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="16c2c-138">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="16c2c-139">Pour plus d’informations, consultez [Intrinsèques dépendant de la plateforme .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span><span class="sxs-lookup"><span data-stu-id="16c2c-139">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span></span>

## <a name="default-executables"></a><span data-ttu-id="16c2c-140">Exécutables par défaut</span><span class="sxs-lookup"><span data-stu-id="16c2c-140">Default executables</span></span>

<span data-ttu-id="16c2c-141">.NET Core génère désormais des [exécutables dépendant du framework](../deploying/index.md#framework-dependent-executables-fde) par défaut.</span><span class="sxs-lookup"><span data-stu-id="16c2c-141">.NET Core now builds [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="16c2c-142">Ce comportement est nouveau pour les applications qui utilisent une version .NET Core installée de façon globale.</span><span class="sxs-lookup"><span data-stu-id="16c2c-142">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="16c2c-143">Auparavant, seuls les [déploiements autonomes](../deploying/index.md#self-contained-deployments-scd) produisaient un exécutable.</span><span class="sxs-lookup"><span data-stu-id="16c2c-143">Previously, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="16c2c-144">Lors de l’étape `dotnet build` ou `dotnet publish`, un exécutable est créé, qui correspond à l’environnement et à la plateforme du Kit de développement que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="16c2c-144">During `dotnet build` or `dotnet publish`, an executable is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="16c2c-145">Vous pouvez obtenir le même résultat avec ces exécutables, comme vous le feriez avec d’autres exécutables natifs comme :</span><span class="sxs-lookup"><span data-stu-id="16c2c-145">You can expect the same things with these executables as you would other native executables, such as:</span></span>

- <span data-ttu-id="16c2c-146">Vous pouvez double-cliquer sur l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="16c2c-146">You can double-click on the executable.</span></span>
- <span data-ttu-id="16c2c-147">Vous pouvez lancer l’application directement à partir d’une invite de commandes, par exemple `myapp.exe` sous Windows, et `./myapp` sous Linux et macOS.</span><span class="sxs-lookup"><span data-stu-id="16c2c-147">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

## <a name="single-file-executables"></a><span data-ttu-id="16c2c-148">Exécutable monofichier</span><span class="sxs-lookup"><span data-stu-id="16c2c-148">Single-file executables</span></span>

<span data-ttu-id="16c2c-149">La commande `dotnet publish` prend en charge l’empaquetage de votre application dans un exécutable monofichier spécifique de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="16c2c-149">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="16c2c-150">L’exécutable est auto-extractible et contient toutes les dépendances (y compris natives) nécessaires à l’exécution de votre application.</span><span class="sxs-lookup"><span data-stu-id="16c2c-150">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="16c2c-151">Lors de la première exécution de l’application, celle-ci est extraite d’un répertoire basé sur le nom de l’application et l’identificateur de la build.</span><span class="sxs-lookup"><span data-stu-id="16c2c-151">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="16c2c-152">Le démarrage est plus rapide quand l’application est réexécutée.</span><span class="sxs-lookup"><span data-stu-id="16c2c-152">Startup is faster when the application is run again.</span></span> <span data-ttu-id="16c2c-153">L’application n’a pas besoin de s’extraire elle-même une deuxième fois, sauf si une nouvelle version a été utilisée.</span><span class="sxs-lookup"><span data-stu-id="16c2c-153">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="16c2c-154">Pour publier un exécutable monofichier, définissez `PublishSingleFile` dans votre projet ou sur la ligne de commande avec la commande `dotnet publish` :</span><span class="sxs-lookup"><span data-stu-id="16c2c-154">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

<span data-ttu-id="16c2c-155">\- ou -</span><span class="sxs-lookup"><span data-stu-id="16c2c-155">-or-</span></span>

```dotnetcli
dotnet publish -r win10-x64 /p:PublishSingleFile=true
```

<span data-ttu-id="16c2c-156">Pour plus d’informations sur la publication monofichier, consultez le [document conceptuel sur l’outil de regroupement monofichier](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="16c2c-156">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span></span>

## <a name="assembly-linking"></a><span data-ttu-id="16c2c-157">Liaison d’assemblys</span><span class="sxs-lookup"><span data-stu-id="16c2c-157">Assembly linking</span></span>

<span data-ttu-id="16c2c-158">Le SDK .NET Core 3.0 est fourni avec un outil qui peut réduire la taille des applications en analysant le langage intermédiaire et en supprimant les assemblys inutilisés.</span><span class="sxs-lookup"><span data-stu-id="16c2c-158">The .NET core 3.0 SDK comes with a tool that can reduce the size of apps by analyzing IL and trimming unused assemblies.</span></span>

<span data-ttu-id="16c2c-159">Les applications autonomes incluent tous les éléments nécessaires pour exécuter votre code, sans nécessiter que .NET soit installé sur la machine hôte.</span><span class="sxs-lookup"><span data-stu-id="16c2c-159">Self-contained apps include everything needed to run your code, without requiring .NET to be installed on the host computer.</span></span> <span data-ttu-id="16c2c-160">Toutefois, il arrive souvent que l’application nécessite seulement un petit sous-ensemble de l’infrastructure pour fonctionner, et que les autres bibliothèques inutilisées puissent être supprimées.</span><span class="sxs-lookup"><span data-stu-id="16c2c-160">However, many times the app only requires a small subset of the framework to function, and other unused libraries could be removed.</span></span>

<span data-ttu-id="16c2c-161">.NET Core inclut désormais un paramètre qui utilisera l’outil [Éditeur de liens de langage intermédiaire](https://github.com/mono/linker) analyser le langage intermédiaire de votre application.</span><span class="sxs-lookup"><span data-stu-id="16c2c-161">.NET Core now includes a setting that will use the [IL linker](https://github.com/mono/linker) tool to scan the IL of your app.</span></span> <span data-ttu-id="16c2c-162">Cet outil détecte ce que le code nécessite et supprime les bibliothèques inutilisées.</span><span class="sxs-lookup"><span data-stu-id="16c2c-162">this tool detects what code is required, and then trims unused libraries.</span></span> <span data-ttu-id="16c2c-163">Cet outil peut réduire considérablement la taille de déploiement de certaines applications.</span><span class="sxs-lookup"><span data-stu-id="16c2c-163">This tool can significantly reduce the deployment size of some apps.</span></span>

<span data-ttu-id="16c2c-164">Pour activer cet outil, ajoutez le paramètre `<PublishTrimmed>` dans votre projet et publiez une application autonome :</span><span class="sxs-lookup"><span data-stu-id="16c2c-164">To enable this tool, add the `<PublishTrimmed>` setting in your project and publish a self-contained app:</span></span>

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```dotnetcli
dotnet publish -r <rid> -c Release
```

<span data-ttu-id="16c2c-165">Par exemple, le nouveau modèle de projet de console de base « hello world » inclus, lors de sa publication, atteint la taille d’environ 70 Mo.</span><span class="sxs-lookup"><span data-stu-id="16c2c-165">As an example, the basic "hello world" new console project template that is included, when published, hits about 70 MB in size.</span></span> <span data-ttu-id="16c2c-166">Avec `<PublishTrimmed>`, sa taille est réduite à environ 30 Mo.</span><span class="sxs-lookup"><span data-stu-id="16c2c-166">By using `<PublishTrimmed>`, that size is reduced to about 30 MB.</span></span>

<span data-ttu-id="16c2c-167">Il est important de prendre en compte le fait que les applications ou infrastructures (dont ASP.NET Core et WPF) qui utilisent la réflexion ou des fonctionnalités dynamiques associées cesseront souvent de fonctionner après cette troncature.</span><span class="sxs-lookup"><span data-stu-id="16c2c-167">It's important to consider that applications or frameworks (including ASP.NET Core and WPF) that use reflection or related dynamic features, will often break when trimmed.</span></span> <span data-ttu-id="16c2c-168">Cette rupture se produit car l’éditeur de liens ne connaît pas ce comportement dynamique et ne peut pas déterminer les types de framework nécessaires pour la réflexion.</span><span class="sxs-lookup"><span data-stu-id="16c2c-168">This breakage occurs because the linker doesn't know about this dynamic behavior and can't determine which framework types are required for reflection.</span></span> <span data-ttu-id="16c2c-169">L’outil d’éditeur de liens de langage intermédiaire peut être configuré pour être conscient de ce scénario.</span><span class="sxs-lookup"><span data-stu-id="16c2c-169">The IL Linker tool can be configured to be aware of this scenario.</span></span>

<span data-ttu-id="16c2c-170">Avant toute chose, veillez à tester votre application après réduction.</span><span class="sxs-lookup"><span data-stu-id="16c2c-170">Above all else, be sure to test your app after trimming.</span></span>

<span data-ttu-id="16c2c-171">Pour plus d’informations sur l’outil d’éditeur de liens de langage intermédiaire, consultez la [documentation](https://aka.ms/dotnet-illink) ou visitez le référentiel [mono/linker]( https://github.com/mono/linker).</span><span class="sxs-lookup"><span data-stu-id="16c2c-171">For more information about the IL Linker tool, see the [documentation](https://aka.ms/dotnet-illink) or visit the [mono/linker]( https://github.com/mono/linker) repo.</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="16c2c-172">Compilation hiérarchisée</span><span class="sxs-lookup"><span data-stu-id="16c2c-172">Tiered compilation</span></span>

<span data-ttu-id="16c2c-173">La [compilation hiérarchisée](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) est activée par défaut avec .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="16c2c-173">[Tiered compilation](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="16c2c-174">Cette fonctionnalité permet au runtime d’utiliser de manière plus adaptative le compilateur juste-à-temps (Just-In-Time ou JIT) pour obtenir de meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="16c2c-174">This feature enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance.</span></span>

<span data-ttu-id="16c2c-175">Le principal avantage de la compilation hiérarchisée est d’autoriser les méthode (re-) JIT avec un niveau de moins bonne qualité mais plus rapide, ou avec un niveau de meilleure qualité mais plus lent.</span><span class="sxs-lookup"><span data-stu-id="16c2c-175">The main benefit of TC is to enable (re-)jitting methods with a lower-quality-but-faster tier or a higher-quality-but-slower tier.</span></span> <span data-ttu-id="16c2c-176">Cela permet d’améliorer les performances d’une application quand elle passe par les différents stades de l’exécution, du démarrage à l’état stable.</span><span class="sxs-lookup"><span data-stu-id="16c2c-176">This helps increase performance of an application as it goes through various stages of execution, from startup through steady-state.</span></span> <span data-ttu-id="16c2c-177">Ceci contraste avec l’approche de la compilation non hiérarchisée, où chaque méthode est compilée d’une seule manière (la même que le niveau de qualité supérieure), qui privilégie la stabilité de l’état au détriment des performances au démarrage.</span><span class="sxs-lookup"><span data-stu-id="16c2c-177">This contrasts with the non-TC approach, where every method is compiled a single way (the same as the high-quality tier), which is biased to steady-state over startup performance.</span></span>

<span data-ttu-id="16c2c-178">Pour activer Quick JIT (code JIT de niveau 0), utilisez ce paramétrage dans votre fichier projet :</span><span class="sxs-lookup"><span data-stu-id="16c2c-178">To enable Quick JIT (tier 0 jitted code), use this setting in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>true</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="16c2c-179">Pour désactiver complètement la compilation hiérarchisée, utilisez ce paramétrage dans votre fichier projet :</span><span class="sxs-lookup"><span data-stu-id="16c2c-179">To disable TC completely, use this setting in your project file:</span></span>

```xml
<TieredCompilation>false</TieredCompilation>
```

## <a name="readytorun-images"></a><span data-ttu-id="16c2c-180">Images ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="16c2c-180">ReadyToRun images</span></span>

<span data-ttu-id="16c2c-181">Vous pouvez améliorer le temps de démarrage de votre application .NET Core en compilant les assemblys de votre application au format ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="16c2c-181">You can improve the startup time of your .NET Core application by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="16c2c-182">R2R est une forme de compilation ahead-of-time (AOT).</span><span class="sxs-lookup"><span data-stu-id="16c2c-182">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="16c2c-183">Les fichiers binaires R2R améliorent les performances de démarrage en réduisant la quantité de travail que le compilateur juste-à-temps (JIT) doit faire lorsque votre application est chargée.</span><span class="sxs-lookup"><span data-stu-id="16c2c-183">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="16c2c-184">Les fichiers binaires contiennent du code natif similaire à ce que la compilation JIT produirait.</span><span class="sxs-lookup"><span data-stu-id="16c2c-184">The binaries contain similar native code compared to what the JIT would produce.</span></span> <span data-ttu-id="16c2c-185">Cependant, les fichiers binaires R2R sont plus grands, car ils contiennent à la fois le code du langage intermédiaire (IL), qui est toujours nécessaire pour certains scénarios, et la version native du même code.</span><span class="sxs-lookup"><span data-stu-id="16c2c-185">However, R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="16c2c-186">R2R est disponible seulement quand vous publiez une application autonome qui cible des environnements d’exécution spécifiques (RID), comme Linux x64 ou Windows x64.</span><span class="sxs-lookup"><span data-stu-id="16c2c-186">R2R is only available when you publish a self-contained app that targets specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="16c2c-187">Pour compiler votre projet en ReadyToRun, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="16c2c-187">To compile your project as ReadyToRun, do the following:</span></span>

01. <span data-ttu-id="16c2c-188">Ajoutez le paramètre `<PublishReadyToRun>` à votre projet</span><span class="sxs-lookup"><span data-stu-id="16c2c-188">Add the `<PublishReadyToRun>` setting to your project</span></span>

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. <span data-ttu-id="16c2c-189">Publiez une application autonome.</span><span class="sxs-lookup"><span data-stu-id="16c2c-189">Publish a self-contained app.</span></span> <span data-ttu-id="16c2c-190">Par exemple, cette commande crée une application autonome pour la version 64 bits de Windows :</span><span class="sxs-lookup"><span data-stu-id="16c2c-190">For example, this command creates a self-contained app for the 64-bit version of Windows:</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64 --self-contained true
    ```

### <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="16c2c-191">Restrictions d’architecture/de multiplateforme</span><span class="sxs-lookup"><span data-stu-id="16c2c-191">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="16c2c-192">Le compilateur ReadyToRun ne prend actuellement pas en charge le ciblage croisé.</span><span class="sxs-lookup"><span data-stu-id="16c2c-192">The ReadyToRun compiler doesn't currently support cross-targeting.</span></span> <span data-ttu-id="16c2c-193">Vous devez compiler sur une cible donnée.</span><span class="sxs-lookup"><span data-stu-id="16c2c-193">You must compile on a given target.</span></span> <span data-ttu-id="16c2c-194">Par exemple, si vous souhaitez avoir des images R2R Windows x64, vous devez exécuter la commande de publication sur cet environnement.</span><span class="sxs-lookup"><span data-stu-id="16c2c-194">For example, if you want R2R images for Windows x64, you need to run the publish command on that environment.</span></span>

<span data-ttu-id="16c2c-195">Exceptions au ciblage croisé :</span><span class="sxs-lookup"><span data-stu-id="16c2c-195">Exceptions to cross-targeting:</span></span>

- <span data-ttu-id="16c2c-196">Windows x64 peut être utilisé pour compiler des images Windows ARM32, ARM64 et x86.</span><span class="sxs-lookup"><span data-stu-id="16c2c-196">Windows x64 can be used to compile Windows ARM32, ARM64, and x86 images.</span></span>
- <span data-ttu-id="16c2c-197">Windows x86 peut être utilisé pour compiler des images Windows ARM32.</span><span class="sxs-lookup"><span data-stu-id="16c2c-197">Windows x86 can be used to compile Windows ARM32 images.</span></span>
- <span data-ttu-id="16c2c-198">Linux x64 peut être utilisé pour compiler des images Linux ARM32 et ARM64.</span><span class="sxs-lookup"><span data-stu-id="16c2c-198">Linux x64 can be used to compile Linux ARM32 and ARM64 images.</span></span>

## <a name="build-copies-dependencies"></a><span data-ttu-id="16c2c-199">Dépendances de copies de build</span><span class="sxs-lookup"><span data-stu-id="16c2c-199">Build copies dependencies</span></span>

<span data-ttu-id="16c2c-200">La commande `dotnet build` copie maintenant les dépendances NuGet pour votre application à partir du cache NuGet vers le dossier de sortie de build.</span><span class="sxs-lookup"><span data-stu-id="16c2c-200">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="16c2c-201">Auparavant, les dépendances étaient copiées uniquement dans le cadre de `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="16c2c-201">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="16c2c-202">Certaines opérations, par exemple la liaison et la publication d’une page de type Razor, nécessiteront toujours une publication.</span><span class="sxs-lookup"><span data-stu-id="16c2c-202">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

## <a name="local-tools"></a><span data-ttu-id="16c2c-203">Outils locaux</span><span class="sxs-lookup"><span data-stu-id="16c2c-203">Local tools</span></span>

<span data-ttu-id="16c2c-204">.NET Core 3.0 introduit des outils locaux.</span><span class="sxs-lookup"><span data-stu-id="16c2c-204">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="16c2c-205">Les outils locaux sont similaires aux [outils globaux](../tools/global-tools.md), mais ils sont associés à un emplacement particulier sur le disque.</span><span class="sxs-lookup"><span data-stu-id="16c2c-205">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="16c2c-206">Les outils locaux ne sont pas disponibles globalement et sont distribués en tant que packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="16c2c-206">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="16c2c-207">Si vous avez essayé des outils locaux dans .NET Core 3.0 Preview 1, par exemple pour exécuter `dotnet tool restore` ou `dotnet tool install`, supprimez le dossier de cache des outils locaux.</span><span class="sxs-lookup"><span data-stu-id="16c2c-207">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="16c2c-208">Sinon, les outils locaux ne fonctionneront sur aucune nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="16c2c-208">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="16c2c-209">Ce dossier se trouve à ces emplacements :</span><span class="sxs-lookup"><span data-stu-id="16c2c-209">This folder is located at:</span></span>
>
> <span data-ttu-id="16c2c-210">Sur macOS, Linux : `rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="16c2c-210">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="16c2c-211">Sur Windows : `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="16c2c-211">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="16c2c-212">Les outils locaux s’appuient sur un nom de fichier manifeste `dotnet-tools.json` dans votre répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="16c2c-212">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="16c2c-213">Ce fichier manifeste définit les outils qui doivent être disponibles dans ce dossier et sous-celui-ci.</span><span class="sxs-lookup"><span data-stu-id="16c2c-213">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="16c2c-214">Vous pouvez distribuer le fichier manifeste avec votre code pour que toute personne qui utilise votre code puisse restaurer et utiliser les mêmes outils.</span><span class="sxs-lookup"><span data-stu-id="16c2c-214">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="16c2c-215">Pour les outils locaux et globaux, une version compatible du runtime est requise.</span><span class="sxs-lookup"><span data-stu-id="16c2c-215">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="16c2c-216">De nombreux outils actuellement sur NuGet.org ciblent le runtime .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="16c2c-216">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="16c2c-217">Pour installer ces outils de façon locale ou globale, vous devez toujours installer le [runtime NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="16c2c-217">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

## <a name="major-version-roll-forward"></a><span data-ttu-id="16c2c-218">Restauration par progression d’une version majeure</span><span class="sxs-lookup"><span data-stu-id="16c2c-218">Major-version Roll Forward</span></span>

<span data-ttu-id="16c2c-219">.NET Core 3.0 introduit une fonctionnalité que vous pouvez choisir d’utiliser et qui permet de restaurer par progression votre application vers la dernière version majeure de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="16c2c-219">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="16c2c-220">En outre, un nouveau paramètre a été ajouté pour contrôler la façon dont la restauration par progression est appliquée à votre application.</span><span class="sxs-lookup"><span data-stu-id="16c2c-220">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="16c2c-221">Ce paramètre peut être configuré des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="16c2c-221">This can be configured in the following ways:</span></span>

- <span data-ttu-id="16c2c-222">Propriété du fichier projet : `RollForward`</span><span class="sxs-lookup"><span data-stu-id="16c2c-222">Project file property: `RollForward`</span></span>
- <span data-ttu-id="16c2c-223">Propriété du fichier config du runtime : `rollForward`</span><span class="sxs-lookup"><span data-stu-id="16c2c-223">Runtime configuration file property: `rollForward`</span></span>
- <span data-ttu-id="16c2c-224">Variable d’environnement : `DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="16c2c-224">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="16c2c-225">Argument de ligne de commande : `--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="16c2c-225">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="16c2c-226">L’une des valeurs suivantes doit être spécifiée.</span><span class="sxs-lookup"><span data-stu-id="16c2c-226">One of the following values must be specified.</span></span> <span data-ttu-id="16c2c-227">Si le paramètre est omis, **Minor** est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="16c2c-227">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="16c2c-228">**LatestPatch**</span><span class="sxs-lookup"><span data-stu-id="16c2c-228">**LatestPatch**</span></span>\
<span data-ttu-id="16c2c-229">Restauration par progression vers la version de correctif la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="16c2c-229">Roll forward to the highest patch version.</span></span> <span data-ttu-id="16c2c-230">Cette valeur désactive la restauration par progression d’une version mineure.</span><span class="sxs-lookup"><span data-stu-id="16c2c-230">This disables minor version roll forward.</span></span>
- <span data-ttu-id="16c2c-231">**Minor**</span><span class="sxs-lookup"><span data-stu-id="16c2c-231">**Minor**</span></span>\
<span data-ttu-id="16c2c-232">Restauration par progression vers la version mineure supérieure la plus basse, si la version mineure demandée est manquante.</span><span class="sxs-lookup"><span data-stu-id="16c2c-232">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="16c2c-233">Si la version mineure demandée est présente, la stratégie **LatestPatch** est utilisée.</span><span class="sxs-lookup"><span data-stu-id="16c2c-233">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="16c2c-234">**Major**</span><span class="sxs-lookup"><span data-stu-id="16c2c-234">**Major**</span></span>\
<span data-ttu-id="16c2c-235">Restauration par progression vers la version majeure supérieure la plus basse, et la version mineure la plus basse, si la version majeure demandée est manquante.</span><span class="sxs-lookup"><span data-stu-id="16c2c-235">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="16c2c-236">Si la version majeure demandée est présente, la stratégie **Minor** est utilisée.</span><span class="sxs-lookup"><span data-stu-id="16c2c-236">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="16c2c-237">**LatestMinor**</span><span class="sxs-lookup"><span data-stu-id="16c2c-237">**LatestMinor**</span></span>\
<span data-ttu-id="16c2c-238">Restauration par progression vers la version mineure la plus élevée, si la version mineure demandée est présente.</span><span class="sxs-lookup"><span data-stu-id="16c2c-238">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="16c2c-239">Conçu pour les scénarios d’hébergement de composant.</span><span class="sxs-lookup"><span data-stu-id="16c2c-239">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="16c2c-240">**LatestMajor**</span><span class="sxs-lookup"><span data-stu-id="16c2c-240">**LatestMajor**</span></span>\
<span data-ttu-id="16c2c-241">Restauration par progression vers la version majeure la plus élevée et la version mineure la plus élevée, si la version majeure demandée est présente.</span><span class="sxs-lookup"><span data-stu-id="16c2c-241">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="16c2c-242">Conçu pour les scénarios d’hébergement de composant.</span><span class="sxs-lookup"><span data-stu-id="16c2c-242">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="16c2c-243">**Disable**</span><span class="sxs-lookup"><span data-stu-id="16c2c-243">**Disable**</span></span>\
<span data-ttu-id="16c2c-244">Ne pas effectuer de restauration par progression.</span><span class="sxs-lookup"><span data-stu-id="16c2c-244">Don't roll forward.</span></span> <span data-ttu-id="16c2c-245">Lier uniquement à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="16c2c-245">Only bind to specified version.</span></span> <span data-ttu-id="16c2c-246">Cette stratégie n’est pas recommandée pour une utilisation générale, car elle désactive la possibilité d’effectuer une restauration par progression vers les derniers correctifs.</span><span class="sxs-lookup"><span data-stu-id="16c2c-246">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="16c2c-247">Cette valeur est recommandée uniquement à des fins de test.</span><span class="sxs-lookup"><span data-stu-id="16c2c-247">This value is only recommended for testing.</span></span>

<span data-ttu-id="16c2c-248">Outre le paramètre **Disable**, tous les paramètres utilisent la version de correctif disponible la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="16c2c-248">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

## <a name="windows-desktop"></a><span data-ttu-id="16c2c-249">Bureau Windows</span><span class="sxs-lookup"><span data-stu-id="16c2c-249">Windows desktop</span></span>

<span data-ttu-id="16c2c-250">.NET Core 3.0 prend en charge les applications de bureau Windows utilisant Windows Presentation Foundation (WPF) et Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="16c2c-250">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="16c2c-251">Ces infrastructures prennent également en charge l’utilisation de contrôles modernes et le style Fluent à partir de la bibliothèque XAML de l’interface utilisateur Windows (WinUI) via des [îles XAML](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="16c2c-251">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="16c2c-252">Le composant Bureau Windows fait partie du SDK .NET Core 3.0 Windows.</span><span class="sxs-lookup"><span data-stu-id="16c2c-252">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="16c2c-253">Vous pouvez créer une nouvelle application WPF ou Windows Forms à l’aide des commandes `dotnet` suivantes :</span><span class="sxs-lookup"><span data-stu-id="16c2c-253">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```dotnetcli
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="16c2c-254">Visual Studio 2019 ajoute des modèles **Nouveau projet** pour Windows Forms et WPF .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="16c2c-254">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="16c2c-255">Pour plus d’informations sur la façon de porter une application .NET Framework existante, consultez [Porter des projets WPF](../porting/wpf.md) et [Porter des projets Windows Forms](../porting/winforms.md).</span><span class="sxs-lookup"><span data-stu-id="16c2c-255">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../porting/wpf.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

## <a name="com-callable-components---windows-desktop"></a><span data-ttu-id="16c2c-256">Composants appelables par COM : Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="16c2c-256">COM-callable components - Windows Desktop</span></span>

<span data-ttu-id="16c2c-257">Sur Windows, vous pouvez maintenant créer des composants gérés appelables par COM.</span><span class="sxs-lookup"><span data-stu-id="16c2c-257">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="16c2c-258">Cette fonctionnalité est essentielle pour utiliser .NET Core avec les modèles de compléments COM et également pour assurer la parité avec .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16c2c-258">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="16c2c-259">Contrairement à .NET Framework, où *mscoree.dll* était utilisé comme serveur COM, .NET Core ajoute une dll de lanceur natif au répertoire *bin* quand vous générez votre composant COM.</span><span class="sxs-lookup"><span data-stu-id="16c2c-259">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="16c2c-260">Pour obtenir un exemple montrant comment créer un composant COM et le consommer, consultez la [démonstration COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span><span class="sxs-lookup"><span data-stu-id="16c2c-260">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

## <a name="msix-deployment---windows-desktop"></a><span data-ttu-id="16c2c-261">Déploiement MSIX : Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="16c2c-261">MSIX Deployment - Windows Desktop</span></span>

<span data-ttu-id="16c2c-262">[MSIX](https://docs.microsoft.com/windows/msix/) est un nouveau format de package d’application Windows.</span><span class="sxs-lookup"><span data-stu-id="16c2c-262">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="16c2c-263">Il peut être utilisé pour déployer des applications de poste de travail .NET Core 3.0 pour Windows 10.</span><span class="sxs-lookup"><span data-stu-id="16c2c-263">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="16c2c-264">Le [projet de package d’application Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), disponible dans Visual Studio 2019, vous permet de créer des packages MSIX avec des applications .NET Core [autonomes](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="16c2c-264">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#self-contained-deployments-scd) .NET Core applications.</span></span>

<span data-ttu-id="16c2c-265">Le fichier projet .NET Core doit spécifier les runtimes pris en charge dans la propriété `<RuntimeIdentifiers>` :</span><span class="sxs-lookup"><span data-stu-id="16c2c-265">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="winforms-high-dpi"></a><span data-ttu-id="16c2c-266">Haute résolution WinForms</span><span class="sxs-lookup"><span data-stu-id="16c2c-266">WinForms high DPI</span></span>

<span data-ttu-id="16c2c-267">Les applications Windows Forms .NET Core peuvent définir le mode de haute résolution avec <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="16c2c-267">.NET Core Windows Forms applications can set high DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="16c2c-268">La méthode `SetHighDpiMode` définit le mode de haute résolution correspondant, sauf si le paramètre a été défini par d’autres moyens, comme `App.Manifest` ou P/Invoke avant `Application.Run`.</span><span class="sxs-lookup"><span data-stu-id="16c2c-268">The `SetHighDpiMode` method sets the corresponding high DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="16c2c-269">Les valeurs `highDpiMode` possibles, telles qu’exprimées par l’enum <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType>, sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="16c2c-269">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

<span data-ttu-id="16c2c-270">Pour plus d’informations sur les modes de haute résolution, consultez [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) (Développement d’applications de bureau haute résolution sur Windows).</span><span class="sxs-lookup"><span data-stu-id="16c2c-270">For more information about high DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

## <a name="ranges-and-indices"></a><span data-ttu-id="16c2c-271">Plages et index</span><span class="sxs-lookup"><span data-stu-id="16c2c-271">Ranges and indices</span></span>

<span data-ttu-id="16c2c-272">Le nouveau type <xref:System.Index?displayProperty=nameWithType> peut être utilisé pour l’indexation.</span><span class="sxs-lookup"><span data-stu-id="16c2c-272">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="16c2c-273">Vous pouvez en créer un à partir d’un `int` qui compte à partir du début, ou avec un opérateur (C#) `^` préfixé qui compte à partir de la fin :</span><span class="sxs-lookup"><span data-stu-id="16c2c-273">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="16c2c-274">Il existe également le type <xref:System.Range?displayProperty=nameWithType>, composé de deux valeurs `Index`, une pour le début et une pour la fin, et qui peut être écrit avec une expression de plage (C#) `x..y`.</span><span class="sxs-lookup"><span data-stu-id="16c2c-274">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="16c2c-275">Vous pouvez indexer ensuite avec un `Range`, ce qui génère une tranche :</span><span class="sxs-lookup"><span data-stu-id="16c2c-275">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="16c2c-276">Pour plus d’informations, consultez le [tutoriel sur les plages et les index](../../csharp/tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="16c2c-276">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

## <a name="async-streams"></a><span data-ttu-id="16c2c-277">Flux asynchrones</span><span class="sxs-lookup"><span data-stu-id="16c2c-277">Async streams</span></span>

<span data-ttu-id="16c2c-278">Le type <xref:System.Collections.Generic.IAsyncEnumerable%601> est une nouvelle version asynchrone de <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="16c2c-278">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="16c2c-279">Le langage vous permet d’utiliser `await foreach` sur `IAsyncEnumerable<T>` pour consommer ses éléments, et `yield return` sur ceux-ci pour produire des éléments.</span><span class="sxs-lookup"><span data-stu-id="16c2c-279">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="16c2c-280">L’exemple suivant montre la production et la consommation de flux de données asynchrones.</span><span class="sxs-lookup"><span data-stu-id="16c2c-280">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="16c2c-281">L’instruction `foreach` est asynchrone et utilise elle-même `yield return` afin de produire un flux asynchrone pour les appelants.</span><span class="sxs-lookup"><span data-stu-id="16c2c-281">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="16c2c-282">Ce modèle (qui utilise `yield return`) est le modèle recommandé pour produire des flux de données asynchrones.</span><span class="sxs-lookup"><span data-stu-id="16c2c-282">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

<span data-ttu-id="16c2c-283">Outre la possibilité d’effectuer une opération `await foreach`, vous pouvez également créer des itérateurs asynchrones, par exemple un itérateur qui retourne un objet `IAsyncEnumerable/IAsyncEnumerator` auquel vous pouvez à la fois appliquer des opérations `await` et `yield`.</span><span class="sxs-lookup"><span data-stu-id="16c2c-283">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="16c2c-284">Pour les objets qui doivent être supprimés, vous pouvez utiliser `IAsyncDisposable`, qui implémentent différents types BCL, notamment `Stream` et `Timer`.</span><span class="sxs-lookup"><span data-stu-id="16c2c-284">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="16c2c-285">Pour plus d’informations, consultez le [tutoriel sur les flux asynchrones](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="16c2c-285">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="ieee-floating-point-improvements"></a><span data-ttu-id="16c2c-286">Améliorations apportées à la virgule flottante IEEE</span><span class="sxs-lookup"><span data-stu-id="16c2c-286">IEEE Floating-point improvements</span></span>

<span data-ttu-id="16c2c-287">Les API de virgule flottante sont en cours de mise à jour pour devenir conformes à la [révision 754-2008 d’IEEE](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span><span class="sxs-lookup"><span data-stu-id="16c2c-287">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="16c2c-288">L’objectif de ces modifications est d’exposer toutes les opérations **obligatoires** et de garantir que leur comportement est conforme à la spécification IEEE. Pour plus d’informations sur les améliorations apportées aux opérations à virgule flottante, consultez le billet de blog [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="16c2c-288">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="16c2c-289">Les correctifs de l’analyse et de la mise en forme comprennent :</span><span class="sxs-lookup"><span data-stu-id="16c2c-289">Parsing and formatting fixes include:</span></span>

- <span data-ttu-id="16c2c-290">Analyse et arrondi corrects des entrées, quelle que soit leur longueur.</span><span class="sxs-lookup"><span data-stu-id="16c2c-290">Correctly parse and round inputs of any length.</span></span>
- <span data-ttu-id="16c2c-291">Analyse et mise en forme correctes des zéros négatifs.</span><span class="sxs-lookup"><span data-stu-id="16c2c-291">Correctly parse and format negative zero.</span></span>
- <span data-ttu-id="16c2c-292">Analyse correcte de `Infinity` et `NaN` en effectuant une vérification sans tenir compte de la casse et en autorisant un signe `+` facultatif de début là où c’est applicable.</span><span class="sxs-lookup"><span data-stu-id="16c2c-292">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="16c2c-293">Les nouvelles API <xref:System.Math?displayProperty=nameWithType> incluent :</span><span class="sxs-lookup"><span data-stu-id="16c2c-293">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

- <span data-ttu-id="16c2c-294"><xref:System.Math.BitIncrement(System.Double)> et <xref:System.Math.BitDecrement(System.Double)></span><span class="sxs-lookup"><span data-stu-id="16c2c-294"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)></span></span>\
<span data-ttu-id="16c2c-295">Correspond aux opérations IEEE `nextUp` et `nextDown`.</span><span class="sxs-lookup"><span data-stu-id="16c2c-295">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="16c2c-296">Elles retournent le plus petit nombre à virgule flottante dont la valeur est supérieure ou inférieure à l’entrée (respectivement).</span><span class="sxs-lookup"><span data-stu-id="16c2c-296">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="16c2c-297">Par exemple, `Math.BitIncrement(0.0)` retourne `double.Epsilon`.</span><span class="sxs-lookup"><span data-stu-id="16c2c-297">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

- <span data-ttu-id="16c2c-298"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> et <xref:System.Math.MinMagnitude(System.Double,System.Double)></span><span class="sxs-lookup"><span data-stu-id="16c2c-298"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)></span></span>\
<span data-ttu-id="16c2c-299">Correspond aux opérations IEEE `maxNumMag` et `minNumMag`. Elles retournent la valeur la plus grande ou la plus petite des deux entrées (respectivement).</span><span class="sxs-lookup"><span data-stu-id="16c2c-299">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="16c2c-300">Par exemple, `Math.MaxMagnitude(2.0, -3.0)` retourne `-3.0`.</span><span class="sxs-lookup"><span data-stu-id="16c2c-300">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

- <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="16c2c-301">Correspond à l’opération IEEE `logB` qui retourne une valeur intégrale ; elle retourne le logarithme de base 2 intégral du paramètre d’entrée.</span><span class="sxs-lookup"><span data-stu-id="16c2c-301">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="16c2c-302">Cette méthode est identique à `floor(log2(x))`, mais effectuée avec une erreur d’arrondi minimale.</span><span class="sxs-lookup"><span data-stu-id="16c2c-302">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="16c2c-303">Correspond à l’opération IEEE `scaleB` qui prend une valeur intégrale ; elle retourne `x * pow(2, n)`, mais est effectuée avec une erreur d’arrondi minimale.</span><span class="sxs-lookup"><span data-stu-id="16c2c-303">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

- <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="16c2c-304">Correspond à l’opération IEEE `log2` ; elle retourne le logarithme de base 2.</span><span class="sxs-lookup"><span data-stu-id="16c2c-304">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="16c2c-305">Son erreur d’arrondi est minimale.</span><span class="sxs-lookup"><span data-stu-id="16c2c-305">It minimizes rounding error.</span></span>

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="16c2c-306">Correspond à l’opération IEEE `fma` ; elle effectue une multiplication-addition fusionnée.</span><span class="sxs-lookup"><span data-stu-id="16c2c-306">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="16c2c-307">Elle effectue `(x * y) + z` comme une seule opération, avec une erreur d’arrondi minimale.</span><span class="sxs-lookup"><span data-stu-id="16c2c-307">That is, it does `(x * y) + z` as a single operation, thereby minimizing the rounding error.</span></span> <span data-ttu-id="16c2c-308">Par exemple, `FusedMultiplyAdd(1e308, 2.0, -1e308)` retourne `1e308`.</span><span class="sxs-lookup"><span data-stu-id="16c2c-308">An example would be `FusedMultiplyAdd(1e308, 2.0, -1e308)` which returns `1e308`.</span></span> <span data-ttu-id="16c2c-309">L’opération régulière `(1e308 * 2.0) - 1e308` retourne `double.PositiveInfinity`.</span><span class="sxs-lookup"><span data-stu-id="16c2c-309">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

- <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="16c2c-310">Correspond à l’opération IEEE `copySign` ; elle retourne la valeur de `x`, mais avec le signe de `y`.</span><span class="sxs-lookup"><span data-stu-id="16c2c-310">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

## <a name="fast-built-in-json-support"></a><span data-ttu-id="16c2c-311">Prise en charge JSON intégrée rapide</span><span class="sxs-lookup"><span data-stu-id="16c2c-311">Fast built-in JSON support</span></span>

<span data-ttu-id="16c2c-312">Les utilisateurs de .NET se sont largement appuyés sur [**Json.NET**](https://www.newtonsoft.com/json) et d’autres bibliothèques JSON populaires, qui restent de bons choix.</span><span class="sxs-lookup"><span data-stu-id="16c2c-312">.NET users have largely relied on [**Json.NET**](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="16c2c-313">**Json.NET** utilise des chaînes .NET comme type de données de base, au format UTF-16.</span><span class="sxs-lookup"><span data-stu-id="16c2c-313">**Json.NET** uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="16c2c-314">La nouvelle prise en charge JSON intégrée offre des hautes performances et une allocation faible, et elle est basée sur `Span<byte>`.</span><span class="sxs-lookup"><span data-stu-id="16c2c-314">The new built-in JSON support is high-performance, low allocation, and based on `Span<byte>`.</span></span> <span data-ttu-id="16c2c-315">Trois nouveaux types principaux liés à JSON ont été ajoutés à l’espace de noms <xref:System.Text.Json?displayProperty=nameWithType> de .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="16c2c-315">Three new main JSON-related types have been added to .NET Core 3.0 the <xref:System.Text.Json?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="16c2c-316">Ces types ne prennent pas *encore* en charge la sérialisation et la désérialisation des objets CLR traditionnels (OCT).</span><span class="sxs-lookup"><span data-stu-id="16c2c-316">These types don't *yet* support plain old CLR object (POCO) serialization and deserialization.</span></span>

### <a name="utf8jsonreader"></a><span data-ttu-id="16c2c-317">Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="16c2c-317">Utf8JsonReader</span></span>

<span data-ttu-id="16c2c-318"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> est un lecteur hautes performances et à faible allocation de type forward-only pour le texte JSON codé au format UTF-8 et lu à partir de `ReadOnlySpan<byte>`.</span><span class="sxs-lookup"><span data-stu-id="16c2c-318"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="16c2c-319">`Utf8JsonReader` est un type fondamental de bas niveau, permettant de générer des analyseurs et des désérialiseurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="16c2c-319">The `Utf8JsonReader` is a foundational, low-level type, that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="16c2c-320">La lecture d’une charge utile JSON à l’aide du nouveau `Utf8JsonReader` est 2 fois plus rapide qu’avec le lecteur proposé par **Json.NET**.</span><span class="sxs-lookup"><span data-stu-id="16c2c-320">Reading through a JSON payload using the new `Utf8JsonReader` is 2x faster than using the reader from **Json.NET**.</span></span> <span data-ttu-id="16c2c-321">Aucune allocation n’a lieu tant que vous n’avez pas besoin d’actualiser des jetons JSON sous forme de chaînes (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="16c2c-321">It doesn't allocate until you need to actualize JSON tokens as (UTF-16) strings.</span></span>

<span data-ttu-id="16c2c-322">Voici un exemple de lecture par le biais du fichier [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) créé par Visual Studio Code :</span><span class="sxs-lookup"><span data-stu-id="16c2c-322">Here is an example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJson)]

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJsonCall)]

### <a name="utf8jsonwriter"></a><span data-ttu-id="16c2c-323">Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="16c2c-323">Utf8JsonWriter</span></span>

<span data-ttu-id="16c2c-324"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> fournit un moyen d’écrire du texte JSON encodé en UTF-8 partir de types .NET courants, comme `String`, `Int32`, et `DateTime`, avec des hautes performances, sans mise en cache et vers l’avant uniquement.</span><span class="sxs-lookup"><span data-stu-id="16c2c-324"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> provides a high-performance, non-cached, forward-only way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="16c2c-325">Comme le lecteur, l’enregistreur (writer) est un type fondamental de bas niveau, permettant de générer des sérialiseurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="16c2c-325">Like the reader, the writer is a foundational, low-level type, that can be used to build custom serializers.</span></span> <span data-ttu-id="16c2c-326">L’écriture d’une charge utile JSON avec le nouveau `Utf8JsonWriter` est de 30 à 80 % plus rapide qu’avec l’enregistreur (writer) de **Json.NET** et elle n’effectue pas d’allocation.</span><span class="sxs-lookup"><span data-stu-id="16c2c-326">Writing a JSON payload using the new `Utf8JsonWriter` is 30-80% faster than using the writer from **Json.NET** and doesn't allocate.</span></span>

### <a name="jsondocument"></a><span data-ttu-id="16c2c-327">JsonDocument</span><span class="sxs-lookup"><span data-stu-id="16c2c-327">JsonDocument</span></span>

<span data-ttu-id="16c2c-328"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> est basé sur le `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="16c2c-328"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> is built on top of the `Utf8JsonReader`.</span></span> <span data-ttu-id="16c2c-329">Le `JsonDocument` fournit la possibilité d’analyser les données JSON et de générer un modèle DOM (Document Object Model) qui peut être interrogé, et prendre en charge l’accès aléatoire et l’énumération.</span><span class="sxs-lookup"><span data-stu-id="16c2c-329">The `JsonDocument` provides the ability to parse JSON data and build a read-only Document Object Model (DOM) that can be queried to support random access and enumeration.</span></span> <span data-ttu-id="16c2c-330">Les éléments JSON qui composent les données sont accessibles via le type <xref:System.Text.Json.JsonElement> qui est exposé par le `JsonDocument` comme propriété appelée `RootElement`.</span><span class="sxs-lookup"><span data-stu-id="16c2c-330">The JSON elements that compose the data can be accessed via the <xref:System.Text.Json.JsonElement> type that is exposed by the `JsonDocument` as a property called `RootElement`.</span></span> <span data-ttu-id="16c2c-331">Le `JsonElement` contient le tableau et les énumérateurs d’objets JSON, ainsi que des API pour convertir le texte JSON en types .NET courants.</span><span class="sxs-lookup"><span data-stu-id="16c2c-331">The `JsonElement` contains the JSON array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="16c2c-332">L’analyse d’une charge utile JSON classique et l’accès à tous ses membres avec le `JsonDocument` est de 2 à 3 fois plus rapide que **Json.NET**, avec peu d’allocations pour les données de dimension raisonnable (c’est-à-dire, < 1 Mo).</span><span class="sxs-lookup"><span data-stu-id="16c2c-332">Parsing a typical JSON payload and accessing all its members using the `JsonDocument` is 2-3x faster than **Json.NET** with little allocations for data that is reasonably sized (that is, < 1 MB).</span></span>

<span data-ttu-id="16c2c-333">Voici un exemple d’utilisation de `JsonDocument` et de `JsonElement`, qui peut être utilisé comme point de départ :</span><span class="sxs-lookup"><span data-stu-id="16c2c-333">Here is a sample usage of the `JsonDocument` and `JsonElement` that can be used as a starting point:</span></span>

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJson)]

<span data-ttu-id="16c2c-334">Voici un exemple C# 8.0 de lecture par le biais du fichier [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) créé par Visual Studio Code :</span><span class="sxs-lookup"><span data-stu-id="16c2c-334">Here is a C# 8.0 example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJsonCall)]

### <a name="jsonserializer"></a><span data-ttu-id="16c2c-335">JsonSerializer</span><span class="sxs-lookup"><span data-stu-id="16c2c-335">JsonSerializer</span></span>

<span data-ttu-id="16c2c-336"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> s’appuie sur <xref:System.Text.Json.Utf8JsonReader> et <xref:System.Text.Json.Utf8JsonWriter> pour fournir une option de sérialisation rapide à faible consommation de mémoire quand vous utilisez des fragments et des documents JSON.</span><span class="sxs-lookup"><span data-stu-id="16c2c-336"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> is built on top of <xref:System.Text.Json.Utf8JsonReader> and <xref:System.Text.Json.Utf8JsonWriter> to provide a fast, low-memory serialization option when working with JSON documents and fragments.</span></span>

<span data-ttu-id="16c2c-337">Voici un exemple de sérialisation d’un objet dans le format JSON :</span><span class="sxs-lookup"><span data-stu-id="16c2c-337">Here is an example of serializing an object to JSON:</span></span>

[!CODE-csharp[JsonSerializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonSerialize)]

<span data-ttu-id="16c2c-338">Voici un exemple de désérialisation d’une chaîne JSON en un objet.</span><span class="sxs-lookup"><span data-stu-id="16c2c-338">Here is an example of deserializing a JSON string to an object.</span></span> <span data-ttu-id="16c2c-339">Vous pouvez utiliser la chaîne JSON produite par l’exemple précédent :</span><span class="sxs-lookup"><span data-stu-id="16c2c-339">You can use the JSON string produced by the previous example:</span></span>

[!CODE-csharp[JsonDeserializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonDeserialize)]

## <a name="interop-improvements"></a><span data-ttu-id="16c2c-340">Améliorations de l’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="16c2c-340">Interop improvements</span></span>

<span data-ttu-id="16c2c-341">.NET Core 3.0 améliore l’interopérabilité des API natives.</span><span class="sxs-lookup"><span data-stu-id="16c2c-341">.NET Core 3.0 improves native API interop.</span></span>

### <a name="type-nativelibrary"></a><span data-ttu-id="16c2c-342">Type : NativeLibrary</span><span class="sxs-lookup"><span data-stu-id="16c2c-342">Type: NativeLibrary</span></span>

<span data-ttu-id="16c2c-343"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> fournit une encapsulation pour le chargement d’une bibliothèque native (à l’aide de la même logique de chargement que .NET Core P/Invoke) et la fourniture des fonctions d’assistance pertinentes telles que `getSymbol`.</span><span class="sxs-lookup"><span data-stu-id="16c2c-343"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> provides an encapsulation for loading a native library (using the same load logic as .NET Core P/Invoke) and providing the relevant helper functions such as `getSymbol`.</span></span> <span data-ttu-id="16c2c-344">Pour obtenir un exemple de code, consultez la [démonstration DLLMap](https://github.com/dotnet/samples/tree/master/core/extensions/DllMapDemo).</span><span class="sxs-lookup"><span data-stu-id="16c2c-344">For a code example, see the [DLLMap Demo](https://github.com/dotnet/samples/tree/master/core/extensions/DllMapDemo).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="16c2c-345">Interopérabilité native Windows</span><span class="sxs-lookup"><span data-stu-id="16c2c-345">Windows Native Interop</span></span>

<span data-ttu-id="16c2c-346">Windows offre une API native riche sous la forme d’API C plates, de COM et de WinRT.</span><span class="sxs-lookup"><span data-stu-id="16c2c-346">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="16c2c-347">Tandis que .NET Core prend en charge **P/Invoke**, .NET Core 3.0 ajoute la possibilité de **cocréer des API COM** et d’**activer des API WinRT**.</span><span class="sxs-lookup"><span data-stu-id="16c2c-347">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="16c2c-348">Pour obtenir un exemple de code, consultez la [démonstration Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="16c2c-348">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

## <a name="http2-support"></a><span data-ttu-id="16c2c-349">Prise en charge de HTTP/2</span><span class="sxs-lookup"><span data-stu-id="16c2c-349">HTTP/2 support</span></span>

<span data-ttu-id="16c2c-350">Le type <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> prend en charge le protocole HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="16c2c-350">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="16c2c-351">Si HTTP/2 est activé, la version du protocole HTTP est négociée par le biais de TLS/ALPN, et HTTP/2 n’est utilisée que si le serveur le choisit.</span><span class="sxs-lookup"><span data-stu-id="16c2c-351">If HTTP/2 is enabled, the HTTP protocol version is negotiated via TLS/ALPN, and HTTP/2 is used if the server elects to use it.</span></span>

<span data-ttu-id="16c2c-352">Le protocole par défaut reste HTTP/1.1, mais HTTP/2 peut être activé de deux manières différentes.</span><span class="sxs-lookup"><span data-stu-id="16c2c-352">The default protocol remains HTTP/1.1, but HTTP/2 can be enabled in two different ways.</span></span> <span data-ttu-id="16c2c-353">Tout d’abord, vous pouvez définir le message de requête HTTP de sorte à utiliser HTTP/2 :</span><span class="sxs-lookup"><span data-stu-id="16c2c-353">First, you can set the HTTP request message to use HTTP/2:</span></span>

[!CODE-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

<span data-ttu-id="16c2c-354">Ensuite, vous pouvez modifier <xref:System.Net.Http.HttpClient> pour utiliser HTTP/2 par défaut :</span><span class="sxs-lookup"><span data-stu-id="16c2c-354">Second, you can change <xref:System.Net.Http.HttpClient> to use HTTP/2 by default:</span></span>

[!CODE-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

<span data-ttu-id="16c2c-355">Souvent, lorsque vous développez une application, vous souhaiterez utiliser une connexion non chiffrée.</span><span class="sxs-lookup"><span data-stu-id="16c2c-355">Many times when you're developing an application, you want to use an unencrypted connection.</span></span> <span data-ttu-id="16c2c-356">Si vous savez que le point de terminaison cible utilisera HTTP/2, vous pouvez activer les connexions non chiffrées pour HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="16c2c-356">If you know the target endpoint will be using HTTP/2, you can turn on unencrypted connections for HTTP/2.</span></span> <span data-ttu-id="16c2c-357">Vous pouvez activer cela en définissant la variable d’environnement `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` sur `1` ou en l’activant dans le contexte de l’application :</span><span class="sxs-lookup"><span data-stu-id="16c2c-357">You can turn it on by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` environment variable to `1` or by enabling it in the app context:</span></span>

[!CODE-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="16c2c-358">TLS 1.3 et OpenSSL 1.1.1 sous Linux</span><span class="sxs-lookup"><span data-stu-id="16c2c-358">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="16c2c-359">.NET Core tire désormais parti de la [prise en charge de TLS 1.3 dans OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), si disponible dans un environnement donné.</span><span class="sxs-lookup"><span data-stu-id="16c2c-359">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="16c2c-360">Avec TLS 1.3 :</span><span class="sxs-lookup"><span data-stu-id="16c2c-360">With TLS 1.3:</span></span>

- <span data-ttu-id="16c2c-361">Les délais de connexion sont améliorés grâce à une réduction des allers-retours requis entre le client et le serveur.</span><span class="sxs-lookup"><span data-stu-id="16c2c-361">Connection times are improved with reduced round trips required between the client and server.</span></span>
- <span data-ttu-id="16c2c-362">La sécurité est améliorée en raison de la suppression de différents algorithmes de chiffrement obsolètes et non sécurisés.</span><span class="sxs-lookup"><span data-stu-id="16c2c-362">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="16c2c-363">.NET Core 3.0 utilise **OpenSSL 1.1.1**, **OpenSSL 1.1.0** ou **OpenSSL 1.0.2** sur un système Linux s’ils sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="16c2c-363">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="16c2c-364">Quand **OpenSSL 1.1.1** est disponible, les types <xref:System.Net.Security.SslStream?displayProperty=nameWithType> et <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> utilisent **TLS 1.3** (sous réserve que le client et le serveur prennent en charge **TLS 1.3**).</span><span class="sxs-lookup"><span data-stu-id="16c2c-364">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

>[!IMPORTANT]
><span data-ttu-id="16c2c-365">Windows et macOS ne prennent pas encore en charge **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="16c2c-365">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="16c2c-366">.NET Core 3.0 prendra en charge **TLS 1.3** sur ces systèmes d’exploitation dès que de la prise en charge sera disponible.</span><span class="sxs-lookup"><span data-stu-id="16c2c-366">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="16c2c-367">L’exemple C# 8.0 suivant montre comment .NET Core 3.0 sur Ubuntu 18.10 se connecte à <https://www.cloudflare.com> :</span><span class="sxs-lookup"><span data-stu-id="16c2c-367">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

## <a name="cryptography-ciphers"></a><span data-ttu-id="16c2c-368">Chiffrements</span><span class="sxs-lookup"><span data-stu-id="16c2c-368">Cryptography ciphers</span></span>

<span data-ttu-id="16c2c-369">.NET 3.0 prend en charge les chiffrements **AES-GCM** et **AES-CCM**, implémentés avec <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> et <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectivement.</span><span class="sxs-lookup"><span data-stu-id="16c2c-369">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="16c2c-370">Ces algorithmes sont tous deux des [algorithmes AEAD (Authenticated Encryption with Association Data)](https://en.wikipedia.org/wiki/Authenticated_encryption).</span><span class="sxs-lookup"><span data-stu-id="16c2c-370">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="16c2c-371">Le code suivant montre l’utilisation du chiffrement `AesGcm` pour chiffrer et déchiffrer des données aléatoires.</span><span class="sxs-lookup"><span data-stu-id="16c2c-371">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

## <a name="cryptographic-key-importexport"></a><span data-ttu-id="16c2c-372">Importation/exportation d’une clé de chiffrement</span><span class="sxs-lookup"><span data-stu-id="16c2c-372">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="16c2c-373">.NET Core 3.0 prend en charge l’importation et l’exportation de clés publiques et privées asymétriques aux formats standard.</span><span class="sxs-lookup"><span data-stu-id="16c2c-373">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="16c2c-374">Vous n’avez pas besoin d’utiliser un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="16c2c-374">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="16c2c-375">Tous les types de clés, tels que *RSA*, *DSA*, *ECDsa* et *ECDiffieHellman*, prennent en charge les formats suivants :</span><span class="sxs-lookup"><span data-stu-id="16c2c-375">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

- <span data-ttu-id="16c2c-376">**Clé publique**</span><span class="sxs-lookup"><span data-stu-id="16c2c-376">**Public Key**</span></span>
  - <span data-ttu-id="16c2c-377">X.509 SubjectPublicKeyInfo</span><span class="sxs-lookup"><span data-stu-id="16c2c-377">X.509 SubjectPublicKeyInfo</span></span>

- <span data-ttu-id="16c2c-378">**Clé privée**</span><span class="sxs-lookup"><span data-stu-id="16c2c-378">**Private key**</span></span>
  - <span data-ttu-id="16c2c-379">PKCS#8 PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="16c2c-379">PKCS#8 PrivateKeyInfo</span></span>
  - <span data-ttu-id="16c2c-380">PKCS#8 EncryptedPrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="16c2c-380">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="16c2c-381">Les clés RSA prennent également en charge :</span><span class="sxs-lookup"><span data-stu-id="16c2c-381">RSA keys also support:</span></span>

- <span data-ttu-id="16c2c-382">**Clé publique**</span><span class="sxs-lookup"><span data-stu-id="16c2c-382">**Public Key**</span></span>
  - <span data-ttu-id="16c2c-383">PKCS#1 RSAPublicKey</span><span class="sxs-lookup"><span data-stu-id="16c2c-383">PKCS#1 RSAPublicKey</span></span>

- <span data-ttu-id="16c2c-384">**Clé privée**</span><span class="sxs-lookup"><span data-stu-id="16c2c-384">**Private key**</span></span>
  - <span data-ttu-id="16c2c-385">PKCS#1 RSAPrivateKey</span><span class="sxs-lookup"><span data-stu-id="16c2c-385">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="16c2c-386">Les méthodes d’exportation produisent des données binaires encodées au format DER, tout comme les méthodes d’importation.</span><span class="sxs-lookup"><span data-stu-id="16c2c-386">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="16c2c-387">Si une clé est stockée au format PEM compatible avec le texte, l’appelant devra décoder le contenu au format base64 avant d’appeler une méthode d’importation.</span><span class="sxs-lookup"><span data-stu-id="16c2c-387">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

<span data-ttu-id="16c2c-388">Les fichiers **PKCS#8** peuvent être inspectés avec <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType>, tandis que les fichiers **PFX/PKCS#12** peuvent être inspectés avec <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="16c2c-388">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="16c2c-389">Les fichiers **PFX/PKCS#12** peuvent être manipulés avec <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="16c2c-389">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="serialport-for-linux"></a><span data-ttu-id="16c2c-390">SerialPort pour Linux</span><span class="sxs-lookup"><span data-stu-id="16c2c-390">SerialPort for Linux</span></span>

<span data-ttu-id="16c2c-391">.NET Core 3.0 offre une prise en charge de base de <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> sur Linux.</span><span class="sxs-lookup"><span data-stu-id="16c2c-391">.NET Core 3.0 provides basic support for <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="16c2c-392">Auparavant, .NET Core était uniquement pris en charge au moyen de `SerialPort` sur Windows.</span><span class="sxs-lookup"><span data-stu-id="16c2c-392">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

<span data-ttu-id="16c2c-393">Pour plus d’informations sur la prise en charge limitée du port série sur Linux, consultez [GitHub issue #33146](https://github.com/dotnet/corefx/issues/33146).</span><span class="sxs-lookup"><span data-stu-id="16c2c-393">For more information about the limited support for the serial port on Linux, see [GitHub issue #33146](https://github.com/dotnet/corefx/issues/33146).</span></span>

## <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="16c2c-394">Docker et limites de mémoire cgroup</span><span class="sxs-lookup"><span data-stu-id="16c2c-394">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="16c2c-395">L’exécution de .NET Core 3,0 sur Linux avec l’arrimeur fonctionne mieux avec les limites de mémoire cgroup.</span><span class="sxs-lookup"><span data-stu-id="16c2c-395">Running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="16c2c-396">L’exécution d’un conteneur Docker avec des limites de mémoire, par exemple avec `docker run -m`, change le comportement de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="16c2c-396">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

- <span data-ttu-id="16c2c-397">Taille de tas par défaut du récupérateur de mémoire (GC) : au maximum 20 Mo ou 75 % de la limite de mémoire sur le conteneur.</span><span class="sxs-lookup"><span data-stu-id="16c2c-397">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
- <span data-ttu-id="16c2c-398">Une taille explicite peut être définie sous forme de nombre absolu ou de pourcentage de la limite cgroup.</span><span class="sxs-lookup"><span data-stu-id="16c2c-398">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
- <span data-ttu-id="16c2c-399">La taille de segment réservée minimale par tas GC est de 16 Mo.</span><span class="sxs-lookup"><span data-stu-id="16c2c-399">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="16c2c-400">Cette taille réduit le nombre de segments de mémoire qui sont créés sur les machines.</span><span class="sxs-lookup"><span data-stu-id="16c2c-400">This size reduces the number of heaps that are created on machines.</span></span>

## <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="16c2c-401">Tailles de tas de garbage collection plus petites</span><span class="sxs-lookup"><span data-stu-id="16c2c-401">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="16c2c-402">La taille de tas par défaut du récupérateur de mémoire a été réduite, aboutissant à une diminution de la quantité de mémoire utilisée par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="16c2c-402">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="16c2c-403">Ce changement est plus conforme au budget d’allocation de génération 0 avec les tailles des caches des processeurs modernes.</span><span class="sxs-lookup"><span data-stu-id="16c2c-403">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

## <a name="garbage-collection-large-page-support"></a><span data-ttu-id="16c2c-404">Prise en charge de grandes pages du garbage collection</span><span class="sxs-lookup"><span data-stu-id="16c2c-404">Garbage Collection Large Page support</span></span>

<span data-ttu-id="16c2c-405">Les grandes pages (également appelées HugePages sur Linux) sont une fonctionnalité qui permet au système d’exploitation d’établir des régions de mémoire plus grandes que la taille de page native (souvent 4 Ko) pour améliorer les performances de l’application qui demande ces grandes pages.</span><span class="sxs-lookup"><span data-stu-id="16c2c-405">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="16c2c-406">Vous pouvez maintenant configurer le récupérateur de mémoire avec la définition **GCLargePages** en tant que fonctionnalité que vous pouvez choisir d’utiliser et qui permet d’allouer de grandes pages sur Windows.</span><span class="sxs-lookup"><span data-stu-id="16c2c-406">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="16c2c-407">Prise en charge de GPIO pour Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="16c2c-407">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="16c2c-408">Deux packages ont été publiés sur NuGet, que vous pouvez utiliser pour la programmation de GPIO :</span><span class="sxs-lookup"><span data-stu-id="16c2c-408">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

- [<span data-ttu-id="16c2c-409">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="16c2c-409">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
- [<span data-ttu-id="16c2c-410">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="16c2c-410">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="16c2c-411">Les packages GPIO incluent des API pour les appareils *GPIO*, *SPI*, *I2C* et *PWM*.</span><span class="sxs-lookup"><span data-stu-id="16c2c-411">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="16c2c-412">Le package de liaisons IoT comprend des liaisons d’appareil.</span><span class="sxs-lookup"><span data-stu-id="16c2c-412">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="16c2c-413">Pour plus d’informations, consultez le [dépôt GitHub devices](https://github.com/dotnet/iot/blob/master/src/devices/).</span><span class="sxs-lookup"><span data-stu-id="16c2c-413">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

## <a name="arm64-linux-support"></a><span data-ttu-id="16c2c-414">Support ARM64 Linux</span><span class="sxs-lookup"><span data-stu-id="16c2c-414">ARM64 Linux support</span></span>

<span data-ttu-id="16c2c-415">.NET Core 3.0 prend en charge ARM64 pour Linux.</span><span class="sxs-lookup"><span data-stu-id="16c2c-415">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="16c2c-416">Actuellement, ARM64 est principallement utilisé dans des scénarios IoT.</span><span class="sxs-lookup"><span data-stu-id="16c2c-416">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="16c2c-417">Pour plus d’informations, consultez [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span><span class="sxs-lookup"><span data-stu-id="16c2c-417">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="16c2c-418">Des [images Docker pour .NET Core sur ARM64](https://hub.docker.com/r/microsoft/dotnet/) sont disponibles pour Alpine, Debian et Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="16c2c-418">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="16c2c-419">La prise en charge d’**ARM64** sous Windows n’est pas encore disponible.</span><span class="sxs-lookup"><span data-stu-id="16c2c-419">**ARM64** Windows support isn't yet available.</span></span>
