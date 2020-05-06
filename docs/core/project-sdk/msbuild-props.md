---
title: Propriétés MSBuild pour Microsoft. NET. Sdk
description: Référence pour les propriétés MSBuild comprises par l’kit SDK .NET Core.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 800ff59310d8437d7f770bf20a5bdf37714f8515
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795571"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="7859c-103">Propriétés MSBuild pour les projets kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="7859c-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="7859c-104">Cette page décrit les propriétés MSBuild pour la configuration des projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7859c-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span> <span data-ttu-id="7859c-105">Vous pouvez spécifier des *métadonnées* pour chaque propriété en tant qu’éléments enfants de la propriété.</span><span class="sxs-lookup"><span data-stu-id="7859c-105">You can specify *metadata* for each property as child elements of the property.</span></span>

> [!NOTE]
> <span data-ttu-id="7859c-106">Cette page est un travail en cours et ne répertorie pas toutes les propriétés MSBuild utiles pour le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7859c-106">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="7859c-107">Pour obtenir la liste des propriétés MSBuild courantes, consultez [propriétés MSBuild communes](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="7859c-107">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="7859c-108">Propriétés du Framework</span><span class="sxs-lookup"><span data-stu-id="7859c-108">Framework properties</span></span>

- [<span data-ttu-id="7859c-109">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="7859c-109">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="7859c-110">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="7859c-110">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="7859c-111">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="7859c-111">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="7859c-112">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="7859c-112">TargetFramework</span></span>

<span data-ttu-id="7859c-113">La `TargetFramework` propriété spécifie la version cible de .NET Framework pour l’application, qui référence implicitement un [repackage](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="7859c-113">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="7859c-114">Pour obtenir la liste des monikers du Framework cible valides, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="7859c-114">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="7859c-115">Pour plus d’informations, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="7859c-115">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="7859c-116">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="7859c-116">TargetFrameworks</span></span>

<span data-ttu-id="7859c-117">Utilisez la `TargetFrameworks` propriété lorsque vous souhaitez que votre application cible plusieurs plateformes.</span><span class="sxs-lookup"><span data-stu-id="7859c-117">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="7859c-118">Pour obtenir la liste des monikers du Framework cible valides, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="7859c-118">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="7859c-119">Cette propriété est ignorée `TargetFramework` si (singulier) est spécifié.</span><span class="sxs-lookup"><span data-stu-id="7859c-119">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="7859c-120">Pour plus d’informations, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="7859c-120">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="7859c-121">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="7859c-121">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="7859c-122">Cette propriété s’applique uniquement aux projets `netstandard1.x`qui utilisent.</span><span class="sxs-lookup"><span data-stu-id="7859c-122">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="7859c-123">Elle ne s’applique pas aux projets `netstandard2.x`qui utilisent.</span><span class="sxs-lookup"><span data-stu-id="7859c-123">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="7859c-124">Utilisez la `NetStandardImplicitPackageVersion` propriété lorsque vous souhaitez spécifier une version de Framework inférieure à la version de l' [ensemble de packages](../packages.md#metapackages) .</span><span class="sxs-lookup"><span data-stu-id="7859c-124">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="7859c-125">Le fichier projet dans l’exemple suivant cible `netstandard1.3` , mais utilise la version 1.6.0 `NETStandard.Library`de.</span><span class="sxs-lookup"><span data-stu-id="7859c-125">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="7859c-126">Propriétés du package</span><span class="sxs-lookup"><span data-stu-id="7859c-126">Package properties</span></span>

<span data-ttu-id="7859c-127">Vous pouvez spécifier des propriétés telles `PackageId`que `PackageVersion`, `PackageIcon`, `Title`, et `Description` pour décrire le package qui est créé à partir de votre projet.</span><span class="sxs-lookup"><span data-stu-id="7859c-127">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="7859c-128">Pour plus d’informations sur ces propriétés et d’autres, consultez [package Target](/nuget/reference/msbuild-targets#pack-target).</span><span class="sxs-lookup"><span data-stu-id="7859c-128">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties"></a><span data-ttu-id="7859c-129">Propriétés de publication</span><span class="sxs-lookup"><span data-stu-id="7859c-129">Publish properties</span></span>

- [<span data-ttu-id="7859c-130">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="7859c-130">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="7859c-131">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="7859c-131">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="7859c-132">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="7859c-132">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="7859c-133">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="7859c-133">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="7859c-134">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="7859c-134">RuntimeIdentifier</span></span>

<span data-ttu-id="7859c-135">La `RuntimeIdentifier` propriété vous permet de spécifier un [identificateur de Runtime unique (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="7859c-135">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="7859c-136">Le RID permet de publier un déploiement autonome.</span><span class="sxs-lookup"><span data-stu-id="7859c-136">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="7859c-137">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="7859c-137">RuntimeIdentifiers</span></span>

<span data-ttu-id="7859c-138">La `RuntimeIdentifiers` propriété vous permet de spécifier une liste délimitée par des points-virgules des [identificateurs de Runtime (RID)](../rid-catalog.md) pour le projet.</span><span class="sxs-lookup"><span data-stu-id="7859c-138">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="7859c-139">Utilisez cette propriété si vous devez publier pour plusieurs runtimes.</span><span class="sxs-lookup"><span data-stu-id="7859c-139">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="7859c-140">`RuntimeIdentifiers`est utilisé au moment de la restauration pour s’assurer que les ressources appropriées sont dans le graphique.</span><span class="sxs-lookup"><span data-stu-id="7859c-140">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="7859c-141">`RuntimeIdentifier`(singulier) peut fournir des builds plus rapides quand un seul Runtime est requis.</span><span class="sxs-lookup"><span data-stu-id="7859c-141">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="7859c-142">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="7859c-142">TrimmerRootAssembly</span></span>

<span data-ttu-id="7859c-143">L' `TrimmerRootAssembly` élément vous permet d’exclure un assembly du [*découpage*](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="7859c-143">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="7859c-144">Le découpage est le processus qui consiste à supprimer des parties inutilisées du runtime d’une application empaquetée.</span><span class="sxs-lookup"><span data-stu-id="7859c-144">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="7859c-145">Dans certains cas, la suppression peut supprimer incorrectement les références requises.</span><span class="sxs-lookup"><span data-stu-id="7859c-145">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="7859c-146">Le code XML suivant exclut `System.Security` de la suppression de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="7859c-146">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="7859c-147">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="7859c-147">UseAppHost</span></span>

<span data-ttu-id="7859c-148">La `UseAppHost` propriété a été introduite dans la version 2.1.400 de l’kit SDK .net core.</span><span class="sxs-lookup"><span data-stu-id="7859c-148">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="7859c-149">Il contrôle si un exécutable natif est créé ou non pour un déploiement.</span><span class="sxs-lookup"><span data-stu-id="7859c-149">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="7859c-150">Un exécutable natif est requis pour les déploiements autonomes.</span><span class="sxs-lookup"><span data-stu-id="7859c-150">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="7859c-151">Dans .NET Core 3,0 et versions ultérieures, un fichier exécutable dépendant du Framework est créé par défaut.</span><span class="sxs-lookup"><span data-stu-id="7859c-151">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="7859c-152">Affectez `UseAppHost` à la `false` propriété la valeur pour désactiver la génération de l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="7859c-152">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="7859c-153">Pour plus d’informations sur le déploiement, consultez [déploiement d’applications .net Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="7859c-153">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="7859c-154">Propriétés de compilation</span><span class="sxs-lookup"><span data-stu-id="7859c-154">Compile properties</span></span>

- [<span data-ttu-id="7859c-155">LangVersion</span><span class="sxs-lookup"><span data-stu-id="7859c-155">LangVersion</span></span>](#langversion)

### <a name="langversion"></a><span data-ttu-id="7859c-156">LangVersion</span><span class="sxs-lookup"><span data-stu-id="7859c-156">LangVersion</span></span>

<span data-ttu-id="7859c-157">La `LangVersion` propriété vous permet de spécifier une version du langage de programmation spécifique.</span><span class="sxs-lookup"><span data-stu-id="7859c-157">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="7859c-158">Par exemple, si vous souhaitez accéder aux fonctionnalités de la version préliminaire `LangVersion` de `preview`C#, affectez à la valeur.</span><span class="sxs-lookup"><span data-stu-id="7859c-158">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="7859c-159">Pour plus d’informations, consultez contrôle de [version du langage C#](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="7859c-159">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="7859c-160">Propriétés de configuration au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="7859c-160">Run-time configuration properties</span></span>

<span data-ttu-id="7859c-161">Vous pouvez configurer certains comportements au moment de l’exécution en spécifiant des propriétés MSBuild dans le fichier projet de l’application.</span><span class="sxs-lookup"><span data-stu-id="7859c-161">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="7859c-162">Pour plus d’informations sur les autres méthodes de configuration du comportement au moment de l’exécution, consultez Paramètres de configuration du runtime [.net Core](../run-time-config/index.md).</span><span class="sxs-lookup"><span data-stu-id="7859c-162">For information about other ways of configuring run-time behavior, see [.NET Core run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="7859c-163">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="7859c-163">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="7859c-164">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="7859c-164">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="7859c-165">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="7859c-165">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="7859c-166">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="7859c-166">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="7859c-167">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="7859c-167">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="7859c-168">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="7859c-168">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="7859c-169">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="7859c-169">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="7859c-170">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="7859c-170">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="7859c-171">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="7859c-171">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="7859c-172">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="7859c-172">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="7859c-173">La `ConcurrentGarbageCollection` propriété configure si l' [garbage collection d’arrière-plan (simultané)](../../standard/garbage-collection/background-gc.md) est activée.</span><span class="sxs-lookup"><span data-stu-id="7859c-173">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="7859c-174">Affectez la valeur `false` à pour désactiver les garbage collection d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="7859c-174">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="7859c-175">Pour plus d’informations, consultez [System. gc. concurrent/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span><span class="sxs-lookup"><span data-stu-id="7859c-175">For more information, see [System.GC.Concurrent/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="7859c-176">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="7859c-176">InvariantGlobalization</span></span>

<span data-ttu-id="7859c-177">La `InvariantGlobalization` propriété configure si l’application s’exécute en mode de *globalisation invariant* , ce qui signifie qu’elle n’a pas accès aux données spécifiques à la culture.</span><span class="sxs-lookup"><span data-stu-id="7859c-177">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="7859c-178">Affectez à la `true` valeur la valeur pour qu’elle s’exécute en mode de globalisation-indifférent.</span><span class="sxs-lookup"><span data-stu-id="7859c-178">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="7859c-179">Pour plus d’informations, consultez [mode indifférent](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="7859c-179">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="7859c-180">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="7859c-180">RetainVMGarbageCollection</span></span>

<span data-ttu-id="7859c-181">La `RetainVMGarbageCollection` propriété configure le garbage collector pour placer les segments de mémoire supprimés sur une liste d’attente pour une utilisation ultérieure ou les libérer.</span><span class="sxs-lookup"><span data-stu-id="7859c-181">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="7859c-182">La définition de `true` la valeur indique au garbage collector de placer les segments sur une liste d’attente.</span><span class="sxs-lookup"><span data-stu-id="7859c-182">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="7859c-183">Pour plus d’informations, consultez [System. gc. RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span><span class="sxs-lookup"><span data-stu-id="7859c-183">For more information, see [System.GC.RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="7859c-184">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="7859c-184">ServerGarbageCollection</span></span>

<span data-ttu-id="7859c-185">La `ServerGarbageCollection` propriété configure si l’application utilise des [garbage collection de station de travail ou des garbage collection de serveur](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="7859c-185">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="7859c-186">Définissez la valeur sur `true` sur utiliser le garbage collection serveur.</span><span class="sxs-lookup"><span data-stu-id="7859c-186">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="7859c-187">Pour plus d’informations, consultez [System. gc. Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span><span class="sxs-lookup"><span data-stu-id="7859c-187">For more information, see [System.GC.Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="7859c-188">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="7859c-188">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="7859c-189">La `ThreadPoolMaxThreads` propriété configure le nombre maximal de threads pour le pool de threads de travail.</span><span class="sxs-lookup"><span data-stu-id="7859c-189">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="7859c-190">Pour plus d’informations, consultez [nombre maximal de threads](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="7859c-190">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="7859c-191">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="7859c-191">ThreadPoolMinThreads</span></span>

<span data-ttu-id="7859c-192">La `ThreadPoolMinThreads` propriété configure le nombre minimal de threads pour le pool de threads de travail.</span><span class="sxs-lookup"><span data-stu-id="7859c-192">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="7859c-193">Pour plus d’informations, consultez [minimum threads](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="7859c-193">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="7859c-194">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="7859c-194">TieredCompilation</span></span>

<span data-ttu-id="7859c-195">La `TieredCompilation` propriété configure si le compilateur juste-à-temps (JIT) utilise la [compilation à plusieurs niveaux](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="7859c-195">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="7859c-196">Définissez la valeur sur `false` pour désactiver la compilation à plusieurs niveaux.</span><span class="sxs-lookup"><span data-stu-id="7859c-196">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="7859c-197">Pour plus d’informations, consultez compilation à plusieurs [niveaux](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="7859c-197">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="7859c-198">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="7859c-198">TieredCompilationQuickJit</span></span>

<span data-ttu-id="7859c-199">La `TieredCompilationQuickJit` propriété configure si le compilateur JIT utilise Quick JIT.</span><span class="sxs-lookup"><span data-stu-id="7859c-199">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="7859c-200">Définissez la valeur sur `false` pour désactiver le JIT rapide.</span><span class="sxs-lookup"><span data-stu-id="7859c-200">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="7859c-201">Pour plus d’informations, consultez [Quick JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="7859c-201">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="7859c-202">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="7859c-202">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="7859c-203">La `TieredCompilationQuickJitForLoops` propriété configure si le compilateur JIT utilise le JIT rapide sur les méthodes qui contiennent des boucles.</span><span class="sxs-lookup"><span data-stu-id="7859c-203">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="7859c-204">Affectez la valeur `true` à pour activer le JIT rapide sur les méthodes qui contiennent des boucles.</span><span class="sxs-lookup"><span data-stu-id="7859c-204">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="7859c-205">Pour plus d’informations, consultez [Quick JIT for Loops](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="7859c-205">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties"></a><span data-ttu-id="7859c-206">Propriétés de référence</span><span class="sxs-lookup"><span data-stu-id="7859c-206">Reference properties</span></span>

- [<span data-ttu-id="7859c-207">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="7859c-207">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="7859c-208">PackageReference</span><span class="sxs-lookup"><span data-stu-id="7859c-208">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="7859c-209">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="7859c-209">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="7859c-210">Référence</span><span class="sxs-lookup"><span data-stu-id="7859c-210">Reference</span></span>](#reference)
- [<span data-ttu-id="7859c-211">Propriétés de restauration</span><span class="sxs-lookup"><span data-stu-id="7859c-211">Restore properties</span></span>](#restore-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="7859c-212">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="7859c-212">AssetTargetFallback</span></span>

<span data-ttu-id="7859c-213">La `AssetTargetFallback` propriété vous permet de spécifier des versions de Framework compatibles supplémentaires pour les références de projet et les packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="7859c-213">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="7859c-214">Par exemple, si vous spécifiez une dépendance de `PackageReference` package à l’aide de mais que ce package ne contient pas de `TargetFramework`ressources compatibles `AssetTargetFallback` avec les projets, la propriété entre en lecture.</span><span class="sxs-lookup"><span data-stu-id="7859c-214">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="7859c-215">La compatibilité du package référencé est revérifiée à l’aide de chaque version cible de .NET Framework `AssetTargetFallback`spécifiée dans.</span><span class="sxs-lookup"><span data-stu-id="7859c-215">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="7859c-216">Vous pouvez définir la `AssetTargetFallback` propriété sur une ou plusieurs [versions du Framework cible](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="7859c-216">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="7859c-217">PackageReference</span><span class="sxs-lookup"><span data-stu-id="7859c-217">PackageReference</span></span>

<span data-ttu-id="7859c-218">`PackageReference` Définit une référence à un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="7859c-218">The `PackageReference` defines a reference to a NuGet package.</span></span> <span data-ttu-id="7859c-219">Par exemple, vous souhaiterez peut-être référencer un package unique au lieu d’un sous- [package](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="7859c-219">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span>

<span data-ttu-id="7859c-220">L’attribut `Include` spécifie l’ID du package.</span><span class="sxs-lookup"><span data-stu-id="7859c-220">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="7859c-221">L' `Version` attribut spécifie la version ou la plage de versions.</span><span class="sxs-lookup"><span data-stu-id="7859c-221">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="7859c-222">Pour plus d’informations sur la spécification d’une version minimale, d’une version maximale, d’une plage ou d’une correspondance exacte, consultez [plages de versions](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="7859c-222">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="7859c-223">Vous pouvez également ajouter les métadonnées suivantes à une référence de `IncludeAssets`projet `ExcludeAssets`:, `PrivateAssets`et.</span><span class="sxs-lookup"><span data-stu-id="7859c-223">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="7859c-224">L’extrait de code du fichier projet dans l’exemple suivant référence le package [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .</span><span class="sxs-lookup"><span data-stu-id="7859c-224">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="7859c-225">Pour plus d’informations, consultez [références de package dans les fichiers projet](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="7859c-225">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="projectreference"></a><span data-ttu-id="7859c-226">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="7859c-226">ProjectReference</span></span>

<span data-ttu-id="7859c-227">L' `ProjectReference` élément définit une référence à un autre projet.</span><span class="sxs-lookup"><span data-stu-id="7859c-227">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="7859c-228">Le projet référencé est ajouté en tant que dépendance de package NuGet, autrement dit, il est traité de la même `PackageReference`façon qu’un.</span><span class="sxs-lookup"><span data-stu-id="7859c-228">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="7859c-229">L' `Include` attribut spécifie le chemin d’accès au projet.</span><span class="sxs-lookup"><span data-stu-id="7859c-229">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="7859c-230">Vous pouvez également ajouter les métadonnées suivantes à une référence de `IncludeAssets`projet `ExcludeAssets`:, `PrivateAssets`et.</span><span class="sxs-lookup"><span data-stu-id="7859c-230">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="7859c-231">L’extrait de code du fichier projet dans l’exemple suivant fait `Project2`référence à un projet nommé.</span><span class="sxs-lookup"><span data-stu-id="7859c-231">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="7859c-232">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="7859c-232">Reference</span></span>

<span data-ttu-id="7859c-233">L' `Reference` élément définit une référence à un fichier d’assembly.</span><span class="sxs-lookup"><span data-stu-id="7859c-233">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="7859c-234">L' `Include` attribut spécifie le nom du fichier et l' `HintPath` élément enfant spécifie le chemin d’accès à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="7859c-234">The `Include` attribute specifies the name of the file, and the `HintPath` child element specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a><span data-ttu-id="7859c-235">Propriétés de restauration</span><span class="sxs-lookup"><span data-stu-id="7859c-235">Restore properties</span></span>

<span data-ttu-id="7859c-236">La restauration d’un package référencé installe toutes ses dépendances directes et toutes les dépendances de ces dépendances.</span><span class="sxs-lookup"><span data-stu-id="7859c-236">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="7859c-237">Vous pouvez personnaliser la restauration des packages en spécifiant `RestorePackagesPath` des `RestoreIgnoreFailedSources`propriétés telles que et.</span><span class="sxs-lookup"><span data-stu-id="7859c-237">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="7859c-238">Pour plus d’informations sur ces propriétés et d’autres, consultez [restaurer la cible](/nuget/reference/msbuild-targets#restore-target).</span><span class="sxs-lookup"><span data-stu-id="7859c-238">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="7859c-239">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7859c-239">See also</span></span>

- [<span data-ttu-id="7859c-240">Référence du schéma MSBuild</span><span class="sxs-lookup"><span data-stu-id="7859c-240">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="7859c-241">Propriétés MSBuild communes</span><span class="sxs-lookup"><span data-stu-id="7859c-241">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="7859c-242">Propriétés MSBuild pour le Pack NuGet</span><span class="sxs-lookup"><span data-stu-id="7859c-242">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="7859c-243">Propriétés MSBuild pour la restauration NuGet</span><span class="sxs-lookup"><span data-stu-id="7859c-243">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="7859c-244">Personnaliser une build</span><span class="sxs-lookup"><span data-stu-id="7859c-244">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
