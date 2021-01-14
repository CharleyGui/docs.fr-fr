---
title: Propriétés MSBuild pour Microsoft. NET. Sdk
description: Référence pour les propriétés et les éléments MSBuild compris par le kit de développement logiciel (SDK) .NET.
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: e35ccc3540756a4cb7905d5864caf65cded4362b
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189976"
---
# <a name="msbuild-reference-for-net-sdk-projects"></a><span data-ttu-id="688df-103">Référence MSBuild pour les projets SDK .NET</span><span class="sxs-lookup"><span data-stu-id="688df-103">MSBuild reference for .NET SDK projects</span></span>

<span data-ttu-id="688df-104">Cette page est une référence pour les propriétés et les éléments MSBuild que vous pouvez utiliser pour configurer des projets .NET.</span><span class="sxs-lookup"><span data-stu-id="688df-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET projects.</span></span>

> [!NOTE]
> <span data-ttu-id="688df-105">Cette page est un travail en cours et ne répertorie pas toutes les propriétés MSBuild utiles pour le kit de développement logiciel (SDK) .NET.</span><span class="sxs-lookup"><span data-stu-id="688df-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET SDK.</span></span> <span data-ttu-id="688df-106">Pour obtenir la liste des propriétés MSBuild courantes, consultez [propriétés MSBuild communes](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="688df-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="688df-107">Propriétés du Framework</span><span class="sxs-lookup"><span data-stu-id="688df-107">Framework properties</span></span>

