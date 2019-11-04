---
title: Nouveautés de .NET Core 3.0
description: Découvrez les nouvelles fonctionnalités de .NET Core 3.0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 10/22/2019
ms.openlocfilehash: dcbf1073c12650101efdcf6022db0b29ace2eb3f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420756"
---
# <a name="whats-new-in-net-core-30"></a><span data-ttu-id="0bc25-103">Nouveautés de .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0bc25-103">What's new in .NET Core 3.0</span></span>

<span data-ttu-id="0bc25-104">Cet article décrit les nouveautés de .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="0bc25-104">This article describes what is new in .NET Core 3.0.</span></span> <span data-ttu-id="0bc25-105">Une des principales améliorations est la prise en charge des applications de bureau Windows (Windows uniquement).</span><span class="sxs-lookup"><span data-stu-id="0bc25-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="0bc25-106">En utilisant le composant du SDK .NET Core 3.0 Windows Desktop, vous pouvez porter vos applications Windows Forms et Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="0bc25-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="0bc25-107">Pour être clair, le composant Windows Desktop est pris en charge et inclus seulement sur Windows.</span><span class="sxs-lookup"><span data-stu-id="0bc25-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="0bc25-108">Pour plus d’informations, consultez la section [Bureau Windows](#windows-desktop) plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="0bc25-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="0bc25-109">.NET Core 3.0 prend en charge C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="0bc25-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="0bc25-110">Il est fortement recommandé d’utiliser [Visual Studio 2019 version 16,3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou ultérieure, [Visual Studio pour Mac 8,3](/visualstudio/mac/install-preview) ou version ultérieure, ou [Visual Studio code](https://code.visualstudio.com/) avec l'  **C# extension**la plus récente.</span><span class="sxs-lookup"><span data-stu-id="0bc25-110">It's highly recommended that you use [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or newer, [Visual Studio for Mac 8.3](/visualstudio/mac/install-preview) or newer, or [Visual Studio Code](https://code.visualstudio.com/) with the latest **C# extension**.</span></span>

