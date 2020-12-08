---
title: Propriétés MSBuild pour Microsoft. NET. Sdk
description: Référence pour les propriétés et les éléments MSBuild compris par le kit de développement logiciel (SDK) .NET.
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: 3b58fd080439c73ee30d5c8dc59c50c0410db164
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851573"
---
# <a name="msbuild-reference-for-net-sdk-projects"></a><span data-ttu-id="85050-103">Référence MSBuild pour les projets SDK .NET</span><span class="sxs-lookup"><span data-stu-id="85050-103">MSBuild reference for .NET SDK projects</span></span>

<span data-ttu-id="85050-104">Cette page est une référence pour les propriétés et les éléments MSBuild que vous pouvez utiliser pour configurer des projets .NET.</span><span class="sxs-lookup"><span data-stu-id="85050-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET projects.</span></span>

> [!NOTE]
> <span data-ttu-id="85050-105">Cette page est un travail en cours et ne répertorie pas toutes les propriétés MSBuild utiles pour le kit de développement logiciel (SDK) .NET.</span><span class="sxs-lookup"><span data-stu-id="85050-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET SDK.</span></span> <span data-ttu-id="85050-106">Pour obtenir la liste des propriétés MSBuild courantes, consultez [propriétés MSBuild communes](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="85050-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="85050-107">Propriétés du Framework</span><span class="sxs-lookup"><span data-stu-id="85050-107">Framework properties</span></span>