- [<span data-ttu-id="688df-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="688df-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="688df-109">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="688df-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="688df-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="688df-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="688df-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="688df-111">TargetFramework</span></span>

<span data-ttu-id="688df-112">La `TargetFramework` propriété spécifie la version cible de .NET Framework pour l’application.</span><span class="sxs-lookup"><span data-stu-id="688df-112">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="688df-113">Pour obtenir la liste des monikers du Framework cible valides, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="688df-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="688df-114">Pour plus d’informations, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="688df-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="688df-115">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="688df-115">TargetFrameworks</span></span>

<span data-ttu-id="688df-116">Utilisez la `TargetFrameworks` propriété lorsque vous souhaitez que votre application cible plusieurs plateformes.</span><span class="sxs-lookup"><span data-stu-id="688df-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="688df-117">Pour obtenir la liste des monikers du Framework cible valides, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="688df-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

> [!NOTE]
> <span data-ttu-id="688df-118">Cette propriété est ignorée si `TargetFramework` (singulier) est spécifié.</span><span class="sxs-lookup"><span data-stu-id="688df-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="688df-119">Pour plus d’informations, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="688df-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="688df-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="688df-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="688df-121">Cette propriété s’applique uniquement aux projets qui utilisent `netstandard1.x` .</span><span class="sxs-lookup"><span data-stu-id="688df-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="688df-122">Elle ne s’applique pas aux projets qui utilisent `netstandard2.x` .</span><span class="sxs-lookup"><span data-stu-id="688df-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="688df-123">Utilisez la `NetStandardImplicitPackageVersion` propriété lorsque vous souhaitez spécifier une version de Framework inférieure à la version de l’ensemble de packages.</span><span class="sxs-lookup"><span data-stu-id="688df-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="688df-124">Le fichier projet dans l’exemple suivant cible, `netstandard1.3` mais utilise la version 1.6.0 de `NETStandard.Library` .</span><span class="sxs-lookup"><span data-stu-id="688df-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="688df-125">Propriétés du package</span><span class="sxs-lookup"><span data-stu-id="688df-125">Package properties</span></span>

<span data-ttu-id="688df-126">Vous pouvez spécifier des propriétés telles que `PackageId` , `PackageVersion` ,, `PackageIcon` `Title` et `Description` pour décrire le package qui est créé à partir de votre projet.</span><span class="sxs-lookup"><span data-stu-id="688df-126">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="688df-127">Pour plus d’informations sur ces propriétés et d’autres, consultez [package Target](/nuget/reference/msbuild-targets#pack-target).</span><span class="sxs-lookup"><span data-stu-id="688df-127">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-items-and-metadata"></a><span data-ttu-id="688df-128">Publier les propriétés, les éléments et les métadonnées</span><span class="sxs-lookup"><span data-stu-id="688df-128">Publish properties, items, and metadata</span></span>

- [<span data-ttu-id="688df-129">AppendRuntimeIdentifierToOutputPath</span><span class="sxs-lookup"><span data-stu-id="688df-129">AppendRuntimeIdentifierToOutputPath</span></span>](#appendruntimeidentifiertooutputpath)
- [<span data-ttu-id="688df-130">AppendTargetFrameworkToOutputPath</span><span class="sxs-lookup"><span data-stu-id="688df-130">AppendTargetFrameworkToOutputPath</span></span>](#appendtargetframeworktooutputpath)
- [<span data-ttu-id="688df-131">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="688df-131">CopyLocalLockFileAssemblies</span></span>](#copylocallockfileassemblies)
- [<span data-ttu-id="688df-132">CopyToPublishDirectory</span><span class="sxs-lookup"><span data-stu-id="688df-132">CopyToPublishDirectory</span></span>](#copytopublishdirectory)
- [<span data-ttu-id="688df-133">Ressources</span><span class="sxs-lookup"><span data-stu-id="688df-133">LinkBase</span></span>](#linkbase)
- [<span data-ttu-id="688df-134">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="688df-134">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="688df-135">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="688df-135">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="688df-136">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="688df-136">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="688df-137">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="688df-137">UseAppHost</span></span>](#useapphost)

### <a name="copytopublishdirectory"></a><span data-ttu-id="688df-138">CopyToPublishDirectory</span><span class="sxs-lookup"><span data-stu-id="688df-138">CopyToPublishDirectory</span></span>

<span data-ttu-id="688df-139">Les `CopyToPublishDirectory` métadonnées d’un élément MSBuild contrôlent le moment où l’élément est copié dans le répertoire de publication.</span><span class="sxs-lookup"><span data-stu-id="688df-139">The `CopyToPublishDirectory` metadata on an MSBuild item controls when the item is copied to the publish directory.</span></span> <span data-ttu-id="688df-140">Les valeurs autorisées sont `PreserveNewest` , qui copient uniquement l’élément s’il a changé, `Always` , qui copie toujours l’élément, et `Never` , qui ne copie jamais l’élément.</span><span class="sxs-lookup"><span data-stu-id="688df-140">Allowable values are `PreserveNewest`, which only copies the item if it has changed, `Always`, which always copies the item, and `Never`, which never copies the item.</span></span> <span data-ttu-id="688df-141">Du point de vue des performances, `PreserveNewest` est préférable, car il permet une génération incrémentielle.</span><span class="sxs-lookup"><span data-stu-id="688df-141">From a performance standpoint, `PreserveNewest` is preferable because it enables an incremental build.</span></span>

```xml
<ItemGroup>
  <None Update="appsettings.Development.json" CopyToOutputDirectory="PreserveNewest" CopyToPublishDirectory="PreserveNewest" />
</ItemGroup>
```

### <a name="linkbase"></a><span data-ttu-id="688df-142">Ressources</span><span class="sxs-lookup"><span data-stu-id="688df-142">LinkBase</span></span>

<span data-ttu-id="688df-143">Pour un élément qui se trouve en dehors du répertoire du projet et de ses sous-répertoires, la cible de publication utilise les [métadonnées de lien](/visualstudio/msbuild/common-msbuild-item-metadata) de l’élément pour déterminer où copier l’élément.</span><span class="sxs-lookup"><span data-stu-id="688df-143">For an item that's outside of the project directory and its subdirectories, the publish target uses the item's [Link metadata](/visualstudio/msbuild/common-msbuild-item-metadata) to determine where to copy the item to.</span></span> <span data-ttu-id="688df-144">`Link` détermine également la manière dont les éléments en dehors de l’arborescence du projet s’affichent dans la fenêtre Explorateur de solutions de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="688df-144">`Link` also determines how items outside of the project tree are displayed in the Solution Explorer window of Visual Studio.</span></span>

<span data-ttu-id="688df-145">Si `Link` n’est pas spécifié pour un élément qui se trouve en dehors du cône du projet, la valeur par défaut est `%(LinkBase)\%(RecursiveDir)%(Filename)%(Extension)` .</span><span class="sxs-lookup"><span data-stu-id="688df-145">If `Link` is not specified for an item that's outside of the project cone, it defaults to `%(LinkBase)\%(RecursiveDir)%(Filename)%(Extension)`.</span></span> <span data-ttu-id="688df-146">`LinkBase` vous permet de spécifier un dossier de base raisonnable pour les éléments en dehors du cône du projet.</span><span class="sxs-lookup"><span data-stu-id="688df-146">`LinkBase` lets you specify a sensible base folder for items outside of the project cone.</span></span> <span data-ttu-id="688df-147">L’arborescence des dossiers sous le dossier de base est conservée via `RecursiveDir` .</span><span class="sxs-lookup"><span data-stu-id="688df-147">The folder hierarchy under the base folder is preserved via `RecursiveDir`.</span></span> <span data-ttu-id="688df-148">Si `LinkBase` n’est pas spécifié, il est omis du `Link` chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="688df-148">If `LinkBase` is not specified, it's omitted from the `Link` path.</span></span>

```xml
<ItemGroup>
  <Content Include="..\Extras\**\*.cs" LinkBase="Shared"/>
</ItemGroup>
```

<span data-ttu-id="688df-149">L’illustration suivante montre comment un fichier inclus via l’élément précédent `Include` glob s’affiche dans Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="688df-149">The following image shows how a file that's included via the previous item `Include` glob displays in Solution Explorer.</span></span>

:::image type="content" source="media/solution-explorer-linkbase.png" alt-text="Explorateur de solutions présentant l’élément avec les métadonnées de lienet.":::

### <a name="appendtargetframeworktooutputpath"></a><span data-ttu-id="688df-151">AppendTargetFrameworkToOutputPath</span><span class="sxs-lookup"><span data-stu-id="688df-151">AppendTargetFrameworkToOutputPath</span></span>

<span data-ttu-id="688df-152">La `AppendTargetFrameworkToOutputPath` propriété détermine si le [moniker du Framework cible (TFM)](../../standard/frameworks.md) est ajouté au chemin de sortie (qui est défini par [OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)).</span><span class="sxs-lookup"><span data-stu-id="688df-152">The `AppendTargetFrameworkToOutputPath` property controls whether the [target framework moniker (TFM)](../../standard/frameworks.md) is appended to the output path (which is defined by [OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)).</span></span> <span data-ttu-id="688df-153">Le kit de développement logiciel (SDK) .NET ajoute automatiquement le Framework cible et, le cas échéant, l’identificateur du Runtime au chemin de sortie.</span><span class="sxs-lookup"><span data-stu-id="688df-153">The .NET SDK automatically appends the target framework and, if present, the runtime identifier to the output path.</span></span> <span data-ttu-id="688df-154">L’affectation de `AppendTargetFrameworkToOutputPath` la valeur à `false` empêche le TFM d’être ajouté au chemin de sortie.</span><span class="sxs-lookup"><span data-stu-id="688df-154">Setting `AppendTargetFrameworkToOutputPath` to `false` prevents the TFM from being appended to the output path.</span></span> <span data-ttu-id="688df-155">Toutefois, si le chemin de sortie n’est pas TFM, plusieurs artefacts de build peuvent se remplacer mutuellement.</span><span class="sxs-lookup"><span data-stu-id="688df-155">However, without the TFM in the output path, multiple build artifacts may overwrite each other.</span></span>

<span data-ttu-id="688df-156">Par exemple, pour une application .NET 5,0, le chemin de sortie passe de `bin\Debug\net5.0` à `bin\Debug` avec le paramètre suivant :</span><span class="sxs-lookup"><span data-stu-id="688df-156">For example, for a .NET 5.0 app, the output path changes from `bin\Debug\net5.0` to `bin\Debug` with the following setting:</span></span>

```xml
<PropertyGroup>
  <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
</PropertyGroup>
```

### <a name="appendruntimeidentifiertooutputpath"></a><span data-ttu-id="688df-157">AppendRuntimeIdentifierToOutputPath</span><span class="sxs-lookup"><span data-stu-id="688df-157">AppendRuntimeIdentifierToOutputPath</span></span>

<span data-ttu-id="688df-158">La `AppendRuntimeIdentifierToOutputPath` propriété détermine si l' [identificateur de Runtime (RID)](../rid-catalog.md) est ajouté au chemin de sortie.</span><span class="sxs-lookup"><span data-stu-id="688df-158">The `AppendRuntimeIdentifierToOutputPath` property controls whether the [runtime identifier (RID)](../rid-catalog.md) is appended to the output path.</span></span> <span data-ttu-id="688df-159">Le kit de développement logiciel (SDK) .NET ajoute automatiquement le Framework cible et, le cas échéant, l’identificateur du Runtime au chemin de sortie.</span><span class="sxs-lookup"><span data-stu-id="688df-159">The .NET SDK automatically appends the target framework and, if present, the runtime identifier to the output path.</span></span> <span data-ttu-id="688df-160">`AppendRuntimeIdentifierToOutputPath`La définition de `false` la valeur empêche l’ajout du RID au chemin de sortie.</span><span class="sxs-lookup"><span data-stu-id="688df-160">Setting `AppendRuntimeIdentifierToOutputPath` to `false` prevents the RID from being appended to the output path.</span></span>

<span data-ttu-id="688df-161">Par exemple, pour une application .NET 5,0 et un RID `win10-x64` , le chemin de sortie passe de `bin\Debug\net5.0\win10-x64` à `bin\Debug\net5.0` avec le paramètre suivant :</span><span class="sxs-lookup"><span data-stu-id="688df-161">For example, for a .NET 5.0 app and an RID of `win10-x64`, the output path changes from `bin\Debug\net5.0\win10-x64` to `bin\Debug\net5.0` with the following setting:</span></span>

```xml
<PropertyGroup>
  <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
</PropertyGroup>
```

### <a name="copylocallockfileassemblies"></a><span data-ttu-id="688df-162">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="688df-162">CopyLocalLockFileAssemblies</span></span>

<span data-ttu-id="688df-163">La `CopyLocalLockFileAssemblies` propriété est utile pour les projets de plug-in qui ont des dépendances sur d’autres bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="688df-163">The `CopyLocalLockFileAssemblies` property is useful for plugin projects that have dependencies on other libraries.</span></span> <span data-ttu-id="688df-164">Si vous affectez à cette propriété `true` la valeur, toutes les dépendances de package NuGet sont copiées dans le répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="688df-164">If you set this property to `true`, any NuGet package dependencies are copied to the output directory.</span></span> <span data-ttu-id="688df-165">Cela signifie que vous pouvez utiliser la sortie de `dotnet build` pour exécuter votre plug-in sur n’importe quel ordinateur.</span><span class="sxs-lookup"><span data-stu-id="688df-165">That means you can use the output of `dotnet build` to run your plugin on any machine.</span></span>

```xml
<PropertyGroup>
  <CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="688df-166">Vous pouvez également utiliser `dotnet publish` pour publier la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="688df-166">Alternatively, you can use `dotnet publish` to publish the class library.</span></span> <span data-ttu-id="688df-167">Pour plus d’informations, consultez [dotnet Publish](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="688df-167">For more information, see [dotnet publish](../tools/dotnet-publish.md).</span></span>

### <a name="runtimeidentifier"></a><span data-ttu-id="688df-168">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="688df-168">RuntimeIdentifier</span></span>

<span data-ttu-id="688df-169">La `RuntimeIdentifier` propriété vous permet de spécifier un [identificateur de Runtime unique (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="688df-169">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="688df-170">Le RID permet de publier un déploiement autonome.</span><span class="sxs-lookup"><span data-stu-id="688df-170">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="688df-171">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="688df-171">RuntimeIdentifiers</span></span>

<span data-ttu-id="688df-172">La `RuntimeIdentifiers` propriété vous permet de spécifier une liste délimitée par des points-virgules des [identificateurs de Runtime (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="688df-172">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="688df-173">Utilisez cette propriété si vous devez publier pour plusieurs runtimes.</span><span class="sxs-lookup"><span data-stu-id="688df-173">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="688df-174">`RuntimeIdentifiers` est utilisé au moment de la restauration pour s’assurer que les ressources appropriées sont dans le graphique.</span><span class="sxs-lookup"><span data-stu-id="688df-174">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="688df-175">`RuntimeIdentifier` (singulier) peut fournir des builds plus rapides quand un seul Runtime est requis.</span><span class="sxs-lookup"><span data-stu-id="688df-175">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="688df-176">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="688df-176">TrimmerRootAssembly</span></span>

<span data-ttu-id="688df-177">L' `TrimmerRootAssembly` élément vous permet d’exclure un assembly du [*découpage*](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="688df-177">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="688df-178">Le découpage est le processus qui consiste à supprimer des parties inutilisées du runtime d’une application empaquetée.</span><span class="sxs-lookup"><span data-stu-id="688df-178">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="688df-179">Dans certains cas, la suppression peut supprimer incorrectement les références requises.</span><span class="sxs-lookup"><span data-stu-id="688df-179">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="688df-180">Le code XML suivant exclut `System.Security` de la suppression de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="688df-180">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="688df-181">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="688df-181">UseAppHost</span></span>

<span data-ttu-id="688df-182">La `UseAppHost` propriété contrôle si un exécutable natif est créé ou non pour un déploiement.</span><span class="sxs-lookup"><span data-stu-id="688df-182">The `UseAppHost` property controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="688df-183">Un exécutable natif est requis pour les déploiements autonomes.</span><span class="sxs-lookup"><span data-stu-id="688df-183">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="688df-184">Dans .NET Core 3,0 et versions ultérieures, un fichier exécutable dépendant du Framework est créé par défaut.</span><span class="sxs-lookup"><span data-stu-id="688df-184">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="688df-185">Affectez à la propriété la valeur `UseAppHost` `false` pour désactiver la génération de l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="688df-185">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="688df-186">Pour plus d’informations sur le déploiement, consultez [déploiement d’applications .net](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="688df-186">For more information about deployment, see [.NET application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="688df-187">Propriétés de compilation</span><span class="sxs-lookup"><span data-stu-id="688df-187">Compile properties</span></span>

- [<span data-ttu-id="688df-188">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="688df-188">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="688df-189">LangVersion</span><span class="sxs-lookup"><span data-stu-id="688df-189">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="688df-190">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="688df-190">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="688df-191">La `EmbeddedResourceUseDependentUponConvention` propriété définit si les noms des fichiers manifestes de ressources sont générés à partir des informations de type dans les fichiers sources qui sont colocalisés avec les fichiers de ressources.</span><span class="sxs-lookup"><span data-stu-id="688df-191">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="688df-192">Par exemple, si *Form1. resx* se trouve dans le même dossier que *Form1.cs* et que `EmbeddedResourceUseDependentUponConvention` a la valeur `true` , le fichier *. Resources* généré prend son nom dans le premier type défini dans *Form1.cs*.</span><span class="sxs-lookup"><span data-stu-id="688df-192">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="688df-193">Par exemple, si `MyNamespace.Form1` est le premier type défini dans *Form1.cs*, le nom de fichier généré est *MyNamespace. Form1. Resources*.</span><span class="sxs-lookup"><span data-stu-id="688df-193">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="688df-194">Si `LogicalName` `ManifestResourceName` `DependentUpon` les métadonnées, ou sont spécifiées pour un `EmbeddedResource` élément, le nom de fichier manifeste généré pour ce fichier de ressources est basé sur ces métadonnées à la place.</span><span class="sxs-lookup"><span data-stu-id="688df-194">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="688df-195">Par défaut, dans un nouveau projet .NET, cette propriété a la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="688df-195">By default, in a new .NET project, this property is set to `true`.</span></span> <span data-ttu-id="688df-196">Si la valeur `false` est définie sur, et si aucune `LogicalName` `ManifestResourceName` `DependentUpon` métadonnée n’est spécifiée pour l' `EmbeddedResource` élément dans le fichier projet, le nom du fichier manifeste de la ressource est basé sur l’espace de noms racine du projet et le chemin d’accès relatif au fichier *. resx* .</span><span class="sxs-lookup"><span data-stu-id="688df-196">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="688df-197">Pour plus d’informations, consultez [Comment les fichiers manifestes de ressources sont nommés](../resources/manifest-file-names.md).</span><span class="sxs-lookup"><span data-stu-id="688df-197">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="688df-198">LangVersion</span><span class="sxs-lookup"><span data-stu-id="688df-198">LangVersion</span></span>

<span data-ttu-id="688df-199">La `LangVersion` propriété vous permet de spécifier une version du langage de programmation spécifique.</span><span class="sxs-lookup"><span data-stu-id="688df-199">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="688df-200">Par exemple, si vous souhaitez accéder aux fonctionnalités de la version préliminaire de C#, affectez à la valeur `LangVersion` `preview` .</span><span class="sxs-lookup"><span data-stu-id="688df-200">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="688df-201">Pour plus d’informations, consultez contrôle de [version du langage C#](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="688df-201">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="default-item-inclusion-properties"></a><span data-ttu-id="688df-202">Propriétés d’inclusion d’élément par défaut</span><span class="sxs-lookup"><span data-stu-id="688df-202">Default item inclusion properties</span></span>

- [<span data-ttu-id="688df-203">DefaultExcludesInProjectFolder</span><span class="sxs-lookup"><span data-stu-id="688df-203">DefaultExcludesInProjectFolder</span></span>](#defaultexcludesinprojectfolder)
- [<span data-ttu-id="688df-204">DefaultItemExcludes</span><span class="sxs-lookup"><span data-stu-id="688df-204">DefaultItemExcludes</span></span>](#defaultitemexcludes)
- [<span data-ttu-id="688df-205">EnableDefaultCompileItems</span><span class="sxs-lookup"><span data-stu-id="688df-205">EnableDefaultCompileItems</span></span>](#enabledefaultcompileitems)
- [<span data-ttu-id="688df-206">EnableDefaultEmbeddedResourceItems</span><span class="sxs-lookup"><span data-stu-id="688df-206">EnableDefaultEmbeddedResourceItems</span></span>](#enabledefaultembeddedresourceitems)
- [<span data-ttu-id="688df-207">EnableDefaultItems</span><span class="sxs-lookup"><span data-stu-id="688df-207">EnableDefaultItems</span></span>](#enabledefaultitems)
- [<span data-ttu-id="688df-208">EnableDefaultNoneItems</span><span class="sxs-lookup"><span data-stu-id="688df-208">EnableDefaultNoneItems</span></span>](#enabledefaultnoneitems)

<span data-ttu-id="688df-209">Pour plus d’informations, consultez [include et Exclude par défaut](overview.md#default-includes-and-excludes).</span><span class="sxs-lookup"><span data-stu-id="688df-209">For more information, see [Default includes and excludes](overview.md#default-includes-and-excludes).</span></span>

### <a name="defaultitemexcludes"></a><span data-ttu-id="688df-210">DefaultItemExcludes</span><span class="sxs-lookup"><span data-stu-id="688df-210">DefaultItemExcludes</span></span>

<span data-ttu-id="688df-211">Utilisez la `DefaultItemExcludes` propriété pour définir les modèles glob pour les fichiers et les dossiers qui doivent être exclus des modèles glob include, Exclude et Remove.</span><span class="sxs-lookup"><span data-stu-id="688df-211">Use the `DefaultItemExcludes` property to define glob patterns for files and folders that should be excluded from the include, exclude, and remove globs.</span></span> <span data-ttu-id="688df-212">Par défaut, les dossiers *./bin* et *./obj* sont exclus des modèles glob.</span><span class="sxs-lookup"><span data-stu-id="688df-212">By default, the *./bin* and *./obj* folders are excluded from the glob patterns.</span></span>

```xml
<PropertyGroup>
  <DefaultItemExcludes>$(DefaultItemExcludes);**/*.myextension</DefaultItemExcludes>
</PropertyGroup>
```

### <a name="defaultexcludesinprojectfolder"></a><span data-ttu-id="688df-213">DefaultExcludesInProjectFolder</span><span class="sxs-lookup"><span data-stu-id="688df-213">DefaultExcludesInProjectFolder</span></span>

<span data-ttu-id="688df-214">Utilisez la `DefaultExcludesInProjectFolder` propriété pour définir les modèles glob pour les fichiers et les dossiers dans le dossier du projet qui doivent être exclus des modèles glob include, Exclude et Remove.</span><span class="sxs-lookup"><span data-stu-id="688df-214">Use the `DefaultExcludesInProjectFolder` property to define glob patterns for files and folders in the project folder that should be excluded from the include, exclude, and remove globs.</span></span> <span data-ttu-id="688df-215">Par défaut, les dossiers qui commencent par un point ( `.` ), tels que *. git* et *. vs*, sont exclus des modèles glob.</span><span class="sxs-lookup"><span data-stu-id="688df-215">By default, folders that start with a period (`.`), such as *.git* and *.vs*, are excluded from the glob patterns.</span></span>

<span data-ttu-id="688df-216">Cette propriété est très similaire à la `DefaultItemExcludes` propriété, sauf qu’elle considère uniquement les fichiers et les dossiers dans le dossier du projet.</span><span class="sxs-lookup"><span data-stu-id="688df-216">This property is very similar to the `DefaultItemExcludes` property, except that it only considers files and folders in the project folder.</span></span> <span data-ttu-id="688df-217">Quand un modèle glob correspondrait involontairement à des éléments en dehors du dossier du projet avec un chemin d’accès relatif, utilisez la propriété à la `DefaultExcludesInProjectFolder` place de la `DefaultItemExcludes` propriété.</span><span class="sxs-lookup"><span data-stu-id="688df-217">When a glob pattern would unintentionally match items outside the project folder with a relative path, use the `DefaultExcludesInProjectFolder` property instead of the `DefaultItemExcludes` property.</span></span>

```xml
<PropertyGroup>
  <DefaultExcludesInProjectFolder>$(DefaultExcludesInProjectFolder);**/myprefix*/**</DefaultExcludesInProjectFolder>
</PropertyGroup>
```

### <a name="enabledefaultitems"></a><span data-ttu-id="688df-218">EnableDefaultItems</span><span class="sxs-lookup"><span data-stu-id="688df-218">EnableDefaultItems</span></span>

<span data-ttu-id="688df-219">La `EnableDefaultItems` propriété contrôle si les éléments de compilation, les éléments de ressources incorporés et les `None` éléments sont implicitement inclus dans le projet.</span><span class="sxs-lookup"><span data-stu-id="688df-219">The `EnableDefaultItems` property controls whether compile items, embedded resource items, and `None` items are implicitly included in the project.</span></span> <span data-ttu-id="688df-220">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="688df-220">The default value is `true`.</span></span> <span data-ttu-id="688df-221">Affectez à la propriété la valeur `EnableDefaultItems` `false` pour désactiver toute inclusion de fichier implicite.</span><span class="sxs-lookup"><span data-stu-id="688df-221">Set the `EnableDefaultItems` property to `false` to disable all implicit file inclusion.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="enabledefaultcompileitems"></a><span data-ttu-id="688df-222">EnableDefaultCompileItems</span><span class="sxs-lookup"><span data-stu-id="688df-222">EnableDefaultCompileItems</span></span>

<span data-ttu-id="688df-223">La `EnableDefaultCompileItems` propriété contrôle si les éléments de compilation sont inclus implicitement dans le projet.</span><span class="sxs-lookup"><span data-stu-id="688df-223">The `EnableDefaultCompileItems` property controls whether compile items are implicitly included in the project.</span></span> <span data-ttu-id="688df-224">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="688df-224">The default value is `true`.</span></span> <span data-ttu-id="688df-225">Affectez à la propriété la valeur `EnableDefaultCompileItems` `false` pour désactiver l’inclusion implicite des fichiers \*. cs et d’autres extensions de langage.</span><span class="sxs-lookup"><span data-stu-id="688df-225">Set the `EnableDefaultCompileItems` property to `false` to disable implicit inclusion of \*.cs and other language-extension files.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

### <a name="enabledefaultembeddedresourceitems"></a><span data-ttu-id="688df-226">EnableDefaultEmbeddedResourceItems</span><span class="sxs-lookup"><span data-stu-id="688df-226">EnableDefaultEmbeddedResourceItems</span></span>

<span data-ttu-id="688df-227">La `EnableDefaultEmbeddedResourceItems` propriété contrôle si les éléments de ressources incorporés sont implicitement inclus dans le projet.</span><span class="sxs-lookup"><span data-stu-id="688df-227">The `EnableDefaultEmbeddedResourceItems` property controls whether embedded resource items are implicitly included in the project.</span></span> <span data-ttu-id="688df-228">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="688df-228">The default value is `true`.</span></span> <span data-ttu-id="688df-229">Affectez à la propriété la valeur `EnableDefaultEmbeddedResourceItems` `false` pour désactiver l’inclusion implicite des fichiers de ressources incorporés.</span><span class="sxs-lookup"><span data-stu-id="688df-229">Set the `EnableDefaultEmbeddedResourceItems` property to `false` to disable implicit inclusion of embedded resource files.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
</PropertyGroup>
```

### <a name="enabledefaultnoneitems"></a><span data-ttu-id="688df-230">EnableDefaultNoneItems</span><span class="sxs-lookup"><span data-stu-id="688df-230">EnableDefaultNoneItems</span></span>

<span data-ttu-id="688df-231">La `EnableDefaultNoneItems` propriété contrôle si les `None` éléments (fichiers qui n’ont pas de rôle dans le processus de génération) sont implicitement inclus dans le projet.</span><span class="sxs-lookup"><span data-stu-id="688df-231">The `EnableDefaultNoneItems` property controls whether `None` items (files that have no role in the build process) are implicitly included in the project.</span></span> <span data-ttu-id="688df-232">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="688df-232">The default value is `true`.</span></span> <span data-ttu-id="688df-233">Affectez à la propriété la valeur `EnableDefaultNoneItems` `false` pour désactiver l’inclusion implicite d' `None` éléments.</span><span class="sxs-lookup"><span data-stu-id="688df-233">Set the `EnableDefaultNoneItems` property to `false` to disable implicit inclusion of `None` items.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

## <a name="code-analysis-properties"></a><span data-ttu-id="688df-234">Propriétés de l’analyse du code</span><span class="sxs-lookup"><span data-stu-id="688df-234">Code analysis properties</span></span>

- [<span data-ttu-id="688df-235">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="688df-235">AnalysisLevel</span></span>](#analysislevel)
- [<span data-ttu-id="688df-236">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="688df-236">AnalysisMode</span></span>](#analysismode)
- [<span data-ttu-id="688df-237">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="688df-237">CodeAnalysisTreatWarningsAsErrors</span></span>](#codeanalysistreatwarningsaserrors)
- [<span data-ttu-id="688df-238">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="688df-238">EnableNETAnalyzers</span></span>](#enablenetanalyzers)
- [<span data-ttu-id="688df-239">EnforceCodeStyleInBuild</span><span class="sxs-lookup"><span data-stu-id="688df-239">EnforceCodeStyleInBuild</span></span>](#enforcecodestyleinbuild)

### <a name="analysislevel"></a><span data-ttu-id="688df-240">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="688df-240">AnalysisLevel</span></span>

<span data-ttu-id="688df-241">La `AnalysisLevel` propriété vous permet de spécifier un niveau d’analyse du code.</span><span class="sxs-lookup"><span data-stu-id="688df-241">The `AnalysisLevel` property lets you specify a code analysis level.</span></span> <span data-ttu-id="688df-242">Par exemple, si vous souhaitez accéder à l’aperçu des analyseurs de code, affectez à la valeur `AnalysisLevel` `preview` .</span><span class="sxs-lookup"><span data-stu-id="688df-242">For example, if you want access to preview code analyzers, set `AnalysisLevel` to `preview`.</span></span> <span data-ttu-id="688df-243">La valeur par défaut est `latest`.</span><span class="sxs-lookup"><span data-stu-id="688df-243">The default value is `latest`.</span></span>

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

<span data-ttu-id="688df-244">Le tableau suivant présente les options disponibles.</span><span class="sxs-lookup"><span data-stu-id="688df-244">The following table shows the available options.</span></span>

| <span data-ttu-id="688df-245">Valeur</span><span class="sxs-lookup"><span data-stu-id="688df-245">Value</span></span> | <span data-ttu-id="688df-246">Signification</span><span class="sxs-lookup"><span data-stu-id="688df-246">Meaning</span></span> |
|-|-|
| `latest` | <span data-ttu-id="688df-247">Les derniers analyseurs de code qui ont été publiés sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="688df-247">The latest code analyzers that have been released are used.</span></span> <span data-ttu-id="688df-248">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="688df-248">This is the default.</span></span> |
| `preview` | <span data-ttu-id="688df-249">Les derniers analyseurs de code sont utilisés, même s’ils sont en version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="688df-249">The latest code analyzers are used, even if they are in preview.</span></span> |
| `5.0` | <span data-ttu-id="688df-250">L’ensemble de règles activé pour la version .NET 5,0 est utilisé, même si des règles plus récentes sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="688df-250">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |
| `5` | <span data-ttu-id="688df-251">L’ensemble de règles activé pour la version .NET 5,0 est utilisé, même si des règles plus récentes sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="688df-251">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |

### <a name="analysismode"></a><span data-ttu-id="688df-252">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="688df-252">AnalysisMode</span></span>

<span data-ttu-id="688df-253">À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET est fourni avec toutes les [règles de qualité du code « ca »](../../fundamentals/code-analysis/quality-rules/index.md).</span><span class="sxs-lookup"><span data-stu-id="688df-253">Starting with .NET 5.0, the .NET SDK ships with all of the ["CA" code quality rules](../../fundamentals/code-analysis/quality-rules/index.md).</span></span> <span data-ttu-id="688df-254">Par défaut, seules [certaines règles sont activées](../../fundamentals/code-analysis/overview.md#enabled-rules) en tant qu’avertissements de génération.</span><span class="sxs-lookup"><span data-stu-id="688df-254">By default, only [some rules are enabled](../../fundamentals/code-analysis/overview.md#enabled-rules) as build warnings.</span></span> <span data-ttu-id="688df-255">La `AnalysisMode` propriété vous permet de personnaliser l’ensemble des règles qui sont activées par défaut.</span><span class="sxs-lookup"><span data-stu-id="688df-255">The `AnalysisMode` property lets you customize the set of rules that are enabled by default.</span></span> <span data-ttu-id="688df-256">Vous pouvez basculer vers un mode d’analyse plus agressif ou un mode d’analyse plus prudent (abonnement).</span><span class="sxs-lookup"><span data-stu-id="688df-256">You can either switch to a more aggressive (opt-out) analysis mode or a more conservative (opt-in) analysis mode.</span></span> <span data-ttu-id="688df-257">Par exemple, si vous souhaitez activer toutes les règles par défaut en tant qu’avertissements de build, affectez la valeur à `AllEnabledByDefault` .</span><span class="sxs-lookup"><span data-stu-id="688df-257">For example, if you want to enable all rules by default as build warnings, set the value to `AllEnabledByDefault`.</span></span>

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
</PropertyGroup>
```

<span data-ttu-id="688df-258">Le tableau suivant présente les options disponibles.</span><span class="sxs-lookup"><span data-stu-id="688df-258">The following table shows the available options.</span></span>

| <span data-ttu-id="688df-259">Valeur</span><span class="sxs-lookup"><span data-stu-id="688df-259">Value</span></span> | <span data-ttu-id="688df-260">Signification</span><span class="sxs-lookup"><span data-stu-id="688df-260">Meaning</span></span> |
|-|-|
| `Default` | <span data-ttu-id="688df-261">Mode par défaut, où certaines règles sont activées en tant qu’avertissements de build, certaines règles sont activées en tant que suggestions de l’IDE Visual Studio, et le reste est désactivé.</span><span class="sxs-lookup"><span data-stu-id="688df-261">Default mode, where certain rules are enabled as build warnings, certain rules are enabled as Visual Studio IDE suggestions, and the remainder are disabled.</span></span> |
| `AllEnabledByDefault` | <span data-ttu-id="688df-262">Mode agressif ou opt-out, où toutes les règles sont activées par défaut en tant qu’avertissements de génération.</span><span class="sxs-lookup"><span data-stu-id="688df-262">Aggressive or opt-out mode, where all rules are enabled by default as build warnings.</span></span> <span data-ttu-id="688df-263">Vous pouvez [choisir](../../fundamentals/code-analysis/configuration-options.md) de désactiver les règles individuelles de manière sélective pour les désactiver.</span><span class="sxs-lookup"><span data-stu-id="688df-263">You can selectively [opt out](../../fundamentals/code-analysis/configuration-options.md) of individual rules to disable them.</span></span> |
| `AllDisabledByDefault` | <span data-ttu-id="688df-264">Mode conservateur ou opt-in, où toutes les règles sont désactivées par défaut.</span><span class="sxs-lookup"><span data-stu-id="688df-264">Conservative or opt-in mode, where all rules are disabled by default.</span></span> <span data-ttu-id="688df-265">Vous pouvez [choisir](../../fundamentals/code-analysis/configuration-options.md) des règles individuelles pour les activer.</span><span class="sxs-lookup"><span data-stu-id="688df-265">You can selectively [opt into](../../fundamentals/code-analysis/configuration-options.md) individual rules to enable them.</span></span> |

### <a name="codeanalysistreatwarningsaserrors"></a><span data-ttu-id="688df-266">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="688df-266">CodeAnalysisTreatWarningsAsErrors</span></span>

<span data-ttu-id="688df-267">La `CodeAnalysisTreatWarningsAsErrors` propriété vous permet de configurer si les avertissements d’analyse de la qualité du code (CAXXXX) doivent être traités comme des avertissements et rompre la génération.</span><span class="sxs-lookup"><span data-stu-id="688df-267">The `CodeAnalysisTreatWarningsAsErrors` property lets you configure whether code quality analysis warnings (CAxxxx) should be treated as warnings and break the build.</span></span> <span data-ttu-id="688df-268">Si vous utilisez l' `-warnaserror` indicateur lorsque vous générez vos projets, les avertissements de l’analyse de la [qualité du code .net](../../fundamentals/code-analysis/overview.md#code-quality-analysis) sont également traités comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="688df-268">If you use the `-warnaserror` flag when you build your projects, [.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) warnings are also treated as errors.</span></span> <span data-ttu-id="688df-269">Si vous ne souhaitez pas que les avertissements d’analyse de la qualité du code soient traités comme des erreurs, vous pouvez définir la `CodeAnalysisTreatWarningsAsErrors` propriété MSBuild sur `false` dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="688df-269">If you do not want code quality analysis warnings to be treated as errors, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a><span data-ttu-id="688df-270">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="688df-270">EnableNETAnalyzers</span></span>

<span data-ttu-id="688df-271">L’analyse de la [qualité du code .net](../../fundamentals/code-analysis/overview.md#code-quality-analysis) est activée, par défaut, pour les projets qui ciblent .net 5,0 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="688df-271">[.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="688df-272">Vous pouvez activer l’analyse du code .NET pour les projets qui ciblent des versions antérieures de .NET en affectant à la propriété la valeur `EnableNETAnalyzers` `true` .</span><span class="sxs-lookup"><span data-stu-id="688df-272">You can enable .NET code analysis for projects that target earlier versions of .NET by setting the `EnableNETAnalyzers` property to `true`.</span></span> <span data-ttu-id="688df-273">Pour désactiver l’analyse du code dans un projet, affectez la valeur à cette propriété `false` .</span><span class="sxs-lookup"><span data-stu-id="688df-273">To disable code analysis in any project, set this property to `false`.</span></span>

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="688df-274">Une autre façon d’activer l’analyse du code .NET sur les projets qui ciblent les versions .NET antérieures à .NET 5,0 consiste à définir la propriété [AnalysisLevel](#analysislevel) sur `latest` .</span><span class="sxs-lookup"><span data-stu-id="688df-274">Another way to enable .NET code analysis on projects that target .NET versions prior to .NET 5.0 is to set the [AnalysisLevel](#analysislevel) property to `latest`.</span></span>

### <a name="enforcecodestyleinbuild"></a><span data-ttu-id="688df-275">EnforceCodeStyleInBuild</span><span class="sxs-lookup"><span data-stu-id="688df-275">EnforceCodeStyleInBuild</span></span>

> [!NOTE]
> <span data-ttu-id="688df-276">Cette fonctionnalité est actuellement expérimentale et peut changer entre les versions .NET 5 et .NET 6.</span><span class="sxs-lookup"><span data-stu-id="688df-276">This feature is currently experimental and may change between the .NET 5 and .NET 6 releases.</span></span>

<span data-ttu-id="688df-277">L' [analyse du style de code .net](../../fundamentals/code-analysis/overview.md#code-style-analysis) est désactivée, par défaut, à la génération pour tous les projets .net.</span><span class="sxs-lookup"><span data-stu-id="688df-277">[.NET code style analysis](../../fundamentals/code-analysis/overview.md#code-style-analysis) is disabled, by default, on build for all .NET projects.</span></span> <span data-ttu-id="688df-278">Vous pouvez activer l’analyse de style de code pour les projets .NET en affectant à la propriété la valeur `EnforceCodeStyleInBuild` `true` .</span><span class="sxs-lookup"><span data-stu-id="688df-278">You can enable code style analysis for .NET projects by setting the `EnforceCodeStyleInBuild` property to `true`.</span></span>

```xml
<PropertyGroup>
  <EnforceCodeStyleInBuild>true</EnforceCodeStyleInBuild>
</PropertyGroup>
```

<span data-ttu-id="688df-279">Toutes les règles de style de code qui sont [configurées](../../fundamentals/code-analysis/overview.md#code-style-analysis) pour être des avertissements ou des erreurs sont exécutées lors des violations de la build et des rapports.</span><span class="sxs-lookup"><span data-stu-id="688df-279">All code style rules that are [configured](../../fundamentals/code-analysis/overview.md#code-style-analysis) to be warnings or errors will execute on build and report violations.</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="688df-280">Propriétés de configuration au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="688df-280">Run-time configuration properties</span></span>

<span data-ttu-id="688df-281">Vous pouvez configurer certains comportements au moment de l’exécution en spécifiant des propriétés MSBuild dans le fichier projet de l’application.</span><span class="sxs-lookup"><span data-stu-id="688df-281">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="688df-282">Pour plus d’informations sur les autres méthodes de configuration du comportement au moment de l’exécution, consultez [paramètres de configuration](../run-time-config/index.md)de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="688df-282">For information about other ways of configuring run-time behavior, see [Run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="688df-283">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="688df-283">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="688df-284">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="688df-284">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="688df-285">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="688df-285">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="688df-286">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="688df-286">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="688df-287">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="688df-287">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="688df-288">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="688df-288">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="688df-289">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="688df-289">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="688df-290">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="688df-290">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="688df-291">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="688df-291">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="688df-292">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="688df-292">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="688df-293">La `ConcurrentGarbageCollection` propriété configure si l' [garbage collection d’arrière-plan (simultané)](../../standard/garbage-collection/background-gc.md) est activée.</span><span class="sxs-lookup"><span data-stu-id="688df-293">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="688df-294">Affectez la valeur `false` à pour désactiver les garbage collection d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="688df-294">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="688df-295">Pour plus d’informations, consultez [Background gc](../run-time-config/garbage-collector.md#background-gc).</span><span class="sxs-lookup"><span data-stu-id="688df-295">For more information, see [Background GC](../run-time-config/garbage-collector.md#background-gc).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="688df-296">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="688df-296">InvariantGlobalization</span></span>

<span data-ttu-id="688df-297">La `InvariantGlobalization` propriété configure si l’application s’exécute en mode de *globalisation invariant* , ce qui signifie qu’elle n’a pas accès aux données spécifiques à la culture.</span><span class="sxs-lookup"><span data-stu-id="688df-297">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="688df-298">Affectez à la valeur la valeur `true` pour qu’elle s’exécute en mode de globalisation-indifférent.</span><span class="sxs-lookup"><span data-stu-id="688df-298">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="688df-299">Pour plus d’informations, consultez [mode indifférent](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="688df-299">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="688df-300">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="688df-300">RetainVMGarbageCollection</span></span>

<span data-ttu-id="688df-301">La `RetainVMGarbageCollection` propriété configure le garbage collector pour placer les segments de mémoire supprimés sur une liste d’attente pour une utilisation ultérieure ou les libérer.</span><span class="sxs-lookup"><span data-stu-id="688df-301">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="688df-302">La définition de la valeur `true` indique au garbage collector de placer les segments sur une liste d’attente.</span><span class="sxs-lookup"><span data-stu-id="688df-302">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="688df-303">Pour plus d’informations, consultez [conserver la machine virtuelle](../run-time-config/garbage-collector.md#retain-vm).</span><span class="sxs-lookup"><span data-stu-id="688df-303">For more information, see [Retain VM](../run-time-config/garbage-collector.md#retain-vm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="688df-304">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="688df-304">ServerGarbageCollection</span></span>

<span data-ttu-id="688df-305">La `ServerGarbageCollection` propriété configure si l’application utilise des [garbage collection de station de travail ou des garbage collection de serveur](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="688df-305">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="688df-306">Définissez la valeur sur `true` sur utiliser le garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="688df-306">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="688df-307">Pour plus d’informations, consultez [station de travail et serveur](../run-time-config/garbage-collector.md#workstation-vs-server).</span><span class="sxs-lookup"><span data-stu-id="688df-307">For more information, see [Workstation vs. server](../run-time-config/garbage-collector.md#workstation-vs-server).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="688df-308">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="688df-308">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="688df-309">La `ThreadPoolMaxThreads` propriété configure le nombre maximal de threads pour le pool de threads de travail.</span><span class="sxs-lookup"><span data-stu-id="688df-309">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="688df-310">Pour plus d’informations, consultez [nombre maximal de threads](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="688df-310">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="688df-311">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="688df-311">ThreadPoolMinThreads</span></span>

<span data-ttu-id="688df-312">La `ThreadPoolMinThreads` propriété configure le nombre minimal de threads pour le pool de threads de travail.</span><span class="sxs-lookup"><span data-stu-id="688df-312">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="688df-313">Pour plus d’informations, consultez [minimum threads](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="688df-313">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="688df-314">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="688df-314">TieredCompilation</span></span>

<span data-ttu-id="688df-315">La `TieredCompilation` propriété configure si le compilateur juste-à-temps (JIT) utilise la [compilation à plusieurs niveaux](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="688df-315">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="688df-316">Définissez la valeur sur `false` pour désactiver la compilation à plusieurs niveaux.</span><span class="sxs-lookup"><span data-stu-id="688df-316">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="688df-317">Pour plus d’informations, consultez compilation à plusieurs [niveaux](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="688df-317">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="688df-318">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="688df-318">TieredCompilationQuickJit</span></span>

<span data-ttu-id="688df-319">La `TieredCompilationQuickJit` propriété configure si le compilateur JIT utilise Quick JIT.</span><span class="sxs-lookup"><span data-stu-id="688df-319">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="688df-320">Définissez la valeur sur `false` pour désactiver le JIT rapide.</span><span class="sxs-lookup"><span data-stu-id="688df-320">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="688df-321">Pour plus d’informations, consultez [Quick JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="688df-321">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="688df-322">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="688df-322">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="688df-323">La `TieredCompilationQuickJitForLoops` propriété configure si le compilateur JIT utilise le JIT rapide sur les méthodes qui contiennent des boucles.</span><span class="sxs-lookup"><span data-stu-id="688df-323">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="688df-324">Affectez la valeur `true` à pour activer le JIT rapide sur les méthodes qui contiennent des boucles.</span><span class="sxs-lookup"><span data-stu-id="688df-324">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="688df-325">Pour plus d’informations, consultez [Quick JIT for Loops](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="688df-325">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a><span data-ttu-id="688df-326">Propriétés et éléments de référence</span><span class="sxs-lookup"><span data-stu-id="688df-326">Reference properties and items</span></span>

- [<span data-ttu-id="688df-327">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="688df-327">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="688df-328">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="688df-328">DisableImplicitFrameworkReferences</span></span>](#disableimplicitframeworkreferences)
- [<span data-ttu-id="688df-329">PackageReference</span><span class="sxs-lookup"><span data-stu-id="688df-329">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="688df-330">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="688df-330">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="688df-331">Référence</span><span class="sxs-lookup"><span data-stu-id="688df-331">Reference</span></span>](#reference)
- [<span data-ttu-id="688df-332">Propriétés liées à la restauration</span><span class="sxs-lookup"><span data-stu-id="688df-332">Restore-related properties</span></span>](#restore-related-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="688df-333">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="688df-333">AssetTargetFallback</span></span>

<span data-ttu-id="688df-334">La `AssetTargetFallback` propriété vous permet de spécifier des versions de Framework compatibles supplémentaires pour les références de projet et les packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="688df-334">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="688df-335">Par exemple, si vous spécifiez une dépendance de package à l’aide de `PackageReference` mais que ce package ne contient pas de ressources compatibles avec les projets `TargetFramework` , la `AssetTargetFallback` propriété entre en lecture.</span><span class="sxs-lookup"><span data-stu-id="688df-335">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="688df-336">La compatibilité du package référencé est revérifiée à l’aide de chaque version cible de .NET Framework spécifiée dans `AssetTargetFallback` .</span><span class="sxs-lookup"><span data-stu-id="688df-336">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span> <span data-ttu-id="688df-337">Cette propriété remplace la propriété déconseillée `PackageTargetFallback` .</span><span class="sxs-lookup"><span data-stu-id="688df-337">This property replaces the deprecated property `PackageTargetFallback`.</span></span>

<span data-ttu-id="688df-338">Vous pouvez définir la `AssetTargetFallback` propriété sur une ou plusieurs [versions du Framework cible](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="688df-338">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="disableimplicitframeworkreferences"></a><span data-ttu-id="688df-339">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="688df-339">DisableImplicitFrameworkReferences</span></span>

<span data-ttu-id="688df-340">La `DisableImplicitFrameworkReferences` propriété contrôle les `FrameworkReference` éléments implicites lors du ciblage de .net Core 3,0 et des versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="688df-340">The `DisableImplicitFrameworkReferences` property controls implicit `FrameworkReference` items when targeting .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="688df-341">Quand vous ciblez .NET Core 2,1 ou .NET Standard 2,0 et versions antérieures, il contrôle les éléments [PackageReference](#packagereference) implicites pour les packages dans un sous-package.</span><span class="sxs-lookup"><span data-stu-id="688df-341">When targeting .NET Core 2.1 or .NET Standard 2.0 and earlier versions, it controls implicit [PackageReference](#packagereference) items to packages in a metapackage.</span></span> <span data-ttu-id="688df-342">(Un reconditionnement est un package basé sur une infrastructure qui se compose uniquement de dépendances sur d’autres packages.) Cette propriété contrôle également les références implicites telles que `System` et `System.Core` lorsque vous ciblez .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="688df-342">(A metapackage is a framework-based package that consist only of dependencies on other packages.) This property also controls implicit references such as `System` and `System.Core` when targeting .NET Framework.</span></span>

<span data-ttu-id="688df-343">Affectez à cette propriété la valeur `true` pour désactiver les éléments implicites `FrameworkReference` ou [PackageReference](#packagereference) .</span><span class="sxs-lookup"><span data-stu-id="688df-343">Set this property to `true` to disable implicit `FrameworkReference` or [PackageReference](#packagereference) items.</span></span> <span data-ttu-id="688df-344">Si vous affectez à cette propriété `true` la valeur, vous pouvez ajouter des références explicites uniquement aux frameworks ou aux packages dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="688df-344">If you set this property to `true`, you can add explicit references to just the frameworks or packages you need.</span></span>

```xml
<PropertyGroup>
  <DisableImplicitFrameworkReferences>true</DisableImplicitFrameworkReferences>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="688df-345">PackageReference</span><span class="sxs-lookup"><span data-stu-id="688df-345">PackageReference</span></span>

<span data-ttu-id="688df-346">L' `PackageReference` élément définit une référence à un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="688df-346">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="688df-347">L’attribut `Include` spécifie l’ID du package.</span><span class="sxs-lookup"><span data-stu-id="688df-347">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="688df-348">L' `Version` attribut spécifie la version ou la plage de versions.</span><span class="sxs-lookup"><span data-stu-id="688df-348">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="688df-349">Pour plus d’informations sur la spécification d’une version minimale, d’une version maximale, d’une plage ou d’une correspondance exacte, consultez [plages de versions](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="688df-349">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="688df-350">Vous pouvez également ajouter des [attributs de ressource](#asset-attributes) à une référence de package.</span><span class="sxs-lookup"><span data-stu-id="688df-350">You can also add [asset attributes](#asset-attributes) to a package reference.</span></span>

<span data-ttu-id="688df-351">L’extrait de code du fichier projet dans l’exemple suivant référence le package [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .</span><span class="sxs-lookup"><span data-stu-id="688df-351">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="688df-352">Pour plus d’informations, consultez [références de package dans les fichiers projet](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="688df-352">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

#### <a name="asset-attributes"></a><span data-ttu-id="688df-353">Attributs de ressource</span><span class="sxs-lookup"><span data-stu-id="688df-353">Asset attributes</span></span>

<span data-ttu-id="688df-354">Les `IncludeAssets` `ExcludeAssets` `PrivateAssets` métadonnées, et peuvent être ajoutées à une référence de package.</span><span class="sxs-lookup"><span data-stu-id="688df-354">The `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets` metadata can be added to a package reference.</span></span>

| <span data-ttu-id="688df-355">Attribut</span><span class="sxs-lookup"><span data-stu-id="688df-355">Attribute</span></span> | <span data-ttu-id="688df-356">Description</span><span class="sxs-lookup"><span data-stu-id="688df-356">Description</span></span> |
| - | - |
| `IncludeAssets` | <span data-ttu-id="688df-357">Spécifie quelles ressources appartenant au package spécifié par `<PackageReference>` doivent être consommées.</span><span class="sxs-lookup"><span data-stu-id="688df-357">Specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="688df-358">Par défaut, toutes les ressources du package sont incluses.</span><span class="sxs-lookup"><span data-stu-id="688df-358">By default, all package assets are included.</span></span> |
| `ExcludeAssets`| <span data-ttu-id="688df-359">Spécifie les ressources appartenant au package spécifié par ne `<PackageReference>` doivent pas être consommées.</span><span class="sxs-lookup"><span data-stu-id="688df-359">Specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span> |
| `PrivateAssets` | <span data-ttu-id="688df-360">Spécifie les ressources appartenant au package spécifié par `<PackageReference>` doivent être consommées, mais pas transmises au projet suivant.</span><span class="sxs-lookup"><span data-stu-id="688df-360">Specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="688df-361">Les `Analyzers` `Build` ressources, et `ContentFiles` sont privées par défaut lorsque cet attribut n’est pas présent.</span><span class="sxs-lookup"><span data-stu-id="688df-361">The `Analyzers`, `Build`, and `ContentFiles` assets are private by default when this attribute is not present.</span></span> |

<span data-ttu-id="688df-362">Ces attributs peuvent contenir un ou plusieurs des éléments suivants, séparés par un point-virgule `;` si plus d’un élément est listé :</span><span class="sxs-lookup"><span data-stu-id="688df-362">These attributes can contain one or more of the following items, separated by a semicolon `;` if more than one is listed:</span></span>

- <span data-ttu-id="688df-363">`Compile` : le contenu du dossier *lib* est disponible pour la compilation.</span><span class="sxs-lookup"><span data-stu-id="688df-363">`Compile` – the contents of the *lib* folder are available to compile against.</span></span>
- <span data-ttu-id="688df-364">`Runtime` : le contenu du dossier *Runtime* est distribué.</span><span class="sxs-lookup"><span data-stu-id="688df-364">`Runtime` – the contents of the *runtime* folder are distributed.</span></span>
- <span data-ttu-id="688df-365">`ContentFiles` : Le contenu du dossier *contentfiles* est utilisé.</span><span class="sxs-lookup"><span data-stu-id="688df-365">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
- <span data-ttu-id="688df-366">`Build` : les propriétés/cibles du dossier de *génération* sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="688df-366">`Build` – the props/targets in the *build* folder are used.</span></span>
- <span data-ttu-id="688df-367">`Native` : le contenu des ressources natives est copié dans le dossier de *sortie* pour l’exécution.</span><span class="sxs-lookup"><span data-stu-id="688df-367">`Native` – the contents from native assets are copied to the *output* folder for runtime.</span></span>
- <span data-ttu-id="688df-368">`Analyzers` : Les analyseurs sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="688df-368">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="688df-369">Sinon, l’attribut peut contenir :</span><span class="sxs-lookup"><span data-stu-id="688df-369">Alternatively, the attribute can contain:</span></span>

- <span data-ttu-id="688df-370">`None` : Aucune ressource n’est utilisée.</span><span class="sxs-lookup"><span data-stu-id="688df-370">`None` – none of the assets are used.</span></span>
- <span data-ttu-id="688df-371">`All` : Toutes les ressources sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="688df-371">`All` – all assets are used.</span></span>

### <a name="projectreference"></a><span data-ttu-id="688df-372">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="688df-372">ProjectReference</span></span>

<span data-ttu-id="688df-373">L' `ProjectReference` élément définit une référence à un autre projet.</span><span class="sxs-lookup"><span data-stu-id="688df-373">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="688df-374">Le projet référencé est ajouté en tant que dépendance de package NuGet, autrement dit, il est traité de la même façon qu’un `PackageReference` .</span><span class="sxs-lookup"><span data-stu-id="688df-374">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="688df-375">L' `Include` attribut spécifie le chemin d’accès au projet.</span><span class="sxs-lookup"><span data-stu-id="688df-375">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="688df-376">Vous pouvez également ajouter les métadonnées suivantes à une référence de projet : `IncludeAssets` , `ExcludeAssets` et `PrivateAssets` .</span><span class="sxs-lookup"><span data-stu-id="688df-376">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="688df-377">L’extrait de code du fichier projet dans l’exemple suivant fait référence à un projet nommé `Project2` .</span><span class="sxs-lookup"><span data-stu-id="688df-377">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="688df-378">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="688df-378">Reference</span></span>

<span data-ttu-id="688df-379">L' `Reference` élément définit une référence à un fichier d’assembly.</span><span class="sxs-lookup"><span data-stu-id="688df-379">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="688df-380">L' `Include` attribut spécifie le nom du fichier, et les `HintPath` métadonnées spécifient le chemin d’accès à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="688df-380">The `Include` attribute specifies the name of the file, and the `HintPath` metadata specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-related-properties"></a><span data-ttu-id="688df-381">Propriétés liées à la restauration</span><span class="sxs-lookup"><span data-stu-id="688df-381">Restore-related properties</span></span>

<span data-ttu-id="688df-382">La restauration d’un package référencé installe toutes ses dépendances directes et toutes les dépendances de ces dépendances.</span><span class="sxs-lookup"><span data-stu-id="688df-382">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="688df-383">Vous pouvez personnaliser la restauration des packages en spécifiant des propriétés telles que `RestorePackagesPath` et `RestoreIgnoreFailedSources` .</span><span class="sxs-lookup"><span data-stu-id="688df-383">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="688df-384">Pour plus d’informations sur ces propriétés et d’autres, consultez [restaurer la cible](/nuget/reference/msbuild-targets#restore-target).</span><span class="sxs-lookup"><span data-stu-id="688df-384">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="run-properties"></a><span data-ttu-id="688df-385">Propriétés d’exécution</span><span class="sxs-lookup"><span data-stu-id="688df-385">Run properties</span></span>

<span data-ttu-id="688df-386">Les propriétés suivantes sont utilisées pour lancer une application à l’aide de la [`dotnet run`](../tools/dotnet-run.md) commande :</span><span class="sxs-lookup"><span data-stu-id="688df-386">The following properties are used for launching an app with the [`dotnet run`](../tools/dotnet-run.md) command:</span></span>

- [<span data-ttu-id="688df-387">RunArguments</span><span class="sxs-lookup"><span data-stu-id="688df-387">RunArguments</span></span>](#runarguments)
- [<span data-ttu-id="688df-388">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="688df-388">RunWorkingDirectory</span></span>](#runworkingdirectory)

### <a name="runarguments"></a><span data-ttu-id="688df-389">RunArguments</span><span class="sxs-lookup"><span data-stu-id="688df-389">RunArguments</span></span>

<span data-ttu-id="688df-390">La `RunArguments` propriété définit les arguments passés à l’application lorsqu’elle est exécutée.</span><span class="sxs-lookup"><span data-stu-id="688df-390">The `RunArguments` property defines the arguments that are passed to the app when it is run.</span></span>

```xml
<PropertyGroup>
  <RunArguments>-mode dryrun</RunArguments>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="688df-391">Vous pouvez spécifier des arguments supplémentaires à passer à l’application à l’aide [ `--` de l' `dotnet run` option pour ](../tools/dotnet-run.md#options).</span><span class="sxs-lookup"><span data-stu-id="688df-391">You can specify additional arguments to be passed to the app by using the [`--` option for `dotnet run`](../tools/dotnet-run.md#options).</span></span>

### <a name="runworkingdirectory"></a><span data-ttu-id="688df-392">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="688df-392">RunWorkingDirectory</span></span>

<span data-ttu-id="688df-393">La `RunWorkingDirectory` propriété définit le répertoire de travail pour le processus d’application à démarrer dans.</span><span class="sxs-lookup"><span data-stu-id="688df-393">The `RunWorkingDirectory` property defines the working directory for the application process to be started in.</span></span> <span data-ttu-id="688df-394">Il peut s’agir d’un chemin d’accès absolu ou d’un chemin d’accès relatif au répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="688df-394">It can be an absolute path or a path that's relative to the project directory.</span></span> <span data-ttu-id="688df-395">Si vous ne spécifiez pas de répertoire, `OutDir` est utilisé comme répertoire de travail.</span><span class="sxs-lookup"><span data-stu-id="688df-395">If you don't specify a directory, `OutDir` is used as the working directory.</span></span>

```xml
<PropertyGroup>
  <RunWorkingDirectory>c:\temp</RunWorkingDirectory>
</PropertyGroup>
```

## <a name="hosting-properties"></a><span data-ttu-id="688df-396">Propriétés d’hébergement</span><span class="sxs-lookup"><span data-stu-id="688df-396">Hosting properties</span></span>

- [<span data-ttu-id="688df-397">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="688df-397">EnableComHosting</span></span>](#enablecomhosting)
- [<span data-ttu-id="688df-398">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="688df-398">EnableDynamicLoading</span></span>](#enabledynamicloading)

### <a name="enablecomhosting"></a><span data-ttu-id="688df-399">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="688df-399">EnableComHosting</span></span>

<span data-ttu-id="688df-400">La `EnableComHosting` propriété indique qu’un assembly fournit un serveur com.</span><span class="sxs-lookup"><span data-stu-id="688df-400">The `EnableComHosting` property indicates that an assembly provides a COM server.</span></span> <span data-ttu-id="688df-401">Le `EnableComHosting` fait d’affecter à la valeur `true` implique également que [EnableDynamicLoading](#enabledynamicloading) est `true` .</span><span class="sxs-lookup"><span data-stu-id="688df-401">Setting the `EnableComHosting` to `true` also implies that [EnableDynamicLoading](#enabledynamicloading) is `true`.</span></span>

```xml
<PropertyGroup>
  <EnableComHosting>True</EnableComHosting>
</PropertyGroup>
```

<span data-ttu-id="688df-402">Pour plus d’informations, consultez [exposer des composants .net à com](../native-interop/expose-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="688df-402">For more information, see [Expose .NET components to COM](../native-interop/expose-components-to-com.md).</span></span>

### <a name="enabledynamicloading"></a><span data-ttu-id="688df-403">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="688df-403">EnableDynamicLoading</span></span>

<span data-ttu-id="688df-404">La `EnableDynamicLoading` propriété indique qu’un assembly est un composant chargé dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="688df-404">The `EnableDynamicLoading` property indicates that an assembly is a dynamically loaded component.</span></span> <span data-ttu-id="688df-405">Le composant peut être une bibliothèque [com](/windows/win32/com/the-component-object-model) ou une bibliothèque non-com qui peut être [utilisée à partir d’un hôte natif](../tutorials/netcore-hosting.md).</span><span class="sxs-lookup"><span data-stu-id="688df-405">The component could be a [COM library](/windows/win32/com/the-component-object-model) or a non-COM library that can be [used from a native host](../tutorials/netcore-hosting.md).</span></span> <span data-ttu-id="688df-406">L’affectation de la valeur à cette propriété `true` a les effets suivants :</span><span class="sxs-lookup"><span data-stu-id="688df-406">Setting this property to `true` has the following effects:</span></span>

- <span data-ttu-id="688df-407">Un *.runtimeconfig.jssur le* fichier est généré.</span><span class="sxs-lookup"><span data-stu-id="688df-407">A *.runtimeconfig.json* file is generated.</span></span>
- <span data-ttu-id="688df-408">La [restauration par progression](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) est définie sur `LatestMinor` .</span><span class="sxs-lookup"><span data-stu-id="688df-408">[Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) is set to `LatestMinor`.</span></span>
- <span data-ttu-id="688df-409">Les références NuGet sont copiées localement.</span><span class="sxs-lookup"><span data-stu-id="688df-409">NuGet references are copied locally.</span></span>

```xml
<PropertyGroup>
  <EnableDynamicLoading>true</EnableDynamicLoading>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="688df-410">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="688df-410">See also</span></span>

- [<span data-ttu-id="688df-411">Référence du schéma MSBuild</span><span class="sxs-lookup"><span data-stu-id="688df-411">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="688df-412">Propriétés MSBuild communes</span><span class="sxs-lookup"><span data-stu-id="688df-412">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="688df-413">Propriétés MSBuild pour le Pack NuGet</span><span class="sxs-lookup"><span data-stu-id="688df-413">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="688df-414">Propriétés MSBuild pour la restauration NuGet</span><span class="sxs-lookup"><span data-stu-id="688df-414">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="688df-415">Personnaliser une build</span><span class="sxs-lookup"><span data-stu-id="688df-415">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
