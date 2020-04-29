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
# <a name="msbuild-properties-for-net-core-sdk-projects"></a>Propriétés MSBuild pour les projets kit SDK .NET Core

Cette page décrit les propriétés MSBuild pour la configuration des projets .NET Core.

> [!NOTE]
> Cette page est un travail en cours et ne répertorie pas toutes les propriétés MSBuild utiles pour le kit SDK .NET Core. Pour obtenir la liste des propriétés MSBuild courantes, consultez [propriétés MSBuild communes](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="framework-properties"></a>Propriétés du Framework

- [TargetFramework](#targetframework)
- [TargetFrameworks](#targetframeworks)
- [NetStandardImplicitPackageVersion](#netstandardimplicitpackageversion)

### <a name="targetframework"></a>TargetFramework

La `TargetFramework` propriété spécifie la version cible de .NET Framework pour l’application, qui référence implicitement un [repackage](../packages.md#metapackages). Pour obtenir la liste des monikers du Framework cible valides, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

Pour plus d’informations, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md).

### <a name="targetframeworks"></a>TargetFrameworks

Utilisez la `TargetFrameworks` propriété lorsque vous souhaitez que votre application cible plusieurs plateformes. Pour obtenir la liste des monikers du Framework cible valides, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md#supported-target-framework-versions).

> [!NOTE]
> Cette propriété est ignorée `TargetFramework` si (singulier) est spécifié.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

Pour plus d’informations, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md).

### <a name="netstandardimplicitpackageversion"></a>NetStandardImplicitPackageVersion

> [!NOTE]
> Cette propriété s’applique uniquement aux projets `netstandard1.x`qui utilisent. Elle ne s’applique pas aux projets `netstandard2.x`qui utilisent.

Utilisez la `NetStandardImplicitPackageVersion` propriété lorsque vous souhaitez spécifier une version de Framework inférieure à la version de l' [ensemble de packages](../packages.md#metapackages) . Le fichier projet dans l’exemple suivant cible `netstandard1.3` , mais utilise la version 1.6.0 `NETStandard.Library`de.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a>Propriétés de publication

- [RuntimeIdentifier](#runtimeidentifier)
- [RuntimeIdentifiers](#runtimeidentifiers)
- [TrimmerRootAssembly](#trimmerrootassembly)
- [UseAppHost](#useapphost)

### <a name="runtimeidentifier"></a>RuntimeIdentifier

La `RuntimeIdentifier` propriété vous permet de spécifier un [identificateur de Runtime unique (RID)](../rid-catalog.md) pour le projet. Le RID permet de publier un déploiement autonome.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

La `RuntimeIdentifiers` propriété vous permet de spécifier une liste délimitée par des points-virgules des [identificateurs de Runtime (RID)](../rid-catalog.md) pour le projet. Utilisez cette propriété si vous devez publier pour plusieurs runtimes. `RuntimeIdentifiers`est utilisé au moment de la restauration pour s’assurer que les ressources appropriées sont dans le graphique.

> [!TIP]
> `RuntimeIdentifier`(singulier) peut fournir des builds plus rapides quand un seul Runtime est requis.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="trimmerrootassembly"></a>TrimmerRootAssembly

L' `TrimmerRootAssembly` élément vous permet d’exclure un assembly du [*découpage*](../deploying/trim-self-contained.md). Le découpage est le processus qui consiste à supprimer des parties inutilisées du runtime d’une application empaquetée. Dans certains cas, la suppression peut supprimer incorrectement les références requises.

Le code XML suivant exclut `System.Security` de la suppression de l’assembly.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
  </ItemGroup>
</Project>
```

### <a name="useapphost"></a>UseAppHost

La `UseAppHost` propriété a été introduite dans la version 2.1.400 de l’kit SDK .net core. Il contrôle si un exécutable natif est créé ou non pour un déploiement. Un exécutable natif est requis pour les déploiements autonomes.

Dans .NET Core 3,0 et versions ultérieures, un fichier exécutable dépendant du Framework est créé par défaut. Affectez `UseAppHost` à la `false` propriété la valeur pour désactiver la génération de l’exécutable.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

Pour plus d’informations sur le déploiement, consultez [déploiement d’applications .net Core](../deploying/index.md).

## <a name="compile-properties"></a>Propriétés de compilation

- [LangVersion](#langversion)

### <a name="langversion"></a>LangVersion

La `LangVersion` propriété vous permet de spécifier une version du langage de programmation spécifique. Par exemple, si vous souhaitez accéder aux fonctionnalités de la version préliminaire `LangVersion` de `preview`C#, affectez à la valeur.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

Pour plus d’informations, consultez contrôle de [version du langage C#](../../csharp/language-reference/configure-language-version.md#override-a-default).

## <a name="run-time-configuration-properties"></a>Propriétés de configuration au moment de l’exécution

Vous pouvez configurer certains comportements au moment de l’exécution en spécifiant des propriétés MSBuild dans le fichier projet de l’application. Pour plus d’informations sur les autres méthodes de configuration du comportement au moment de l’exécution, consultez Paramètres de configuration du runtime [.net Core](../run-time-config/index.md).

- [ConcurrentGarbageCollection](#concurrentgarbagecollection)
- [InvariantGlobalization](#invariantglobalization)
- [RetainVMGarbageCollection](#retainvmgarbagecollection)
- [ServerGarbageCollection](#servergarbagecollection)
- [ThreadPoolMaxThreads](#threadpoolmaxthreads)
- [ThreadPoolMinThreads](#threadpoolminthreads)
- [TieredCompilation](#tieredcompilation)
- [TieredCompilationQuickJit](#tieredcompilationquickjit)
- [TieredCompilationQuickJitForLoops](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a>ConcurrentGarbageCollection

La `ConcurrentGarbageCollection` propriété configure si l' [garbage collection d’arrière-plan (simultané)](../../standard/garbage-collection/background-gc.md) est activée. Affectez la valeur `false` à pour désactiver les garbage collection d’arrière-plan. Pour plus d’informations, consultez [System. gc. concurrent/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="invariantglobalization"></a>InvariantGlobalization

La `InvariantGlobalization` propriété configure si l’application s’exécute en mode de *globalisation invariant* , ce qui signifie qu’elle n’a pas accès aux données spécifiques à la culture. Affectez à la `true` valeur la valeur pour qu’elle s’exécute en mode de globalisation-indifférent. Pour plus d’informations, consultez [mode indifférent](../run-time-config/globalization.md#invariant-mode).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>
</Project>
```

### <a name="retainvmgarbagecollection"></a>RetainVMGarbageCollection

La `RetainVMGarbageCollection` propriété configure le garbage collector pour placer les segments de mémoire supprimés sur une liste d’attente pour une utilisation ultérieure ou les libérer. La définition de `true` la valeur indique au garbage collector de placer les segments sur une liste d’attente. Pour plus d’informations, consultez [System. gc. RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="servergarbagecollection"></a>ServerGarbageCollection

La `ServerGarbageCollection` propriété configure si l’application utilise des [garbage collection de station de travail ou des garbage collection de serveur](../../standard/garbage-collection/workstation-server-gc.md). Définissez la valeur sur `true` sur utiliser le garbage collection serveur. Pour plus d’informations, consultez [System. gc. Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="threadpoolmaxthreads"></a>ThreadPoolMaxThreads

La `ThreadPoolMaxThreads` propriété configure le nombre maximal de threads pour le pool de threads de travail. Pour plus d’informations, consultez [nombre maximal de threads](../run-time-config/threading.md#maximum-threads).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>
</Project>
```

### <a name="threadpoolminthreads"></a>ThreadPoolMinThreads

La `ThreadPoolMinThreads` propriété configure le nombre minimal de threads pour le pool de threads de travail. Pour plus d’informations, consultez [minimum threads](../run-time-config/threading.md#minimum-threads).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilation"></a>TieredCompilation

La `TieredCompilation` propriété configure si le compilateur juste-à-temps (JIT) utilise la [compilation à plusieurs niveaux](../whats-new/dotnet-core-3-0.md#tiered-compilation). Définissez la valeur sur `false` pour désactiver la compilation à plusieurs niveaux. Pour plus d’informations, consultez compilation à plusieurs [niveaux](../run-time-config/compilation.md#tiered-compilation).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilationquickjit"></a>TieredCompilationQuickJit

La `TieredCompilationQuickJit` propriété configure si le compilateur JIT utilise Quick JIT. Définissez la valeur sur `false` pour désactiver le JIT rapide. Pour plus d’informations, consultez [Quick JIT](../run-time-config/compilation.md#quick-jit).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilationquickjitforloops"></a>TieredCompilationQuickJitForLoops

La `TieredCompilationQuickJitForLoops` propriété configure si le compilateur JIT utilise le JIT rapide sur les méthodes qui contiennent des boucles. Affectez la valeur `true` à pour activer le JIT rapide sur les méthodes qui contiennent des boucles. Pour plus d’informations, consultez [Quick JIT for Loops](../run-time-config/compilation.md#quick-jit-for-loops).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
  </PropertyGroup>
</Project>
```

## <a name="nuget-packages"></a>Packages NuGet

- [PackageReference](#packagereference)
- [AssetTargetFallback](#assettargetfallback)

### <a name="packagereference"></a>PackageReference

L' `PackageReference` élément vous permet de spécifier une dépendance NuGet. Par exemple, vous souhaiterez peut-être référencer un package unique au lieu d’un sous- [package](../packages.md#metapackages). L’attribut `Include` spécifie l’ID du package. L’extrait de code du fichier projet dans l’exemple suivant référence le package [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

Pour plus d’informations, consultez [références de package dans les fichiers projet](/nuget/consume-packages/package-references-in-project-files).

### <a name="assettargetfallback"></a>AssetTargetFallback

La `AssetTargetFallback` propriété vous permet de spécifier des versions de Framework compatibles supplémentaires pour les projets que votre projet référence et les packages NuGet que votre projet utilise. Par exemple, si vous spécifiez une dépendance de `PackageReference` package à l’aide de mais que ce package ne contient pas de `TargetFramework`ressources compatibles `AssetTargetFallback` avec les projets, la propriété entre en lecture. La compatibilité du package référencé est revérifiée à l’aide de chaque version cible de .NET Framework `AssetTargetFallback`spécifiée dans.

Vous pouvez définir la `AssetTargetFallback` propriété sur une ou plusieurs [versions du Framework cible](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <PropertyGroup>
    <AssetTargetFallback>net461</AssetTargetFallback>
  </PropertyGroup>
</Project>
```

### <a name="pack-and-restore-targets"></a>Cibles de Pack et de restauration

MSBuild 15,1 introduit `pack` et `restore` cible pour la création et la restauration de packages NuGet dans le cadre d’une build. Pour plus d’informations sur les propriétés MSBuild pour ces cibles `PackageTargetFallback`, y compris, consultez [NuGet Pack et Restore en tant que cibles MSBuild](/nuget/reference/msbuild-targets).

## <a name="see-also"></a>Voir aussi

- [Référence du schéma MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [Propriétés MSBuild communes](/visualstudio/msbuild/common-msbuild-project-properties)
- [Propriétés MSBuild pour le Pack NuGet](/nuget/reference/msbuild-targets#pack-target)
- [Propriétés MSBuild pour la restauration NuGet](/nuget/reference/msbuild-targets#restore-properties)
- [Personnaliser une build](/visualstudio/msbuild/customize-your-build)
