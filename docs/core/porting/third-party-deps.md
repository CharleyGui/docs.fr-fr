---
title: Analyser les dépendances pour porter le code sur .NET Core
description: Découvrez comment analyser les dépendances externes afin de porter votre projet de .NET Framework sur .NET Core.
author: cartermp
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 36d1c1d2090a0fb9e6f48fe519d15897579df2d5
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72521473"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a><span data-ttu-id="f06e7-103">Analyser vos dépendances pour porter le code sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="f06e7-103">Analyze your dependencies to port code to .NET Core</span></span>

<span data-ttu-id="f06e7-104">Pour porter votre code sur .NET Core ou .NET Standard, vous devez comprendre vos dépendances.</span><span class="sxs-lookup"><span data-stu-id="f06e7-104">To port your code to .NET Core or .NET Standard, you must understand your dependencies.</span></span> <span data-ttu-id="f06e7-105">Les dépendances externes sont les [packages NuGet](#analyze-referenced-nuget-packages-in-your-projects) ou les [DLL](#analyze-dependencies-that-arent-nuget-packages) que vous référencez dans votre projet, mais que vous ne générez pas.</span><span class="sxs-lookup"><span data-stu-id="f06e7-105">External dependencies are the [NuGet packages](#analyze-referenced-nuget-packages-in-your-projects) or [DLLs](#analyze-dependencies-that-arent-nuget-packages) you reference in your project, but that you don't build.</span></span> <span data-ttu-id="f06e7-106">Évaluez chaque dépendance et développez un plan d’urgence pour les dépendances qui ne sont pas compatibles avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f06e7-106">Evaluate each dependency and develop a contingency plan for the ones that aren't compatible with .NET Core.</span></span> <span data-ttu-id="f06e7-107">Voici comment déterminer si une dépendance est compatible avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f06e7-107">Here's how to determine if a dependency is compatible with .NET Core.</span></span>

## <a name="analyze-referenced-nuget-packages-in-your-projects"></a><span data-ttu-id="f06e7-108">Analyser les packages NuGet référencés dans vos projets</span><span class="sxs-lookup"><span data-stu-id="f06e7-108">Analyze referenced NuGet packages in your projects</span></span>

<span data-ttu-id="f06e7-109">Si vous référencez des packages NuGet dans votre projet, vous devez vérifier s’ils sont compatibles avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f06e7-109">If you reference NuGet packages in your project, you need to verify if they're compatible with .NET Core.</span></span>
<span data-ttu-id="f06e7-110">Pour cela, vous avez le choix entre :</span><span class="sxs-lookup"><span data-stu-id="f06e7-110">There are two ways to accomplish that:</span></span>

- [<span data-ttu-id="f06e7-111">Utilisation de l’application NuGet Package Explorer</span><span class="sxs-lookup"><span data-stu-id="f06e7-111">Using the NuGet Package Explorer app</span></span>](#analyze-nuget-packages-using-nuget-package-explorer)
- [<span data-ttu-id="f06e7-112">Utiliser le site nuget.org</span><span class="sxs-lookup"><span data-stu-id="f06e7-112">Using the nuget.org site</span></span>](#analyze-nuget-packages-using-nugetorg)

<span data-ttu-id="f06e7-113">Après avoir analysé les packages, s’il s’avère qu’ils ne sont pas compatibles avec .NET Core et ne ciblent que le .NET Framework, vous pouvez vérifier si le [mode de compatibilité du .NET Framework](#net-framework-compatibility-mode) peut vous être utile pour le processus de portage.</span><span class="sxs-lookup"><span data-stu-id="f06e7-113">After analyzing the packages, if they're not compatible with .NET Core and only target .NET Framework, you can check if the [.NET Framework compatibility mode](#net-framework-compatibility-mode) can help with your porting process.</span></span>

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a><span data-ttu-id="f06e7-114">Analyser les packages NuGet à l’aide de NuGet Package Explorer</span><span class="sxs-lookup"><span data-stu-id="f06e7-114">Analyze NuGet packages using NuGet Package Explorer</span></span>

<span data-ttu-id="f06e7-115">Un package NuGet est lui-même un ensemble de dossiers qui contiennent des assemblys spécifiques aux plateformes.</span><span class="sxs-lookup"><span data-stu-id="f06e7-115">A NuGet package is itself a set of folders that contain platform-specific assemblies.</span></span> <span data-ttu-id="f06e7-116">Vous devez donc vérifier s’il existe dans le package un dossier qui contient un assembly compatible.</span><span class="sxs-lookup"><span data-stu-id="f06e7-116">So you need to check if there's a folder that contains a compatible assembly inside the package.</span></span>

<span data-ttu-id="f06e7-117">La méthode la plus facile pour inspecter les dossiers NuGet consiste à utiliser l’outil [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer).</span><span class="sxs-lookup"><span data-stu-id="f06e7-117">The easiest way to inspect NuGet Package folders is to use the [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) tool.</span></span> <span data-ttu-id="f06e7-118">Après l’avoir installé, effectuez les étapes suivantes pour afficher les noms de dossiers :</span><span class="sxs-lookup"><span data-stu-id="f06e7-118">After installing it, use the following steps to see the folder names:</span></span>

1. <span data-ttu-id="f06e7-119">Ouvrez NuGet Package Explorer.</span><span class="sxs-lookup"><span data-stu-id="f06e7-119">Open the NuGet Package Explorer.</span></span>
2. <span data-ttu-id="f06e7-120">Cliquez sur **Open package from online feed**.</span><span class="sxs-lookup"><span data-stu-id="f06e7-120">Click **Open package from online feed**.</span></span>
3. <span data-ttu-id="f06e7-121">Recherchez le nom du package.</span><span class="sxs-lookup"><span data-stu-id="f06e7-121">Search for the name of the package.</span></span>
4. <span data-ttu-id="f06e7-122">Sélectionnez le nom du package dans les résultats de la recherche et cliquez sur **Open**.</span><span class="sxs-lookup"><span data-stu-id="f06e7-122">Select the package name from the search results and click **open**.</span></span>
5. <span data-ttu-id="f06e7-123">Développez le dossier *lib* qui se trouve sur la droite et examinez les noms de dossiers.</span><span class="sxs-lookup"><span data-stu-id="f06e7-123">Expand the *lib* folder on the right-hand side and look at folder names.</span></span>

<span data-ttu-id="f06e7-124">Recherchez un dossier portant l’un des noms suivants :</span><span class="sxs-lookup"><span data-stu-id="f06e7-124">Look for a folder with any of the following names:</span></span>

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netstandard2.0
netcoreapp1.0
netcoreapp1.1
netcoreapp2.0
netcoreapp2.1
netcoreapp2.2
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

<span data-ttu-id="f06e7-125">Ces valeurs sont les [monikers de framework cible (TFM, Target Framework Monikers)](../../standard/frameworks.md) qui correspondent aux versions des profils de bibliothèques de classes portables [.NET Standard](../../standard/net-standard.md), .NET Core et traditionnels qui sont compatibles avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f06e7-125">These values are the [Target Framework Monikers (TFMs)](../../standard/frameworks.md) that map to versions of the [.NET Standard](../../standard/net-standard.md), .NET Core, and traditional Portable Class Library (PCL) profiles that are compatible with .NET Core.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f06e7-126">Lorsque vous observez les TFM pris en charge par un package, notez que `netcoreapp*`, bien que compatible, ne s’applique qu’aux projets .NET Core, pas aux projets .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="f06e7-126">When looking at the TFMs that a package supports, note that `netcoreapp*`, while compatible, is for .NET Core projects only and not for .NET Standard projects.</span></span>
> <span data-ttu-id="f06e7-127">Une bibliothèque qui cible uniquement `netcoreapp*` et pas `netstandard*` ne peut être consommée que par d’autres applications .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f06e7-127">A library that only targets `netcoreapp*` and not `netstandard*` can only be consumed by other .NET Core apps.</span></span>

### <a name="analyze-nuget-packages-using-nugetorg"></a><span data-ttu-id="f06e7-128">Analyser les packages NuGet à l’aide de nuget.org</span><span class="sxs-lookup"><span data-stu-id="f06e7-128">Analyze NuGet packages using nuget.org</span></span>

<span data-ttu-id="f06e7-129">Vous pouvez également connaître les TFM pris en charge par chaque package sur [nuget.org](https://www.nuget.org/), dans la section **Dependencies** de la page du package spécifique.</span><span class="sxs-lookup"><span data-stu-id="f06e7-129">Alternatively, you can see the TFMs that each package supports on [nuget.org](https://www.nuget.org/) under the **Dependencies** section of the package page.</span></span>

<span data-ttu-id="f06e7-130">Bien qu’il soit plus facile d’utiliser le site pour vérifier la compatibilité, les informations de **dépendances** ne sont pas disponibles sur le site de tous les packages.</span><span class="sxs-lookup"><span data-stu-id="f06e7-130">Although using the site is an easier method to verify the compatibility, **Dependencies** information is not available on the site for all packages.</span></span>

### <a name="net-framework-compatibility-mode"></a><span data-ttu-id="f06e7-131">Mode de compatibilité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f06e7-131">.NET Framework compatibility mode</span></span>

<span data-ttu-id="f06e7-132">Après avoir analysé les packages NuGet, vous constaterez peut-être qu’ils ne ciblent que le .NET Framework, comme c’est le cas de la plupart des packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="f06e7-132">After analyzing the NuGet packages, you might find that they only target the .NET Framework, as most NuGet packages do.</span></span>

<span data-ttu-id="f06e7-133">Le mode de compatibilité du .NET Framework a été introduit dans .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="f06e7-133">Starting with .NET Standard 2.0, the .NET Framework compatibility mode was introduced.</span></span> <span data-ttu-id="f06e7-134">Ce mode de compatibilité permet aux projets .NET Standard et .NET Core de référencer des bibliothèques .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f06e7-134">This compatibility mode allows .NET Standard and .NET Core projects to reference .NET Framework libraries.</span></span> <span data-ttu-id="f06e7-135">Le référencement de bibliothèques .NET Framework ne fonctionne pas pour tous les projets, par exemple si la bibliothèque utilise des API WPF (Windows Presentation Foundation), mais cela débloque de nombreux scénarios de portage.</span><span class="sxs-lookup"><span data-stu-id="f06e7-135">Referencing .NET Framework libraries doesn't work for all projects, such as if the library uses Windows Presentation Foundation (WPF) APIs, but it does unblock many porting scenarios.</span></span>

<span data-ttu-id="f06e7-136">Lorsque vous référencez des packages NuGet qui ciblent le .NET Framework dans votre projet, comme [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), vous obtenez un avertissement de package de secours ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) similaire à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f06e7-136">When you reference NuGet packages that target the .NET Framework in your project, such as [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), you get a package fallback warning ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) similar to the following example:</span></span>

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

<span data-ttu-id="f06e7-137">Cet avertissement s’affiche lorsque vous ajoutez le package et chaque fois que vous générez une build, pour vous rappeler de tester ce package avec votre projet.</span><span class="sxs-lookup"><span data-stu-id="f06e7-137">That warning is displayed when you add the package and every time you build to make sure you test that package with your project.</span></span> <span data-ttu-id="f06e7-138">Si votre projet fonctionne comme prévu, vous pouvez supprimer cet avertissement en modifiant les propriétés du package dans Visual Studio ou en modifiant manuellement le fichier projet dans votre éditeur de code favori.</span><span class="sxs-lookup"><span data-stu-id="f06e7-138">If your project is working as expected, you can suppress that warning by editing the package properties in Visual Studio or by manually editing the project file in your favorite code editor.</span></span>

<span data-ttu-id="f06e7-139">Pour supprimer l’avertissement en modifiant le fichier projet, recherchez l’entrée `PackageReference` du package pour lequel vous souhaitez supprimer l’avertissement, puis ajoutez l’attribut `NoWarn`.</span><span class="sxs-lookup"><span data-stu-id="f06e7-139">To suppress the warning by editing the project file, find the `PackageReference` entry for the package you want to suppress the warning for and add the `NoWarn` attribute.</span></span> <span data-ttu-id="f06e7-140">L’attribut `NoWarn` accepte une liste séparée par des virgules de tous les ID d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="f06e7-140">The `NoWarn` attribute accepts a comma-separated list of all the warning IDs.</span></span> <span data-ttu-id="f06e7-141">L’exemple suivant montre comment supprimer l’avertissement `NU1701` pour le package `Huitian.PowerCollections` en modifiant votre fichier projet manuellement :</span><span class="sxs-lookup"><span data-stu-id="f06e7-141">The following example shows how to suppress the `NU1701` warning for the `Huitian.PowerCollections` package by editing your project file manually:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

<span data-ttu-id="f06e7-142">Pour plus d’informations sur la façon de supprimer les avertissements du compilateur dans Visual Studio, consultez [Suppression d’avertissements pour les packages NuGet](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages).</span><span class="sxs-lookup"><span data-stu-id="f06e7-142">For more information on how to suppress compiler warnings in Visual Studio, see [Suppressing warnings for NuGet packages](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages).</span></span>

## <a name="port-your-packages-to-packagereference"></a><span data-ttu-id="f06e7-143">Porter vos packages sur `PackageReference`</span><span class="sxs-lookup"><span data-stu-id="f06e7-143">Port your packages to `PackageReference`</span></span>

<span data-ttu-id="f06e7-144">.NET core utilise [PackageReference](/nuget/consume-packages/package-references-in-project-files) pour spécifier les dépendances de package.</span><span class="sxs-lookup"><span data-stu-id="f06e7-144">.NET Core uses [PackageReference](/nuget/consume-packages/package-references-in-project-files) to specify package dependencies.</span></span> <span data-ttu-id="f06e7-145">Si vous utilisez [packages.config](/nuget/reference/packages-config) pour spécifier vos packages, vous devrez les convertir vers `PackageReference`.</span><span class="sxs-lookup"><span data-stu-id="f06e7-145">If you are using [packages.config](/nuget/reference/packages-config) to specify your packages, you will need to convert over to `PackageReference`.</span></span>

<span data-ttu-id="f06e7-146">Pour en savoir plus, consultez [Migrer de packages.config vers PackageReference](/nuget/reference/migrate-packages-config-to-package-reference).</span><span class="sxs-lookup"><span data-stu-id="f06e7-146">You can learn more at [Migrate from packages.config to PackageReference](/nuget/reference/migrate-packages-config-to-package-reference).</span></span>

## <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a><span data-ttu-id="f06e7-147">Ce qu’il faut faire quand votre dépendance de package NuGet ne s’exécute pas sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="f06e7-147">What to do when your NuGet package dependency doesn't run on .NET Core</span></span>

<span data-ttu-id="f06e7-148">Voici quelques actions possibles si un package NuGet dont vous dépendez ne s’exécute pas sur .NET Core :</span><span class="sxs-lookup"><span data-stu-id="f06e7-148">There are a few things you can do if a NuGet package you depend on doesn't run on .NET Core:</span></span>

1. <span data-ttu-id="f06e7-149">Si le projet est open source et hébergé à un endroit comme GitHub, vous pouvez demander aux développeurs de le modifier.</span><span class="sxs-lookup"><span data-stu-id="f06e7-149">If the project is open source and hosted somewhere like GitHub, you can engage the developers directly.</span></span>
2. <span data-ttu-id="f06e7-150">Vous pouvez contacter l’auteur directement sur [NuGet.org](https://www.nuget.org/). Recherchez le package, puis cliquez sur **contacter les propriétaires** sur le côté gauche de la page du package.</span><span class="sxs-lookup"><span data-stu-id="f06e7-150">You can contact the author directly on [nuget.org](https://www.nuget.org/). Search for the package and click **Contact Owners** on the left-hand side of the package's page.</span></span>
3. <span data-ttu-id="f06e7-151">Vous pouvez rechercher un autre package qui s’exécute sur .NET Core et qui réalise la même tâche que le package que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="f06e7-151">You can search for another package that runs on .NET Core that accomplishes the same task as the package you were using.</span></span>
4. <span data-ttu-id="f06e7-152">Vous pouvez essayer d’écrire vous-même le code qui était exécuté par le package.</span><span class="sxs-lookup"><span data-stu-id="f06e7-152">You can attempt to write the code the package was doing yourself.</span></span>
5. <span data-ttu-id="f06e7-153">Vous pouvez éliminer la dépendance du package en modifiant les fonctionnalités de votre application, au moins jusqu’à ce qu’une version compatible du package soit disponible.</span><span class="sxs-lookup"><span data-stu-id="f06e7-153">You could eliminate the dependency on the package by changing the functionality of your app, at least until a compatible version of the package becomes available.</span></span>

<span data-ttu-id="f06e7-154">N’oubliez pas que les personnes chargées de la maintenance des projets open source et les éditeurs de packages NuGet sont souvent des bénévoles.</span><span class="sxs-lookup"><span data-stu-id="f06e7-154">Remember that open-source project maintainers and NuGet package publishers are often volunteers.</span></span> <span data-ttu-id="f06e7-155">Ils offrent leur contribution car ils s’intéressent à un domaine donné, ils le font gratuitement et ont souvent un autre travail dans la journée.</span><span class="sxs-lookup"><span data-stu-id="f06e7-155">They contribute because they care about a given domain, do it for free, and often have a different daytime job.</span></span> <span data-ttu-id="f06e7-156">Pensez-y lorsque vous les contactez pour leur demander de l’aide sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f06e7-156">So be mindful of that when contacting them to ask for .NET Core support.</span></span>

<span data-ttu-id="f06e7-157">Si vous ne parvenez pas à résoudre votre problème avec les actions ci-dessus, vous devrez peut-être porter votre code sur .NET Core à une date ultérieure.</span><span class="sxs-lookup"><span data-stu-id="f06e7-157">If you can't resolve your issue with any of the above, you may have to port to .NET Core at a later date.</span></span>

<span data-ttu-id="f06e7-158">L’équipe .NET aimerait savoir quelles bibliothèques doivent être prioritairement prises en charge avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f06e7-158">The .NET Team would like to know which libraries are the most important to support with .NET Core.</span></span> <span data-ttu-id="f06e7-159">Vous pouvez nous envoyer un e-mail à l’adresse dotnet@microsoft.com afin de nous indiquer les bibliothèques que vous voudriez utiliser.</span><span class="sxs-lookup"><span data-stu-id="f06e7-159">You can send an email to dotnet@microsoft.com about the libraries you'd like to use.</span></span>

## <a name="analyze-dependencies-that-arent-nuget-packages"></a><span data-ttu-id="f06e7-160">Analyser des dépendances qui ne sont pas des packages NuGet</span><span class="sxs-lookup"><span data-stu-id="f06e7-160">Analyze dependencies that aren't NuGet packages</span></span>

<span data-ttu-id="f06e7-161">Vous avez peut-être une dépendance qui n’est pas un package NuGet, comme une DLL dans le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="f06e7-161">You may have a dependency that isn't a NuGet package, such as a DLL in the file system.</span></span> <span data-ttu-id="f06e7-162">La seule façon de déterminer la portabilité de cette dépendance est d’exécuter l’outil [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport).</span><span class="sxs-lookup"><span data-stu-id="f06e7-162">The only way to determine the portability of that dependency is to run the [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) tool.</span></span> <span data-ttu-id="f06e7-163">Cet outil peut analyser les assemblys qui ciblent le .NET Framework et identifier les API qui ne sont pas portables sur d’autres plateformes .NET telles que .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f06e7-163">The tool can analyze assemblies that target the .NET Framework and identify APIs that aren't portable to other .NET platforms such as .NET Core.</span></span> <span data-ttu-id="f06e7-164">Vous pouvez exécuter cet outil en tant qu’application console ou qu’[extension Visual Studio](../../standard/analyzers/portability-analyzer.md).</span><span class="sxs-lookup"><span data-stu-id="f06e7-164">You can run the tool as a console application or as a [Visual Studio extension](../../standard/analyzers/portability-analyzer.md).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="f06e7-165">Suivant</span><span class="sxs-lookup"><span data-stu-id="f06e7-165">Next</span></span>](libraries.md)
