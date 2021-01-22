---
title: Propriétés MSBuild pour Microsoft. NET. Sdk
description: Référence pour les propriétés et les éléments MSBuild compris par le kit de développement logiciel (SDK) .NET.
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: 21bbe46cf60540c01344cc8fcb82c62ff0fbbee5
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98692707"
---
# <a name="msbuild-reference-for-net-sdk-projects"></a><span data-ttu-id="9b53d-103">Référence MSBuild pour les projets SDK .NET</span><span class="sxs-lookup"><span data-stu-id="9b53d-103">MSBuild reference for .NET SDK projects</span></span>

<span data-ttu-id="9b53d-104">Cette page est une référence pour les propriétés et les éléments MSBuild que vous pouvez utiliser pour configurer des projets .NET.</span><span class="sxs-lookup"><span data-stu-id="9b53d-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET projects.</span></span>

> [!NOTE]
> <span data-ttu-id="9b53d-105">Cette page est un travail en cours et ne répertorie pas toutes les propriétés MSBuild utiles pour le kit de développement logiciel (SDK) .NET.</span><span class="sxs-lookup"><span data-stu-id="9b53d-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET SDK.</span></span> <span data-ttu-id="9b53d-106">Pour obtenir la liste des propriétés MSBuild courantes, consultez [propriétés MSBuild communes](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="9b53d-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="9b53d-107">Propriétés du Framework</span><span class="sxs-lookup"><span data-stu-id="9b53d-107">Framework properties</span></span>

