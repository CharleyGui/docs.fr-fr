---
title: Propriétés MSBuild pour Microsoft. NET. Sdk
description: Référence pour les propriétés et les éléments MSBuild compris par l’kit SDK .NET Core.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 115c4f32e856dee64abe0c607b8ee595a65692e6
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164375"
---
# <a name="msbuild-reference-for-net-core-sdk-projects"></a><span data-ttu-id="fabf0-103">Référence MSBuild pour les projets kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="fabf0-103">MSBuild reference for .NET Core SDK projects</span></span>

<span data-ttu-id="fabf0-104">Cette page est une référence pour les propriétés et les éléments MSBuild que vous pouvez utiliser pour configurer des projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fabf0-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="fabf0-105">Cette page est un travail en cours et ne répertorie pas toutes les propriétés MSBuild utiles pour le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fabf0-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="fabf0-106">Pour obtenir la liste des propriétés MSBuild courantes, consultez [propriétés MSBuild communes](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="fabf0-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="fabf0-107">Propriétés du Framework</span><span class="sxs-lookup"><span data-stu-id="fabf0-107">Framework properties</span></span>

- [<span data-ttu-id="fabf0-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="fabf0-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="fabf0-109">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="fabf0-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="fabf0-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="fabf0-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="fabf0-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="fabf0-111">TargetFramework</span></span>

<span data-ttu-id="fabf0-112">La `TargetFramework` propriété spécifie la version cible de .NET Framework pour l’application.</span><span class="sxs-lookup"><span data-stu-id="fabf0-112">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="fabf0-113">Pour obtenir la liste des monikers du Framework cible valides, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="fabf0-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="fabf0-114">Pour plus d’informations, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="fabf0-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="fabf0-115">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="fabf0-115">TargetFrameworks</span></span>

<span data-ttu-id="fabf0-116">Utilisez la `TargetFrameworks` propriété lorsque vous souhaitez que votre application cible plusieurs plateformes.</span><span class="sxs-lookup"><span data-stu-id="fabf0-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="fabf0-117">Pour obtenir la liste des monikers du Framework cible valides, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="fabf0-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="fabf0-118">Cette propriété est ignorée si `TargetFramework` (singulier) est spécifié.</span><span class="sxs-lookup"><span data-stu-id="fabf0-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="fabf0-119">Pour plus d’informations, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="fabf0-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="fabf0-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="fabf0-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="fabf0-121">Cette propriété s’applique uniquement aux projets qui utilisent `netstandard1.x` .</span><span class="sxs-lookup"><span data-stu-id="fabf0-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="fabf0-122">Elle ne s’applique pas aux projets qui utilisent `netstandard2.x` .</span><span class="sxs-lookup"><span data-stu-id="fabf0-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="fabf0-123">Utilisez la `NetStandardImplicitPackageVersion` propriété lorsque vous souhaitez spécifier une version de Framework inférieure à la version de l’ensemble de packages.</span><span class="sxs-lookup"><span data-stu-id="fabf0-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="fabf0-124">Le fichier projet dans l’exemple suivant cible, `netstandard1.3` mais utilise la version 1.6.0 de `NETStandard.Library` .</span><span class="sxs-lookup"><span data-stu-id="fabf0-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="fabf0-125">Propriétés du package</span><span class="sxs-lookup"><span data-stu-id="fabf0-125">Package properties</span></span>

<span data-ttu-id="fabf0-126">Vous pouvez spécifier des propriétés telles que `PackageId` , `PackageVersion` ,, `PackageIcon` `Title` et `Description` pour décrire le package qui est créé à partir de votre projet.</span><span class="sxs-lookup"><span data-stu-id="fabf0-126">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="fabf0-127">Pour plus d’informations sur ces propriétés et d’autres, consultez [package Target](/nuget/reference/msbuild-targets#pack-target).</span><span class="sxs-lookup"><span data-stu-id="fabf0-127">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-and-items"></a><span data-ttu-id="fabf0-128">Publier les propriétés et les éléments</span><span class="sxs-lookup"><span data-stu-id="fabf0-128">Publish properties and items</span></span>

- [<span data-ttu-id="fabf0-129">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="fabf0-129">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="fabf0-130">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="fabf0-130">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="fabf0-131">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="fabf0-131">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="fabf0-132">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="fabf0-132">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="fabf0-133">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="fabf0-133">RuntimeIdentifier</span></span>

<span data-ttu-id="fabf0-134">La `RuntimeIdentifier` propriété vous permet de spécifier un [identificateur de Runtime unique (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="fabf0-134">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="fabf0-135">Le RID permet de publier un déploiement autonome.</span><span class="sxs-lookup"><span data-stu-id="fabf0-135">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="fabf0-136">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="fabf0-136">RuntimeIdentifiers</span></span>

<span data-ttu-id="fabf0-137">La `RuntimeIdentifiers` propriété vous permet de spécifier une liste délimitée par des points-virgules des [identificateurs de Runtime (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="fabf0-137">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="fabf0-138">Utilisez cette propriété si vous devez publier pour plusieurs runtimes.</span><span class="sxs-lookup"><span data-stu-id="fabf0-138">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="fabf0-139">`RuntimeIdentifiers`est utilisé au moment de la restauration pour s’assurer que les ressources appropriées sont dans le graphique.</span><span class="sxs-lookup"><span data-stu-id="fabf0-139">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="fabf0-140">`RuntimeIdentifier`(singulier) peut fournir des builds plus rapides quand un seul Runtime est requis.</span><span class="sxs-lookup"><span data-stu-id="fabf0-140">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="fabf0-141">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="fabf0-141">TrimmerRootAssembly</span></span>

<span data-ttu-id="fabf0-142">L' `TrimmerRootAssembly` élément vous permet d’exclure un assembly du [*découpage*](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="fabf0-142">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="fabf0-143">Le découpage est le processus qui consiste à supprimer des parties inutilisées du runtime d’une application empaquetée.</span><span class="sxs-lookup"><span data-stu-id="fabf0-143">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="fabf0-144">Dans certains cas, la suppression peut supprimer incorrectement les références requises.</span><span class="sxs-lookup"><span data-stu-id="fabf0-144">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="fabf0-145">Le code XML suivant exclut `System.Security` de la suppression de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="fabf0-145">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="fabf0-146">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="fabf0-146">UseAppHost</span></span>

<span data-ttu-id="fabf0-147">La `UseAppHost` propriété a été introduite dans la version 2.1.400 de l’kit SDK .net core.</span><span class="sxs-lookup"><span data-stu-id="fabf0-147">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="fabf0-148">Il contrôle si un exécutable natif est créé ou non pour un déploiement.</span><span class="sxs-lookup"><span data-stu-id="fabf0-148">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="fabf0-149">Un exécutable natif est requis pour les déploiements autonomes.</span><span class="sxs-lookup"><span data-stu-id="fabf0-149">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="fabf0-150">Dans .NET Core 3,0 et versions ultérieures, un fichier exécutable dépendant du Framework est créé par défaut.</span><span class="sxs-lookup"><span data-stu-id="fabf0-150">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="fabf0-151">Affectez à la propriété la valeur `UseAppHost` `false` pour désactiver la génération de l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="fabf0-151">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="fabf0-152">Pour plus d’informations sur le déploiement, consultez [déploiement d’applications .net Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="fabf0-152">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="fabf0-153">Propriétés de compilation</span><span class="sxs-lookup"><span data-stu-id="fabf0-153">Compile properties</span></span>

- [<span data-ttu-id="fabf0-154">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="fabf0-154">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="fabf0-155">LangVersion</span><span class="sxs-lookup"><span data-stu-id="fabf0-155">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="fabf0-156">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="fabf0-156">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="fabf0-157">La `EmbeddedResourceUseDependentUponConvention` propriété définit si les noms des fichiers manifestes de ressources sont générés à partir des informations de type dans les fichiers sources qui sont colocalisés avec les fichiers de ressources.</span><span class="sxs-lookup"><span data-stu-id="fabf0-157">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="fabf0-158">Par exemple, si *Form1. resx* se trouve dans le même dossier que *Form1.cs*et que `EmbeddedResourceUseDependentUponConvention` a la valeur `true` , le fichier *. Resources* généré prend son nom dans le premier type défini dans *Form1.cs*.</span><span class="sxs-lookup"><span data-stu-id="fabf0-158">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="fabf0-159">Par exemple, si `MyNamespace.Form1` est le premier type défini dans *Form1.cs*, le nom de fichier généré est *MyNamespace. Form1. Resources*.</span><span class="sxs-lookup"><span data-stu-id="fabf0-159">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="fabf0-160">Si `LogicalName` `ManifestResourceName` `DependentUpon` les métadonnées, ou sont spécifiées pour un `EmbeddedResource` élément, le nom de fichier manifeste généré pour ce fichier de ressources est basé sur ces métadonnées à la place.</span><span class="sxs-lookup"><span data-stu-id="fabf0-160">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="fabf0-161">Par défaut, dans un nouveau projet .NET Core, cette propriété a la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="fabf0-161">By default, in a new .NET Core project, this property is set to `true`.</span></span> <span data-ttu-id="fabf0-162">Si la valeur `false` est définie sur, et si aucune `LogicalName` `ManifestResourceName` `DependentUpon` métadonnée n’est spécifiée pour l' `EmbeddedResource` élément dans le fichier projet, le nom du fichier manifeste de la ressource est basé sur l’espace de noms racine du projet et le chemin d’accès relatif au fichier *. resx* .</span><span class="sxs-lookup"><span data-stu-id="fabf0-162">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="fabf0-163">Pour plus d’informations, consultez [Comment les fichiers manifestes de ressources sont nommés](../resources/manifest-file-names.md).</span><span class="sxs-lookup"><span data-stu-id="fabf0-163">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="fabf0-164">LangVersion</span><span class="sxs-lookup"><span data-stu-id="fabf0-164">LangVersion</span></span>

<span data-ttu-id="fabf0-165">La `LangVersion` propriété vous permet de spécifier une version du langage de programmation spécifique.</span><span class="sxs-lookup"><span data-stu-id="fabf0-165">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="fabf0-166">Par exemple, si vous souhaitez accéder aux fonctionnalités de la version préliminaire de C#, affectez à la valeur `LangVersion` `preview` .</span><span class="sxs-lookup"><span data-stu-id="fabf0-166">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="fabf0-167">Pour plus d’informations, consultez contrôle de [version du langage C#](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="fabf0-167">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="fabf0-168">Propriétés de configuration au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="fabf0-168">Run-time configuration properties</span></span>

<span data-ttu-id="fabf0-169">Vous pouvez configurer certains comportements au moment de l’exécution en spécifiant des propriétés MSBuild dans le fichier projet de l’application.</span><span class="sxs-lookup"><span data-stu-id="fabf0-169">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="fabf0-170">Pour plus d’informations sur les autres méthodes de configuration du comportement au moment de l’exécution, consultez Paramètres de configuration du runtime [.net Core](../run-time-config/index.md).</span><span class="sxs-lookup"><span data-stu-id="fabf0-170">For information about other ways of configuring run-time behavior, see [.NET Core run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="fabf0-171">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="fabf0-171">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="fabf0-172">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="fabf0-172">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="fabf0-173">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="fabf0-173">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="fabf0-174">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="fabf0-174">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="fabf0-175">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="fabf0-175">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="fabf0-176">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="fabf0-176">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="fabf0-177">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="fabf0-177">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="fabf0-178">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="fabf0-178">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="fabf0-179">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="fabf0-179">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="fabf0-180">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="fabf0-180">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="fabf0-181">La `ConcurrentGarbageCollection` propriété configure si l' [garbage collection d’arrière-plan (simultané)](../../standard/garbage-collection/background-gc.md) est activée.</span><span class="sxs-lookup"><span data-stu-id="fabf0-181">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="fabf0-182">Affectez la valeur `false` à pour désactiver les garbage collection d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="fabf0-182">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="fabf0-183">Pour plus d’informations, consultez [System. gc. concurrent/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span><span class="sxs-lookup"><span data-stu-id="fabf0-183">For more information, see [System.GC.Concurrent/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="fabf0-184">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="fabf0-184">InvariantGlobalization</span></span>

<span data-ttu-id="fabf0-185">La `InvariantGlobalization` propriété configure si l’application s’exécute en mode de *globalisation invariant* , ce qui signifie qu’elle n’a pas accès aux données spécifiques à la culture.</span><span class="sxs-lookup"><span data-stu-id="fabf0-185">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="fabf0-186">Affectez à la valeur la valeur `true` pour qu’elle s’exécute en mode de globalisation-indifférent.</span><span class="sxs-lookup"><span data-stu-id="fabf0-186">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="fabf0-187">Pour plus d’informations, consultez [mode indifférent](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="fabf0-187">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="fabf0-188">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="fabf0-188">RetainVMGarbageCollection</span></span>

<span data-ttu-id="fabf0-189">La `RetainVMGarbageCollection` propriété configure le garbage collector pour placer les segments de mémoire supprimés sur une liste d’attente pour une utilisation ultérieure ou les libérer.</span><span class="sxs-lookup"><span data-stu-id="fabf0-189">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="fabf0-190">La définition de la valeur `true` indique au garbage collector de placer les segments sur une liste d’attente.</span><span class="sxs-lookup"><span data-stu-id="fabf0-190">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="fabf0-191">Pour plus d’informations, consultez [System. gc. RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span><span class="sxs-lookup"><span data-stu-id="fabf0-191">For more information, see [System.GC.RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="fabf0-192">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="fabf0-192">ServerGarbageCollection</span></span>

<span data-ttu-id="fabf0-193">La `ServerGarbageCollection` propriété configure si l’application utilise des [garbage collection de station de travail ou des garbage collection de serveur](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="fabf0-193">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="fabf0-194">Définissez la valeur sur `true` sur utiliser le garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="fabf0-194">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="fabf0-195">Pour plus d’informations, consultez [System. gc. Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span><span class="sxs-lookup"><span data-stu-id="fabf0-195">For more information, see [System.GC.Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="fabf0-196">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="fabf0-196">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="fabf0-197">La `ThreadPoolMaxThreads` propriété configure le nombre maximal de threads pour le pool de threads de travail.</span><span class="sxs-lookup"><span data-stu-id="fabf0-197">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="fabf0-198">Pour plus d’informations, consultez [nombre maximal de threads](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="fabf0-198">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="fabf0-199">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="fabf0-199">ThreadPoolMinThreads</span></span>

<span data-ttu-id="fabf0-200">La `ThreadPoolMinThreads` propriété configure le nombre minimal de threads pour le pool de threads de travail.</span><span class="sxs-lookup"><span data-stu-id="fabf0-200">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="fabf0-201">Pour plus d’informations, consultez [minimum threads](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="fabf0-201">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="fabf0-202">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="fabf0-202">TieredCompilation</span></span>

<span data-ttu-id="fabf0-203">La `TieredCompilation` propriété configure si le compilateur juste-à-temps (JIT) utilise la [compilation à plusieurs niveaux](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="fabf0-203">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="fabf0-204">Définissez la valeur sur `false` pour désactiver la compilation à plusieurs niveaux.</span><span class="sxs-lookup"><span data-stu-id="fabf0-204">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="fabf0-205">Pour plus d’informations, consultez compilation à plusieurs [niveaux](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="fabf0-205">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="fabf0-206">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="fabf0-206">TieredCompilationQuickJit</span></span>

<span data-ttu-id="fabf0-207">La `TieredCompilationQuickJit` propriété configure si le compilateur JIT utilise Quick JIT.</span><span class="sxs-lookup"><span data-stu-id="fabf0-207">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="fabf0-208">Définissez la valeur sur `false` pour désactiver le JIT rapide.</span><span class="sxs-lookup"><span data-stu-id="fabf0-208">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="fabf0-209">Pour plus d’informations, consultez [Quick JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="fabf0-209">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="fabf0-210">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="fabf0-210">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="fabf0-211">La `TieredCompilationQuickJitForLoops` propriété configure si le compilateur JIT utilise le JIT rapide sur les méthodes qui contiennent des boucles.</span><span class="sxs-lookup"><span data-stu-id="fabf0-211">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="fabf0-212">Affectez la valeur `true` à pour activer le JIT rapide sur les méthodes qui contiennent des boucles.</span><span class="sxs-lookup"><span data-stu-id="fabf0-212">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="fabf0-213">Pour plus d’informations, consultez [Quick JIT for Loops](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="fabf0-213">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a><span data-ttu-id="fabf0-214">Propriétés et éléments de référence</span><span class="sxs-lookup"><span data-stu-id="fabf0-214">Reference properties and items</span></span>

- [<span data-ttu-id="fabf0-215">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="fabf0-215">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="fabf0-216">PackageReference</span><span class="sxs-lookup"><span data-stu-id="fabf0-216">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="fabf0-217">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="fabf0-217">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="fabf0-218">Référence</span><span class="sxs-lookup"><span data-stu-id="fabf0-218">Reference</span></span>](#reference)
- [<span data-ttu-id="fabf0-219">Propriétés de restauration</span><span class="sxs-lookup"><span data-stu-id="fabf0-219">Restore properties</span></span>](#restore-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="fabf0-220">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="fabf0-220">AssetTargetFallback</span></span>

<span data-ttu-id="fabf0-221">La `AssetTargetFallback` propriété vous permet de spécifier des versions de Framework compatibles supplémentaires pour les références de projet et les packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="fabf0-221">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="fabf0-222">Par exemple, si vous spécifiez une dépendance de package à l’aide de `PackageReference` mais que ce package ne contient pas de ressources compatibles avec les projets `TargetFramework` , la `AssetTargetFallback` propriété entre en lecture.</span><span class="sxs-lookup"><span data-stu-id="fabf0-222">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="fabf0-223">La compatibilité du package référencé est revérifiée à l’aide de chaque version cible de .NET Framework spécifiée dans `AssetTargetFallback` .</span><span class="sxs-lookup"><span data-stu-id="fabf0-223">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="fabf0-224">Vous pouvez définir la `AssetTargetFallback` propriété sur une ou plusieurs [versions du Framework cible](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="fabf0-224">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="fabf0-225">PackageReference</span><span class="sxs-lookup"><span data-stu-id="fabf0-225">PackageReference</span></span>

<span data-ttu-id="fabf0-226">L' `PackageReference` élément définit une référence à un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="fabf0-226">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="fabf0-227">L’attribut `Include` spécifie l’ID du package.</span><span class="sxs-lookup"><span data-stu-id="fabf0-227">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="fabf0-228">L' `Version` attribut spécifie la version ou la plage de versions.</span><span class="sxs-lookup"><span data-stu-id="fabf0-228">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="fabf0-229">Pour plus d’informations sur la spécification d’une version minimale, d’une version maximale, d’une plage ou d’une correspondance exacte, consultez [plages de versions](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="fabf0-229">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="fabf0-230">Vous pouvez également ajouter les métadonnées suivantes à une référence de projet : `IncludeAssets` , `ExcludeAssets` et `PrivateAssets` .</span><span class="sxs-lookup"><span data-stu-id="fabf0-230">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="fabf0-231">L’extrait de code du fichier projet dans l’exemple suivant référence le package [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .</span><span class="sxs-lookup"><span data-stu-id="fabf0-231">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="fabf0-232">Pour plus d’informations, consultez [références de package dans les fichiers projet](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="fabf0-232">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="projectreference"></a><span data-ttu-id="fabf0-233">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="fabf0-233">ProjectReference</span></span>

<span data-ttu-id="fabf0-234">L' `ProjectReference` élément définit une référence à un autre projet.</span><span class="sxs-lookup"><span data-stu-id="fabf0-234">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="fabf0-235">Le projet référencé est ajouté en tant que dépendance de package NuGet, autrement dit, il est traité de la même façon qu’un `PackageReference` .</span><span class="sxs-lookup"><span data-stu-id="fabf0-235">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="fabf0-236">L' `Include` attribut spécifie le chemin d’accès au projet.</span><span class="sxs-lookup"><span data-stu-id="fabf0-236">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="fabf0-237">Vous pouvez également ajouter les métadonnées suivantes à une référence de projet : `IncludeAssets` , `ExcludeAssets` et `PrivateAssets` .</span><span class="sxs-lookup"><span data-stu-id="fabf0-237">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="fabf0-238">L’extrait de code du fichier projet dans l’exemple suivant fait référence à un projet nommé `Project2` .</span><span class="sxs-lookup"><span data-stu-id="fabf0-238">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="fabf0-239">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="fabf0-239">Reference</span></span>

<span data-ttu-id="fabf0-240">L' `Reference` élément définit une référence à un fichier d’assembly.</span><span class="sxs-lookup"><span data-stu-id="fabf0-240">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="fabf0-241">L' `Include` attribut spécifie le nom du fichier, et les `HintPath` métadonnées spécifient le chemin d’accès à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="fabf0-241">The `Include` attribute specifies the name of the file, and the `HintPath` metadata specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a><span data-ttu-id="fabf0-242">Propriétés de restauration</span><span class="sxs-lookup"><span data-stu-id="fabf0-242">Restore properties</span></span>

<span data-ttu-id="fabf0-243">La restauration d’un package référencé installe toutes ses dépendances directes et toutes les dépendances de ces dépendances.</span><span class="sxs-lookup"><span data-stu-id="fabf0-243">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="fabf0-244">Vous pouvez personnaliser la restauration des packages en spécifiant des propriétés telles que `RestorePackagesPath` et `RestoreIgnoreFailedSources` .</span><span class="sxs-lookup"><span data-stu-id="fabf0-244">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="fabf0-245">Pour plus d’informations sur ces propriétés et d’autres, consultez [restaurer la cible](/nuget/reference/msbuild-targets#restore-target).</span><span class="sxs-lookup"><span data-stu-id="fabf0-245">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="fabf0-246">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fabf0-246">See also</span></span>

- [<span data-ttu-id="fabf0-247">Référence du schéma MSBuild</span><span class="sxs-lookup"><span data-stu-id="fabf0-247">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="fabf0-248">Propriétés MSBuild communes</span><span class="sxs-lookup"><span data-stu-id="fabf0-248">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="fabf0-249">Propriétés MSBuild pour le Pack NuGet</span><span class="sxs-lookup"><span data-stu-id="fabf0-249">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="fabf0-250">Propriétés MSBuild pour la restauration NuGet</span><span class="sxs-lookup"><span data-stu-id="fabf0-250">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="fabf0-251">Personnaliser une build</span><span class="sxs-lookup"><span data-stu-id="fabf0-251">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