- [<span data-ttu-id="85050-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="85050-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="85050-109">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="85050-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="85050-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="85050-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="85050-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="85050-111">TargetFramework</span></span>

<span data-ttu-id="85050-112">La `TargetFramework` propriété spécifie la version cible de .NET Framework pour l’application.</span><span class="sxs-lookup"><span data-stu-id="85050-112">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="85050-113">Pour obtenir la liste des monikers du Framework cible valides, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="85050-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="85050-114">Pour plus d’informations, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="85050-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="85050-115">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="85050-115">TargetFrameworks</span></span>

<span data-ttu-id="85050-116">Utilisez la `TargetFrameworks` propriété lorsque vous souhaitez que votre application cible plusieurs plateformes.</span><span class="sxs-lookup"><span data-stu-id="85050-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="85050-117">Pour obtenir la liste des monikers du Framework cible valides, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="85050-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

> [!NOTE]
> <span data-ttu-id="85050-118">Cette propriété est ignorée si `TargetFramework` (singulier) est spécifié.</span><span class="sxs-lookup"><span data-stu-id="85050-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="85050-119">Pour plus d’informations, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="85050-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="85050-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="85050-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="85050-121">Cette propriété s’applique uniquement aux projets qui utilisent `netstandard1.x` .</span><span class="sxs-lookup"><span data-stu-id="85050-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="85050-122">Elle ne s’applique pas aux projets qui utilisent `netstandard2.x` .</span><span class="sxs-lookup"><span data-stu-id="85050-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="85050-123">Utilisez la `NetStandardImplicitPackageVersion` propriété lorsque vous souhaitez spécifier une version de Framework inférieure à la version de l’ensemble de packages.</span><span class="sxs-lookup"><span data-stu-id="85050-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="85050-124">Le fichier projet dans l’exemple suivant cible, `netstandard1.3` mais utilise la version 1.6.0 de `NETStandard.Library` .</span><span class="sxs-lookup"><span data-stu-id="85050-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="85050-125">Propriétés du package</span><span class="sxs-lookup"><span data-stu-id="85050-125">Package properties</span></span>

<span data-ttu-id="85050-126">Vous pouvez spécifier des propriétés telles que `PackageId` , `PackageVersion` ,, `PackageIcon` `Title` et `Description` pour décrire le package qui est créé à partir de votre projet.</span><span class="sxs-lookup"><span data-stu-id="85050-126">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="85050-127">Pour plus d’informations sur ces propriétés et d’autres, consultez [package Target](/nuget/reference/msbuild-targets#pack-target).</span><span class="sxs-lookup"><span data-stu-id="85050-127">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-and-items"></a><span data-ttu-id="85050-128">Publier les propriétés et les éléments</span><span class="sxs-lookup"><span data-stu-id="85050-128">Publish properties and items</span></span>

- [<span data-ttu-id="85050-129">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="85050-129">CopyLocalLockFileAssemblies</span></span>](#copylocallockfileassemblies)
- [<span data-ttu-id="85050-130">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="85050-130">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="85050-131">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="85050-131">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="85050-132">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="85050-132">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="85050-133">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="85050-133">UseAppHost</span></span>](#useapphost)

### <a name="copylocallockfileassemblies"></a><span data-ttu-id="85050-134">CopyLocalLockFileAssemblies</span><span class="sxs-lookup"><span data-stu-id="85050-134">CopyLocalLockFileAssemblies</span></span>

<span data-ttu-id="85050-135">La `CopyLocalLockFileAssemblies` propriété est utile pour les projets de plug-in qui ont des dépendances sur d’autres bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="85050-135">The `CopyLocalLockFileAssemblies` property is useful for plugin projects that have dependencies on other libraries.</span></span> <span data-ttu-id="85050-136">Si vous affectez à cette propriété `true` la valeur, toutes les dépendances de package NuGet sont copiées dans le répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="85050-136">If you set this property to `true`, any NuGet package dependencies are copied to the output directory.</span></span> <span data-ttu-id="85050-137">Cela signifie que vous pouvez utiliser la sortie de `dotnet build` pour exécuter votre plug-in sur n’importe quel ordinateur.</span><span class="sxs-lookup"><span data-stu-id="85050-137">That means you can use the output of `dotnet build` to run your plugin on any machine.</span></span>

```xml
<PropertyGroup>
  <CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="85050-138">Vous pouvez également utiliser `dotnet publish` pour publier la bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="85050-138">Alternatively, you can use `dotnet publish` to publish the class library.</span></span> <span data-ttu-id="85050-139">Pour plus d’informations, consultez [dotnet Publish](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="85050-139">For more information, see [dotnet publish](../tools/dotnet-publish.md).</span></span>

### <a name="runtimeidentifier"></a><span data-ttu-id="85050-140">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="85050-140">RuntimeIdentifier</span></span>

<span data-ttu-id="85050-141">La `RuntimeIdentifier` propriété vous permet de spécifier un [identificateur de Runtime unique (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="85050-141">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="85050-142">Le RID permet de publier un déploiement autonome.</span><span class="sxs-lookup"><span data-stu-id="85050-142">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="85050-143">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="85050-143">RuntimeIdentifiers</span></span>

<span data-ttu-id="85050-144">La `RuntimeIdentifiers` propriété vous permet de spécifier une liste délimitée par des points-virgules des [identificateurs de Runtime (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="85050-144">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="85050-145">Utilisez cette propriété si vous devez publier pour plusieurs runtimes.</span><span class="sxs-lookup"><span data-stu-id="85050-145">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="85050-146">`RuntimeIdentifiers` est utilisé au moment de la restauration pour s’assurer que les ressources appropriées sont dans le graphique.</span><span class="sxs-lookup"><span data-stu-id="85050-146">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="85050-147">`RuntimeIdentifier` (singulier) peut fournir des builds plus rapides quand un seul Runtime est requis.</span><span class="sxs-lookup"><span data-stu-id="85050-147">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="85050-148">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="85050-148">TrimmerRootAssembly</span></span>

<span data-ttu-id="85050-149">L' `TrimmerRootAssembly` élément vous permet d’exclure un assembly du [*découpage*](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="85050-149">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="85050-150">Le découpage est le processus qui consiste à supprimer des parties inutilisées du runtime d’une application empaquetée.</span><span class="sxs-lookup"><span data-stu-id="85050-150">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="85050-151">Dans certains cas, la suppression peut supprimer incorrectement les références requises.</span><span class="sxs-lookup"><span data-stu-id="85050-151">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="85050-152">Le code XML suivant exclut `System.Security` de la suppression de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="85050-152">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="85050-153">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="85050-153">UseAppHost</span></span>

<span data-ttu-id="85050-154">La `UseAppHost` propriété contrôle si un exécutable natif est créé ou non pour un déploiement.</span><span class="sxs-lookup"><span data-stu-id="85050-154">The `UseAppHost` property controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="85050-155">Un exécutable natif est requis pour les déploiements autonomes.</span><span class="sxs-lookup"><span data-stu-id="85050-155">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="85050-156">Dans .NET Core 3,0 et versions ultérieures, un fichier exécutable dépendant du Framework est créé par défaut.</span><span class="sxs-lookup"><span data-stu-id="85050-156">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="85050-157">Affectez à la propriété la valeur `UseAppHost` `false` pour désactiver la génération de l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="85050-157">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="85050-158">Pour plus d’informations sur le déploiement, consultez [déploiement d’applications .net](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="85050-158">For more information about deployment, see [.NET application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="85050-159">Propriétés de compilation</span><span class="sxs-lookup"><span data-stu-id="85050-159">Compile properties</span></span>

- [<span data-ttu-id="85050-160">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="85050-160">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="85050-161">LangVersion</span><span class="sxs-lookup"><span data-stu-id="85050-161">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="85050-162">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="85050-162">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="85050-163">La `EmbeddedResourceUseDependentUponConvention` propriété définit si les noms des fichiers manifestes de ressources sont générés à partir des informations de type dans les fichiers sources qui sont colocalisés avec les fichiers de ressources.</span><span class="sxs-lookup"><span data-stu-id="85050-163">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="85050-164">Par exemple, si *Form1. resx* se trouve dans le même dossier que *Form1.cs* et que `EmbeddedResourceUseDependentUponConvention` a la valeur `true` , le fichier *. Resources* généré prend son nom dans le premier type défini dans *Form1.cs*.</span><span class="sxs-lookup"><span data-stu-id="85050-164">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="85050-165">Par exemple, si `MyNamespace.Form1` est le premier type défini dans *Form1.cs*, le nom de fichier généré est *MyNamespace. Form1. Resources*.</span><span class="sxs-lookup"><span data-stu-id="85050-165">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="85050-166">Si `LogicalName` `ManifestResourceName` `DependentUpon` les métadonnées, ou sont spécifiées pour un `EmbeddedResource` élément, le nom de fichier manifeste généré pour ce fichier de ressources est basé sur ces métadonnées à la place.</span><span class="sxs-lookup"><span data-stu-id="85050-166">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="85050-167">Par défaut, dans un nouveau projet .NET, cette propriété a la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="85050-167">By default, in a new .NET project, this property is set to `true`.</span></span> <span data-ttu-id="85050-168">Si la valeur `false` est définie sur, et si aucune `LogicalName` `ManifestResourceName` `DependentUpon` métadonnée n’est spécifiée pour l' `EmbeddedResource` élément dans le fichier projet, le nom du fichier manifeste de la ressource est basé sur l’espace de noms racine du projet et le chemin d’accès relatif au fichier *. resx* .</span><span class="sxs-lookup"><span data-stu-id="85050-168">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="85050-169">Pour plus d’informations, consultez [Comment les fichiers manifestes de ressources sont nommés](../resources/manifest-file-names.md).</span><span class="sxs-lookup"><span data-stu-id="85050-169">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="85050-170">LangVersion</span><span class="sxs-lookup"><span data-stu-id="85050-170">LangVersion</span></span>

<span data-ttu-id="85050-171">La `LangVersion` propriété vous permet de spécifier une version du langage de programmation spécifique.</span><span class="sxs-lookup"><span data-stu-id="85050-171">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="85050-172">Par exemple, si vous souhaitez accéder aux fonctionnalités de la version préliminaire de C#, affectez à la valeur `LangVersion` `preview` .</span><span class="sxs-lookup"><span data-stu-id="85050-172">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="85050-173">Pour plus d’informations, consultez contrôle de [version du langage C#](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="85050-173">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="code-analysis-properties"></a><span data-ttu-id="85050-174">Propriétés de l’analyse du code</span><span class="sxs-lookup"><span data-stu-id="85050-174">Code analysis properties</span></span>

### <a name="analysislevel"></a><span data-ttu-id="85050-175">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="85050-175">AnalysisLevel</span></span>

<span data-ttu-id="85050-176">La `AnalysisLevel` propriété vous permet de spécifier un niveau d’analyse du code.</span><span class="sxs-lookup"><span data-stu-id="85050-176">The `AnalysisLevel` property lets you specify a code analysis level.</span></span> <span data-ttu-id="85050-177">Par exemple, si vous souhaitez accéder à l’aperçu des analyseurs de code, affectez à la valeur `AnalysisLevel` `preview` .</span><span class="sxs-lookup"><span data-stu-id="85050-177">For example, if you want access to preview code analyzers, set `AnalysisLevel` to `preview`.</span></span> <span data-ttu-id="85050-178">La valeur par défaut est `latest`.</span><span class="sxs-lookup"><span data-stu-id="85050-178">The default value is `latest`.</span></span>

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

<span data-ttu-id="85050-179">Le tableau suivant présente les options disponibles.</span><span class="sxs-lookup"><span data-stu-id="85050-179">The following table shows the available options.</span></span>

| <span data-ttu-id="85050-180">Valeur</span><span class="sxs-lookup"><span data-stu-id="85050-180">Value</span></span> | <span data-ttu-id="85050-181">Signification</span><span class="sxs-lookup"><span data-stu-id="85050-181">Meaning</span></span> |
|-|-|
| `latest` | <span data-ttu-id="85050-182">Les derniers analyseurs de code qui ont été publiés sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="85050-182">The latest code analyzers that have been released are used.</span></span> <span data-ttu-id="85050-183">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="85050-183">This is the default.</span></span> |
| `preview` | <span data-ttu-id="85050-184">Les derniers analyseurs de code sont utilisés, même s’ils sont en version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="85050-184">The latest code analyzers are used, even if they are in preview.</span></span> |
| `5.0` | <span data-ttu-id="85050-185">L’ensemble de règles activé pour la version .NET 5,0 est utilisé, même si des règles plus récentes sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="85050-185">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |
| `5` | <span data-ttu-id="85050-186">L’ensemble de règles activé pour la version .NET 5,0 est utilisé, même si des règles plus récentes sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="85050-186">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |

### <a name="analysismode"></a><span data-ttu-id="85050-187">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="85050-187">AnalysisMode</span></span>

<span data-ttu-id="85050-188">À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET est fourni avec toutes les [règles de qualité du code « ca »](../../fundamentals/code-analysis/quality-rules/index.md).</span><span class="sxs-lookup"><span data-stu-id="85050-188">Starting with .NET 5.0, the .NET SDK ships with all of the ["CA" code quality rules](../../fundamentals/code-analysis/quality-rules/index.md).</span></span> <span data-ttu-id="85050-189">Par défaut, seules [certaines règles sont activées](../../fundamentals/code-analysis/overview.md#enabled-rules) en tant qu’avertissements de génération.</span><span class="sxs-lookup"><span data-stu-id="85050-189">By default, only [some rules are enabled](../../fundamentals/code-analysis/overview.md#enabled-rules) as build warnings.</span></span> <span data-ttu-id="85050-190">La `AnalysisMode` propriété vous permet de personnaliser l’ensemble des règles qui sont activées par défaut.</span><span class="sxs-lookup"><span data-stu-id="85050-190">The `AnalysisMode` property lets you customize the set of rules that are enabled by default.</span></span> <span data-ttu-id="85050-191">Vous pouvez basculer vers un mode d’analyse plus agressif ou un mode d’analyse plus prudent (abonnement).</span><span class="sxs-lookup"><span data-stu-id="85050-191">You can either switch to a more aggressive (opt-out) analysis mode or a more conservative (opt-in) analysis mode.</span></span> <span data-ttu-id="85050-192">Par exemple, si vous souhaitez activer toutes les règles par défaut en tant qu’avertissements de build, affectez la valeur à `AllEnabledByDefault` .</span><span class="sxs-lookup"><span data-stu-id="85050-192">For example, if you want to enable all rules by default as build warnings, set the value to `AllEnabledByDefault`.</span></span>

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
</PropertyGroup>
```

<span data-ttu-id="85050-193">Le tableau suivant présente les options disponibles.</span><span class="sxs-lookup"><span data-stu-id="85050-193">The following table shows the available options.</span></span>

| <span data-ttu-id="85050-194">Valeur</span><span class="sxs-lookup"><span data-stu-id="85050-194">Value</span></span> | <span data-ttu-id="85050-195">Signification</span><span class="sxs-lookup"><span data-stu-id="85050-195">Meaning</span></span> |
|-|-|
| `Default` | <span data-ttu-id="85050-196">Mode par défaut, où certaines règles sont activées en tant qu’avertissements de build, certaines règles sont activées en tant que suggestions de l’IDE Visual Studio, et le reste est désactivé.</span><span class="sxs-lookup"><span data-stu-id="85050-196">Default mode, where certain rules are enabled as build warnings, certain rules are enabled as Visual Studio IDE suggestions, and the remainder are disabled.</span></span> |
| `AllEnabledByDefault` | <span data-ttu-id="85050-197">Mode agressif ou opt-out, où toutes les règles sont activées par défaut en tant qu’avertissements de génération.</span><span class="sxs-lookup"><span data-stu-id="85050-197">Aggressive or opt-out mode, where all rules are enabled by default as build warnings.</span></span> <span data-ttu-id="85050-198">Vous pouvez [choisir](../../fundamentals/code-analysis/configuration-options.md) de désactiver les règles individuelles de manière sélective pour les désactiver.</span><span class="sxs-lookup"><span data-stu-id="85050-198">You can selectively [opt out](../../fundamentals/code-analysis/configuration-options.md) of individual rules to disable them.</span></span> |
| `AllDisabledByDefault` | <span data-ttu-id="85050-199">Mode conservateur ou opt-in, où toutes les règles sont désactivées par défaut.</span><span class="sxs-lookup"><span data-stu-id="85050-199">Conservative or opt-in mode, where all rules are disabled by default.</span></span> <span data-ttu-id="85050-200">Vous pouvez [choisir](../../fundamentals/code-analysis/configuration-options.md) des règles individuelles pour les activer.</span><span class="sxs-lookup"><span data-stu-id="85050-200">You can selectively [opt into](../../fundamentals/code-analysis/configuration-options.md) individual rules to enable them.</span></span> |

### <a name="codeanalysistreatwarningsaserrors"></a><span data-ttu-id="85050-201">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="85050-201">CodeAnalysisTreatWarningsAsErrors</span></span>

<span data-ttu-id="85050-202">La `CodeAnalysisTreatWarningsAsErrors` propriété vous permet de configurer si les avertissements d’analyse de la qualité du code (CAXXXX) doivent être traités comme des avertissements et rompre la génération.</span><span class="sxs-lookup"><span data-stu-id="85050-202">The `CodeAnalysisTreatWarningsAsErrors` property lets you configure whether code quality analysis warnings (CAxxxx) should be treated as warnings and break the build.</span></span> <span data-ttu-id="85050-203">Si vous utilisez l' `-warnaserror` indicateur lorsque vous générez vos projets, les avertissements de l’analyse de la [qualité du code .net](../../fundamentals/code-analysis/overview.md#code-quality-analysis) sont également traités comme des erreurs.</span><span class="sxs-lookup"><span data-stu-id="85050-203">If you use the `-warnaserror` flag when you build your projects, [.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) warnings are also treated as errors.</span></span> <span data-ttu-id="85050-204">Si vous ne souhaitez pas que les avertissements d’analyse de la qualité du code soient traités comme des erreurs, vous pouvez définir la `CodeAnalysisTreatWarningsAsErrors` propriété MSBuild sur `false` dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="85050-204">If you do not want code quality analysis warnings to be treated as errors, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a><span data-ttu-id="85050-205">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="85050-205">EnableNETAnalyzers</span></span>

<span data-ttu-id="85050-206">L’analyse de la [qualité du code .net](../../fundamentals/code-analysis/overview.md#code-quality-analysis) est activée, par défaut, pour les projets qui ciblent .net 5,0 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="85050-206">[.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="85050-207">Vous pouvez activer l’analyse du code .NET pour les projets qui ciblent des versions antérieures de .NET en affectant à la propriété la valeur `EnableNETAnalyzers` `true` .</span><span class="sxs-lookup"><span data-stu-id="85050-207">You can enable .NET code analysis for projects that target earlier versions of .NET by setting the `EnableNETAnalyzers` property to `true`.</span></span> <span data-ttu-id="85050-208">Pour désactiver l’analyse du code dans un projet, affectez la valeur à cette propriété `false` .</span><span class="sxs-lookup"><span data-stu-id="85050-208">To disable code analysis in any project, set this property to `false`.</span></span>

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="85050-209">Une autre façon d’activer l’analyse du code .NET sur les projets qui ciblent les versions .NET antérieures à .NET 5,0 consiste à définir la propriété [AnalysisLevel](#analysislevel) sur `latest` .</span><span class="sxs-lookup"><span data-stu-id="85050-209">Another way to enable .NET code analysis on projects that target .NET versions prior to .NET 5.0 is to set the [AnalysisLevel](#analysislevel) property to `latest`.</span></span>

### <a name="enforcecodestyleinbuild"></a><span data-ttu-id="85050-210">EnforceCodeStyleInBuild</span><span class="sxs-lookup"><span data-stu-id="85050-210">EnforceCodeStyleInBuild</span></span>

> [!NOTE]
> <span data-ttu-id="85050-211">Cette fonctionnalité est actuellement expérimentale et peut changer entre les versions .NET 5 et .NET 6.</span><span class="sxs-lookup"><span data-stu-id="85050-211">This feature is currently experimental and may change between the .NET 5 and .NET 6 releases.</span></span>

<span data-ttu-id="85050-212">L' [analyse du style de code .net](../../fundamentals/code-analysis/overview.md#code-style-analysis) est désactivée, par défaut, à la génération pour tous les projets .net.</span><span class="sxs-lookup"><span data-stu-id="85050-212">[.NET code style analysis](../../fundamentals/code-analysis/overview.md#code-style-analysis) is disabled, by default, on build for all .NET projects.</span></span> <span data-ttu-id="85050-213">Vous pouvez activer l’analyse de style de code pour les projets .NET en affectant à la propriété la valeur `EnforceCodeStyleInBuild` `true` .</span><span class="sxs-lookup"><span data-stu-id="85050-213">You can enable code style analysis for .NET projects by setting the `EnforceCodeStyleInBuild` property to `true`.</span></span>

```xml
<PropertyGroup>
  <EnforceCodeStyleInBuild>true</EnforceCodeStyleInBuild>
</PropertyGroup>
```

<span data-ttu-id="85050-214">Toutes les règles de style de code qui sont [configurées](../../fundamentals/code-analysis/overview.md#code-style-analysis) pour être des avertissements ou des erreurs sont exécutées lors des violations de la build et des rapports.</span><span class="sxs-lookup"><span data-stu-id="85050-214">All code style rules that are [configured](../../fundamentals/code-analysis/overview.md#code-style-analysis) to be warnings or errors will execute on build and report violations.</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="85050-215">Propriétés de configuration au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="85050-215">Run-time configuration properties</span></span>

<span data-ttu-id="85050-216">Vous pouvez configurer certains comportements au moment de l’exécution en spécifiant des propriétés MSBuild dans le fichier projet de l’application.</span><span class="sxs-lookup"><span data-stu-id="85050-216">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="85050-217">Pour plus d’informations sur les autres méthodes de configuration du comportement au moment de l’exécution, consultez [paramètres de configuration](../run-time-config/index.md)de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="85050-217">For information about other ways of configuring run-time behavior, see [Run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="85050-218">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="85050-218">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="85050-219">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="85050-219">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="85050-220">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="85050-220">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="85050-221">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="85050-221">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="85050-222">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="85050-222">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="85050-223">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="85050-223">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="85050-224">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="85050-224">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="85050-225">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="85050-225">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="85050-226">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="85050-226">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="85050-227">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="85050-227">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="85050-228">La `ConcurrentGarbageCollection` propriété configure si l' [garbage collection d’arrière-plan (simultané)](../../standard/garbage-collection/background-gc.md) est activée.</span><span class="sxs-lookup"><span data-stu-id="85050-228">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="85050-229">Affectez la valeur `false` à pour désactiver les garbage collection d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="85050-229">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="85050-230">Pour plus d’informations, consultez [Background gc](../run-time-config/garbage-collector.md#background-gc).</span><span class="sxs-lookup"><span data-stu-id="85050-230">For more information, see [Background GC](../run-time-config/garbage-collector.md#background-gc).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="85050-231">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="85050-231">InvariantGlobalization</span></span>

<span data-ttu-id="85050-232">La `InvariantGlobalization` propriété configure si l’application s’exécute en mode de *globalisation invariant* , ce qui signifie qu’elle n’a pas accès aux données spécifiques à la culture.</span><span class="sxs-lookup"><span data-stu-id="85050-232">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="85050-233">Affectez à la valeur la valeur `true` pour qu’elle s’exécute en mode de globalisation-indifférent.</span><span class="sxs-lookup"><span data-stu-id="85050-233">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="85050-234">Pour plus d’informations, consultez [mode indifférent](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="85050-234">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="85050-235">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="85050-235">RetainVMGarbageCollection</span></span>

<span data-ttu-id="85050-236">La `RetainVMGarbageCollection` propriété configure le garbage collector pour placer les segments de mémoire supprimés sur une liste d’attente pour une utilisation ultérieure ou les libérer.</span><span class="sxs-lookup"><span data-stu-id="85050-236">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="85050-237">La définition de la valeur `true` indique au garbage collector de placer les segments sur une liste d’attente.</span><span class="sxs-lookup"><span data-stu-id="85050-237">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="85050-238">Pour plus d’informations, consultez [conserver la machine virtuelle](../run-time-config/garbage-collector.md#retain-vm).</span><span class="sxs-lookup"><span data-stu-id="85050-238">For more information, see [Retain VM](../run-time-config/garbage-collector.md#retain-vm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="85050-239">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="85050-239">ServerGarbageCollection</span></span>

<span data-ttu-id="85050-240">La `ServerGarbageCollection` propriété configure si l’application utilise des [garbage collection de station de travail ou des garbage collection de serveur](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="85050-240">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="85050-241">Définissez la valeur sur `true` sur utiliser le garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="85050-241">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="85050-242">Pour plus d’informations, consultez [station de travail et serveur](../run-time-config/garbage-collector.md#workstation-vs-server).</span><span class="sxs-lookup"><span data-stu-id="85050-242">For more information, see [Workstation vs. server](../run-time-config/garbage-collector.md#workstation-vs-server).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="85050-243">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="85050-243">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="85050-244">La `ThreadPoolMaxThreads` propriété configure le nombre maximal de threads pour le pool de threads de travail.</span><span class="sxs-lookup"><span data-stu-id="85050-244">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="85050-245">Pour plus d’informations, consultez [nombre maximal de threads](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="85050-245">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="85050-246">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="85050-246">ThreadPoolMinThreads</span></span>

<span data-ttu-id="85050-247">La `ThreadPoolMinThreads` propriété configure le nombre minimal de threads pour le pool de threads de travail.</span><span class="sxs-lookup"><span data-stu-id="85050-247">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="85050-248">Pour plus d’informations, consultez [minimum threads](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="85050-248">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="85050-249">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="85050-249">TieredCompilation</span></span>

<span data-ttu-id="85050-250">La `TieredCompilation` propriété configure si le compilateur juste-à-temps (JIT) utilise la [compilation à plusieurs niveaux](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="85050-250">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="85050-251">Définissez la valeur sur `false` pour désactiver la compilation à plusieurs niveaux.</span><span class="sxs-lookup"><span data-stu-id="85050-251">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="85050-252">Pour plus d’informations, consultez compilation à plusieurs [niveaux](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="85050-252">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="85050-253">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="85050-253">TieredCompilationQuickJit</span></span>

<span data-ttu-id="85050-254">La `TieredCompilationQuickJit` propriété configure si le compilateur JIT utilise Quick JIT.</span><span class="sxs-lookup"><span data-stu-id="85050-254">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="85050-255">Définissez la valeur sur `false` pour désactiver le JIT rapide.</span><span class="sxs-lookup"><span data-stu-id="85050-255">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="85050-256">Pour plus d’informations, consultez [Quick JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="85050-256">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="85050-257">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="85050-257">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="85050-258">La `TieredCompilationQuickJitForLoops` propriété configure si le compilateur JIT utilise le JIT rapide sur les méthodes qui contiennent des boucles.</span><span class="sxs-lookup"><span data-stu-id="85050-258">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="85050-259">Affectez la valeur `true` à pour activer le JIT rapide sur les méthodes qui contiennent des boucles.</span><span class="sxs-lookup"><span data-stu-id="85050-259">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="85050-260">Pour plus d’informations, consultez [Quick JIT for Loops](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="85050-260">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a><span data-ttu-id="85050-261">Propriétés et éléments de référence</span><span class="sxs-lookup"><span data-stu-id="85050-261">Reference properties and items</span></span>

- [<span data-ttu-id="85050-262">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="85050-262">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="85050-263">PackageReference</span><span class="sxs-lookup"><span data-stu-id="85050-263">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="85050-264">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="85050-264">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="85050-265">Référence</span><span class="sxs-lookup"><span data-stu-id="85050-265">Reference</span></span>](#reference)
- [<span data-ttu-id="85050-266">Propriétés liées à la restauration</span><span class="sxs-lookup"><span data-stu-id="85050-266">Restore-related properties</span></span>](#restore-related-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="85050-267">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="85050-267">AssetTargetFallback</span></span>

<span data-ttu-id="85050-268">La `AssetTargetFallback` propriété vous permet de spécifier des versions de Framework compatibles supplémentaires pour les références de projet et les packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="85050-268">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="85050-269">Par exemple, si vous spécifiez une dépendance de package à l’aide de `PackageReference` mais que ce package ne contient pas de ressources compatibles avec les projets `TargetFramework` , la `AssetTargetFallback` propriété entre en lecture.</span><span class="sxs-lookup"><span data-stu-id="85050-269">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="85050-270">La compatibilité du package référencé est revérifiée à l’aide de chaque version cible de .NET Framework spécifiée dans `AssetTargetFallback` .</span><span class="sxs-lookup"><span data-stu-id="85050-270">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="85050-271">Vous pouvez définir la `AssetTargetFallback` propriété sur une ou plusieurs [versions du Framework cible](../../standard/frameworks.md#supported-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="85050-271">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="85050-272">PackageReference</span><span class="sxs-lookup"><span data-stu-id="85050-272">PackageReference</span></span>

<span data-ttu-id="85050-273">L' `PackageReference` élément définit une référence à un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="85050-273">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="85050-274">L’attribut `Include` spécifie l’ID du package.</span><span class="sxs-lookup"><span data-stu-id="85050-274">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="85050-275">L' `Version` attribut spécifie la version ou la plage de versions.</span><span class="sxs-lookup"><span data-stu-id="85050-275">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="85050-276">Pour plus d’informations sur la spécification d’une version minimale, d’une version maximale, d’une plage ou d’une correspondance exacte, consultez [plages de versions](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="85050-276">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="85050-277">Vous pouvez également ajouter les métadonnées suivantes à une référence de projet : `IncludeAssets` , `ExcludeAssets` et `PrivateAssets` .</span><span class="sxs-lookup"><span data-stu-id="85050-277">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="85050-278">L’extrait de code du fichier projet dans l’exemple suivant référence le package [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .</span><span class="sxs-lookup"><span data-stu-id="85050-278">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="85050-279">Pour plus d’informations, consultez [références de package dans les fichiers projet](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="85050-279">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="projectreference"></a><span data-ttu-id="85050-280">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="85050-280">ProjectReference</span></span>

<span data-ttu-id="85050-281">L' `ProjectReference` élément définit une référence à un autre projet.</span><span class="sxs-lookup"><span data-stu-id="85050-281">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="85050-282">Le projet référencé est ajouté en tant que dépendance de package NuGet, autrement dit, il est traité de la même façon qu’un `PackageReference` .</span><span class="sxs-lookup"><span data-stu-id="85050-282">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="85050-283">L' `Include` attribut spécifie le chemin d’accès au projet.</span><span class="sxs-lookup"><span data-stu-id="85050-283">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="85050-284">Vous pouvez également ajouter les métadonnées suivantes à une référence de projet : `IncludeAssets` , `ExcludeAssets` et `PrivateAssets` .</span><span class="sxs-lookup"><span data-stu-id="85050-284">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="85050-285">L’extrait de code du fichier projet dans l’exemple suivant fait référence à un projet nommé `Project2` .</span><span class="sxs-lookup"><span data-stu-id="85050-285">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="85050-286">Référence</span><span class="sxs-lookup"><span data-stu-id="85050-286">Reference</span></span>

<span data-ttu-id="85050-287">L' `Reference` élément définit une référence à un fichier d’assembly.</span><span class="sxs-lookup"><span data-stu-id="85050-287">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="85050-288">L' `Include` attribut spécifie le nom du fichier, et les `HintPath` métadonnées spécifient le chemin d’accès à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="85050-288">The `Include` attribute specifies the name of the file, and the `HintPath` metadata specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-related-properties"></a><span data-ttu-id="85050-289">Propriétés liées à la restauration</span><span class="sxs-lookup"><span data-stu-id="85050-289">Restore-related properties</span></span>

<span data-ttu-id="85050-290">La restauration d’un package référencé installe toutes ses dépendances directes et toutes les dépendances de ces dépendances.</span><span class="sxs-lookup"><span data-stu-id="85050-290">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="85050-291">Vous pouvez personnaliser la restauration des packages en spécifiant des propriétés telles que `RestorePackagesPath` et `RestoreIgnoreFailedSources` .</span><span class="sxs-lookup"><span data-stu-id="85050-291">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="85050-292">Pour plus d’informations sur ces propriétés et d’autres, consultez [restaurer la cible](/nuget/reference/msbuild-targets#restore-target).</span><span class="sxs-lookup"><span data-stu-id="85050-292">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="hosting-properties-and-items"></a><span data-ttu-id="85050-293">Propriétés et éléments d’hébergement</span><span class="sxs-lookup"><span data-stu-id="85050-293">Hosting properties and items</span></span>

- [<span data-ttu-id="85050-294">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="85050-294">EnableComHosting</span></span>](#enablecomhosting)
- [<span data-ttu-id="85050-295">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="85050-295">EnableDynamicLoading</span></span>](#enabledynamicloading)

### <a name="enablecomhosting"></a><span data-ttu-id="85050-296">EnableComHosting</span><span class="sxs-lookup"><span data-stu-id="85050-296">EnableComHosting</span></span>

<span data-ttu-id="85050-297">La `EnableComHosting` propriété indique qu’un assembly fournit un serveur com.</span><span class="sxs-lookup"><span data-stu-id="85050-297">The `EnableComHosting` property indicates that an assembly provides a COM server.</span></span> <span data-ttu-id="85050-298">Le `EnableComHosting` fait d’affecter à la valeur `true` implique également que [EnableDynamicLoading](#enabledynamicloading) est `true` .</span><span class="sxs-lookup"><span data-stu-id="85050-298">Setting the `EnableComHosting` to `true` also implies that [EnableDynamicLoading](#enabledynamicloading) is `true`.</span></span>

```xml
<PropertyGroup>
  <EnableComHosting>True</EnableComHosting>
</PropertyGroup>
```

<span data-ttu-id="85050-299">Pour plus d’informations, consultez [exposer des composants .net à com](../native-interop/expose-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="85050-299">For more information, see [Expose .NET components to COM](../native-interop/expose-components-to-com.md).</span></span>

### <a name="enabledynamicloading"></a><span data-ttu-id="85050-300">EnableDynamicLoading</span><span class="sxs-lookup"><span data-stu-id="85050-300">EnableDynamicLoading</span></span>

<span data-ttu-id="85050-301">La `EnableDynamicLoading` propriété indique qu’un assembly est un composant chargé dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="85050-301">The `EnableDynamicLoading` property indicates that an assembly is a dynamically loaded component.</span></span> <span data-ttu-id="85050-302">Le composant peut être une bibliothèque [com](/windows/win32/com/the-component-object-model) ou une bibliothèque non-com qui peut être [utilisée à partir d’un hôte natif](../tutorials/netcore-hosting.md).</span><span class="sxs-lookup"><span data-stu-id="85050-302">The component could be a [COM library](/windows/win32/com/the-component-object-model) or a non-COM library that can be [used from a native host](../tutorials/netcore-hosting.md).</span></span> <span data-ttu-id="85050-303">L’affectation de la valeur à cette propriété `true` a les effets suivants :</span><span class="sxs-lookup"><span data-stu-id="85050-303">Setting this property to `true` has the following effects:</span></span>

- <span data-ttu-id="85050-304">Un *.runtimeconfig.jssur le* fichier est généré.</span><span class="sxs-lookup"><span data-stu-id="85050-304">A *.runtimeconfig.json* file is generated.</span></span>
- <span data-ttu-id="85050-305">La [restauration par progression](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) est définie sur `LatestMinor` .</span><span class="sxs-lookup"><span data-stu-id="85050-305">[Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) is set to `LatestMinor`.</span></span>
- <span data-ttu-id="85050-306">Les références NuGet sont copiées localement.</span><span class="sxs-lookup"><span data-stu-id="85050-306">NuGet references are copied locally.</span></span>

```xml
<PropertyGroup>
  <EnableDynamicLoading>true</EnableDynamicLoading>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="85050-307">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85050-307">See also</span></span>

- [<span data-ttu-id="85050-308">Référence du schéma MSBuild</span><span class="sxs-lookup"><span data-stu-id="85050-308">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="85050-309">Propriétés MSBuild communes</span><span class="sxs-lookup"><span data-stu-id="85050-309">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="85050-310">Propriétés MSBuild pour le Pack NuGet</span><span class="sxs-lookup"><span data-stu-id="85050-310">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="85050-311">Propriétés MSBuild pour la restauration NuGet</span><span class="sxs-lookup"><span data-stu-id="85050-311">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="85050-312">Personnaliser une build</span><span class="sxs-lookup"><span data-stu-id="85050-312">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