<span data-ttu-id="0bc25-111">[Téléchargez et commencez à utiliser .net Core 3,0](https://aka.ms/netcore3download) pour le moment sur Windows, MacOS ou Linux.</span><span class="sxs-lookup"><span data-stu-id="0bc25-111">[Download and get started with .NET Core 3.0](https://aka.ms/netcore3download) right now on Windows, macOS, or Linux.</span></span>

<span data-ttu-id="0bc25-112">Pour plus d’informations sur la version, consultez l' [annonce de .net Core 3,0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="0bc25-112">For more information about the release, see the [.NET Core 3.0 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).</span></span>

<span data-ttu-id="0bc25-113">.NET Core RC1 a été considéré comme une production prête par Microsoft et a été entièrement pris en charge.</span><span class="sxs-lookup"><span data-stu-id="0bc25-113">.NET Core RC1 was considered production ready by Microsoft and was fully supported.</span></span> <span data-ttu-id="0bc25-114">Si vous utilisez une version préliminaire, vous devez passer à la version RTM pour une prise en charge continue.</span><span class="sxs-lookup"><span data-stu-id="0bc25-114">If you're using a preview release, you must move to the RTM version for continued support.</span></span>

## <a name="language-improvements-c-80"></a><span data-ttu-id="0bc25-115">Améliorations C# du langage 8,0</span><span class="sxs-lookup"><span data-stu-id="0bc25-115">Language improvements C# 8.0</span></span>

<span data-ttu-id="0bc25-116">C#8,0 fait également partie de cette version, qui comprend la fonctionnalité de [types de référence Nullable](../../csharp/tutorials/nullable-reference-types.md) , les [flux asynchrones](../../csharp/tutorials/generate-consume-asynchronous-stream.md)et [plus de modèles](../../csharp/tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="0bc25-116">C# 8.0 is also part of this release, which includes the [nullable reference types](../../csharp/tutorials/nullable-reference-types.md) feature, [async streams](../../csharp/tutorials/generate-consume-asynchronous-stream.md), and [more patterns](../../csharp/tutorials/pattern-matching.md).</span></span> <span data-ttu-id="0bc25-117">Pour plus d’informations sur les fonctionnalités de C# 8.0, consultez [Nouveautés de C# 8.0](../../csharp/whats-new/csharp-8.md).</span><span class="sxs-lookup"><span data-stu-id="0bc25-117">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

<span data-ttu-id="0bc25-118">Des améliorations ont été apportées au langage pour prendre en charge les fonctionnalités d’API suivantes, détaillées ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="0bc25-118">Language enhancements were added to support the following API features detailed below:</span></span>

- [<span data-ttu-id="0bc25-119">Plages et index</span><span class="sxs-lookup"><span data-stu-id="0bc25-119">Ranges and indices</span></span>](#ranges-and-indices)
- [<span data-ttu-id="0bc25-120">Flux asynchrones</span><span class="sxs-lookup"><span data-stu-id="0bc25-120">Async streams</span></span>](#async-streams)

## <a name="net-standard-21"></a><span data-ttu-id="0bc25-121">.NET Standard 2.1</span><span class="sxs-lookup"><span data-stu-id="0bc25-121">.NET Standard 2.1</span></span>

<span data-ttu-id="0bc25-122">.NET Core 3,0 implémente **.NET Standard 2,1**.</span><span class="sxs-lookup"><span data-stu-id="0bc25-122">.NET Core 3.0 implements **.NET Standard 2.1**.</span></span> <span data-ttu-id="0bc25-123">Toutefois, le modèle de `dotnet new classlib` par défaut génère un projet qui cible toujours **.NET Standard 2,0**.</span><span class="sxs-lookup"><span data-stu-id="0bc25-123">However, the default `dotnet new classlib` template generates a project that still targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="0bc25-124">Pour cibler **.NET Standard 2.1**, modifiez votre fichier projet et définissez la propriété `TargetFramework` sur `netstandard2.1` :</span><span class="sxs-lookup"><span data-stu-id="0bc25-124">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="0bc25-125">Si vous utilisez Visual Studio, vous avez besoin de [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), car Visual Studio 2017 ne prend pas en charge **.NET Standard 2.1** ou **.NET Core 3.0**.</span><span class="sxs-lookup"><span data-stu-id="0bc25-125">If you're using Visual Studio, you need [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span>

## <a name="compiledeploy"></a><span data-ttu-id="0bc25-126">Compiler/déployer</span><span class="sxs-lookup"><span data-stu-id="0bc25-126">Compile/Deploy</span></span>

### <a name="default-executables"></a><span data-ttu-id="0bc25-127">Exécutables par défaut</span><span class="sxs-lookup"><span data-stu-id="0bc25-127">Default executables</span></span>

<span data-ttu-id="0bc25-128">.NET Core génère désormais des [exécutables dépendant du framework](../deploying/index.md#framework-dependent-executables-fde) par défaut.</span><span class="sxs-lookup"><span data-stu-id="0bc25-128">.NET Core now builds [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="0bc25-129">Ce comportement est nouveau pour les applications qui utilisent une version .NET Core installée de façon globale.</span><span class="sxs-lookup"><span data-stu-id="0bc25-129">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="0bc25-130">Auparavant, seuls les [déploiements autonomes](../deploying/index.md#self-contained-deployments-scd) produisaient un exécutable.</span><span class="sxs-lookup"><span data-stu-id="0bc25-130">Previously, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="0bc25-131">Lors de l’étape `dotnet build` ou `dotnet publish`, un exécutable est créé, qui correspond à l’environnement et à la plateforme du Kit de développement que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="0bc25-131">During `dotnet build` or `dotnet publish`, an executable is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="0bc25-132">Vous pouvez obtenir le même résultat avec ces exécutables, comme vous le feriez avec d’autres exécutables natifs comme :</span><span class="sxs-lookup"><span data-stu-id="0bc25-132">You can expect the same things with these executables as you would other native executables, such as:</span></span>

- <span data-ttu-id="0bc25-133">Vous pouvez double-cliquer sur l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="0bc25-133">You can double-click on the executable.</span></span>
- <span data-ttu-id="0bc25-134">Vous pouvez lancer l’application directement à partir d’une invite de commandes, par exemple `myapp.exe` sous Windows, et `./myapp` sous Linux et macOS.</span><span class="sxs-lookup"><span data-stu-id="0bc25-134">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

### <a name="single-file-executables"></a><span data-ttu-id="0bc25-135">Exécutable monofichier</span><span class="sxs-lookup"><span data-stu-id="0bc25-135">Single-file executables</span></span>

<span data-ttu-id="0bc25-136">La commande `dotnet publish` prend en charge l’empaquetage de votre application dans un exécutable monofichier spécifique de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="0bc25-136">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="0bc25-137">L’exécutable est auto-extractible et contient toutes les dépendances (y compris natives) nécessaires à l’exécution de votre application.</span><span class="sxs-lookup"><span data-stu-id="0bc25-137">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="0bc25-138">Lors de la première exécution de l’application, celle-ci est extraite d’un répertoire basé sur le nom de l’application et l’identificateur de la build.</span><span class="sxs-lookup"><span data-stu-id="0bc25-138">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="0bc25-139">Le démarrage est plus rapide quand l’application est réexécutée.</span><span class="sxs-lookup"><span data-stu-id="0bc25-139">Startup is faster when the application is run again.</span></span> <span data-ttu-id="0bc25-140">L’application n’a pas besoin de s’extraire elle-même une deuxième fois, sauf si une nouvelle version a été utilisée.</span><span class="sxs-lookup"><span data-stu-id="0bc25-140">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="0bc25-141">Pour publier un exécutable monofichier, définissez `PublishSingleFile` dans votre projet ou sur la ligne de commande avec la commande `dotnet publish` :</span><span class="sxs-lookup"><span data-stu-id="0bc25-141">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

<span data-ttu-id="0bc25-142">ou</span><span class="sxs-lookup"><span data-stu-id="0bc25-142">-or-</span></span>

```dotnetcli
dotnet publish -r win10-x64 -p:PublishSingleFile=true
```

<span data-ttu-id="0bc25-143">Pour plus d’informations sur la publication monofichier, consultez le [document conceptuel sur l’outil de regroupement monofichier](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="0bc25-143">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span></span>

### <a name="assembly-linking"></a><span data-ttu-id="0bc25-144">Liaison d’assemblys</span><span class="sxs-lookup"><span data-stu-id="0bc25-144">Assembly linking</span></span>

<span data-ttu-id="0bc25-145">Le SDK .NET Core 3.0 est fourni avec un outil qui peut réduire la taille des applications en analysant le langage intermédiaire et en supprimant les assemblys inutilisés.</span><span class="sxs-lookup"><span data-stu-id="0bc25-145">The .NET core 3.0 SDK comes with a tool that can reduce the size of apps by analyzing IL and trimming unused assemblies.</span></span>

<span data-ttu-id="0bc25-146">Les applications autonomes incluent tous les éléments nécessaires pour exécuter votre code, sans nécessiter que .NET soit installé sur la machine hôte.</span><span class="sxs-lookup"><span data-stu-id="0bc25-146">Self-contained apps include everything needed to run your code, without requiring .NET to be installed on the host computer.</span></span> <span data-ttu-id="0bc25-147">Toutefois, il arrive souvent que l’application nécessite seulement un petit sous-ensemble de l’infrastructure pour fonctionner, et que les autres bibliothèques inutilisées puissent être supprimées.</span><span class="sxs-lookup"><span data-stu-id="0bc25-147">However, many times the app only requires a small subset of the framework to function, and other unused libraries could be removed.</span></span>

<span data-ttu-id="0bc25-148">.NET Core inclut désormais un paramètre qui utilisera l’outil [Éditeur de liens de langage intermédiaire](https://github.com/mono/linker) analyser le langage intermédiaire de votre application.</span><span class="sxs-lookup"><span data-stu-id="0bc25-148">.NET Core now includes a setting that will use the [IL linker](https://github.com/mono/linker) tool to scan the IL of your app.</span></span> <span data-ttu-id="0bc25-149">Cet outil détecte le code requis, puis supprime les bibliothèques inutilisées.</span><span class="sxs-lookup"><span data-stu-id="0bc25-149">This tool detects what code is required, and then trims unused libraries.</span></span> <span data-ttu-id="0bc25-150">Cet outil peut réduire considérablement la taille de déploiement de certaines applications.</span><span class="sxs-lookup"><span data-stu-id="0bc25-150">This tool can significantly reduce the deployment size of some apps.</span></span>

<span data-ttu-id="0bc25-151">Pour activer cet outil, ajoutez le paramètre `<PublishTrimmed>` dans votre projet et publiez une application autonome :</span><span class="sxs-lookup"><span data-stu-id="0bc25-151">To enable this tool, add the `<PublishTrimmed>` setting in your project and publish a self-contained app:</span></span>

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```dotnetcli
dotnet publish -r <rid> -c Release
```

<span data-ttu-id="0bc25-152">Par exemple, le nouveau modèle de projet de console de base « hello world » inclus, lors de sa publication, atteint la taille d’environ 70 Mo.</span><span class="sxs-lookup"><span data-stu-id="0bc25-152">As an example, the basic "hello world" new console project template that is included, when published, hits about 70 MB in size.</span></span> <span data-ttu-id="0bc25-153">Avec `<PublishTrimmed>`, sa taille est réduite à environ 30 Mo.</span><span class="sxs-lookup"><span data-stu-id="0bc25-153">By using `<PublishTrimmed>`, that size is reduced to about 30 MB.</span></span>

<span data-ttu-id="0bc25-154">Il est important de prendre en compte le fait que les applications ou infrastructures (dont ASP.NET Core et WPF) qui utilisent la réflexion ou des fonctionnalités dynamiques associées cesseront souvent de fonctionner après cette troncature.</span><span class="sxs-lookup"><span data-stu-id="0bc25-154">It's important to consider that applications or frameworks (including ASP.NET Core and WPF) that use reflection or related dynamic features, will often break when trimmed.</span></span> <span data-ttu-id="0bc25-155">Cette rupture se produit car l’éditeur de liens ne connaît pas ce comportement dynamique et ne peut pas déterminer les types de framework nécessaires pour la réflexion.</span><span class="sxs-lookup"><span data-stu-id="0bc25-155">This breakage occurs because the linker doesn't know about this dynamic behavior and can't determine which framework types are required for reflection.</span></span> <span data-ttu-id="0bc25-156">L’outil d’éditeur de liens de langage intermédiaire peut être configuré pour être conscient de ce scénario.</span><span class="sxs-lookup"><span data-stu-id="0bc25-156">The IL Linker tool can be configured to be aware of this scenario.</span></span>

<span data-ttu-id="0bc25-157">Avant toute chose, veillez à tester votre application après réduction.</span><span class="sxs-lookup"><span data-stu-id="0bc25-157">Above all else, be sure to test your app after trimming.</span></span>

<span data-ttu-id="0bc25-158">Pour plus d’informations sur l’outil d’éditeur de liens de langage intermédiaire, consultez la [documentation](https://aka.ms/dotnet-illink) ou visitez le référentiel [mono/linker]( https://github.com/mono/linker).</span><span class="sxs-lookup"><span data-stu-id="0bc25-158">For more information about the IL Linker tool, see the [documentation](https://aka.ms/dotnet-illink) or visit the [mono/linker]( https://github.com/mono/linker) repo.</span></span>

### <a name="tiered-compilation"></a><span data-ttu-id="0bc25-159">Compilation hiérarchisée</span><span class="sxs-lookup"><span data-stu-id="0bc25-159">Tiered compilation</span></span>

<span data-ttu-id="0bc25-160">La [compilation hiérarchisée](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) est activée par défaut avec .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="0bc25-160">[Tiered compilation](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="0bc25-161">Cette fonctionnalité permet au runtime d’utiliser de manière plus adaptative le compilateur juste-à-temps (Just-In-Time ou JIT) pour obtenir de meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="0bc25-161">This feature enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance.</span></span>

<span data-ttu-id="0bc25-162">Le principal avantage de la compilation hiérarchisée est d’autoriser les méthode (re-) JIT avec un niveau de moins bonne qualité mais plus rapide, ou avec un niveau de meilleure qualité mais plus lent.</span><span class="sxs-lookup"><span data-stu-id="0bc25-162">The main benefit of TC is to enable (re-)jitting methods with a lower-quality-but-faster tier or a higher-quality-but-slower tier.</span></span> <span data-ttu-id="0bc25-163">Cela permet d’améliorer les performances d’une application quand elle passe par les différents stades de l’exécution, du démarrage à l’état stable.</span><span class="sxs-lookup"><span data-stu-id="0bc25-163">This helps increase performance of an application as it goes through various stages of execution, from startup through steady-state.</span></span> <span data-ttu-id="0bc25-164">Ceci contraste avec l’approche de la compilation non hiérarchisée, où chaque méthode est compilée d’une seule manière (la même que le niveau de qualité supérieure), qui privilégie la stabilité de l’état au détriment des performances au démarrage.</span><span class="sxs-lookup"><span data-stu-id="0bc25-164">This contrasts with the non-TC approach, where every method is compiled a single way (the same as the high-quality tier), which is biased to steady-state over startup performance.</span></span>

<span data-ttu-id="0bc25-165">Pour activer Quick JIT (code JIT de niveau 0), utilisez ce paramétrage dans votre fichier projet :</span><span class="sxs-lookup"><span data-stu-id="0bc25-165">To enable Quick JIT (tier 0 jitted code), use this setting in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>true</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="0bc25-166">Pour désactiver complètement la compilation hiérarchisée, utilisez ce paramétrage dans votre fichier projet :</span><span class="sxs-lookup"><span data-stu-id="0bc25-166">To disable TC completely, use this setting in your project file:</span></span>

```xml
<TieredCompilation>false</TieredCompilation>
```

### <a name="readytorun-images"></a><span data-ttu-id="0bc25-167">Images ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="0bc25-167">ReadyToRun images</span></span>

<span data-ttu-id="0bc25-168">Vous pouvez améliorer le temps de démarrage de votre application .NET Core en compilant les assemblys de votre application au format ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="0bc25-168">You can improve the startup time of your .NET Core application by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="0bc25-169">R2R est une forme de compilation ahead-of-time (AOT).</span><span class="sxs-lookup"><span data-stu-id="0bc25-169">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="0bc25-170">Les fichiers binaires R2R améliorent les performances de démarrage en réduisant la quantité de travail que le compilateur juste-à-temps (JIT) doit faire lorsque votre application est chargée.</span><span class="sxs-lookup"><span data-stu-id="0bc25-170">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="0bc25-171">Les fichiers binaires contiennent du code natif similaire à ce que la compilation JIT produirait.</span><span class="sxs-lookup"><span data-stu-id="0bc25-171">The binaries contain similar native code compared to what the JIT would produce.</span></span> <span data-ttu-id="0bc25-172">Cependant, les fichiers binaires R2R sont plus grands, car ils contiennent à la fois le code du langage intermédiaire (IL), qui est toujours nécessaire pour certains scénarios, et la version native du même code.</span><span class="sxs-lookup"><span data-stu-id="0bc25-172">However, R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="0bc25-173">R2R est disponible seulement quand vous publiez une application autonome qui cible des environnements d’exécution spécifiques (RID), comme Linux x64 ou Windows x64.</span><span class="sxs-lookup"><span data-stu-id="0bc25-173">R2R is only available when you publish a self-contained app that targets specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="0bc25-174">Pour compiler votre projet en ReadyToRun, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="0bc25-174">To compile your project as ReadyToRun, do the following:</span></span>

01. <span data-ttu-id="0bc25-175">Ajoutez le paramètre `<PublishReadyToRun>` à votre projet :</span><span class="sxs-lookup"><span data-stu-id="0bc25-175">Add the `<PublishReadyToRun>` setting to your project:</span></span>

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. <span data-ttu-id="0bc25-176">Publiez une application autonome.</span><span class="sxs-lookup"><span data-stu-id="0bc25-176">Publish a self-contained app.</span></span> <span data-ttu-id="0bc25-177">Par exemple, cette commande crée une application autonome pour la version 64 bits de Windows :</span><span class="sxs-lookup"><span data-stu-id="0bc25-177">For example, this command creates a self-contained app for the 64-bit version of Windows:</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64 --self-contained
    ```

#### <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="0bc25-178">Restrictions d’architecture/de multiplateforme</span><span class="sxs-lookup"><span data-stu-id="0bc25-178">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="0bc25-179">Le compilateur ReadyToRun ne prend actuellement pas en charge le ciblage croisé.</span><span class="sxs-lookup"><span data-stu-id="0bc25-179">The ReadyToRun compiler doesn't currently support cross-targeting.</span></span> <span data-ttu-id="0bc25-180">Vous devez compiler sur une cible donnée.</span><span class="sxs-lookup"><span data-stu-id="0bc25-180">You must compile on a given target.</span></span> <span data-ttu-id="0bc25-181">Par exemple, si vous souhaitez avoir des images R2R Windows x64, vous devez exécuter la commande de publication sur cet environnement.</span><span class="sxs-lookup"><span data-stu-id="0bc25-181">For example, if you want R2R images for Windows x64, you need to run the publish command on that environment.</span></span>

<span data-ttu-id="0bc25-182">Exceptions au ciblage croisé :</span><span class="sxs-lookup"><span data-stu-id="0bc25-182">Exceptions to cross-targeting:</span></span>

- <span data-ttu-id="0bc25-183">Windows x64 peut être utilisé pour compiler des images Windows ARM32, ARM64 et x86.</span><span class="sxs-lookup"><span data-stu-id="0bc25-183">Windows x64 can be used to compile Windows ARM32, ARM64, and x86 images.</span></span>
- <span data-ttu-id="0bc25-184">Windows x86 peut être utilisé pour compiler des images Windows ARM32.</span><span class="sxs-lookup"><span data-stu-id="0bc25-184">Windows x86 can be used to compile Windows ARM32 images.</span></span>
- <span data-ttu-id="0bc25-185">Linux x64 peut être utilisé pour compiler des images Linux ARM32 et ARM64.</span><span class="sxs-lookup"><span data-stu-id="0bc25-185">Linux x64 can be used to compile Linux ARM32 and ARM64 images.</span></span>

## <a name="runtimesdk"></a><span data-ttu-id="0bc25-186">Runtime/SDK</span><span class="sxs-lookup"><span data-stu-id="0bc25-186">Runtime/SDK</span></span>

### <a name="major-version-roll-forward"></a><span data-ttu-id="0bc25-187">Restauration par progression d’une version majeure</span><span class="sxs-lookup"><span data-stu-id="0bc25-187">Major-version Roll Forward</span></span>

<span data-ttu-id="0bc25-188">.NET Core 3.0 introduit une fonctionnalité que vous pouvez choisir d’utiliser et qui permet de restaurer par progression votre application vers la dernière version majeure de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0bc25-188">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="0bc25-189">En outre, un nouveau paramètre a été ajouté pour contrôler la façon dont la restauration par progression est appliquée à votre application.</span><span class="sxs-lookup"><span data-stu-id="0bc25-189">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="0bc25-190">Ce paramètre peut être configuré des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="0bc25-190">This can be configured in the following ways:</span></span>

- <span data-ttu-id="0bc25-191">Propriété du fichier projet : `RollForward`</span><span class="sxs-lookup"><span data-stu-id="0bc25-191">Project file property: `RollForward`</span></span>
- <span data-ttu-id="0bc25-192">Propriété du fichier config du runtime : `rollForward`</span><span class="sxs-lookup"><span data-stu-id="0bc25-192">Runtime configuration file property: `rollForward`</span></span>
- <span data-ttu-id="0bc25-193">Variable d’environnement : `DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="0bc25-193">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="0bc25-194">Argument de ligne de commande : `--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="0bc25-194">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="0bc25-195">L’une des valeurs suivantes doit être spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0bc25-195">One of the following values must be specified.</span></span> <span data-ttu-id="0bc25-196">Si le paramètre est omis, **Minor** est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="0bc25-196">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="0bc25-197">**LatestPatch**</span><span class="sxs-lookup"><span data-stu-id="0bc25-197">**LatestPatch**</span></span>\
<span data-ttu-id="0bc25-198">Restauration par progression vers la version de correctif la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="0bc25-198">Roll forward to the highest patch version.</span></span> <span data-ttu-id="0bc25-199">Cette valeur désactive la restauration par progression d’une version mineure.</span><span class="sxs-lookup"><span data-stu-id="0bc25-199">This disables minor version roll forward.</span></span>
- <span data-ttu-id="0bc25-200">**Minor**</span><span class="sxs-lookup"><span data-stu-id="0bc25-200">**Minor**</span></span>\
<span data-ttu-id="0bc25-201">Restauration par progression vers la version mineure supérieure la plus basse, si la version mineure demandée est manquante.</span><span class="sxs-lookup"><span data-stu-id="0bc25-201">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="0bc25-202">Si la version mineure demandée est présente, la stratégie **LatestPatch** est utilisée.</span><span class="sxs-lookup"><span data-stu-id="0bc25-202">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="0bc25-203">**Major**</span><span class="sxs-lookup"><span data-stu-id="0bc25-203">**Major**</span></span>\
<span data-ttu-id="0bc25-204">Restauration par progression vers la version majeure supérieure la plus basse, et la version mineure la plus basse, si la version majeure demandée est manquante.</span><span class="sxs-lookup"><span data-stu-id="0bc25-204">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="0bc25-205">Si la version majeure demandée est présente, la stratégie **Minor** est utilisée.</span><span class="sxs-lookup"><span data-stu-id="0bc25-205">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="0bc25-206">**LatestMinor**</span><span class="sxs-lookup"><span data-stu-id="0bc25-206">**LatestMinor**</span></span>\
<span data-ttu-id="0bc25-207">Restauration par progression vers la version mineure la plus élevée, si la version mineure demandée est présente.</span><span class="sxs-lookup"><span data-stu-id="0bc25-207">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="0bc25-208">Conçu pour les scénarios d’hébergement de composant.</span><span class="sxs-lookup"><span data-stu-id="0bc25-208">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="0bc25-209">**LatestMajor**</span><span class="sxs-lookup"><span data-stu-id="0bc25-209">**LatestMajor**</span></span>\
<span data-ttu-id="0bc25-210">Restauration par progression vers la version majeure la plus élevée et la version mineure la plus élevée, si la version majeure demandée est présente.</span><span class="sxs-lookup"><span data-stu-id="0bc25-210">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="0bc25-211">Conçu pour les scénarios d’hébergement de composant.</span><span class="sxs-lookup"><span data-stu-id="0bc25-211">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="0bc25-212">**Disable**</span><span class="sxs-lookup"><span data-stu-id="0bc25-212">**Disable**</span></span>\
<span data-ttu-id="0bc25-213">Ne pas effectuer de restauration par progression.</span><span class="sxs-lookup"><span data-stu-id="0bc25-213">Don't roll forward.</span></span> <span data-ttu-id="0bc25-214">Lier uniquement à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0bc25-214">Only bind to specified version.</span></span> <span data-ttu-id="0bc25-215">Cette stratégie n’est pas recommandée pour une utilisation générale, car elle désactive la possibilité d’effectuer une restauration par progression vers les derniers correctifs.</span><span class="sxs-lookup"><span data-stu-id="0bc25-215">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="0bc25-216">Cette valeur est recommandée uniquement à des fins de test.</span><span class="sxs-lookup"><span data-stu-id="0bc25-216">This value is only recommended for testing.</span></span>

<span data-ttu-id="0bc25-217">Outre le paramètre **Disable**, tous les paramètres utilisent la version de correctif disponible la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="0bc25-217">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

### <a name="build-copies-dependencies"></a><span data-ttu-id="0bc25-218">Dépendances de copies de build</span><span class="sxs-lookup"><span data-stu-id="0bc25-218">Build copies dependencies</span></span>

<span data-ttu-id="0bc25-219">La commande `dotnet build` copie maintenant les dépendances NuGet pour votre application à partir du cache NuGet vers le dossier de sortie de build.</span><span class="sxs-lookup"><span data-stu-id="0bc25-219">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="0bc25-220">Auparavant, les dépendances étaient copiées uniquement dans le cadre de `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="0bc25-220">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="0bc25-221">Certaines opérations, par exemple la liaison et la publication d’une page de type Razor, nécessiteront toujours une publication.</span><span class="sxs-lookup"><span data-stu-id="0bc25-221">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

### <a name="local-tools"></a><span data-ttu-id="0bc25-222">Outils locaux</span><span class="sxs-lookup"><span data-stu-id="0bc25-222">Local tools</span></span>

<span data-ttu-id="0bc25-223">.NET Core 3.0 introduit des outils locaux.</span><span class="sxs-lookup"><span data-stu-id="0bc25-223">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="0bc25-224">Les outils locaux sont similaires aux [outils globaux](../tools/global-tools.md), mais ils sont associés à un emplacement particulier sur le disque.</span><span class="sxs-lookup"><span data-stu-id="0bc25-224">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="0bc25-225">Les outils locaux ne sont pas disponibles globalement et sont distribués en tant que packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="0bc25-225">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="0bc25-226">Si vous avez essayé des outils locaux dans .NET Core 3.0 Preview 1, par exemple pour exécuter `dotnet tool restore` ou `dotnet tool install`, supprimez le dossier de cache des outils locaux.</span><span class="sxs-lookup"><span data-stu-id="0bc25-226">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="0bc25-227">Sinon, les outils locaux ne fonctionneront sur aucune nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="0bc25-227">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="0bc25-228">Ce dossier se trouve à ces emplacements :</span><span class="sxs-lookup"><span data-stu-id="0bc25-228">This folder is located at:</span></span>
>
> <span data-ttu-id="0bc25-229">Sur macOS, Linux : `rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="0bc25-229">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="0bc25-230">Sur Windows : `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="0bc25-230">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="0bc25-231">Les outils locaux s’appuient sur un nom de fichier manifeste `dotnet-tools.json` dans votre répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="0bc25-231">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="0bc25-232">Ce fichier manifeste définit les outils qui doivent être disponibles dans ce dossier et sous-celui-ci.</span><span class="sxs-lookup"><span data-stu-id="0bc25-232">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="0bc25-233">Vous pouvez distribuer le fichier manifeste avec votre code pour que toute personne qui utilise votre code puisse restaurer et utiliser les mêmes outils.</span><span class="sxs-lookup"><span data-stu-id="0bc25-233">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="0bc25-234">Pour les outils locaux et globaux, une version compatible du runtime est requise.</span><span class="sxs-lookup"><span data-stu-id="0bc25-234">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="0bc25-235">De nombreux outils actuellement sur NuGet.org ciblent le runtime .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="0bc25-235">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="0bc25-236">Pour installer ces outils de façon locale ou globale, vous devez toujours installer le [runtime NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="0bc25-236">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

### <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="0bc25-237">Tailles de tas de garbage collection plus petites</span><span class="sxs-lookup"><span data-stu-id="0bc25-237">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="0bc25-238">La taille de tas par défaut du récupérateur de mémoire a été réduite, aboutissant à une diminution de la quantité de mémoire utilisée par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0bc25-238">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="0bc25-239">Ce changement est plus conforme au budget d’allocation de génération 0 avec les tailles des caches des processeurs modernes.</span><span class="sxs-lookup"><span data-stu-id="0bc25-239">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

### <a name="garbage-collection-large-page-support"></a><span data-ttu-id="0bc25-240">Prise en charge de grandes pages du garbage collection</span><span class="sxs-lookup"><span data-stu-id="0bc25-240">Garbage Collection Large Page support</span></span>

<span data-ttu-id="0bc25-241">Les grandes pages (également appelées HugePages sur Linux) sont une fonctionnalité qui permet au système d’exploitation d’établir des régions de mémoire plus grandes que la taille de page native (souvent 4 Ko) pour améliorer les performances de l’application qui demande ces grandes pages.</span><span class="sxs-lookup"><span data-stu-id="0bc25-241">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="0bc25-242">Vous pouvez maintenant configurer le récupérateur de mémoire avec la définition **GCLargePages** en tant que fonctionnalité que vous pouvez choisir d’utiliser et qui permet d’allouer de grandes pages sur Windows.</span><span class="sxs-lookup"><span data-stu-id="0bc25-242">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="windows-desktop--com"></a><span data-ttu-id="0bc25-243">Windows Desktop & COM</span><span class="sxs-lookup"><span data-stu-id="0bc25-243">Windows Desktop & COM</span></span>

### <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="0bc25-244">Windows Installer pour le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="0bc25-244">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="0bc25-245">Le programme d’installation MSI pour Windows a changé à compter de .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="0bc25-245">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="0bc25-246">Les programmes d’installation du SDK mettent désormais à niveau les versions des plages de fonctionnalités du SDK.</span><span class="sxs-lookup"><span data-stu-id="0bc25-246">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="0bc25-247">Les plages de fonctionnalités sont définies dans les groupes *hundreds* de la section *patch* du numéro de version.</span><span class="sxs-lookup"><span data-stu-id="0bc25-247">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="0bc25-248">Par exemple, **3.0._101_** et **3.0._201_** sont des versions dans deux plages de fonctionnalités différentes, tandis que **3.0._101_** et **3.0._199_** se trouvent dans la même plages de fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="0bc25-248">For example, **3.0._101_** and **3.0._201_** are versions in two different feature bands while **3.0._101_** and **3.0._199_** are in the same feature band.</span></span> <span data-ttu-id="0bc25-249">En outre, quand le SDK .NET Core **3.0._101_** est installé, le SDK .NET Core **3.0._100_** est supprimé de la machine s’il existe.</span><span class="sxs-lookup"><span data-stu-id="0bc25-249">And, when .NET Core SDK **3.0._101_** is installed, .NET Core SDK **3.0._100_** will be removed from the machine if it exists.</span></span> <span data-ttu-id="0bc25-250">Quand le SDK .NET Core **3.0._200_** est installé sur la même machine, le SDK .NET Core **3.0._101_** n’est pas supprimé.</span><span class="sxs-lookup"><span data-stu-id="0bc25-250">When .NET Core SDK **3.0._200_** is installed on the same machine, .NET Core SDK **3.0._101_** won't be removed.</span></span>

<span data-ttu-id="0bc25-251">Pour plus d’informations sur la gestion des versions, consultez [Vue d’ensemble de la gestion des versions .NET Core](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="0bc25-251">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

### <a name="windows-desktop"></a><span data-ttu-id="0bc25-252">Bureau Windows</span><span class="sxs-lookup"><span data-stu-id="0bc25-252">Windows desktop</span></span>

<span data-ttu-id="0bc25-253">.NET Core 3.0 prend en charge les applications de bureau Windows utilisant Windows Presentation Foundation (WPF) et Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0bc25-253">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="0bc25-254">Ces infrastructures prennent également en charge l’utilisation de contrôles modernes et le style Fluent à partir de la bibliothèque XAML de l’interface utilisateur Windows (WinUI) via des [îles XAML](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="0bc25-254">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="0bc25-255">Le composant Bureau Windows fait partie du SDK .NET Core 3.0 Windows.</span><span class="sxs-lookup"><span data-stu-id="0bc25-255">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="0bc25-256">Vous pouvez créer une nouvelle application WPF ou Windows Forms à l’aide des commandes `dotnet` suivantes :</span><span class="sxs-lookup"><span data-stu-id="0bc25-256">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```dotnetcli
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="0bc25-257">Visual Studio 2019 ajoute des modèles **Nouveau projet** pour Windows Forms et WPF .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="0bc25-257">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="0bc25-258">Pour plus d’informations sur la façon de porter une application .NET Framework existante, consultez [Porter des projets WPF](../../desktop-wpf/migration/convert-project-from-net-framework.md) et [Porter des projets Windows Forms](../porting/winforms.md).</span><span class="sxs-lookup"><span data-stu-id="0bc25-258">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../../desktop-wpf/migration/convert-project-from-net-framework.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

#### <a name="winforms-high-dpi"></a><span data-ttu-id="0bc25-259">Haute résolution WinForms</span><span class="sxs-lookup"><span data-stu-id="0bc25-259">WinForms high DPI</span></span>

<span data-ttu-id="0bc25-260">Les applications Windows Forms .NET Core peuvent définir le mode de haute résolution avec <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0bc25-260">.NET Core Windows Forms applications can set high DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0bc25-261">La méthode `SetHighDpiMode` définit le mode de haute résolution correspondant, sauf si le paramètre a été défini par d’autres moyens, comme `App.Manifest` ou P/Invoke avant `Application.Run`.</span><span class="sxs-lookup"><span data-stu-id="0bc25-261">The `SetHighDpiMode` method sets the corresponding high DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="0bc25-262">Les valeurs `highDpiMode` possibles, telles qu’exprimées par l’enum <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType>, sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0bc25-262">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

<span data-ttu-id="0bc25-263">Pour plus d’informations sur les modes de haute résolution, consultez [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) (Développement d’applications de bureau haute résolution sur Windows).</span><span class="sxs-lookup"><span data-stu-id="0bc25-263">For more information about high DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

### <a name="create-com-components"></a><span data-ttu-id="0bc25-264">Créer des composants COM</span><span class="sxs-lookup"><span data-stu-id="0bc25-264">Create COM components</span></span>

<span data-ttu-id="0bc25-265">Sur Windows, vous pouvez maintenant créer des composants gérés appelables par COM.</span><span class="sxs-lookup"><span data-stu-id="0bc25-265">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="0bc25-266">Cette fonctionnalité est essentielle pour utiliser .NET Core avec les modèles de compléments COM et également pour assurer la parité avec .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0bc25-266">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="0bc25-267">Contrairement à .NET Framework, où *mscoree.dll* était utilisé comme serveur COM, .NET Core ajoute une dll de lanceur natif au répertoire *bin* quand vous générez votre composant COM.</span><span class="sxs-lookup"><span data-stu-id="0bc25-267">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="0bc25-268">Pour obtenir un exemple montrant comment créer un composant COM et le consommer, consultez la [démonstration COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span><span class="sxs-lookup"><span data-stu-id="0bc25-268">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="0bc25-269">Interopérabilité native Windows</span><span class="sxs-lookup"><span data-stu-id="0bc25-269">Windows Native Interop</span></span>

<span data-ttu-id="0bc25-270">Windows offre une API native riche sous la forme d’API C plates, de COM et de WinRT.</span><span class="sxs-lookup"><span data-stu-id="0bc25-270">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="0bc25-271">Tandis que .NET Core prend en charge **P/Invoke**, .NET Core 3.0 ajoute la possibilité de **cocréer des API COM** et d’**activer des API WinRT**.</span><span class="sxs-lookup"><span data-stu-id="0bc25-271">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="0bc25-272">Pour obtenir un exemple de code, consultez la [démonstration Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="0bc25-272">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

### <a name="msix-deployment"></a><span data-ttu-id="0bc25-273">Déploiement de MSIX</span><span class="sxs-lookup"><span data-stu-id="0bc25-273">MSIX Deployment</span></span>

<span data-ttu-id="0bc25-274">[MSIX](https://docs.microsoft.com/windows/msix/) est un nouveau format de package d’application Windows.</span><span class="sxs-lookup"><span data-stu-id="0bc25-274">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="0bc25-275">Il peut être utilisé pour déployer des applications de poste de travail .NET Core 3.0 pour Windows 10.</span><span class="sxs-lookup"><span data-stu-id="0bc25-275">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="0bc25-276">Le [projet de package d’application Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), disponible dans Visual Studio 2019, vous permet de créer des packages MSIX avec des applications .NET Core [autonomes](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="0bc25-276">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#self-contained-deployments-scd) .NET Core applications.</span></span>

<span data-ttu-id="0bc25-277">Le fichier projet .NET Core doit spécifier les runtimes pris en charge dans la propriété `<RuntimeIdentifiers>` :</span><span class="sxs-lookup"><span data-stu-id="0bc25-277">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="linux-improvements"></a><span data-ttu-id="0bc25-278">Améliorations de Linux</span><span class="sxs-lookup"><span data-stu-id="0bc25-278">Linux improvements</span></span>

### <a name="serialport-for-linux"></a><span data-ttu-id="0bc25-279">SerialPort pour Linux</span><span class="sxs-lookup"><span data-stu-id="0bc25-279">SerialPort for Linux</span></span>

<span data-ttu-id="0bc25-280">.NET Core 3.0 offre une prise en charge de base de <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> sur Linux.</span><span class="sxs-lookup"><span data-stu-id="0bc25-280">.NET Core 3.0 provides basic support for <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="0bc25-281">Auparavant, .NET Core était uniquement pris en charge au moyen de `SerialPort` sur Windows.</span><span class="sxs-lookup"><span data-stu-id="0bc25-281">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

<span data-ttu-id="0bc25-282">Pour plus d’informations sur la prise en charge limitée du port série sur Linux, consultez [GitHub issue #33146](https://github.com/dotnet/corefx/issues/33146).</span><span class="sxs-lookup"><span data-stu-id="0bc25-282">For more information about the limited support for the serial port on Linux, see [GitHub issue #33146](https://github.com/dotnet/corefx/issues/33146).</span></span>

### <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="0bc25-283">Docker et limites de mémoire cgroup</span><span class="sxs-lookup"><span data-stu-id="0bc25-283">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="0bc25-284">L’exécution de .NET Core 3,0 sur Linux avec l’arrimeur fonctionne mieux avec les limites de mémoire cgroup.</span><span class="sxs-lookup"><span data-stu-id="0bc25-284">Running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="0bc25-285">L’exécution d’un conteneur Docker avec des limites de mémoire, par exemple avec `docker run -m`, change le comportement de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0bc25-285">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

- <span data-ttu-id="0bc25-286">Taille de tas par défaut du récupérateur de mémoire (GC) : au maximum 20 Mo ou 75 % de la limite de mémoire sur le conteneur.</span><span class="sxs-lookup"><span data-stu-id="0bc25-286">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
- <span data-ttu-id="0bc25-287">Une taille explicite peut être définie sous forme de nombre absolu ou de pourcentage de la limite cgroup.</span><span class="sxs-lookup"><span data-stu-id="0bc25-287">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
- <span data-ttu-id="0bc25-288">La taille de segment réservée minimale par tas GC est de 16 Mo.</span><span class="sxs-lookup"><span data-stu-id="0bc25-288">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="0bc25-289">Cette taille réduit le nombre de segments de mémoire qui sont créés sur les machines.</span><span class="sxs-lookup"><span data-stu-id="0bc25-289">This size reduces the number of heaps that are created on machines.</span></span>

### <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="0bc25-290">Prise en charge de GPIO pour Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="0bc25-290">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="0bc25-291">Deux packages ont été publiés sur NuGet, que vous pouvez utiliser pour la programmation de GPIO :</span><span class="sxs-lookup"><span data-stu-id="0bc25-291">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

- [<span data-ttu-id="0bc25-292">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="0bc25-292">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
- [<span data-ttu-id="0bc25-293">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="0bc25-293">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="0bc25-294">Les packages GPIO incluent des API pour les appareils *GPIO*, *SPI*, *I2C* et *PWM*.</span><span class="sxs-lookup"><span data-stu-id="0bc25-294">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="0bc25-295">Le package de liaisons IoT comprend des liaisons d’appareil.</span><span class="sxs-lookup"><span data-stu-id="0bc25-295">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="0bc25-296">Pour plus d’informations, consultez le [dépôt GitHub devices](https://github.com/dotnet/iot/blob/master/src/devices/).</span><span class="sxs-lookup"><span data-stu-id="0bc25-296">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

### <a name="arm64-linux-support"></a><span data-ttu-id="0bc25-297">Support ARM64 Linux</span><span class="sxs-lookup"><span data-stu-id="0bc25-297">ARM64 Linux support</span></span>

<span data-ttu-id="0bc25-298">.NET Core 3.0 prend en charge ARM64 pour Linux.</span><span class="sxs-lookup"><span data-stu-id="0bc25-298">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="0bc25-299">Actuellement, ARM64 est principallement utilisé dans des scénarios IoT.</span><span class="sxs-lookup"><span data-stu-id="0bc25-299">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="0bc25-300">Pour plus d’informations, consultez [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span><span class="sxs-lookup"><span data-stu-id="0bc25-300">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="0bc25-301">Des [images Docker pour .NET Core sur ARM64](https://hub.docker.com/r/microsoft/dotnet/) sont disponibles pour Alpine, Debian et Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="0bc25-301">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="0bc25-302">La prise en charge d’**ARM64** sous Windows n’est pas encore disponible.</span><span class="sxs-lookup"><span data-stu-id="0bc25-302">**ARM64** Windows support isn't yet available.</span></span>

## <a name="security"></a><span data-ttu-id="0bc25-303">Sécurité</span><span class="sxs-lookup"><span data-stu-id="0bc25-303">Security</span></span>

### <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="0bc25-304">TLS 1.3 et OpenSSL 1.1.1 sous Linux</span><span class="sxs-lookup"><span data-stu-id="0bc25-304">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="0bc25-305">.NET Core tire désormais parti de la [prise en charge de TLS 1.3 dans OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), si disponible dans un environnement donné.</span><span class="sxs-lookup"><span data-stu-id="0bc25-305">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="0bc25-306">Avec TLS 1.3 :</span><span class="sxs-lookup"><span data-stu-id="0bc25-306">With TLS 1.3:</span></span>

- <span data-ttu-id="0bc25-307">Les délais de connexion sont améliorés grâce à une réduction des allers-retours requis entre le client et le serveur.</span><span class="sxs-lookup"><span data-stu-id="0bc25-307">Connection times are improved with reduced round trips required between the client and server.</span></span>
- <span data-ttu-id="0bc25-308">La sécurité est améliorée en raison de la suppression de différents algorithmes de chiffrement obsolètes et non sécurisés.</span><span class="sxs-lookup"><span data-stu-id="0bc25-308">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="0bc25-309">.NET Core 3.0 utilise **OpenSSL 1.1.1**, **OpenSSL 1.1.0** ou **OpenSSL 1.0.2** sur un système Linux s’ils sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="0bc25-309">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="0bc25-310">Quand **OpenSSL 1.1.1** est disponible, les types <xref:System.Net.Security.SslStream?displayProperty=nameWithType> et <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> utilisent **TLS 1.3** (sous réserve que le client et le serveur prennent en charge **TLS 1.3**).</span><span class="sxs-lookup"><span data-stu-id="0bc25-310">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

>[!IMPORTANT]
><span data-ttu-id="0bc25-311">Windows et macOS ne prennent pas encore en charge **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="0bc25-311">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="0bc25-312">.NET Core 3.0 prendra en charge **TLS 1.3** sur ces systèmes d’exploitation dès que de la prise en charge sera disponible.</span><span class="sxs-lookup"><span data-stu-id="0bc25-312">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="0bc25-313">L’exemple C# 8.0 suivant montre comment .NET Core 3.0 sur Ubuntu 18.10 se connecte à <https://www.cloudflare.com> :</span><span class="sxs-lookup"><span data-stu-id="0bc25-313">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

### <a name="cryptography-ciphers"></a><span data-ttu-id="0bc25-314">Chiffrements</span><span class="sxs-lookup"><span data-stu-id="0bc25-314">Cryptography ciphers</span></span>

<span data-ttu-id="0bc25-315">.NET 3.0 prend en charge les chiffrements **AES-GCM** et **AES-CCM**, implémentés avec <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> et <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectivement.</span><span class="sxs-lookup"><span data-stu-id="0bc25-315">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="0bc25-316">Ces algorithmes sont tous deux des [algorithmes AEAD (Authenticated Encryption with Association Data)](https://en.wikipedia.org/wiki/Authenticated_encryption).</span><span class="sxs-lookup"><span data-stu-id="0bc25-316">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="0bc25-317">Le code suivant montre l’utilisation du chiffrement `AesGcm` pour chiffrer et déchiffrer des données aléatoires.</span><span class="sxs-lookup"><span data-stu-id="0bc25-317">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

### <a name="cryptographic-key-importexport"></a><span data-ttu-id="0bc25-318">Importation/exportation d’une clé de chiffrement</span><span class="sxs-lookup"><span data-stu-id="0bc25-318">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="0bc25-319">.NET Core 3.0 prend en charge l’importation et l’exportation de clés publiques et privées asymétriques aux formats standard.</span><span class="sxs-lookup"><span data-stu-id="0bc25-319">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="0bc25-320">Vous n’avez pas besoin d’utiliser un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="0bc25-320">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="0bc25-321">Tous les types de clés, tels que *RSA*, *DSA*, *ECDsa* et *ECDiffieHellman*, prennent en charge les formats suivants :</span><span class="sxs-lookup"><span data-stu-id="0bc25-321">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

- <span data-ttu-id="0bc25-322">**Clé publique**</span><span class="sxs-lookup"><span data-stu-id="0bc25-322">**Public Key**</span></span>
  - <span data-ttu-id="0bc25-323">X.509 SubjectPublicKeyInfo</span><span class="sxs-lookup"><span data-stu-id="0bc25-323">X.509 SubjectPublicKeyInfo</span></span>

- <span data-ttu-id="0bc25-324">**Clé privée**</span><span class="sxs-lookup"><span data-stu-id="0bc25-324">**Private key**</span></span>
  - <span data-ttu-id="0bc25-325">PKCS#8 PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="0bc25-325">PKCS#8 PrivateKeyInfo</span></span>
  - <span data-ttu-id="0bc25-326">PKCS#8 EncryptedPrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="0bc25-326">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="0bc25-327">Les clés RSA prennent également en charge :</span><span class="sxs-lookup"><span data-stu-id="0bc25-327">RSA keys also support:</span></span>

- <span data-ttu-id="0bc25-328">**Clé publique**</span><span class="sxs-lookup"><span data-stu-id="0bc25-328">**Public Key**</span></span>
  - <span data-ttu-id="0bc25-329">PKCS#1 RSAPublicKey</span><span class="sxs-lookup"><span data-stu-id="0bc25-329">PKCS#1 RSAPublicKey</span></span>

- <span data-ttu-id="0bc25-330">**Clé privée**</span><span class="sxs-lookup"><span data-stu-id="0bc25-330">**Private key**</span></span>
  - <span data-ttu-id="0bc25-331">PKCS#1 RSAPrivateKey</span><span class="sxs-lookup"><span data-stu-id="0bc25-331">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="0bc25-332">Les méthodes d’exportation produisent des données binaires encodées au format DER, tout comme les méthodes d’importation.</span><span class="sxs-lookup"><span data-stu-id="0bc25-332">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="0bc25-333">Si une clé est stockée au format PEM compatible avec le texte, l’appelant devra décoder le contenu au format base64 avant d’appeler une méthode d’importation.</span><span class="sxs-lookup"><span data-stu-id="0bc25-333">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

<span data-ttu-id="0bc25-334">Les fichiers **PKCS#8** peuvent être inspectés avec <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType>, tandis que les fichiers **PFX/PKCS#12** peuvent être inspectés avec <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0bc25-334">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0bc25-335">Les fichiers **PFX/PKCS#12** peuvent être manipulés avec <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0bc25-335">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="net-core-30-api-changes"></a><span data-ttu-id="0bc25-336">Modifications de l’API .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="0bc25-336">.NET Core 3.0 API changes</span></span>

### <a name="ranges-and-indices"></a><span data-ttu-id="0bc25-337">Plages et index</span><span class="sxs-lookup"><span data-stu-id="0bc25-337">Ranges and indices</span></span>

<span data-ttu-id="0bc25-338">Le nouveau type <xref:System.Index?displayProperty=nameWithType> peut être utilisé pour l’indexation.</span><span class="sxs-lookup"><span data-stu-id="0bc25-338">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="0bc25-339">Vous pouvez en créer un à partir d’un `int` qui compte à partir du début, ou avec un opérateur (C#) `^` préfixé qui compte à partir de la fin :</span><span class="sxs-lookup"><span data-stu-id="0bc25-339">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="0bc25-340">Il existe également le type <xref:System.Range?displayProperty=nameWithType>, composé de deux valeurs `Index`, une pour le début et une pour la fin, et qui peut être écrit avec une expression de plage (C#) `x..y`.</span><span class="sxs-lookup"><span data-stu-id="0bc25-340">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="0bc25-341">Vous pouvez indexer ensuite avec un `Range`, ce qui génère une tranche :</span><span class="sxs-lookup"><span data-stu-id="0bc25-341">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="0bc25-342">Pour plus d’informations, consultez le [tutoriel sur les plages et les index](../../csharp/tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="0bc25-342">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

### <a name="async-streams"></a><span data-ttu-id="0bc25-343">Flux asynchrones</span><span class="sxs-lookup"><span data-stu-id="0bc25-343">Async streams</span></span>

<span data-ttu-id="0bc25-344">Le type <xref:System.Collections.Generic.IAsyncEnumerable%601> est une nouvelle version asynchrone de <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="0bc25-344">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="0bc25-345">Le langage vous permet d’utiliser `await foreach` sur `IAsyncEnumerable<T>` pour consommer ses éléments, et `yield return` sur ceux-ci pour produire des éléments.</span><span class="sxs-lookup"><span data-stu-id="0bc25-345">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="0bc25-346">L’exemple suivant montre la production et la consommation de flux de données asynchrones.</span><span class="sxs-lookup"><span data-stu-id="0bc25-346">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="0bc25-347">L’instruction `foreach` est asynchrone et utilise elle-même `yield return` afin de produire un flux asynchrone pour les appelants.</span><span class="sxs-lookup"><span data-stu-id="0bc25-347">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="0bc25-348">Ce modèle (qui utilise `yield return`) est le modèle recommandé pour produire des flux de données asynchrones.</span><span class="sxs-lookup"><span data-stu-id="0bc25-348">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

<span data-ttu-id="0bc25-349">Outre la possibilité d’effectuer une opération `await foreach`, vous pouvez également créer des itérateurs asynchrones, par exemple un itérateur qui retourne un objet `IAsyncEnumerable/IAsyncEnumerator` auquel vous pouvez à la fois appliquer des opérations `await` et `yield`.</span><span class="sxs-lookup"><span data-stu-id="0bc25-349">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="0bc25-350">Pour les objets qui doivent être supprimés, vous pouvez utiliser `IAsyncDisposable`, qui implémentent différents types BCL, notamment `Stream` et `Timer`.</span><span class="sxs-lookup"><span data-stu-id="0bc25-350">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="0bc25-351">Pour plus d’informations, consultez le [tutoriel sur les flux asynchrones](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="0bc25-351">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

### <a name="ieee-floating-point"></a><span data-ttu-id="0bc25-352">Virgule flottante IEEE</span><span class="sxs-lookup"><span data-stu-id="0bc25-352">IEEE Floating-point</span></span>

<span data-ttu-id="0bc25-353">Les API de virgule flottante sont en cours de mise à jour pour devenir conformes à la [révision 754-2008 d’IEEE](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span><span class="sxs-lookup"><span data-stu-id="0bc25-353">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="0bc25-354">L’objectif de ces modifications est d’exposer toutes les opérations **requises** et de s’assurer qu’elles sont conformes au comportement des spécifications IEEE. Pour plus d’informations sur les améliorations de la virgule flottante, consultez le billet [de blog améliorations de la mise en forme et de l’analyse de la virgule flottante dans .net Core 3,0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .</span><span class="sxs-lookup"><span data-stu-id="0bc25-354">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="0bc25-355">Les correctifs de l’analyse et de la mise en forme comprennent :</span><span class="sxs-lookup"><span data-stu-id="0bc25-355">Parsing and formatting fixes include:</span></span>

- <span data-ttu-id="0bc25-356">Analyse et arrondi corrects des entrées, quelle que soit leur longueur.</span><span class="sxs-lookup"><span data-stu-id="0bc25-356">Correctly parse and round inputs of any length.</span></span>
- <span data-ttu-id="0bc25-357">Analyse et mise en forme correctes des zéros négatifs.</span><span class="sxs-lookup"><span data-stu-id="0bc25-357">Correctly parse and format negative zero.</span></span>
- <span data-ttu-id="0bc25-358">Analyse correcte de `Infinity` et `NaN` en effectuant une vérification sans tenir compte de la casse et en autorisant un signe `+` facultatif de début là où c’est applicable.</span><span class="sxs-lookup"><span data-stu-id="0bc25-358">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="0bc25-359">Les nouvelles API <xref:System.Math?displayProperty=nameWithType> incluent :</span><span class="sxs-lookup"><span data-stu-id="0bc25-359">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

- <span data-ttu-id="0bc25-360"><xref:System.Math.BitIncrement(System.Double)> et <xref:System.Math.BitDecrement(System.Double)></span><span class="sxs-lookup"><span data-stu-id="0bc25-360"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)></span></span>\
<span data-ttu-id="0bc25-361">Correspond aux opérations IEEE `nextUp` et `nextDown`.</span><span class="sxs-lookup"><span data-stu-id="0bc25-361">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="0bc25-362">Elles retournent le plus petit nombre à virgule flottante dont la valeur est supérieure ou inférieure à l’entrée (respectivement).</span><span class="sxs-lookup"><span data-stu-id="0bc25-362">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="0bc25-363">Par exemple, `Math.BitIncrement(0.0)` retourne `double.Epsilon`.</span><span class="sxs-lookup"><span data-stu-id="0bc25-363">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

- <span data-ttu-id="0bc25-364"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> et <xref:System.Math.MinMagnitude(System.Double,System.Double)></span><span class="sxs-lookup"><span data-stu-id="0bc25-364"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)></span></span>\
<span data-ttu-id="0bc25-365">Correspond aux opérations IEEE `maxNumMag` et `minNumMag`. Elles retournent la valeur la plus grande ou la plus petite des deux entrées (respectivement).</span><span class="sxs-lookup"><span data-stu-id="0bc25-365">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="0bc25-366">Par exemple, `Math.MaxMagnitude(2.0, -3.0)` retourne `-3.0`.</span><span class="sxs-lookup"><span data-stu-id="0bc25-366">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

- <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="0bc25-367">Correspond à l’opération IEEE `logB` qui retourne une valeur intégrale ; elle retourne le logarithme de base 2 intégral du paramètre d’entrée.</span><span class="sxs-lookup"><span data-stu-id="0bc25-367">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="0bc25-368">Cette méthode est identique à `floor(log2(x))`, mais effectuée avec une erreur d’arrondi minimale.</span><span class="sxs-lookup"><span data-stu-id="0bc25-368">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="0bc25-369">Correspond à l’opération IEEE `scaleB` qui prend une valeur intégrale ; elle retourne `x * pow(2, n)`, mais est effectuée avec une erreur d’arrondi minimale.</span><span class="sxs-lookup"><span data-stu-id="0bc25-369">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

- <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="0bc25-370">Correspond à l’opération IEEE `log2` ; elle retourne le logarithme de base 2.</span><span class="sxs-lookup"><span data-stu-id="0bc25-370">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="0bc25-371">Son erreur d’arrondi est minimale.</span><span class="sxs-lookup"><span data-stu-id="0bc25-371">It minimizes rounding error.</span></span>

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="0bc25-372">Correspond à l’opération IEEE `fma` ; elle effectue une multiplication-addition fusionnée.</span><span class="sxs-lookup"><span data-stu-id="0bc25-372">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="0bc25-373">Elle effectue `(x * y) + z` comme une seule opération, avec une erreur d’arrondi minimale.</span><span class="sxs-lookup"><span data-stu-id="0bc25-373">That is, it does `(x * y) + z` as a single operation, thereby minimizing the rounding error.</span></span> <span data-ttu-id="0bc25-374">Par exemple, `FusedMultiplyAdd(1e308, 2.0, -1e308)` retourne `1e308`.</span><span class="sxs-lookup"><span data-stu-id="0bc25-374">An example would be `FusedMultiplyAdd(1e308, 2.0, -1e308)` which returns `1e308`.</span></span> <span data-ttu-id="0bc25-375">L’opération régulière `(1e308 * 2.0) - 1e308` retourne `double.PositiveInfinity`.</span><span class="sxs-lookup"><span data-stu-id="0bc25-375">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

- <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="0bc25-376">Correspond à l’opération IEEE `copySign` ; elle retourne la valeur de `x`, mais avec le signe de `y`.</span><span class="sxs-lookup"><span data-stu-id="0bc25-376">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

### <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="0bc25-377">Intrinsèques dépendant de la plateforme .NET</span><span class="sxs-lookup"><span data-stu-id="0bc25-377">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="0bc25-378">Des API ont été ajoutées, qui permettent d’accéder à certaines instructions de l’UC orientées performances, comme les ensembles **SIMD** ou les ensembles d’**instructions de manipulation de bits**.</span><span class="sxs-lookup"><span data-stu-id="0bc25-378">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="0bc25-379">Ces instructions peuvent améliorer les performances dans certains scénarios de matière significative, comme le traitement efficace de données en parallèle.</span><span class="sxs-lookup"><span data-stu-id="0bc25-379">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span>

<span data-ttu-id="0bc25-380">Le cas échéant, les bibliothèques .NET ont commencé à utiliser ces instructions pour améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="0bc25-380">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="0bc25-381">Pour plus d’informations, consultez [Intrinsèques dépendant de la plateforme .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span><span class="sxs-lookup"><span data-stu-id="0bc25-381">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span></span>

### <a name="improved-net-core-version-apis"></a><span data-ttu-id="0bc25-382">API de version de .NET Core améliorées</span><span class="sxs-lookup"><span data-stu-id="0bc25-382">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="0bc25-383">À compter de .NET Core 3.0, les API de version fournies avec .NET Core retournent les informations souhaitées.</span><span class="sxs-lookup"><span data-stu-id="0bc25-383">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="0bc25-384">Exemple :</span><span class="sxs-lookup"><span data-stu-id="0bc25-384">For example:</span></span>

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
// New result (notice the value includes any preview release information)
//   RuntimeInformation.FrameworkDescription: .NET Core 3.0.0-preview4-27615-11
```

> [!WARNING]
> <span data-ttu-id="0bc25-385">Modification avec rupture.</span><span class="sxs-lookup"><span data-stu-id="0bc25-385">Breaking change.</span></span> <span data-ttu-id="0bc25-386">Il s’agit techniquement d’une modification avec rupture, car le schéma de gestion de version a changé.</span><span class="sxs-lookup"><span data-stu-id="0bc25-386">This is technically a breaking change because the versioning scheme has changed.</span></span>

### <a name="fast-built-in-json-support"></a><span data-ttu-id="0bc25-387">Prise en charge JSON intégrée rapide</span><span class="sxs-lookup"><span data-stu-id="0bc25-387">Fast built-in JSON support</span></span>

<span data-ttu-id="0bc25-388">Les utilisateurs de .NET se sont largement appuyés sur [**Json.NET**](https://www.newtonsoft.com/json) et d’autres bibliothèques JSON populaires, qui restent de bons choix.</span><span class="sxs-lookup"><span data-stu-id="0bc25-388">.NET users have largely relied on [**Json.NET**](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="0bc25-389">**Json.NET** utilise des chaînes .NET comme type de données de base, au format UTF-16.</span><span class="sxs-lookup"><span data-stu-id="0bc25-389">**Json.NET** uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="0bc25-390">La nouvelle prise en charge JSON intégrée offre des hautes performances et une allocation faible, et elle est basée sur `Span<byte>`.</span><span class="sxs-lookup"><span data-stu-id="0bc25-390">The new built-in JSON support is high-performance, low allocation, and based on `Span<byte>`.</span></span> <span data-ttu-id="0bc25-391">Pour plus d’informations sur l’espace de noms et les types <xref:System.Text.Json>, consultez [sérialisation JSON dans .net-vue d’ensemble](../../standard/serialization/system-text-json-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0bc25-391">For more information about the <xref:System.Text.Json> namespace and types, see [JSON serialization in .NET - overview](../../standard/serialization/system-text-json-overview.md).</span></span> <span data-ttu-id="0bc25-392">Pour obtenir des didacticiels sur les scénarios de sérialisation JSON courants, consultez [sérialisation et désérialisation de JSON dans .net](../../standard/serialization/system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="0bc25-392">For tutorials on common JSON serialization scenarios, see [How to serialize and deserialize JSON in .NET](../../standard/serialization/system-text-json-how-to.md).</span></span>

### <a name="http2-support"></a><span data-ttu-id="0bc25-393">Prise en charge de HTTP/2</span><span class="sxs-lookup"><span data-stu-id="0bc25-393">HTTP/2 support</span></span>

<span data-ttu-id="0bc25-394">Le type <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> prend en charge le protocole HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="0bc25-394">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="0bc25-395">Si HTTP/2 est activé, la version du protocole HTTP est négociée par le biais de TLS/ALPN, et HTTP/2 n’est utilisée que si le serveur le choisit.</span><span class="sxs-lookup"><span data-stu-id="0bc25-395">If HTTP/2 is enabled, the HTTP protocol version is negotiated via TLS/ALPN, and HTTP/2 is used if the server elects to use it.</span></span>

<span data-ttu-id="0bc25-396">Le protocole par défaut reste HTTP/1.1, mais HTTP/2 peut être activé de deux manières différentes.</span><span class="sxs-lookup"><span data-stu-id="0bc25-396">The default protocol remains HTTP/1.1, but HTTP/2 can be enabled in two different ways.</span></span> <span data-ttu-id="0bc25-397">Tout d’abord, vous pouvez définir le message de requête HTTP de sorte à utiliser HTTP/2 :</span><span class="sxs-lookup"><span data-stu-id="0bc25-397">First, you can set the HTTP request message to use HTTP/2:</span></span>

[!CODE-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

<span data-ttu-id="0bc25-398">Ensuite, vous pouvez modifier <xref:System.Net.Http.HttpClient> pour utiliser HTTP/2 par défaut :</span><span class="sxs-lookup"><span data-stu-id="0bc25-398">Second, you can change <xref:System.Net.Http.HttpClient> to use HTTP/2 by default:</span></span>

[!CODE-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

<span data-ttu-id="0bc25-399">Souvent, lorsque vous développez une application, vous souhaiterez utiliser une connexion non chiffrée.</span><span class="sxs-lookup"><span data-stu-id="0bc25-399">Many times when you're developing an application, you want to use an unencrypted connection.</span></span> <span data-ttu-id="0bc25-400">Si vous savez que le point de terminaison cible utilisera HTTP/2, vous pouvez activer les connexions non chiffrées pour HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="0bc25-400">If you know the target endpoint will be using HTTP/2, you can turn on unencrypted connections for HTTP/2.</span></span> <span data-ttu-id="0bc25-401">Vous pouvez activer cela en définissant la variable d’environnement `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` sur `1` ou en l’activant dans le contexte de l’application :</span><span class="sxs-lookup"><span data-stu-id="0bc25-401">You can turn it on by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` environment variable to `1` or by enabling it in the app context:</span></span>

[!CODE-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="next-steps"></a><span data-ttu-id="0bc25-402">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="0bc25-402">Next steps</span></span>

- [<span data-ttu-id="0bc25-403">Passez en revue les modifications avec rupture entre .NET Core 2,2 et 3,0.</span><span class="sxs-lookup"><span data-stu-id="0bc25-403">Review the breaking changes between .NET Core 2.2 and 3.0.</span></span>](../compatibility/2.2-3.0.md)
- [<span data-ttu-id="0bc25-404">Passez en revue les modifications avec rupture entre .NET Framework et .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="0bc25-404">Review the breaking changes between .NET Framework and .NET Core 3.0.</span></span>](../compatibility/framework-core.md)