- [<span data-ttu-id="9b53d-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="9b53d-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="9b53d-109">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="9b53d-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="9b53d-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="9b53d-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="9b53d-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="9b53d-111">TargetFramework</span></span>

<span data-ttu-id="9b53d-112">La `TargetFramework` propriété spécifie la version cible de .NET Framework pour l’application.</span><span class="sxs-lookup"><span data-stu-id="9b53d-112">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="9b53d-113">Pour obtenir la liste des monikers du Framework cible valides, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="9b53d-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="9b53d-114">Pour plus d’informations, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="9b53d-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="9b53d-115">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="9b53d-115">TargetFrameworks</span></span>

<span data-ttu-id="9b53d-116">Utilisez la `TargetFrameworks` propriété lorsque vous souhaitez que votre application cible plusieurs plateformes.</span><span class="sxs-lookup"><span data-stu-id="9b53d-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="9b53d-117">Pour obtenir la liste des monikers du Framework cible valides, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="9b53d-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

> [!NOTE]
> <span data-ttu-id="9b53d-118">Cette propriété est ignorée si `TargetFramework` (singulier) est spécifié.</span><span class="sxs-lookup"><span data-stu-id="9b53d-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="9b53d-119">Pour plus d’informations, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="9b53d-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="9b53d-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="9b53d-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="9b53d-121">Cette propriété s’applique uniquement aux projets qui utilisent `netstandard1.x` .</span><span class="sxs-lookup"><span data-stu-id="9b53d-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="9b53d-122">Elle ne s’applique pas aux projets qui utilisent `netstandard2.x` .</span><span class="sxs-lookup"><span data-stu-id="9b53d-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="9b53d-123">Utilisez la `NetStandardImplicitPackageVersion` propriété lorsque vous souhaitez spécifier une version de Framework inférieure à la version de l’ensemble de packages.</span><span class="sxs-lookup"><span data-stu-id="9b53d-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="9b53d-124">Le fichier projet dans l’exemple suivant cible, `netstandard1.3` mais utilise la version 1.6.0 de `NETStandard.Library` .</span><span class="sxs-lookup"><span data-stu-id="9b53d-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="9b53d-125">Propriétés du package</span><span class="sxs-lookup"><span data-stu-id="9b53d-125">Package properties</span></span>

<span data-ttu-id="9b53d-126">Vous pouvez spécifier des propriétés telles que `PackageId` , `PackageVersion` ,, `PackageIcon` `Title` et `Description` pour décrire le package qui est créé à partir de votre projet.</span><span class="sxs-lookup"><span data-stu-id="9b53d-126">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="9b53d-127">Pour plus d’informations sur ces propriétés et d’autres, consultez [package Target](/nuget/reference/msbuild-targets#pack-target).</span><span class="sxs-lookup"><span data-stu-id="9b53d-127">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-items-and-metadata"></a><span data-ttu-id="9b53d-128">Publier les propriétés, les éléments et les métadonnées</span><span class="sxs-lookup"><span data-stu-id="9b53d-128">Publish properties, items, and metadata</span></span>

- [<span data-ttu-id="9b53d-129">AppendRuntimeIdentifierToOutputPath</span><span class="sxs-lookup"><span data-stu-id="9b53d-129">AppendRuntimeIdentifierToOutputPath</span></span>](#appendruntimeidentifiertooutputpath)
- [<span data-ttu-id="9b53d-130">AppendTargetFrameworkToOutputPath</span><span class="sxs-lookup"><span data-stu-id="9b53d-130">AppendTargetFrameworkToOutputPath</span></span>](#appendtargetframeworktooutputpath)
- [<span data-ttu-id="9b53d-131">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="9b53d-131">CopyLocalLockFileAssemblies</span></span>](#copylocallockfileassemblies)
- [<span data-ttu-id="9b53d-132">CopyToPublishDirectory</span><span class="sxs-lookup"><span data-stu-id="9b53d-132">CopyToPublishDirectory</span></span>](#copytopublishdirectory)
- [<span data-ttu-id="9b53d-133">Ressources</span><span class="sxs-lookup"><span data-stu-id="9b53d-133">LinkBase</span></span>](#linkbase)
- [<span data-ttu-id="9b53d-134">PreserveCompilationContext</span><span class="sxs-lookup"><span data-stu-id="9b53d-134">PreserveCompilationContext</span></span>](#preservecompilationcontext)
- [<span data-ttu-id="9b53d-135">PreserveCompilationReferences</span><span class="sxs-lookup"><span data-stu-id="9b53d-135">PreserveCompilationReferences</span></span>](#preservecompilationreferences)
- [<span data-ttu-id="9b53d-136">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="9b53d-136">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="9b53d-137">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="9b53d-137">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="9b53d-138">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="9b53d-138">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="9b53d-139">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="9b53d-139">UseAppHost</span></span>](#useapphost)

### <a name="copytopublishdirectory"></a><span data-ttu-id="9b53d-140">CopyToPublishDirectory</span><span class="sxs-lookup"><span data-stu-id="9b53d-140">CopyToPublishDirectory</span></span>

<span data-ttu-id="9b53d-141">Les `CopyToPublishDirectory` métadonnées d’un élément MSBuild contrôlent le moment où l’élément est copié dans le répertoire de publication.</span><span class="sxs-lookup"><span data-stu-id="9b53d-141">The `CopyToPublishDirectory` metadata on an MSBuild item controls when the item is copied to the publish directory.</span></span> <span data-ttu-id="9b53d-142">Les valeurs autorisées sont `PreserveNewest` , qui copient uniquement l’élément s’il a changé, `Always` , qui copie toujours l’élément, et `Never` , qui ne copie jamais l’élément.</span><span class="sxs-lookup"><span data-stu-id="9b53d-142">Allowable values are `PreserveNewest`, which only copies the item if it has changed, `Always`, which always copies the item, and `Never`, which never copies the item.</span></span> <span data-ttu-id="9b53d-143">Du point de vue des performances, `PreserveNewest` est préférable, car il permet une génération incrémentielle.</span><span class="sxs-lookup"><span data-stu-id="9b53d-143">From a performance standpoint, `PreserveNewest` is preferable because it enables an incremental build.</span></span>

```xml
<ItemGroup>
  <None Update="appsettings.Development.json" CopyToOutputDirectory="PreserveNewest" CopyToPublishDirectory="PreserveNewest" />
</ItemGroup>
```

### <a name="linkbase"></a><span data-ttu-id="9b53d-144">Ressources</span><span class="sxs-lookup"><span data-stu-id="9b53d-144">LinkBase</span></span>

<span data-ttu-id="9b53d-145">Pour un élément qui se trouve en dehors du répertoire du projet et de ses sous-répertoires, la cible de publication utilise les [métadonnées de lien](/visualstudio/msbuild/common-msbuild-item-metadata) de l’élément pour déterminer où copier l’élément.</span><span class="sxs-lookup"><span data-stu-id="9b53d-145">For an item that's outside of the project directory and its subdirectories, the publish target uses the item's [Link metadata](/visualstudio/msbuild/common-msbuild-item-metadata) to determine where to copy the item to.</span></span> <span data-ttu-id="9b53d-146">`Link` détermine également la manière dont les éléments en dehors de l’arborescence du projet s’affichent dans la fenêtre Explorateur de solutions de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9b53d-146">`Link` also determines how items outside of the project tree are displayed in the Solution Explorer window of Visual Studio.</span></span>

<span data-ttu-id="9b53d-147">Si `Link` n’est pas spécifié pour un élément qui se trouve en dehors du cône du projet, la valeur par défaut est `%(LinkBase)\%(RecursiveDir)%(Filename)%(Extension)` .</span><span class="sxs-lookup"><span data-stu-id="9b53d-147">If `Link` is not specified for an item that's outside of the project cone, it defaults to `%(LinkBase)\%(RecursiveDir)%(Filename)%(Extension)`.</span></span> <span data-ttu-id="9b53d-148">`LinkBase` vous permet de spécifier un dossier de base raisonnable pour les éléments en dehors du cône du projet.</span><span class="sxs-lookup"><span data-stu-id="9b53d-148">`LinkBase` lets you specify a sensible base folder for items outside of the project cone.</span></span> <span data-ttu-id="9b53d-149">L’arborescence des dossiers sous le dossier de base est conservée via `RecursiveDir` .</span><span class="sxs-lookup"><span data-stu-id="9b53d-149">The folder hierarchy under the base folder is preserved via `RecursiveDir`.</span></span> <span data-ttu-id="9b53d-150">Si `LinkBase` n’est pas spécifié, il est omis du `Link` chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="9b53d-150">If `LinkBase` is not specified, it's omitted from the `Link` path.</span></span>

```xml
<ItemGroup>
  <Content Include="..\Extras\**\*.cs" LinkBase="Shared"/>
</ItemGroup>
```

<span data-ttu-id="9b53d-151">L’illustration suivante montre comment un fichier inclus via l’élément précédent `Include` glob s’affiche dans Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="9b53d-151">The following image shows how a file that's included via the previous item `Include` glob displays in Solution Explorer.</span></span>

:::image type="content" source="media/solution-explorer-linkbase.png" alt-text="Explorateur de solutions présentant l’élément avec les métadonnées de lienet.":::

### <a name="appendtargetframeworktooutputpath"></a><span data-ttu-id="9b53d-153">AppendTargetFrameworkToOutputPath</span><span class="sxs-lookup"><span data-stu-id="9b53d-153">AppendTargetFrameworkToOutputPath</span></span>

<span data-ttu-id="9b53d-154">La `AppendTargetFrameworkToOutputPath` propriété détermine si le [moniker du Framework cible (TFM)](../../standard/frameworks.md) est ajouté au chemin de sortie (qui est défini par [OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)).</span><span class="sxs-lookup"><span data-stu-id="9b53d-154">The `AppendTargetFrameworkToOutputPath` property controls whether the [target framework moniker (TFM)](../../standard/frameworks.md) is appended to the output path (which is defined by [OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)).</span></span> <span data-ttu-id="9b53d-155">Le kit de développement logiciel (SDK) .NET ajoute automatiquement le Framework cible et, le cas échéant, l’identificateur du Runtime au chemin de sortie.</span><span class="sxs-lookup"><span data-stu-id="9b53d-155">The .NET SDK automatically appends the target framework and, if present, the runtime identifier to the output path.</span></span> <span data-ttu-id="9b53d-156">L’affectation de `AppendTargetFrameworkToOutputPath` la valeur à `false` empêche le TFM d’être ajouté au chemin de sortie.</span><span class="sxs-lookup"><span data-stu-id="9b53d-156">Setting `AppendTargetFrameworkToOutputPath` to `false` prevents the TFM from being appended to the output path.</span></span> <span data-ttu-id="9b53d-157">Toutefois, si le chemin de sortie n’est pas TFM, plusieurs artefacts de build peuvent se remplacer mutuellement.</span><span class="sxs-lookup"><span data-stu-id="9b53d-157">However, without the TFM in the output path, multiple build artifacts may overwrite each other.</span></span>

<span data-ttu-id="9b53d-158">Par exemple, pour une application .NET 5,0, le chemin de sortie passe de `bin\Debug\net5.0` à `bin\Debug` avec le paramètre suivant :</span><span class="sxs-lookup"><span data-stu-id="9b53d-158">For example, for a .NET 5.0 app, the output path changes from `bin\Debug\net5.0` to `bin\Debug` with the following setting:</span></span>

```xml
<PropertyGroup>
  <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
</PropertyGroup>
```

### <a name="appendruntimeidentifiertooutputpath"></a><span data-ttu-id="9b53d-159">AppendRuntimeIdentifierToOutputPath</span><span class="sxs-lookup"><span data-stu-id="9b53d-159">AppendRuntimeIdentifierToOutputPath</span></span>

<span data-ttu-id="9b53d-160">La `AppendRuntimeIdentifierToOutputPath` propriété détermine si l' [identificateur de Runtime (RID)](../rid-catalog.md) est ajouté au chemin de sortie.</span><span class="sxs-lookup"><span data-stu-id="9b53d-160">The `AppendRuntimeIdentifierToOutputPath` property controls whether the [runtime identifier (RID)](../rid-catalog.md) is appended to the output path.</span></span> <span data-ttu-id="9b53d-161">Le kit de développement logiciel (SDK) .NET ajoute automatiquement le Framework cible et, le cas échéant, l’identificateur du Runtime au chemin de sortie.</span><span class="sxs-lookup"><span data-stu-id="9b53d-161">The .NET SDK automatically appends the target framework and, if present, the runtime identifier to the output path.</span></span> <span data-ttu-id="9b53d-162">`AppendRuntimeIdentifierToOutputPath`La définition de `false` la valeur empêche l’ajout du RID au chemin de sortie.</span><span class="sxs-lookup"><span data-stu-id="9b53d-162">Setting `AppendRuntimeIdentifierToOutputPath` to `false` prevents the RID from being appended to the output path.</span></span>

<span data-ttu-id="9b53d-163">Par exemple, pour une application .NET 5,0 et un RID `win10-x64` , le chemin de sortie passe de `bin\Debug\net5.0\win10-x64` à `bin\Debug\net5.0` avec le paramètre suivant :</span><span class="sxs-lookup"><span data-stu-id="9b53d-163">For example, for a .NET 5.0 app and an RID of `win10-x64`, the output path changes from `bin\Debug\net5.0\win10-x64` to `bin\Debug\net5.0` with the following setting:</span></span>

```xml
<PropertyGroup>
  <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
</PropertyGroup>
```

### <a name="copylocallockfileassemblies"></a><span data-ttu-id="9b53d-164">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="9b53d-164">CopyLocalLockFileAssemblies</span></span>

<span data-ttu-id="9b53d-165">La `CopyLocalLockFileAssemblies` propriété est utile pour les projets de plug-in qui ont des dépendances sur d’autres bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="9b53d-165">The `CopyLocalLockFileAssemblies` property is useful for plugin projects that have dependencies on other libraries.</span></span> <span data-ttu-id="9b53d-166">Si vous affectez à cette propriété `true` la valeur, toutes les dépendances de package NuGet sont copiées dans le répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="9b53d-166">If you set this property to `true`, any NuGet package dependencies are copied to the output directory.</span></span> <span data-ttu-id="9b53d-167">Cela signifie que vous pouvez utiliser la sortie de `dotnet build` pour exécuter votre plug-in sur n’importe quel ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9b53d-167">That means you can use the output of `dotnet build` to run your plugin on any machine.</span></span>

```xml
<PropertyGroup>
  <CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="9b53d-168">Vous pouvez également utiliser `dotnet publish` pour publier la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="9b53d-168">Alternatively, you can use `dotnet publish` to publish the class library.</span></span> <span data-ttu-id="9b53d-169">Pour plus d’informations, consultez [dotnet Publish](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="9b53d-169">For more information, see [dotnet publish](../tools/dotnet-publish.md).</span></span>

### <a name="preservecompilationcontext"></a><span data-ttu-id="9b53d-170">PreserveCompilationContext</span><span class="sxs-lookup"><span data-stu-id="9b53d-170">PreserveCompilationContext</span></span>

<span data-ttu-id="9b53d-171">La `PreserveCompilationContext` propriété permet à une application générée ou publiée de compiler davantage de code au moment de l’exécution en utilisant les mêmes paramètres que ceux utilisés au moment de la génération.</span><span class="sxs-lookup"><span data-stu-id="9b53d-171">The `PreserveCompilationContext` property allows a built or published application to compile more code at run time using the same settings that were used at build time.</span></span> <span data-ttu-id="9b53d-172">Les assemblys référencés au moment de la génération sont copiés dans le sous-répertoire *ref* du répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="9b53d-172">The assemblies referenced at build time will be copied into the *ref* subdirectory of the output directory.</span></span> <span data-ttu-id="9b53d-173">Les noms des assemblys de référence sont stockés dans l'.deps.jsde l’application *sur* le fichier, ainsi que les options passées au compilateur.</span><span class="sxs-lookup"><span data-stu-id="9b53d-173">The names of the reference assemblies are stored in the application's *.deps.json* file along with the options passed to the compiler.</span></span> <span data-ttu-id="9b53d-174">Vous pouvez récupérer ces informations à l’aide des <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompileLibraries?displayProperty=nameWithType> <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompilationOptions?displayProperty=nameWithType> Propriétés et.</span><span class="sxs-lookup"><span data-stu-id="9b53d-174">You can retrieve this information using the <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompileLibraries?displayProperty=nameWithType> and <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompilationOptions?displayProperty=nameWithType> properties.</span></span>

<span data-ttu-id="9b53d-175">Cette fonctionnalité est principalement utilisée en interne par ASP.NET Core MVC et les pages Razor pour prendre en charge la compilation des fichiers Razor au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="9b53d-175">This functionality is mostly used internally by ASP.NET Core MVC and Razor pages to support run-time compilation of Razor files.</span></span>

```xml
<PropertyGroup>
  <PreserveCompilationContext>true</PreserveCompilationContext>
</PropertyGroup>
```

### <a name="preservecompilationreferences"></a><span data-ttu-id="9b53d-176">PreserveCompilationReferences</span><span class="sxs-lookup"><span data-stu-id="9b53d-176">PreserveCompilationReferences</span></span>

<span data-ttu-id="9b53d-177">La `PreserveCompilationReferences` propriété est semblable à la propriété [PreserveCompilationContext](#preservecompilationcontext) , à ceci près qu’elle copie uniquement les assemblys référencés dans le répertoire publish, et non le *.deps.jsdans* le fichier.</span><span class="sxs-lookup"><span data-stu-id="9b53d-177">The `PreserveCompilationReferences` property is similar to the [PreserveCompilationContext](#preservecompilationcontext) property, except that it only copies the referenced assemblies to the publish directory, and not the *.deps.json* file.</span></span>

```xml
<PropertyGroup>
  <PreserveCompilationReferences>true</PreserveCompilationReferences>
</PropertyGroup>
```

<span data-ttu-id="9b53d-178">Pour plus d’informations, consultez [Propriétés du kit de développement logiciel (SDK) Razor](/aspnet/core/razor-pages/sdk#properties).</span><span class="sxs-lookup"><span data-stu-id="9b53d-178">For more information, see [Razor SDK properties](/aspnet/core/razor-pages/sdk#properties).</span></span>

### <a name="runtimeidentifier"></a><span data-ttu-id="9b53d-179">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="9b53d-179">RuntimeIdentifier</span></span>

<span data-ttu-id="9b53d-180">La `RuntimeIdentifier` propriété vous permet de spécifier un [identificateur de Runtime unique (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="9b53d-180">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="9b53d-181">Le RID permet de publier un déploiement autonome.</span><span class="sxs-lookup"><span data-stu-id="9b53d-181">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="9b53d-182">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="9b53d-182">RuntimeIdentifiers</span></span>

<span data-ttu-id="9b53d-183">La `RuntimeIdentifiers` propriété vous permet de spécifier une liste délimitée par des points-virgules des [identificateurs de Runtime (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="9b53d-183">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="9b53d-184">Utilisez cette propriété si vous devez publier pour plusieurs runtimes.</span><span class="sxs-lookup"><span data-stu-id="9b53d-184">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="9b53d-185">`RuntimeIdentifiers` est utilisé au moment de la restauration pour s’assurer que les ressources appropriées sont dans le graphique.</span><span class="sxs-lookup"><span data-stu-id="9b53d-185">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="9b53d-186">`RuntimeIdentifier` (singulier) peut fournir des builds plus rapides quand un seul Runtime est requis.</span><span class="sxs-lookup"><span data-stu-id="9b53d-186">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="9b53d-187">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="9b53d-187">TrimmerRootAssembly</span></span>

<span data-ttu-id="9b53d-188">L' `TrimmerRootAssembly` élément vous permet d’exclure un assembly du [*découpage*](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="9b53d-188">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="9b53d-189">Le découpage est le processus qui consiste à supprimer des parties inutilisées du runtime d’une application empaquetée.</span><span class="sxs-lookup"><span data-stu-id="9b53d-189">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="9b53d-190">Dans certains cas, la suppression peut supprimer incorrectement les références requises.</span><span class="sxs-lookup"><span data-stu-id="9b53d-190">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="9b53d-191">Le code XML suivant exclut `System.Security` de la suppression de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="9b53d-191">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="9b53d-192">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="9b53d-192">UseAppHost</span></span>

<span data-ttu-id="9b53d-193">La `UseAppHost` propriété contrôle si un exécutable natif est créé ou non pour un déploiement.</span><span class="sxs-lookup"><span data-stu-id="9b53d-193">The `UseAppHost` property controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="9b53d-194">Un exécutable natif est requis pour les déploiements autonomes.</span><span class="sxs-lookup"><span data-stu-id="9b53d-194">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="9b53d-195">Dans .NET Core 3,0 et versions ultérieures, un fichier exécutable dépendant du Framework est créé par défaut.</span><span class="sxs-lookup"><span data-stu-id="9b53d-195">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="9b53d-196">Affectez à la propriété la valeur `UseAppHost` `false` pour désactiver la génération de l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="9b53d-196">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="9b53d-197">Pour plus d’informations sur le déploiement, consultez [déploiement d’applications .net](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="9b53d-197">For more information about deployment, see [.NET application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="9b53d-198">Propriétés de compilation</span><span class="sxs-lookup"><span data-stu-id="9b53d-198">Compile properties</span></span>

- [<span data-ttu-id="9b53d-199">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="9b53d-199">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="9b53d-200">LangVersion</span><span class="sxs-lookup"><span data-stu-id="9b53d-200">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="9b53d-201">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="9b53d-201">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="9b53d-202">La `EmbeddedResourceUseDependentUponConvention` propriété définit si les noms des fichiers manifestes de ressources sont générés à partir des informations de type dans les fichiers sources qui sont colocalisés avec les fichiers de ressources.</span><span class="sxs-lookup"><span data-stu-id="9b53d-202">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="9b53d-203">Par exemple, si *Form1. resx* se trouve dans le même dossier que *Form1.cs* et que `EmbeddedResourceUseDependentUponConvention` a la valeur `true` , le fichier *. Resources* généré prend son nom dans le premier type défini dans *Form1.cs*.</span><span class="sxs-lookup"><span data-stu-id="9b53d-203">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="9b53d-204">Par exemple, si `MyNamespace.Form1` est le premier type défini dans *Form1.cs*, le nom de fichier généré est *MyNamespace. Form1. Resources*.</span><span class="sxs-lookup"><span data-stu-id="9b53d-204">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="9b53d-205">Si `LogicalName` `ManifestResourceName` `DependentUpon` les métadonnées, ou sont spécifiées pour un `EmbeddedResource` élément, le nom de fichier manifeste généré pour ce fichier de ressources est basé sur ces métadonnées à la place.</span><span class="sxs-lookup"><span data-stu-id="9b53d-205">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="9b53d-206">Par défaut, dans un nouveau projet .NET, cette propriété a la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="9b53d-206">By default, in a new .NET project, this property is set to `true`.</span></span> <span data-ttu-id="9b53d-207">Si la valeur `false` est définie sur, et si aucune `LogicalName` `ManifestResourceName` `DependentUpon` métadonnée n’est spécifiée pour l' `EmbeddedResource` élément dans le fichier projet, le nom du fichier manifeste de la ressource est basé sur l’espace de noms racine du projet et le chemin d’accès relatif au fichier *. resx* .</span><span class="sxs-lookup"><span data-stu-id="9b53d-207">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="9b53d-208">Pour plus d’informations, consultez [Comment les fichiers manifestes de ressources sont nommés](../resources/manifest-file-names.md).</span><span class="sxs-lookup"><span data-stu-id="9b53d-208">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="9b53d-209">LangVersion</span><span class="sxs-lookup"><span data-stu-id="9b53d-209">LangVersion</span></span>

<span data-ttu-id="9b53d-210">La `LangVersion` propriété vous permet de spécifier une version du langage de programmation spécifique.</span><span class="sxs-lookup"><span data-stu-id="9b53d-210">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="9b53d-211">Par exemple, si vous souhaitez accéder aux fonctionnalités de la version préliminaire de C#, affectez à la valeur `LangVersion` `preview` .</span><span class="sxs-lookup"><span data-stu-id="9b53d-211">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="9b53d-212">Pour plus d’informations, consultez contrôle de [version du langage C#](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="9b53d-212">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="default-item-inclusion-properties"></a><span data-ttu-id="9b53d-213">Propriétés d’inclusion d’élément par défaut</span><span class="sxs-lookup"><span data-stu-id="9b53d-213">Default item inclusion properties</span></span>

- [<span data-ttu-id="9b53d-214">DefaultExcludesInProjectFolder</span><span class="sxs-lookup"><span data-stu-id="9b53d-214">DefaultExcludesInProjectFolder</span></span>](#defaultexcludesinprojectfolder)
- [<span data-ttu-id="9b53d-215">DefaultItemExcludes</span><span class="sxs-lookup"><span data-stu-id="9b53d-215">DefaultItemExcludes</span></span>](#defaultitemexcludes)
- [<span data-ttu-id="9b53d-216">EnableDefaultCompileItems</span><span class="sxs-lookup"><span data-stu-id="9b53d-216">EnableDefaultCompileItems</span></span>](#enabledefaultcompileitems)
- [<span data-ttu-id="9b53d-217">EnableDefaultEmbeddedResourceItems</span><span class="sxs-lookup"><span data-stu-id="9b53d-217">EnableDefaultEmbeddedResourceItems</span></span>](#enabledefaultembeddedresourceitems)
- [<span data-ttu-id="9b53d-218">EnableDefaultItems</span><span class="sxs-lookup"><span data-stu-id="9b53d-218">EnableDefaultItems</span></span>](#enabledefaultitems)
- [<span data-ttu-id="9b53d-219">EnableDefaultNoneItems</span><span class="sxs-lookup"><span data-stu-id="9b53d-219">EnableDefaultNoneItems</span></span>](#enabledefaultnoneitems)

<span data-ttu-id="9b53d-220">Pour plus d’informations, consultez [include et Exclude par défaut](overview.md#default-includes-and-excludes).</span><span class="sxs-lookup"><span data-stu-id="9b53d-220">For more information, see [Default includes and excludes](overview.md#default-includes-and-excludes).</span></span>

### <a name="defaultitemexcludes"></a><span data-ttu-id="9b53d-221">DefaultItemExcludes</span><span class="sxs-lookup"><span data-stu-id="9b53d-221">DefaultItemExcludes</span></span>

<span data-ttu-id="9b53d-222">Utilisez la `DefaultItemExcludes` propriété pour définir les modèles glob pour les fichiers et les dossiers qui doivent être exclus des modèles glob include, Exclude et Remove.</span><span class="sxs-lookup"><span data-stu-id="9b53d-222">Use the `DefaultItemExcludes` property to define glob patterns for files and folders that should be excluded from the include, exclude, and remove globs.</span></span> <span data-ttu-id="9b53d-223">Par défaut, les dossiers *./bin* et *./obj* sont exclus des modèles glob.</span><span class="sxs-lookup"><span data-stu-id="9b53d-223">By default, the *./bin* and *./obj* folders are excluded from the glob patterns.</span></span>

```xml
<PropertyGroup>
  <DefaultItemExcludes>$(DefaultItemExcludes);**/*.myextension</DefaultItemExcludes>
</PropertyGroup>
```

### <a name="defaultexcludesinprojectfolder"></a><span data-ttu-id="9b53d-224">DefaultExcludesInProjectFolder</span><span class="sxs-lookup"><span data-stu-id="9b53d-224">DefaultExcludesInProjectFolder</span></span>

<span data-ttu-id="9b53d-225">Utilisez la `DefaultExcludesInProjectFolder` propriété pour définir les modèles glob pour les fichiers et les dossiers dans le dossier du projet qui doivent être exclus des modèles glob include, Exclude et Remove.</span><span class="sxs-lookup"><span data-stu-id="9b53d-225">Use the `DefaultExcludesInProjectFolder` property to define glob patterns for files and folders in the project folder that should be excluded from the include, exclude, and remove globs.</span></span> <span data-ttu-id="9b53d-226">Par défaut, les dossiers qui commencent par un point ( `.` ), tels que *. git* et *. vs*, sont exclus des modèles glob.</span><span class="sxs-lookup"><span data-stu-id="9b53d-226">By default, folders that start with a period (`.`), such as *.git* and *.vs*, are excluded from the glob patterns.</span></span>

<span data-ttu-id="9b53d-227">Cette propriété est très similaire à la `DefaultItemExcludes` propriété, sauf qu’elle considère uniquement les fichiers et les dossiers dans le dossier du projet.</span><span class="sxs-lookup"><span data-stu-id="9b53d-227">This property is very similar to the `DefaultItemExcludes` property, except that it only considers files and folders in the project folder.</span></span> <span data-ttu-id="9b53d-228">Quand un modèle glob correspondrait involontairement à des éléments en dehors du dossier du projet avec un chemin d’accès relatif, utilisez la propriété à la `DefaultExcludesInProjectFolder` place de la `DefaultItemExcludes` propriété.</span><span class="sxs-lookup"><span data-stu-id="9b53d-228">When a glob pattern would unintentionally match items outside the project folder with a relative path, use the `DefaultExcludesInProjectFolder` property instead of the `DefaultItemExcludes` property.</span></span>

```xml
<PropertyGroup>
  <DefaultExcludesInProjectFolder>$(DefaultExcludesInProjectFolder);**/myprefix*/**</DefaultExcludesInProjectFolder>
</PropertyGroup>
```

### <a name="enabledefaultitems"></a><span data-ttu-id="9b53d-229">EnableDefaultItems</span><span class="sxs-lookup"><span data-stu-id="9b53d-229">EnableDefaultItems</span></span>

<span data-ttu-id="9b53d-230">La `EnableDefaultItems` propriété contrôle si les éléments de compilation, les éléments de ressources incorporés et les `None` éléments sont implicitement inclus dans le projet.</span><span class="sxs-lookup"><span data-stu-id="9b53d-230">The `EnableDefaultItems` property controls whether compile items, embedded resource items, and `None` items are implicitly included in the project.</span></span> <span data-ttu-id="9b53d-231">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="9b53d-231">The default value is `true`.</span></span> <span data-ttu-id="9b53d-232">Affectez à la propriété la valeur `EnableDefaultItems` `false` pour désactiver toute inclusion de fichier implicite.</span><span class="sxs-lookup"><span data-stu-id="9b53d-232">Set the `EnableDefaultItems` property to `false` to disable all implicit file inclusion.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="enabledefaultcompileitems"></a><span data-ttu-id="9b53d-233">EnableDefaultCompileItems</span><span class="sxs-lookup"><span data-stu-id="9b53d-233">EnableDefaultCompileItems</span></span>

<span data-ttu-id="9b53d-234">La `EnableDefaultCompileItems` propriété contrôle si les éléments de compilation sont inclus implicitement dans le projet.</span><span class="sxs-lookup"><span data-stu-id="9b53d-234">The `EnableDefaultCompileItems` property controls whether compile items are implicitly included in the project.</span></span> <span data-ttu-id="9b53d-235">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="9b53d-235">The default value is `true`.</span></span> <span data-ttu-id="9b53d-236">Affectez à la propriété la valeur `EnableDefaultCompileItems` `false` pour désactiver l’inclusion implicite des fichiers \*. cs et d’autres extensions de langage.</span><span class="sxs-lookup"><span data-stu-id="9b53d-236">Set the `EnableDefaultCompileItems` property to `false` to disable implicit inclusion of \*.cs and other language-extension files.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

### <a name="enabledefaultembeddedresourceitems"></a><span data-ttu-id="9b53d-237">EnableDefaultEmbeddedResourceItems</span><span class="sxs-lookup"><span data-stu-id="9b53d-237">EnableDefaultEmbeddedResourceItems</span></span>

<span data-ttu-id="9b53d-238">La `EnableDefaultEmbeddedResourceItems` propriété contrôle si les éléments de ressources incorporés sont implicitement inclus dans le projet.</span><span class="sxs-lookup"><span data-stu-id="9b53d-238">The `EnableDefaultEmbeddedResourceItems` property controls whether embedded resource items are implicitly included in the project.</span></span> <span data-ttu-id="9b53d-239">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="9b53d-239">The default value is `true`.</span></span> <span data-ttu-id="9b53d-240">Affectez à la propriété la valeur `EnableDefaultEmbeddedResourceItems` `false` pour désactiver l’inclusion implicite des fichiers de ressources incorporés.</span><span class="sxs-lookup"><span data-stu-id="9b53d-240">Set the `EnableDefaultEmbeddedResourceItems` property to `false` to disable implicit inclusion of embedded resource files.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
</PropertyGroup>
```

### <a name="enabledefaultnoneitems"></a><span data-ttu-id="9b53d-241">EnableDefaultNoneItems</span><span class="sxs-lookup"><span data-stu-id="9b53d-241">EnableDefaultNoneItems</span></span>

<span data-ttu-id="9b53d-242">La `EnableDefaultNoneItems` propriété contrôle si les `None` éléments (fichiers qui n’ont pas de rôle dans le processus de génération) sont implicitement inclus dans le projet.</span><span class="sxs-lookup"><span data-stu-id="9b53d-242">The `EnableDefaultNoneItems` property controls whether `None` items (files that have no role in the build process) are implicitly included in the project.</span></span> <span data-ttu-id="9b53d-243">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="9b53d-243">The default value is `true`.</span></span> <span data-ttu-id="9b53d-244">Affectez à la propriété la valeur `EnableDefaultNoneItems` `false` pour désactiver l’inclusion implicite d' `None` éléments.</span><span class="sxs-lookup"><span data-stu-id="9b53d-244">Set the `EnableDefaultNoneItems` property to `false` to disable implicit inclusion of `None` items.</span></span>

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

## <a name="code-analysis-properties"></a><span data-ttu-id="9b53d-245">Propriétés de l’analyse du code</span><span class="sxs-lookup"><span data-stu-id="9b53d-245">Code analysis properties</span></span>

- [<span data-ttu-id="9b53d-246">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="9b53d-246">AnalysisLevel</span></span>](#analysislevel)
- [<span data-ttu-id="9b53d-247">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="9b53d-247">AnalysisMode</span></span>](#analysismode)
- [<span data-ttu-id="9b53d-248">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="9b53d-248">CodeAnalysisTreatWarningsAsErrors</span></span>](#codeanalysistreatwarningsaserrors)
- [<span data-ttu-id="9b53d-249">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="9b53d-249">EnableNETAnalyzers</span></span>](#enablenetanalyzers)
- [<span data-ttu-id="9b53d-250">EnforceCodeStyleInBuild</span><span class="sxs-lookup"><span data-stu-id="9b53d-250">EnforceCodeStyleInBuild</span></span>](#enforcecodestyleinbuild)

### <a name="analysislevel"></a><span data-ttu-id="9b53d-251">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="9b53d-251">AnalysisLevel</span></span>

<span data-ttu-id="9b53d-252">La `AnalysisLevel` propriété vous permet de spécifier un niveau d’analyse du code.</span><span class="sxs-lookup"><span data-stu-id="9b53d-252">The `AnalysisLevel` property lets you specify a code analysis level.</span></span> <span data-ttu-id="9b53d-253">Par exemple, si vous souhaitez accéder à l’aperçu des analyseurs de code, affectez à la valeur `AnalysisLevel` `preview` .</span><span class="sxs-lookup"><span data-stu-id="9b53d-253">For example, if you want access to preview code analyzers, set `AnalysisLevel` to `preview`.</span></span> <span data-ttu-id="9b53d-254">La valeur par défaut est `latest`.</span><span class="sxs-lookup"><span data-stu-id="9b53d-254">The default value is `latest`.</span></span>

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

<span data-ttu-id="9b53d-255">Le tableau suivant présente les options disponibles.</span><span class="sxs-lookup"><span data-stu-id="9b53d-255">The following table shows the available options.</span></span>

| <span data-ttu-id="9b53d-256">Valeur</span><span class="sxs-lookup"><span data-stu-id="9b53d-256">Value</span></span> | <span data-ttu-id="9b53d-257">Signification</span><span class="sxs-lookup"><span data-stu-id="9b53d-257">Meaning</span></span> |
|-|-|
| `latest` | <span data-ttu-id="9b53d-258">Les derniers analyseurs de code qui ont été publiés sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="9b53d-258">The latest code analyzers that have been released are used.</span></span> <span data-ttu-id="9b53d-259">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="9b53d-259">This is the default.</span></span> |
| `preview` | <span data-ttu-id="9b53d-260">Les derniers analyseurs de code sont utilisés, même s’ils sont en version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="9b53d-260">The latest code analyzers are used, even if they are in preview.</span></span> |
| `5.0` | <span data-ttu-id="9b53d-261">L’ensemble de règles activé pour la version .NET 5,0 est utilisé, même si des règles plus récentes sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="9b53d-261">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |
| `5` | <span data-ttu-id="9b53d-262">L’ensemble de règles activé pour la version .NET 5,0 est utilisé, même si des règles plus récentes sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="9b53d-262">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |

### <a name="analysismode"></a><span data-ttu-id="9b53d-263">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="9b53d-263">AnalysisMode</span></span>

<span data-ttu-id="9b53d-264">À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET est fourni avec toutes les [règles de qualité du code « ca »](../../fundamentals/code-analysis/quality-rules/index.md).</span><span class="sxs-lookup"><span data-stu-id="9b53d-264">Starting with .NET 5.0, the .NET SDK ships with all of the ["CA" code quality rules](../../fundamentals/code-analysis/quality-rules/index.md).</span></span> <span data-ttu-id="9b53d-265">Par défaut, seules [certaines règles sont activées](../../fundamentals/code-analysis/overview.md#enabled-rules) en tant qu’avertissements de génération.</span><span class="sxs-lookup"><span data-stu-id="9b53d-265">By default, only [some rules are enabled](../../fundamentals/code-analysis/overview.md#enabled-rules) as build warnings.</span></span> <span data-ttu-id="9b53d-266">La `AnalysisMode` propriété vous permet de personnaliser l’ensemble des règles qui sont activées par défaut.</span><span class="sxs-lookup"><span data-stu-id="9b53d-266">The `AnalysisMode` property lets you customize the set of rules that are enabled by default.</span></span> <span data-ttu-id="9b53d-267">Vous pouvez basculer vers un mode d’analyse plus agressif ou un mode d’analyse plus prudent (abonnement).</span><span class="sxs-lookup"><span data-stu-id="9b53d-267">You can either switch to a more aggressive (opt-out) analysis mode or a more conservative (opt-in) analysis mode.</span></span> <span data-ttu-id="9b53d-268">Par exemple, si vous souhaitez activer toutes les règles par défaut en tant qu’avertissements de build, affectez la valeur à `AllEnabledByDefault` .</span><span class="sxs-lookup"><span data-stu-id="9b53d-268">For example, if you want to enable all rules by default as build warnings, set the value to `AllEnabledByDefault`.</span></span>

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
</PropertyGroup>
```

<span data-ttu-id="9b53d-269">Le tableau suivant présente les options disponibles.</span><span class="sxs-lookup"><span data-stu-id="9b53d-269">The following table shows the available options.</span></span>

| <span data-ttu-id="9b53d-270">Valeur</span><span class="sxs-lookup"><span data-stu-id="9b53d-270">Value</span></span> | <span data-ttu-id="9b53d-271">Signification</span><span class="sxs-lookup"><span data-stu-id="9b53d-271">Meaning</span></span> |
|-|-|
| `Default` | <span data-ttu-id="9b53d-272">Mode par défaut, où certaines règles sont activées en tant qu’avertissements de build, certaines règles sont activées en tant que suggestions de l’IDE Visual Studio, et le reste est désactivé.</span><span class="sxs-lookup"><span data-stu-id="9b53d-272">Default mode, where certain rules are enabled as build warnings, certain rules are enabled as Visual Studio IDE suggestions, and the remainder are disabled.</span></span> |
| `AllEnabledByDefault` | <span data-ttu-id="9b53d-273">Mode agressif ou opt-out, où toutes les règles sont activées par défaut en tant qu’avertissements de génération.</span><span class="sxs-lookup"><span data-stu-id="9b53d-273">Aggressive or opt-out mode, where all rules are enabled by default as build warnings.</span></span> <span data-ttu-id="9b53d-274">Vous pouvez [choisir](../../fundamentals/code-analysis/configuration-options.md) de désactiver les règles individuelles de manière sélective pour les désactiver.</span><span class="sxs-lookup"><span data-stu-id="9b53d-274">You can selectively [opt out](../../fundamentals/code-analysis/configuration-options.md) of individual rules to disable them.</span></span> |
| `AllDisabledByDefault` | <span data-ttu-id="9b53d-275">Mode conservateur ou opt-in, où toutes les règles sont désactivées par défaut.</span><span class="sxs-lookup"><span data-stu-id="9b53d-275">Conservative or opt-in mode, where all rules are disabled by default.</span></span> <span data-ttu-id="9b53d-276">Vous pouvez [choisir](../../fundamentals/code-analysis/configuration-options.md) des règles individuelles pour les activer.</span><span class="sxs-lookup"><span data-stu-id="9b53d-276">You can selectively [opt into](../../fundamentals/code-analysis/configuration-options.md) individual rules to enable them.</span></span> |

### <a name="codeanalysistreatwarningsaserrors"></a><span data-ttu-id="9b53d-277">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="9b53d-277">CodeAnalysisTreatWarningsAsErrors</span></span>

<span data-ttu-id="9b53d-278">La `CodeAnalysisTreatWarningsAsErrors` propriété vous permet de configurer si les avertissements d’analyse de la qualité du code (CAXXXX) doivent être traités comme des avertissements et rompre la génération.</span><span class="sxs-lookup"><span data-stu-id="9b53d-278">The `CodeAnalysisTreatWarningsAsErrors` property lets you configure whether code quality analysis warnings (CAxxxx) should be treated as warnings and break the build.</span></span> <span data-ttu-id="9b53d-279">Si vous utilisez l' `-warnaserror` indicateur lorsque vous générez vos projets, les avertissements de l’analyse de la [qualité du code .net](../../fundamentals/code-analysis/overview.md#code-quality-analysis) sont également traités comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="9b53d-279">If you use the `-warnaserror` flag when you build your projects, [.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) warnings are also treated as errors.</span></span> <span data-ttu-id="9b53d-280">Si vous ne souhaitez pas que les avertissements d’analyse de la qualité du code soient traités comme des erreurs, vous pouvez définir la `CodeAnalysisTreatWarningsAsErrors` propriété MSBuild sur `false` dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="9b53d-280">If you do not want code quality analysis warnings to be treated as errors, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a><span data-ttu-id="9b53d-281">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="9b53d-281">EnableNETAnalyzers</span></span>

<span data-ttu-id="9b53d-282">L’analyse de la [qualité du code .net](../../fundamentals/code-analysis/overview.md#code-quality-analysis) est activée, par défaut, pour les projets qui ciblent .net 5,0 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="9b53d-282">[.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="9b53d-283">Vous pouvez activer l’analyse du code .NET pour les projets qui ciblent des versions antérieures de .NET en affectant à la propriété la valeur `EnableNETAnalyzers` `true` .</span><span class="sxs-lookup"><span data-stu-id="9b53d-283">You can enable .NET code analysis for projects that target earlier versions of .NET by setting the `EnableNETAnalyzers` property to `true`.</span></span> <span data-ttu-id="9b53d-284">Pour désactiver l’analyse du code dans un projet, affectez la valeur à cette propriété `false` .</span><span class="sxs-lookup"><span data-stu-id="9b53d-284">To disable code analysis in any project, set this property to `false`.</span></span>

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="9b53d-285">Une autre façon d’activer l’analyse du code .NET sur les projets qui ciblent les versions .NET antérieures à .NET 5,0 consiste à définir la propriété [AnalysisLevel](#analysislevel) sur `latest` .</span><span class="sxs-lookup"><span data-stu-id="9b53d-285">Another way to enable .NET code analysis on projects that target .NET versions prior to .NET 5.0 is to set the [AnalysisLevel](#analysislevel) property to `latest`.</span></span>

### <a name="enforcecodestyleinbuild"></a><span data-ttu-id="9b53d-286">EnforceCodeStyleInBuild</span><span class="sxs-lookup"><span data-stu-id="9b53d-286">EnforceCodeStyleInBuild</span></span>

> [!NOTE]
> <span data-ttu-id="9b53d-287">Cette fonctionnalité est actuellement expérimentale et peut changer entre les versions .NET 5 et .NET 6.</span><span class="sxs-lookup"><span data-stu-id="9b53d-287">This feature is currently experimental and may change between the .NET 5 and .NET 6 releases.</span></span>

<span data-ttu-id="9b53d-288">L' [analyse du style de code .net](../../fundamentals/code-analysis/overview.md#code-style-analysis) est désactivée, par défaut, à la génération pour tous les projets .net.</span><span class="sxs-lookup"><span data-stu-id="9b53d-288">[.NET code style analysis](../../fundamentals/code-analysis/overview.md#code-style-analysis) is disabled, by default, on build for all .NET projects.</span></span> <span data-ttu-id="9b53d-289">Vous pouvez activer l’analyse de style de code pour les projets .NET en affectant à la propriété la valeur `EnforceCodeStyleInBuild` `true` .</span><span class="sxs-lookup"><span data-stu-id="9b53d-289">You can enable code style analysis for .NET projects by setting the `EnforceCodeStyleInBuild` property to `true`.</span></span>

```xml
<PropertyGroup>
  <EnforceCodeStyleInBuild>true</EnforceCodeStyleInBuild>
</PropertyGroup>
```

<span data-ttu-id="9b53d-290">Toutes les règles de style de code qui sont [configurées](../../fundamentals/code-analysis/overview.md#code-style-analysis) pour être des avertissements ou des erreurs sont exécutées lors des violations de la build et des rapports.</span><span class="sxs-lookup"><span data-stu-id="9b53d-290">All code style rules that are [configured](../../fundamentals/code-analysis/overview.md#code-style-analysis) to be warnings or errors will execute on build and report violations.</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="9b53d-291">Propriétés de configuration au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="9b53d-291">Run-time configuration properties</span></span>

<span data-ttu-id="9b53d-292">Vous pouvez configurer certains comportements au moment de l’exécution en spécifiant des propriétés MSBuild dans le fichier projet de l’application.</span><span class="sxs-lookup"><span data-stu-id="9b53d-292">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="9b53d-293">Pour plus d’informations sur les autres méthodes de configuration du comportement au moment de l’exécution, consultez [paramètres de configuration](../run-time-config/index.md)de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="9b53d-293">For information about other ways of configuring run-time behavior, see [Run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="9b53d-294">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="9b53d-294">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="9b53d-295">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="9b53d-295">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="9b53d-296">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="9b53d-296">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="9b53d-297">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="9b53d-297">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="9b53d-298">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="9b53d-298">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="9b53d-299">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="9b53d-299">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="9b53d-300">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="9b53d-300">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="9b53d-301">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="9b53d-301">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="9b53d-302">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="9b53d-302">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="9b53d-303">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="9b53d-303">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="9b53d-304">La `ConcurrentGarbageCollection` propriété configure si l' [garbage collection d’arrière-plan (simultané)](../../standard/garbage-collection/background-gc.md) est activée.</span><span class="sxs-lookup"><span data-stu-id="9b53d-304">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="9b53d-305">Affectez la valeur `false` à pour désactiver les garbage collection d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="9b53d-305">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="9b53d-306">Pour plus d’informations, consultez [Background gc](../run-time-config/garbage-collector.md#background-gc).</span><span class="sxs-lookup"><span data-stu-id="9b53d-306">For more information, see [Background GC](../run-time-config/garbage-collector.md#background-gc).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="9b53d-307">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="9b53d-307">InvariantGlobalization</span></span>

<span data-ttu-id="9b53d-308">La `InvariantGlobalization` propriété configure si l’application s’exécute en mode de *globalisation invariant* , ce qui signifie qu’elle n’a pas accès aux données spécifiques à la culture.</span><span class="sxs-lookup"><span data-stu-id="9b53d-308">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="9b53d-309">Affectez à la valeur la valeur `true` pour qu’elle s’exécute en mode de globalisation-indifférent.</span><span class="sxs-lookup"><span data-stu-id="9b53d-309">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="9b53d-310">Pour plus d’informations, consultez [mode indifférent](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="9b53d-310">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="9b53d-311">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="9b53d-311">RetainVMGarbageCollection</span></span>

<span data-ttu-id="9b53d-312">La `RetainVMGarbageCollection` propriété configure le garbage collector pour placer les segments de mémoire supprimés sur une liste d’attente pour une utilisation ultérieure ou les libérer.</span><span class="sxs-lookup"><span data-stu-id="9b53d-312">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="9b53d-313">La définition de la valeur `true` indique au garbage collector de placer les segments sur une liste d’attente.</span><span class="sxs-lookup"><span data-stu-id="9b53d-313">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="9b53d-314">Pour plus d’informations, consultez [conserver la machine virtuelle](../run-time-config/garbage-collector.md#retain-vm).</span><span class="sxs-lookup"><span data-stu-id="9b53d-314">For more information, see [Retain VM](../run-time-config/garbage-collector.md#retain-vm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="9b53d-315">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="9b53d-315">ServerGarbageCollection</span></span>

<span data-ttu-id="9b53d-316">La `ServerGarbageCollection` propriété configure si l’application utilise des [garbage collection de station de travail ou des garbage collection de serveur](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="9b53d-316">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="9b53d-317">Définissez la valeur sur `true` sur utiliser le garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="9b53d-317">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="9b53d-318">Pour plus d’informations, consultez [station de travail et serveur](../run-time-config/garbage-collector.md#workstation-vs-server).</span><span class="sxs-lookup"><span data-stu-id="9b53d-318">For more information, see [Workstation vs. server](../run-time-config/garbage-collector.md#workstation-vs-server).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="9b53d-319">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="9b53d-319">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="9b53d-320">La `ThreadPoolMaxThreads` propriété configure le nombre maximal de threads pour le pool de threads de travail.</span><span class="sxs-lookup"><span data-stu-id="9b53d-320">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="9b53d-321">Pour plus d’informations, consultez [nombre maximal de threads](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="9b53d-321">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="9b53d-322">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="9b53d-322">ThreadPoolMinThreads</span></span>

<span data-ttu-id="9b53d-323">La `ThreadPoolMinThreads` propriété configure le nombre minimal de threads pour le pool de threads de travail.</span><span class="sxs-lookup"><span data-stu-id="9b53d-323">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="9b53d-324">Pour plus d’informations, consultez [minimum threads](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="9b53d-324">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="9b53d-325">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="9b53d-325">TieredCompilation</span></span>

<span data-ttu-id="9b53d-326">La `TieredCompilation` propriété configure si le compilateur juste-à-temps (JIT) utilise la [compilation à plusieurs niveaux](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="9b53d-326">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="9b53d-327">Définissez la valeur sur `false` pour désactiver la compilation à plusieurs niveaux.</span><span class="sxs-lookup"><span data-stu-id="9b53d-327">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="9b53d-328">Pour plus d’informations, consultez compilation à plusieurs [niveaux](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="9b53d-328">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="9b53d-329">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="9b53d-329">TieredCompilationQuickJit</span></span>

<span data-ttu-id="9b53d-330">La `TieredCompilationQuickJit` propriété configure si le compilateur JIT utilise Quick JIT.</span><span class="sxs-lookup"><span data-stu-id="9b53d-330">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="9b53d-331">Définissez la valeur sur `false` pour désactiver le JIT rapide.</span><span class="sxs-lookup"><span data-stu-id="9b53d-331">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="9b53d-332">Pour plus d’informations, consultez [Quick JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="9b53d-332">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="9b53d-333">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="9b53d-333">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="9b53d-334">La `TieredCompilationQuickJitForLoops` propriété configure si le compilateur JIT utilise le JIT rapide sur les méthodes qui contiennent des boucles.</span><span class="sxs-lookup"><span data-stu-id="9b53d-334">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="9b53d-335">Affectez la valeur `true` à pour activer le JIT rapide sur les méthodes qui contiennent des boucles.</span><span class="sxs-lookup"><span data-stu-id="9b53d-335">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="9b53d-336">Pour plus d’informations, consultez [Quick JIT for Loops](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="9b53d-336">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a><span data-ttu-id="9b53d-337">Propriétés et éléments de référence</span><span class="sxs-lookup"><span data-stu-id="9b53d-337">Reference properties and items</span></span>

- [<span data-ttu-id="9b53d-338">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="9b53d-338">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="9b53d-339">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="9b53d-339">DisableImplicitFrameworkReferences</span></span>](#disableimplicitframeworkreferences)
- [<span data-ttu-id="9b53d-340">PackageReference</span><span class="sxs-lookup"><span data-stu-id="9b53d-340">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="9b53d-341">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="9b53d-341">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="9b53d-342">Référence</span><span class="sxs-lookup"><span data-stu-id="9b53d-342">Reference</span></span>](#reference)
- [<span data-ttu-id="9b53d-343">Propriétés liées à la restauration</span><span class="sxs-lookup"><span data-stu-id="9b53d-343">Restore-related properties</span></span>](#restore-related-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="9b53d-344">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="9b53d-344">AssetTargetFallback</span></span>

<span data-ttu-id="9b53d-345">La `AssetTargetFallback` propriété vous permet de spécifier des versions de Framework compatibles supplémentaires pour les références de projet et les packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="9b53d-345">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="9b53d-346">Par exemple, si vous spécifiez une dépendance de package à l’aide de `PackageReference` mais que ce package ne contient pas de ressources compatibles avec les projets `TargetFramework` , la `AssetTargetFallback` propriété entre en lecture.</span><span class="sxs-lookup"><span data-stu-id="9b53d-346">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="9b53d-347">La compatibilité du package référencé est revérifiée à l’aide de chaque version cible de .NET Framework spécifiée dans `AssetTargetFallback` .</span><span class="sxs-lookup"><span data-stu-id="9b53d-347">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span> <span data-ttu-id="9b53d-348">Cette propriété remplace la propriété déconseillée `PackageTargetFallback` .</span><span class="sxs-lookup"><span data-stu-id="9b53d-348">This property replaces the deprecated property `PackageTargetFallback`.</span></span>

<span data-ttu-id="9b53d-349">Vous pouvez définir la `AssetTargetFallback` propriété sur une ou plusieurs [versions du Framework cible](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="9b53d-349">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="disableimplicitframeworkreferences"></a><span data-ttu-id="9b53d-350">DisableImplicitFrameworkReferences</span><span class="sxs-lookup"><span data-stu-id="9b53d-350">DisableImplicitFrameworkReferences</span></span>

<span data-ttu-id="9b53d-351">La `DisableImplicitFrameworkReferences` propriété contrôle les `FrameworkReference` éléments implicites lors du ciblage de .net Core 3,0 et des versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="9b53d-351">The `DisableImplicitFrameworkReferences` property controls implicit `FrameworkReference` items when targeting .NET Core 3.0 and later versions.</span></span> <span data-ttu-id="9b53d-352">Quand vous ciblez .NET Core 2,1 ou .NET Standard 2,0 et versions antérieures, il contrôle les éléments [PackageReference](#packagereference) implicites pour les packages dans un sous-package.</span><span class="sxs-lookup"><span data-stu-id="9b53d-352">When targeting .NET Core 2.1 or .NET Standard 2.0 and earlier versions, it controls implicit [PackageReference](#packagereference) items to packages in a metapackage.</span></span> <span data-ttu-id="9b53d-353">(Un reconditionnement est un package basé sur une infrastructure qui se compose uniquement de dépendances sur d’autres packages.) Cette propriété contrôle également les références implicites telles que `System` et `System.Core` lorsque vous ciblez .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9b53d-353">(A metapackage is a framework-based package that consist only of dependencies on other packages.) This property also controls implicit references such as `System` and `System.Core` when targeting .NET Framework.</span></span>

<span data-ttu-id="9b53d-354">Affectez à cette propriété la valeur `true` pour désactiver les éléments implicites `FrameworkReference` ou [PackageReference](#packagereference) .</span><span class="sxs-lookup"><span data-stu-id="9b53d-354">Set this property to `true` to disable implicit `FrameworkReference` or [PackageReference](#packagereference) items.</span></span> <span data-ttu-id="9b53d-355">Si vous affectez à cette propriété `true` la valeur, vous pouvez ajouter des références explicites uniquement aux frameworks ou aux packages dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="9b53d-355">If you set this property to `true`, you can add explicit references to just the frameworks or packages you need.</span></span>

```xml
<PropertyGroup>
  <DisableImplicitFrameworkReferences>true</DisableImplicitFrameworkReferences>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="9b53d-356">PackageReference</span><span class="sxs-lookup"><span data-stu-id="9b53d-356">PackageReference</span></span>

<span data-ttu-id="9b53d-357">L' `PackageReference` élément définit une référence à un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="9b53d-357">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="9b53d-358">L’attribut `Include` spécifie l’ID du package.</span><span class="sxs-lookup"><span data-stu-id="9b53d-358">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="9b53d-359">L' `Version` attribut spécifie la version ou la plage de versions.</span><span class="sxs-lookup"><span data-stu-id="9b53d-359">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="9b53d-360">Pour plus d’informations sur la spécification d’une version minimale, d’une version maximale, d’une plage ou d’une correspondance exacte, consultez [plages de versions](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="9b53d-360">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="9b53d-361">Vous pouvez également ajouter des [attributs de ressource](#asset-attributes) à une référence de package.</span><span class="sxs-lookup"><span data-stu-id="9b53d-361">You can also add [asset attributes](#asset-attributes) to a package reference.</span></span>

<span data-ttu-id="9b53d-362">L’extrait de code du fichier projet dans l’exemple suivant référence le package [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .</span><span class="sxs-lookup"><span data-stu-id="9b53d-362">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="9b53d-363">Pour plus d’informations, consultez [références de package dans les fichiers projet](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="9b53d-363">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

#### <a name="asset-attributes"></a><span data-ttu-id="9b53d-364">Attributs de ressource</span><span class="sxs-lookup"><span data-stu-id="9b53d-364">Asset attributes</span></span>

<span data-ttu-id="9b53d-365">Les `IncludeAssets` `ExcludeAssets` `PrivateAssets` métadonnées, et peuvent être ajoutées à une référence de package.</span><span class="sxs-lookup"><span data-stu-id="9b53d-365">The `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets` metadata can be added to a package reference.</span></span>

| <span data-ttu-id="9b53d-366">Attribut</span><span class="sxs-lookup"><span data-stu-id="9b53d-366">Attribute</span></span> | <span data-ttu-id="9b53d-367">Description</span><span class="sxs-lookup"><span data-stu-id="9b53d-367">Description</span></span> |
| - | - |
| `IncludeAssets` | <span data-ttu-id="9b53d-368">Spécifie quelles ressources appartenant au package spécifié par `<PackageReference>` doivent être consommées.</span><span class="sxs-lookup"><span data-stu-id="9b53d-368">Specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="9b53d-369">Par défaut, toutes les ressources du package sont incluses.</span><span class="sxs-lookup"><span data-stu-id="9b53d-369">By default, all package assets are included.</span></span> |
| `ExcludeAssets`| <span data-ttu-id="9b53d-370">Spécifie les ressources appartenant au package spécifié par ne `<PackageReference>` doivent pas être consommées.</span><span class="sxs-lookup"><span data-stu-id="9b53d-370">Specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span> |
| `PrivateAssets` | <span data-ttu-id="9b53d-371">Spécifie les ressources appartenant au package spécifié par `<PackageReference>` doivent être consommées, mais pas transmises au projet suivant.</span><span class="sxs-lookup"><span data-stu-id="9b53d-371">Specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="9b53d-372">Les `Analyzers` `Build` ressources, et `ContentFiles` sont privées par défaut lorsque cet attribut n’est pas présent.</span><span class="sxs-lookup"><span data-stu-id="9b53d-372">The `Analyzers`, `Build`, and `ContentFiles` assets are private by default when this attribute is not present.</span></span> |

<span data-ttu-id="9b53d-373">Ces attributs peuvent contenir un ou plusieurs des éléments suivants, séparés par un point-virgule `;` si plus d’un élément est listé :</span><span class="sxs-lookup"><span data-stu-id="9b53d-373">These attributes can contain one or more of the following items, separated by a semicolon `;` if more than one is listed:</span></span>

- <span data-ttu-id="9b53d-374">`Compile` : le contenu du dossier *lib* est disponible pour la compilation.</span><span class="sxs-lookup"><span data-stu-id="9b53d-374">`Compile` – the contents of the *lib* folder are available to compile against.</span></span>
- <span data-ttu-id="9b53d-375">`Runtime` : le contenu du dossier *Runtime* est distribué.</span><span class="sxs-lookup"><span data-stu-id="9b53d-375">`Runtime` – the contents of the *runtime* folder are distributed.</span></span>
- <span data-ttu-id="9b53d-376">`ContentFiles` : Le contenu du dossier *contentfiles* est utilisé.</span><span class="sxs-lookup"><span data-stu-id="9b53d-376">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
- <span data-ttu-id="9b53d-377">`Build` : les propriétés/cibles du dossier de *génération* sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="9b53d-377">`Build` – the props/targets in the *build* folder are used.</span></span>
- <span data-ttu-id="9b53d-378">`Native` : le contenu des ressources natives est copié dans le dossier de *sortie* pour l’exécution.</span><span class="sxs-lookup"><span data-stu-id="9b53d-378">`Native` – the contents from native assets are copied to the *output* folder for runtime.</span></span>
- <span data-ttu-id="9b53d-379">`Analyzers` : Les analyseurs sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="9b53d-379">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="9b53d-380">Sinon, l’attribut peut contenir :</span><span class="sxs-lookup"><span data-stu-id="9b53d-380">Alternatively, the attribute can contain:</span></span>

- <span data-ttu-id="9b53d-381">`None` : Aucune ressource n’est utilisée.</span><span class="sxs-lookup"><span data-stu-id="9b53d-381">`None` – none of the assets are used.</span></span>
- <span data-ttu-id="9b53d-382">`All` : Toutes les ressources sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="9b53d-382">`All` – all assets are used.</span></span>

### <a name="projectreference"></a><span data-ttu-id="9b53d-383">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="9b53d-383">ProjectReference</span></span>

<span data-ttu-id="9b53d-384">L' `ProjectReference` élément définit une référence à un autre projet.</span><span class="sxs-lookup"><span data-stu-id="9b53d-384">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="9b53d-385">Le projet référencé est ajouté en tant que dépendance de package NuGet, autrement dit, il est traité de la même façon qu’un `PackageReference` .</span><span class="sxs-lookup"><span data-stu-id="9b53d-385">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="9b53d-386">L' `Include` attribut spécifie le chemin d’accès au projet.</span><span class="sxs-lookup"><span data-stu-id="9b53d-386">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="9b53d-387">Vous pouvez également ajouter les métadonnées suivantes à une référence de projet : `IncludeAssets` , `ExcludeAssets` et `PrivateAssets` .</span><span class="sxs-lookup"><span data-stu-id="9b53d-387">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="9b53d-388">L’extrait de code du fichier projet dans l’exemple suivant fait référence à un projet nommé `Project2` .</span><span class="sxs-lookup"><span data-stu-id="9b53d-388">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="9b53d-389">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="9b53d-389">Reference</span></span>

<span data-ttu-id="9b53d-390">L' `Reference` élément définit une référence à un fichier d’assembly.</span><span class="sxs-lookup"><span data-stu-id="9b53d-390">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="9b53d-391">L' `Include` attribut spécifie le nom du fichier, et les `HintPath` métadonnées spécifient le chemin d’accès à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="9b53d-391">The `Include` attribute specifies the name of the file, and the `HintPath` metadata specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-related-properties"></a><span data-ttu-id="9b53d-392">Propriétés liées à la restauration</span><span class="sxs-lookup"><span data-stu-id="9b53d-392">Restore-related properties</span></span>

<span data-ttu-id="9b53d-393">La restauration d’un package référencé installe toutes ses dépendances directes et toutes les dépendances de ces dépendances.</span><span class="sxs-lookup"><span data-stu-id="9b53d-393">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="9b53d-394">Vous pouvez personnaliser la restauration des packages en spécifiant des propriétés telles que `RestorePackagesPath` et `RestoreIgnoreFailedSources` .</span><span class="sxs-lookup"><span data-stu-id="9b53d-394">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="9b53d-395">Pour plus d’informations sur ces propriétés et d’autres, consultez [restaurer la cible](/nuget/reference/msbuild-targets#restore-target).</span><span class="sxs-lookup"><span data-stu-id="9b53d-395">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="run-properties"></a><span data-ttu-id="9b53d-396">Propriétés d’exécution</span><span class="sxs-lookup"><span data-stu-id="9b53d-396">Run properties</span></span>

<span data-ttu-id="9b53d-397">Les propriétés suivantes sont utilisées pour lancer une application à l’aide de la [`dotnet run`](../tools/dotnet-run.md) commande :</span><span class="sxs-lookup"><span data-stu-id="9b53d-397">The following properties are used for launching an app with the [`dotnet run`](../tools/dotnet-run.md) command:</span></span>

- [<span data-ttu-id="9b53d-398">RunArguments</span><span class="sxs-lookup"><span data-stu-id="9b53d-398">RunArguments</span></span>](#runarguments)
- [<span data-ttu-id="9b53d-399">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="9b53d-399">RunWorkingDirectory</span></span>](#runworkingdirectory)

### <a name="runarguments"></a><span data-ttu-id="9b53d-400">RunArguments</span><span class="sxs-lookup"><span data-stu-id="9b53d-400">RunArguments</span></span>

<span data-ttu-id="9b53d-401">La `RunArguments` propriété définit les arguments passés à l’application lorsqu’elle est exécutée.</span><span class="sxs-lookup"><span data-stu-id="9b53d-401">The `RunArguments` property defines the arguments that are passed to the app when it is run.</span></span>

```xml
<PropertyGroup>
  <RunArguments>-mode dryrun</RunArguments>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="9b53d-402">Vous pouvez spécifier des arguments supplémentaires à passer à l’application à l’aide [ `--` de l' `dotnet run` option pour ](../tools/dotnet-run.md#options).</span><span class="sxs-lookup"><span data-stu-id="9b53d-402">You can specify additional arguments to be passed to the app by using the [`--` option for `dotnet run`](../tools/dotnet-run.md#options).</span></span>

### <a name="runworkingdirectory"></a><span data-ttu-id="9b53d-403">RunWorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="9b53d-403">RunWorkingDirectory</span></span>

<span data-ttu-id="9b53d-404">La `RunWorkingDirectory` propriété définit le répertoire de travail pour le processus d’application à démarrer dans.</span><span class="sxs-lookup"><span data-stu-id="9b53d-404">The `RunWorkingDirectory` property defines the working directory for the application process to be started in.</span></span> <span data-ttu-id="9b53d-405">Il peut s’agir d’un chemin d’accès absolu ou d’un chemin d’accès relatif au répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="9b53d-405">It can be an absolute path or a path that's relative to the project directory.</span></span> <span data-ttu-id="9b53d-406">Si vous ne spécifiez pas de répertoire, `OutDir` est utilisé comme répertoire de travail.</span><span class="sxs-lookup"><span data-stu-id="9b53d-406">If you don't specify a directory, `OutDir` is used as the working directory.</span></span>

```xml
<PropertyGroup>
  <RunWorkingDirectory>c:\temp</RunWorkingDirectory>
</PropertyGroup>
```

## <a name="hosting-properties"></a><span data-ttu-id="9b53d-407">Propriétés d’hébergement</span><span class="sxs-lookup"><span data-stu-id="9b53d-407">Hosting properties</span></span>

- [<span data-ttu-id="9b53d-408">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="9b53d-408">EnableComHosting</span></span>](#enablecomhosting)
- [<span data-ttu-id="9b53d-409">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="9b53d-409">EnableDynamicLoading</span></span>](#enabledynamicloading)

### <a name="enablecomhosting"></a><span data-ttu-id="9b53d-410">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="9b53d-410">EnableComHosting</span></span>

<span data-ttu-id="9b53d-411">La `EnableComHosting` propriété indique qu’un assembly fournit un serveur com.</span><span class="sxs-lookup"><span data-stu-id="9b53d-411">The `EnableComHosting` property indicates that an assembly provides a COM server.</span></span> <span data-ttu-id="9b53d-412">Le `EnableComHosting` fait d’affecter à la valeur `true` implique également que [EnableDynamicLoading](#enabledynamicloading) est `true` .</span><span class="sxs-lookup"><span data-stu-id="9b53d-412">Setting the `EnableComHosting` to `true` also implies that [EnableDynamicLoading](#enabledynamicloading) is `true`.</span></span>

```xml
<PropertyGroup>
  <EnableComHosting>True</EnableComHosting>
</PropertyGroup>
```

<span data-ttu-id="9b53d-413">Pour plus d’informations, consultez [exposer des composants .net à com](../native-interop/expose-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="9b53d-413">For more information, see [Expose .NET components to COM](../native-interop/expose-components-to-com.md).</span></span>

### <a name="enabledynamicloading"></a><span data-ttu-id="9b53d-414">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="9b53d-414">EnableDynamicLoading</span></span>

<span data-ttu-id="9b53d-415">La `EnableDynamicLoading` propriété indique qu’un assembly est un composant chargé dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="9b53d-415">The `EnableDynamicLoading` property indicates that an assembly is a dynamically loaded component.</span></span> <span data-ttu-id="9b53d-416">Le composant peut être une bibliothèque [com](/windows/win32/com/the-component-object-model) ou une bibliothèque non-com qui peut être [utilisée à partir d’un hôte natif](../tutorials/netcore-hosting.md).</span><span class="sxs-lookup"><span data-stu-id="9b53d-416">The component could be a [COM library](/windows/win32/com/the-component-object-model) or a non-COM library that can be [used from a native host](../tutorials/netcore-hosting.md).</span></span> <span data-ttu-id="9b53d-417">L’affectation de la valeur à cette propriété `true` a les effets suivants :</span><span class="sxs-lookup"><span data-stu-id="9b53d-417">Setting this property to `true` has the following effects:</span></span>

- <span data-ttu-id="9b53d-418">Un *.runtimeconfig.jssur le* fichier est généré.</span><span class="sxs-lookup"><span data-stu-id="9b53d-418">A *.runtimeconfig.json* file is generated.</span></span>
- <span data-ttu-id="9b53d-419">La [restauration par progression](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) est définie sur `LatestMinor` .</span><span class="sxs-lookup"><span data-stu-id="9b53d-419">[Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) is set to `LatestMinor`.</span></span>
- <span data-ttu-id="9b53d-420">Les références NuGet sont copiées localement.</span><span class="sxs-lookup"><span data-stu-id="9b53d-420">NuGet references are copied locally.</span></span>

```xml
<PropertyGroup>
  <EnableDynamicLoading>true</EnableDynamicLoading>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="9b53d-421">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b53d-421">See also</span></span>

- [<span data-ttu-id="9b53d-422">Référence du schéma MSBuild</span><span class="sxs-lookup"><span data-stu-id="9b53d-422">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="9b53d-423">Propriétés MSBuild communes</span><span class="sxs-lookup"><span data-stu-id="9b53d-423">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="9b53d-424">Propriétés MSBuild pour le Pack NuGet</span><span class="sxs-lookup"><span data-stu-id="9b53d-424">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="9b53d-425">Propriétés MSBuild pour la restauration NuGet</span><span class="sxs-lookup"><span data-stu-id="9b53d-425">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="9b53d-426">Personnaliser une build</span><span class="sxs-lookup"><span data-stu-id="9b53d-426">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
