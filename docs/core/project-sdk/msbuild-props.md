---
title: Propriétés MSBuild pour Microsoft. NET. Sdk
description: Référence pour les propriétés MSBuild comprises par l’kit SDK .NET Core.
ms.date: 02/02/2020
ms.topic: reference
ms.openlocfilehash: f5dc2079bc313b8dd9fa5556cd941521a597ae38
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453810"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="e1a01-103">Propriétés MSBuild pour les projets kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="e1a01-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="e1a01-104">Cette page décrit les propriétés MSBuild pour la configuration des projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e1a01-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="e1a01-105">Cette page est un travail en cours et ne répertorie pas toutes les propriétés MSBuild utiles pour le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e1a01-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="e1a01-106">Pour obtenir la liste des propriétés MSBuild courantes, consultez [propriétés MSBuild communes](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="e1a01-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="e1a01-107">Propriétés du Framework</span><span class="sxs-lookup"><span data-stu-id="e1a01-107">Framework properties</span></span>

- [<span data-ttu-id="e1a01-108">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="e1a01-108">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)
- [<span data-ttu-id="e1a01-109">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="e1a01-109">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="e1a01-110">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="e1a01-110">TargetFrameworks</span></span>](#targetframeworks)

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="e1a01-111">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="e1a01-111">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="e1a01-112">Cette propriété s’applique uniquement aux projets qui utilisent `netstandard1.x`.</span><span class="sxs-lookup"><span data-stu-id="e1a01-112">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="e1a01-113">Elle ne s’applique pas aux projets qui utilisent `netstandard2` et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="e1a01-113">It doesn't apply to projects that use `netstandard2` and later.</span></span>

<span data-ttu-id="e1a01-114">Utilisez la propriété `NetStandardImplicitPackageVersion` lorsque vous souhaitez spécifier une version de Framework inférieure à la version de l' [ensemble de packages](../packages.md#metapackages) .</span><span class="sxs-lookup"><span data-stu-id="e1a01-114">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="e1a01-115">Le fichier projet dans l’exemple suivant cible `netstandard1.3` mais utilise la version 1.6.0 de `NETStandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="e1a01-115">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

### <a name="targetframework"></a><span data-ttu-id="e1a01-116">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="e1a01-116">TargetFramework</span></span>

<span data-ttu-id="e1a01-117">La propriété `TargetFramework` spécifie la version cible de .NET Framework pour l’application, qui référence implicitement un [repackage](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="e1a01-117">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="e1a01-118">Pour obtenir la liste des monikers du Framework cible valides, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="e1a01-118">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="e1a01-119">Pour plus d’informations, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e1a01-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="e1a01-120">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="e1a01-120">TargetFrameworks</span></span>

<span data-ttu-id="e1a01-121">Utilisez la propriété `TargetFrameworks` lorsque vous souhaitez que votre application cible plusieurs plateformes.</span><span class="sxs-lookup"><span data-stu-id="e1a01-121">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="e1a01-122">Pour obtenir la liste des monikers du Framework cible valides, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="e1a01-122">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="e1a01-123">Cette propriété est ignorée si `TargetFramework` (singulier) est spécifié.</span><span class="sxs-lookup"><span data-stu-id="e1a01-123">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="e1a01-124">Pour plus d’informations, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e1a01-124">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

## <a name="publish-properties"></a><span data-ttu-id="e1a01-125">Propriétés de publication</span><span class="sxs-lookup"><span data-stu-id="e1a01-125">Publish properties</span></span>

- [<span data-ttu-id="e1a01-126">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="e1a01-126">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="e1a01-127">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="e1a01-127">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="e1a01-128">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="e1a01-128">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="e1a01-129">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="e1a01-129">RuntimeIdentifier</span></span>

<span data-ttu-id="e1a01-130">La propriété `RuntimeIdentifier` vous permet de spécifier un [identificateur de Runtime unique (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="e1a01-130">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="e1a01-131">Le RID permet de publier un déploiement autonome.</span><span class="sxs-lookup"><span data-stu-id="e1a01-131">The RID enables publishing a self-contained deployment.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="e1a01-132">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="e1a01-132">RuntimeIdentifiers</span></span>

<span data-ttu-id="e1a01-133">La propriété `RuntimeIdentifiers` vous permet de spécifier une liste délimitée par des points-virgules des [identificateurs de Runtime (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="e1a01-133">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="e1a01-134">Utilisez cette propriété si vous devez publier pour plusieurs runtimes.</span><span class="sxs-lookup"><span data-stu-id="e1a01-134">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="e1a01-135">`RuntimeIdentifiers` est utilisé au moment de la restauration pour s’assurer que les ressources appropriées sont dans le graphique.</span><span class="sxs-lookup"><span data-stu-id="e1a01-135">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="e1a01-136">`RuntimeIdentifier` (singulier) peut fournir des builds plus rapides quand un seul Runtime est requis.</span><span class="sxs-lookup"><span data-stu-id="e1a01-136">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a><span data-ttu-id="e1a01-137">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="e1a01-137">UseAppHost</span></span>

<span data-ttu-id="e1a01-138">La propriété `UseAppHost` a été introduite dans la version 2.1.400 de l’kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e1a01-138">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="e1a01-139">Il contrôle si un exécutable natif est créé ou non pour un déploiement.</span><span class="sxs-lookup"><span data-stu-id="e1a01-139">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="e1a01-140">Un exécutable natif est requis pour les déploiements autonomes.</span><span class="sxs-lookup"><span data-stu-id="e1a01-140">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="e1a01-141">Dans .NET Core 3,0 et versions ultérieures, un fichier exécutable dépendant du Framework est créé par défaut.</span><span class="sxs-lookup"><span data-stu-id="e1a01-141">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="e1a01-142">Affectez à la propriété `UseAppHost` la valeur `false` pour désactiver la génération du fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="e1a01-142">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="e1a01-143">Pour plus d’informations sur le déploiement, consultez [déploiement d’applications .net Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="e1a01-143">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="e1a01-144">Propriétés de compilation</span><span class="sxs-lookup"><span data-stu-id="e1a01-144">Compile properties</span></span>

### <a name="langversion"></a><span data-ttu-id="e1a01-145">LangVersion</span><span class="sxs-lookup"><span data-stu-id="e1a01-145">LangVersion</span></span>

<span data-ttu-id="e1a01-146">La propriété `LangVersion` vous permet de spécifier une version spécifique du langage de programmation.</span><span class="sxs-lookup"><span data-stu-id="e1a01-146">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="e1a01-147">Par exemple, si vous souhaitez accéder aux C# fonctionnalités en version préliminaire, définissez `LangVersion` sur `preview`.</span><span class="sxs-lookup"><span data-stu-id="e1a01-147">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="e1a01-148">Pour plus d’informations, [ C# ](../../csharp/language-reference/configure-language-version.md#override-a-default)consultez contrôle de version de langage.</span><span class="sxs-lookup"><span data-stu-id="e1a01-148">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="nuget-packages"></a><span data-ttu-id="e1a01-149">Packages NuGet</span><span class="sxs-lookup"><span data-stu-id="e1a01-149">NuGet packages</span></span>

- [<span data-ttu-id="e1a01-150">PackageReference</span><span class="sxs-lookup"><span data-stu-id="e1a01-150">PackageReference</span></span>](#packagereference)

### <a name="packagereference"></a><span data-ttu-id="e1a01-151">PackageReference</span><span class="sxs-lookup"><span data-stu-id="e1a01-151">PackageReference</span></span>

<span data-ttu-id="e1a01-152">L’élément `PackageReference` vous permet de spécifier une dépendance NuGet.</span><span class="sxs-lookup"><span data-stu-id="e1a01-152">The `PackageReference` item lets you specify a NuGet dependency.</span></span> <span data-ttu-id="e1a01-153">Par exemple, vous souhaiterez peut-être référencer un package unique au lieu d’un sous- [package](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="e1a01-153">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="e1a01-154">L’attribut `Include` spécifie l’ID du package.</span><span class="sxs-lookup"><span data-stu-id="e1a01-154">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="e1a01-155">L’extrait de code du fichier projet dans l’exemple suivant référence le package [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .</span><span class="sxs-lookup"><span data-stu-id="e1a01-155">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="e1a01-156">Pour plus d’informations, consultez [références de package dans les fichiers projet](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="e1a01-156">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="pack-and-restore-targets"></a><span data-ttu-id="e1a01-157">Cibles de Pack et de restauration</span><span class="sxs-lookup"><span data-stu-id="e1a01-157">Pack and restore targets</span></span>

<span data-ttu-id="e1a01-158">MSBuild 15,1 a introduit `pack` et `restore` cibles pour la création et la restauration de packages NuGet dans le cadre d’une build.</span><span class="sxs-lookup"><span data-stu-id="e1a01-158">MSBuild 15.1 introduced `pack` and `restore` targets for creating and restoring NuGet packages as part of a build.</span></span> <span data-ttu-id="e1a01-159">Pour plus d’informations sur les propriétés MSBuild pour ces cibles, y compris `PackageTargetFallback`, consultez [NuGet Pack et Restore en tant que cibles MSBuild](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="e1a01-159">For information about the MSBuild properties for these targets, including `PackageTargetFallback`, see [NuGet pack and restore as MSBuild targets](/nuget/reference/msbuild-targets).</span></span>

## <a name="see-also"></a><span data-ttu-id="e1a01-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1a01-160">See also</span></span>

- [<span data-ttu-id="e1a01-161">Référence du schéma MSBuild</span><span class="sxs-lookup"><span data-stu-id="e1a01-161">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="e1a01-162">Propriétés MSBuild communes</span><span class="sxs-lookup"><span data-stu-id="e1a01-162">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="e1a01-163">Propriétés MSBuild pour le Pack NuGet</span><span class="sxs-lookup"><span data-stu-id="e1a01-163">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="e1a01-164">Propriétés MSBuild pour la restauration NuGet</span><span class="sxs-lookup"><span data-stu-id="e1a01-164">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="e1a01-165">Personnaliser une build</span><span class="sxs-lookup"><span data-stu-id="e1a01-165">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
