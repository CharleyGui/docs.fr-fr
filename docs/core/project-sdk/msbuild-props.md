---
title: Propriétés MSBuild pour Microsoft.NET.Sdk
description: Référence pour les propriétés MSBuild qui sont compris par le .NET Core SDK.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: d4a204a1e0216313418d278ec3bd333f72db8751
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399181"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="86da4-103">Propriétés MSBuild pour les projets SDK de base .NET</span><span class="sxs-lookup"><span data-stu-id="86da4-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="86da4-104">Cette page décrit les propriétés MSBuild pour configurer des projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="86da4-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="86da4-105">Cette page est un travail en cours et n’énumère pas toutes les propriétés utiles MSBuild pour le .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="86da4-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="86da4-106">Pour une liste des propriétés COMMUNES MSBuild, voir [propriétés communes MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="86da4-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="86da4-107">Propriétés-cadres</span><span class="sxs-lookup"><span data-stu-id="86da4-107">Framework properties</span></span>

- [<span data-ttu-id="86da4-108">TargetFramework (TargetFramework)</span><span class="sxs-lookup"><span data-stu-id="86da4-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="86da4-109">TargetFrameworks (TargetFrameworks)</span><span class="sxs-lookup"><span data-stu-id="86da4-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="86da4-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="86da4-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="86da4-111">TargetFramework (TargetFramework)</span><span class="sxs-lookup"><span data-stu-id="86da4-111">TargetFramework</span></span>

<span data-ttu-id="86da4-112">La `TargetFramework` propriété spécifie la version cadre cible de l’application, qui fait implicitement référence à un [métapackage](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="86da4-112">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="86da4-113">Pour une liste de nom-cadre cible valide, voir [les cadres Target dans les projets de type SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="86da4-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="86da4-114">Pour plus d’informations, voir [les cadres Target dans les projets de style SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="86da4-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="86da4-115">TargetFrameworks (TargetFrameworks)</span><span class="sxs-lookup"><span data-stu-id="86da4-115">TargetFrameworks</span></span>

<span data-ttu-id="86da4-116">Utilisez `TargetFrameworks` la propriété lorsque vous souhaitez que votre application cible plusieurs plates-formes.</span><span class="sxs-lookup"><span data-stu-id="86da4-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="86da4-117">Pour une liste de nom-cadre cible valide, voir [les cadres Target dans les projets de type SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="86da4-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="86da4-118">Cette propriété est `TargetFramework` ignorée si (singulier) est spécifié.</span><span class="sxs-lookup"><span data-stu-id="86da4-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="86da4-119">Pour plus d’informations, voir [les cadres Target dans les projets de style SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="86da4-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="86da4-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="86da4-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="86da4-121">Cette propriété ne s’applique qu’aux projets utilisant `netstandard1.x`.</span><span class="sxs-lookup"><span data-stu-id="86da4-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="86da4-122">Il ne s’applique pas `netstandard2.x`aux projets qui utilisent .</span><span class="sxs-lookup"><span data-stu-id="86da4-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="86da4-123">Utilisez `NetStandardImplicitPackageVersion` la propriété lorsque vous souhaitez spécifier une version-cadre inférieure à la version [métapackage.](../packages.md#metapackages)</span><span class="sxs-lookup"><span data-stu-id="86da4-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="86da4-124">Le fichier de projet `netstandard1.3` dans l’exemple suivant vise mais utilise `NETStandard.Library`la version 1.6.0 de .</span><span class="sxs-lookup"><span data-stu-id="86da4-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a><span data-ttu-id="86da4-125">Propriétés de publication</span><span class="sxs-lookup"><span data-stu-id="86da4-125">Publish properties</span></span>

- [<span data-ttu-id="86da4-126">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="86da4-126">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="86da4-127">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="86da4-127">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="86da4-128">UtiliserAppHost</span><span class="sxs-lookup"><span data-stu-id="86da4-128">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="86da4-129">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="86da4-129">RuntimeIdentifier</span></span>

<span data-ttu-id="86da4-130">La `RuntimeIdentifier` propriété vous permet de spécifier un [identifiant d’exécution unique (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="86da4-130">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="86da4-131">Le RID permet de publier un déploiement autonome.</span><span class="sxs-lookup"><span data-stu-id="86da4-131">The RID enables publishing a self-contained deployment.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="86da4-132">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="86da4-132">RuntimeIdentifiers</span></span>

<span data-ttu-id="86da4-133">La `RuntimeIdentifiers` propriété vous permet de spécifier une liste d’identifiants de [temps d’exécution (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="86da4-133">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="86da4-134">Utilisez cette propriété si vous avez besoin de publier pour plusieurs runtimes.</span><span class="sxs-lookup"><span data-stu-id="86da4-134">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="86da4-135">`RuntimeIdentifiers`est utilisé au moment de la restauration pour s’assurer que les bons actifs sont dans le graphique.</span><span class="sxs-lookup"><span data-stu-id="86da4-135">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="86da4-136">`RuntimeIdentifier`(singulier) peut fournir des constructions plus rapides quand un seul temps d’exécution est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="86da4-136">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a><span data-ttu-id="86da4-137">UtiliserAppHost</span><span class="sxs-lookup"><span data-stu-id="86da4-137">UseAppHost</span></span>

<span data-ttu-id="86da4-138">La `UseAppHost` propriété a été introduite dans la version 2.1.400 du .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="86da4-138">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="86da4-139">Il contrôle si un natif exécutable est créé pour un déploiement.</span><span class="sxs-lookup"><span data-stu-id="86da4-139">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="86da4-140">Un autochtone exécutable est nécessaire pour les déploiements autonomes.</span><span class="sxs-lookup"><span data-stu-id="86da4-140">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="86da4-141">Dans .NET Core 3.0 et les versions ultérieures, un cadre dépendant exécutable est créé par défaut.</span><span class="sxs-lookup"><span data-stu-id="86da4-141">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="86da4-142">Définissez `UseAppHost` la `false` propriété pour désactiver la génération de l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="86da4-142">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="86da4-143">Pour plus d’informations sur le déploiement, voir [déploiement d’applications .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="86da4-143">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="86da4-144">Propriétés Compile</span><span class="sxs-lookup"><span data-stu-id="86da4-144">Compile properties</span></span>

### <a name="langversion"></a><span data-ttu-id="86da4-145">LangVersion (LangVersion)</span><span class="sxs-lookup"><span data-stu-id="86da4-145">LangVersion</span></span>

<span data-ttu-id="86da4-146">La `LangVersion` propriété vous permet de spécifier une version linguistique de programmation spécifique.</span><span class="sxs-lookup"><span data-stu-id="86da4-146">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="86da4-147">Par exemple, si vous souhaitez accéder aux `LangVersion` `preview`fonctionnalités d’aperçu de C, définissez pour .</span><span class="sxs-lookup"><span data-stu-id="86da4-147">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="86da4-148">Pour plus d’informations, voir [la version linguistique C .](../../csharp/language-reference/configure-language-version.md#override-a-default)</span><span class="sxs-lookup"><span data-stu-id="86da4-148">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="nuget-packages"></a><span data-ttu-id="86da4-149">Packages NuGet</span><span class="sxs-lookup"><span data-stu-id="86da4-149">NuGet packages</span></span>

- [<span data-ttu-id="86da4-150">PackageReference</span><span class="sxs-lookup"><span data-stu-id="86da4-150">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="86da4-151">AssetTargetFallback (en)</span><span class="sxs-lookup"><span data-stu-id="86da4-151">AssetTargetFallback</span></span>](#assettargetfallback)

### <a name="packagereference"></a><span data-ttu-id="86da4-152">PackageReference</span><span class="sxs-lookup"><span data-stu-id="86da4-152">PackageReference</span></span>

<span data-ttu-id="86da4-153">L’article `PackageReference` vous permet de spécifier une dépendance NuGet.</span><span class="sxs-lookup"><span data-stu-id="86da4-153">The `PackageReference` item lets you specify a NuGet dependency.</span></span> <span data-ttu-id="86da4-154">Par exemple, vous pouvez faire référence à un seul paquet au lieu d’un [métapackage](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="86da4-154">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="86da4-155">L’attribut `Include` spécifie l’ID du package.</span><span class="sxs-lookup"><span data-stu-id="86da4-155">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="86da4-156">L’extrait de fichier de projet dans l’exemple suivant fait référence au paquet [System.Runtime.](https://www.nuget.org/packages/System.Runtime/)</span><span class="sxs-lookup"><span data-stu-id="86da4-156">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="86da4-157">Pour plus d’informations, voir [références Paquet dans les fichiers de projet](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="86da4-157">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="assettargetfallback"></a><span data-ttu-id="86da4-158">AssetTargetFallback (en)</span><span class="sxs-lookup"><span data-stu-id="86da4-158">AssetTargetFallback</span></span>

<span data-ttu-id="86da4-159">La `AssetTargetFallback` propriété vous permet de spécifier des versions-cadres compatibles supplémentaires pour les projets que vos références de projet et les forfaits NuGet que votre projet consomme.</span><span class="sxs-lookup"><span data-stu-id="86da4-159">The `AssetTargetFallback` property lets you specify additional compatible framework versions for projects that your project references and NuGet packages that your project consumes.</span></span> <span data-ttu-id="86da4-160">Par exemple, si vous spécifiez une dépendance au forfait à l’aide de l’emballage, `PackageReference` mais que ce paquet ne contient pas d’actifs `TargetFramework`compatibles avec vos projets, la `AssetTargetFallback` propriété entre en jeu.</span><span class="sxs-lookup"><span data-stu-id="86da4-160">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="86da4-161">La compatibilité du paquet référencé est revérifié à `AssetTargetFallback`l’aide de chaque cadre cible spécifié dans .</span><span class="sxs-lookup"><span data-stu-id="86da4-161">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="86da4-162">Vous pouvez `AssetTargetFallback` définir la propriété à une ou plusieurs [versions de cadre cible](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="86da4-162">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <PropertyGroup>
    <AssetTargetFallback>net461</AssetTargetFallback>
  </PropertyGroup>
</Project>
```

### <a name="pack-and-restore-targets"></a><span data-ttu-id="86da4-163">Emballez et rétablissez les cibles</span><span class="sxs-lookup"><span data-stu-id="86da4-163">Pack and restore targets</span></span>

<span data-ttu-id="86da4-164">MSBuild 15.1 `pack` `restore` introduit et des objectifs pour la création et la restauration des paquets NuGet dans le cadre d’une construction.</span><span class="sxs-lookup"><span data-stu-id="86da4-164">MSBuild 15.1 introduced `pack` and `restore` targets for creating and restoring NuGet packages as part of a build.</span></span> <span data-ttu-id="86da4-165">Pour plus d’informations sur les propriétés `PackageTargetFallback`MSBuild pour ces cibles, y compris , voir [NuGet pack et restaurer comme cibles MSBuild](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="86da4-165">For information about the MSBuild properties for these targets, including `PackageTargetFallback`, see [NuGet pack and restore as MSBuild targets](/nuget/reference/msbuild-targets).</span></span>

## <a name="see-also"></a><span data-ttu-id="86da4-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86da4-166">See also</span></span>

- [<span data-ttu-id="86da4-167">Référence du schéma MSBuild</span><span class="sxs-lookup"><span data-stu-id="86da4-167">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="86da4-168">Propriétés MSBuild communes</span><span class="sxs-lookup"><span data-stu-id="86da4-168">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="86da4-169">Propriétés MSBuild pour Pack NuGet</span><span class="sxs-lookup"><span data-stu-id="86da4-169">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="86da4-170">Propriétés MSBuild pour la restauration NuGet</span><span class="sxs-lookup"><span data-stu-id="86da4-170">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="86da4-171">Personnaliser une build</span><span class="sxs-lookup"><span data-stu-id="86da4-171">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
