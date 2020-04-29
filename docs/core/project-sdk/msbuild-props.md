---
title: Propriétés MSBuild pour Microsoft. NET. Sdk
description: Référence pour les propriétés MSBuild comprises par l’kit SDK .NET Core.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 105b7d67ea24515ea88481cb4a4fe42d2a03cfd0
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506785"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="43b3a-103">Propriétés MSBuild pour les projets kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="43b3a-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="43b3a-104">Cette page décrit les propriétés MSBuild pour la configuration des projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="43b3a-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="43b3a-105">Cette page est un travail en cours et ne répertorie pas toutes les propriétés MSBuild utiles pour le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="43b3a-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="43b3a-106">Pour obtenir la liste des propriétés MSBuild courantes, consultez [propriétés MSBuild communes](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="43b3a-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="43b3a-107">Propriétés du Framework</span><span class="sxs-lookup"><span data-stu-id="43b3a-107">Framework properties</span></span>

- [<span data-ttu-id="43b3a-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="43b3a-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="43b3a-109">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="43b3a-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="43b3a-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="43b3a-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="43b3a-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="43b3a-111">TargetFramework</span></span>

<span data-ttu-id="43b3a-112">La `TargetFramework` propriété spécifie la version cible de .NET Framework pour l’application, qui référence implicitement un [repackage](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="43b3a-112">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="43b3a-113">Pour obtenir la liste des monikers du Framework cible valides, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="43b3a-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="43b3a-114">Pour plus d’informations, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="43b3a-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="43b3a-115">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="43b3a-115">TargetFrameworks</span></span>

<span data-ttu-id="43b3a-116">Utilisez la `TargetFrameworks` propriété lorsque vous souhaitez que votre application cible plusieurs plateformes.</span><span class="sxs-lookup"><span data-stu-id="43b3a-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="43b3a-117">Pour obtenir la liste des monikers du Framework cible valides, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="43b3a-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="43b3a-118">Cette propriété est ignorée `TargetFramework` si (singulier) est spécifié.</span><span class="sxs-lookup"><span data-stu-id="43b3a-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="43b3a-119">Pour plus d’informations, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="43b3a-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="43b3a-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="43b3a-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="43b3a-121">Cette propriété s’applique uniquement aux projets `netstandard1.x`qui utilisent.</span><span class="sxs-lookup"><span data-stu-id="43b3a-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="43b3a-122">Elle ne s’applique pas aux projets `netstandard2.x`qui utilisent.</span><span class="sxs-lookup"><span data-stu-id="43b3a-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="43b3a-123">Utilisez la `NetStandardImplicitPackageVersion` propriété lorsque vous souhaitez spécifier une version de Framework inférieure à la version de l' [ensemble de packages](../packages.md#metapackages) .</span><span class="sxs-lookup"><span data-stu-id="43b3a-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="43b3a-124">Le fichier projet dans l’exemple suivant cible `netstandard1.3` , mais utilise la version 1.6.0 `NETStandard.Library`de.</span><span class="sxs-lookup"><span data-stu-id="43b3a-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a><span data-ttu-id="43b3a-125">Propriétés de publication</span><span class="sxs-lookup"><span data-stu-id="43b3a-125">Publish properties</span></span>

- [<span data-ttu-id="43b3a-126">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="43b3a-126">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="43b3a-127">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="43b3a-127">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="43b3a-128">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="43b3a-128">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="43b3a-129">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="43b3a-129">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="43b3a-130">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="43b3a-130">RuntimeIdentifier</span></span>

<span data-ttu-id="43b3a-131">La `RuntimeIdentifier` propriété vous permet de spécifier un [identificateur de Runtime unique (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="43b3a-131">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="43b3a-132">Le RID permet de publier un déploiement autonome.</span><span class="sxs-lookup"><span data-stu-id="43b3a-132">The RID enables publishing a self-contained deployment.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="43b3a-133">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="43b3a-133">RuntimeIdentifiers</span></span>

<span data-ttu-id="43b3a-134">La `RuntimeIdentifiers` propriété vous permet de spécifier une liste délimitée par des points-virgules des [identificateurs de Runtime (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="43b3a-134">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="43b3a-135">Utilisez cette propriété si vous devez publier pour plusieurs runtimes.</span><span class="sxs-lookup"><span data-stu-id="43b3a-135">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="43b3a-136">`RuntimeIdentifiers`est utilisé au moment de la restauration pour s’assurer que les ressources appropriées sont dans le graphique.</span><span class="sxs-lookup"><span data-stu-id="43b3a-136">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="43b3a-137">`RuntimeIdentifier`(singulier) peut fournir des builds plus rapides quand un seul Runtime est requis.</span><span class="sxs-lookup"><span data-stu-id="43b3a-137">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="43b3a-138">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="43b3a-138">TrimmerRootAssembly</span></span>

<span data-ttu-id="43b3a-139">L' `TrimmerRootAssembly` élément vous permet d’exclure un assembly du [*découpage*](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="43b3a-139">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="43b3a-140">Le découpage est le processus qui consiste à supprimer des parties inutilisées du runtime d’une application empaquetée.</span><span class="sxs-lookup"><span data-stu-id="43b3a-140">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="43b3a-141">Dans certains cas, la suppression peut supprimer incorrectement les références requises.</span><span class="sxs-lookup"><span data-stu-id="43b3a-141">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="43b3a-142">Le code XML suivant exclut `System.Security` de la suppression de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="43b3a-142">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
  </ItemGroup>
</Project>
```

### <a name="useapphost"></a><span data-ttu-id="43b3a-143">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="43b3a-143">UseAppHost</span></span>

<span data-ttu-id="43b3a-144">La `UseAppHost` propriété a été introduite dans la version 2.1.400 de l’kit SDK .net core.</span><span class="sxs-lookup"><span data-stu-id="43b3a-144">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="43b3a-145">Il contrôle si un exécutable natif est créé ou non pour un déploiement.</span><span class="sxs-lookup"><span data-stu-id="43b3a-145">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="43b3a-146">Un exécutable natif est requis pour les déploiements autonomes.</span><span class="sxs-lookup"><span data-stu-id="43b3a-146">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="43b3a-147">Dans .NET Core 3,0 et versions ultérieures, un fichier exécutable dépendant du Framework est créé par défaut.</span><span class="sxs-lookup"><span data-stu-id="43b3a-147">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="43b3a-148">Affectez `UseAppHost` à la `false` propriété la valeur pour désactiver la génération de l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="43b3a-148">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="43b3a-149">Pour plus d’informations sur le déploiement, consultez [déploiement d’applications .net Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="43b3a-149">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="43b3a-150">Propriétés de compilation</span><span class="sxs-lookup"><span data-stu-id="43b3a-150">Compile properties</span></span>

- [<span data-ttu-id="43b3a-151">LangVersion</span><span class="sxs-lookup"><span data-stu-id="43b3a-151">LangVersion</span></span>](#langversion)

### <a name="langversion"></a><span data-ttu-id="43b3a-152">LangVersion</span><span class="sxs-lookup"><span data-stu-id="43b3a-152">LangVersion</span></span>

<span data-ttu-id="43b3a-153">La `LangVersion` propriété vous permet de spécifier une version du langage de programmation spécifique.</span><span class="sxs-lookup"><span data-stu-id="43b3a-153">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="43b3a-154">Par exemple, si vous souhaitez accéder aux fonctionnalités de la version préliminaire `LangVersion` de `preview`C#, affectez à la valeur.</span><span class="sxs-lookup"><span data-stu-id="43b3a-154">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="43b3a-155">Pour plus d’informations, consultez contrôle de [version du langage C#](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="43b3a-155">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="43b3a-156">Propriétés de configuration au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="43b3a-156">Run-time configuration properties</span></span>

<span data-ttu-id="43b3a-157">Vous pouvez configurer certains comportements au moment de l’exécution en spécifiant des propriétés MSBuild dans le fichier projet de l’application.</span><span class="sxs-lookup"><span data-stu-id="43b3a-157">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="43b3a-158">Pour plus d’informations sur les autres méthodes de configuration du comportement au moment de l’exécution, consultez Paramètres de configuration du runtime [.net Core](../run-time-config/index.md).</span><span class="sxs-lookup"><span data-stu-id="43b3a-158">For information about other ways of configuring run-time behavior, see [.NET Core run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="43b3a-159">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="43b3a-159">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="43b3a-160">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="43b3a-160">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="43b3a-161">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="43b3a-161">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="43b3a-162">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="43b3a-162">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="43b3a-163">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="43b3a-163">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="43b3a-164">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="43b3a-164">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="43b3a-165">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="43b3a-165">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="43b3a-166">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="43b3a-166">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="43b3a-167">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="43b3a-167">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="43b3a-168">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="43b3a-168">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="43b3a-169">La `ConcurrentGarbageCollection` propriété configure si l' [garbage collection d’arrière-plan (simultané)](../../standard/garbage-collection/background-gc.md) est activée.</span><span class="sxs-lookup"><span data-stu-id="43b3a-169">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="43b3a-170">Affectez la valeur `false` à pour désactiver les garbage collection d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="43b3a-170">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="43b3a-171">Pour plus d’informations, consultez [System. gc. concurrent/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span><span class="sxs-lookup"><span data-stu-id="43b3a-171">For more information, see [System.GC.Concurrent/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="invariantglobalization"></a><span data-ttu-id="43b3a-172">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="43b3a-172">InvariantGlobalization</span></span>

<span data-ttu-id="43b3a-173">La `InvariantGlobalization` propriété configure si l’application s’exécute en mode de *globalisation invariant* , ce qui signifie qu’elle n’a pas accès aux données spécifiques à la culture.</span><span class="sxs-lookup"><span data-stu-id="43b3a-173">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="43b3a-174">Affectez à la `true` valeur la valeur pour qu’elle s’exécute en mode de globalisation-indifférent.</span><span class="sxs-lookup"><span data-stu-id="43b3a-174">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="43b3a-175">Pour plus d’informations, consultez [mode indifférent](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="43b3a-175">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>
</Project>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="43b3a-176">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="43b3a-176">RetainVMGarbageCollection</span></span>

<span data-ttu-id="43b3a-177">La `RetainVMGarbageCollection` propriété configure le garbage collector pour placer les segments de mémoire supprimés sur une liste d’attente pour une utilisation ultérieure ou les libérer.</span><span class="sxs-lookup"><span data-stu-id="43b3a-177">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="43b3a-178">La définition de `true` la valeur indique au garbage collector de placer les segments sur une liste d’attente.</span><span class="sxs-lookup"><span data-stu-id="43b3a-178">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="43b3a-179">Pour plus d’informations, consultez [System. gc. RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span><span class="sxs-lookup"><span data-stu-id="43b3a-179">For more information, see [System.GC.RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="43b3a-180">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="43b3a-180">ServerGarbageCollection</span></span>

<span data-ttu-id="43b3a-181">La `ServerGarbageCollection` propriété configure si l’application utilise des [garbage collection de station de travail ou des garbage collection de serveur](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="43b3a-181">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="43b3a-182">Définissez la valeur sur `true` sur utiliser le garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="43b3a-182">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="43b3a-183">Pour plus d’informations, consultez [System. gc. Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span><span class="sxs-lookup"><span data-stu-id="43b3a-183">For more information, see [System.GC.Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="43b3a-184">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="43b3a-184">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="43b3a-185">La `ThreadPoolMaxThreads` propriété configure le nombre maximal de threads pour le pool de threads de travail.</span><span class="sxs-lookup"><span data-stu-id="43b3a-185">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="43b3a-186">Pour plus d’informations, consultez [nombre maximal de threads](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="43b3a-186">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>
</Project>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="43b3a-187">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="43b3a-187">ThreadPoolMinThreads</span></span>

<span data-ttu-id="43b3a-188">La `ThreadPoolMinThreads` propriété configure le nombre minimal de threads pour le pool de threads de travail.</span><span class="sxs-lookup"><span data-stu-id="43b3a-188">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="43b3a-189">Pour plus d’informations, consultez [minimum threads](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="43b3a-189">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilation"></a><span data-ttu-id="43b3a-190">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="43b3a-190">TieredCompilation</span></span>

<span data-ttu-id="43b3a-191">La `TieredCompilation` propriété configure si le compilateur juste-à-temps (JIT) utilise la [compilation à plusieurs niveaux](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="43b3a-191">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="43b3a-192">Définissez la valeur sur `false` pour désactiver la compilation à plusieurs niveaux.</span><span class="sxs-lookup"><span data-stu-id="43b3a-192">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="43b3a-193">Pour plus d’informations, consultez compilation à plusieurs [niveaux](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="43b3a-193">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="43b3a-194">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="43b3a-194">TieredCompilationQuickJit</span></span>

<span data-ttu-id="43b3a-195">La `TieredCompilationQuickJit` propriété configure si le compilateur JIT utilise Quick JIT.</span><span class="sxs-lookup"><span data-stu-id="43b3a-195">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="43b3a-196">Définissez la valeur sur `false` pour désactiver le JIT rapide.</span><span class="sxs-lookup"><span data-stu-id="43b3a-196">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="43b3a-197">Pour plus d’informations, consultez [Quick JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="43b3a-197">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="43b3a-198">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="43b3a-198">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="43b3a-199">La `TieredCompilationQuickJitForLoops` propriété configure si le compilateur JIT utilise le JIT rapide sur les méthodes qui contiennent des boucles.</span><span class="sxs-lookup"><span data-stu-id="43b3a-199">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="43b3a-200">Affectez la valeur `true` à pour activer le JIT rapide sur les méthodes qui contiennent des boucles.</span><span class="sxs-lookup"><span data-stu-id="43b3a-200">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="43b3a-201">Pour plus d’informations, consultez [Quick JIT for Loops](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="43b3a-201">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
  </PropertyGroup>
</Project>
```

## <a name="nuget-packages"></a><span data-ttu-id="43b3a-202">Packages NuGet</span><span class="sxs-lookup"><span data-stu-id="43b3a-202">NuGet packages</span></span>

- [<span data-ttu-id="43b3a-203">PackageReference</span><span class="sxs-lookup"><span data-stu-id="43b3a-203">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="43b3a-204">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="43b3a-204">AssetTargetFallback</span></span>](#assettargetfallback)

### <a name="packagereference"></a><span data-ttu-id="43b3a-205">PackageReference</span><span class="sxs-lookup"><span data-stu-id="43b3a-205">PackageReference</span></span>

<span data-ttu-id="43b3a-206">L' `PackageReference` élément vous permet de spécifier une dépendance NuGet.</span><span class="sxs-lookup"><span data-stu-id="43b3a-206">The `PackageReference` item lets you specify a NuGet dependency.</span></span> <span data-ttu-id="43b3a-207">Par exemple, vous souhaiterez peut-être référencer un package unique au lieu d’un sous- [package](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="43b3a-207">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="43b3a-208">L’attribut `Include` spécifie l’ID du package.</span><span class="sxs-lookup"><span data-stu-id="43b3a-208">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="43b3a-209">L’extrait de code du fichier projet dans l’exemple suivant référence le package [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .</span><span class="sxs-lookup"><span data-stu-id="43b3a-209">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="43b3a-210">Pour plus d’informations, consultez [références de package dans les fichiers projet](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="43b3a-210">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="assettargetfallback"></a><span data-ttu-id="43b3a-211">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="43b3a-211">AssetTargetFallback</span></span>

<span data-ttu-id="43b3a-212">La `AssetTargetFallback` propriété vous permet de spécifier des versions de Framework compatibles supplémentaires pour les projets que votre projet référence et les packages NuGet que votre projet utilise.</span><span class="sxs-lookup"><span data-stu-id="43b3a-212">The `AssetTargetFallback` property lets you specify additional compatible framework versions for projects that your project references and NuGet packages that your project consumes.</span></span> <span data-ttu-id="43b3a-213">Par exemple, si vous spécifiez une dépendance de `PackageReference` package à l’aide de mais que ce package ne contient pas de `TargetFramework`ressources compatibles `AssetTargetFallback` avec les projets, la propriété entre en lecture.</span><span class="sxs-lookup"><span data-stu-id="43b3a-213">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="43b3a-214">La compatibilité du package référencé est revérifiée à l’aide de chaque version cible de .NET Framework `AssetTargetFallback`spécifiée dans.</span><span class="sxs-lookup"><span data-stu-id="43b3a-214">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="43b3a-215">Vous pouvez définir la `AssetTargetFallback` propriété sur une ou plusieurs [versions du Framework cible](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="43b3a-215">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <PropertyGroup>
    <AssetTargetFallback>net461</AssetTargetFallback>
  </PropertyGroup>
</Project>
```

### <a name="pack-and-restore-targets"></a><span data-ttu-id="43b3a-216">Cibles de Pack et de restauration</span><span class="sxs-lookup"><span data-stu-id="43b3a-216">Pack and restore targets</span></span>

<span data-ttu-id="43b3a-217">MSBuild 15,1 introduit `pack` et `restore` cible pour la création et la restauration de packages NuGet dans le cadre d’une build.</span><span class="sxs-lookup"><span data-stu-id="43b3a-217">MSBuild 15.1 introduced `pack` and `restore` targets for creating and restoring NuGet packages as part of a build.</span></span> <span data-ttu-id="43b3a-218">Pour plus d’informations sur les propriétés MSBuild pour ces cibles `PackageTargetFallback`, y compris, consultez [NuGet Pack et Restore en tant que cibles MSBuild](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="43b3a-218">For information about the MSBuild properties for these targets, including `PackageTargetFallback`, see [NuGet pack and restore as MSBuild targets](/nuget/reference/msbuild-targets).</span></span>

## <a name="see-also"></a><span data-ttu-id="43b3a-219">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43b3a-219">See also</span></span>

- [<span data-ttu-id="43b3a-220">Référence du schéma MSBuild</span><span class="sxs-lookup"><span data-stu-id="43b3a-220">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="43b3a-221">Propriétés MSBuild communes</span><span class="sxs-lookup"><span data-stu-id="43b3a-221">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="43b3a-222">Propriétés MSBuild pour le Pack NuGet</span><span class="sxs-lookup"><span data-stu-id="43b3a-222">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="43b3a-223">Propriétés MSBuild pour la restauration NuGet</span><span class="sxs-lookup"><span data-stu-id="43b3a-223">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="43b3a-224">Personnaliser une build</span><span class="sxs-lookup"><span data-stu-id="43b3a-224">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
