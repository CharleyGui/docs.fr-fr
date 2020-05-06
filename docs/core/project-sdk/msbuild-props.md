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
# <a name="msbuild-properties-for-net-core-sdk-projects"></a>Propriétés MSBuild pour les projets kit SDK .NET Core

Cette page décrit les propriétés MSBuild pour la configuration des projets .NET Core. Vous pouvez spécifier des *métadonnées* pour chaque propriété en tant qu’éléments enfants de la propriété.

> [!NOTE]
> Cette page est un travail en cours et ne répertorie pas toutes les propriétés MSBuild utiles pour le kit SDK .NET Core. Pour obtenir la liste des propriétés MSBuild courantes, consultez [propriétés MSBuild communes](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="framework-properties"></a>Propriétés du Framework

- [TargetFramework](#targetframework)
- [TargetFrameworks](#targetframeworks)
- [NetStandardImplicitPackageVersion](#netstandardimplicitpackageversion)

### <a name="targetframework"></a>TargetFramework

La `TargetFramework` propriété spécifie la version cible de .NET Framework pour l’application, qui référence implicitement un [repackage](../packages.md#metapackages). Pour obtenir la liste des monikers du Framework cible valides, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

Pour plus d’informations, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md).

### <a name="targetframeworks"></a>TargetFrameworks

Utilisez la `TargetFrameworks` propriété lorsque vous souhaitez que votre application cible plusieurs plateformes. Pour obtenir la liste des monikers du Framework cible valides, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md#supported-target-framework-versions).

> [!NOTE]
> Cette propriété est ignorée `TargetFramework` si (singulier) est spécifié.

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

Pour plus d’informations, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md).

### <a name="netstandardimplicitpackageversion"></a>NetStandardImplicitPackageVersion

> [!NOTE]
> Cette propriété s’applique uniquement aux projets `netstandard1.x`qui utilisent. Elle ne s’applique pas aux projets `netstandard2.x`qui utilisent.

Utilisez la `NetStandardImplicitPackageVersion` propriété lorsque vous souhaitez spécifier une version de Framework inférieure à la version de l' [ensemble de packages](../packages.md#metapackages) . Le fichier projet dans l’exemple suivant cible `netstandard1.3` , mais utilise la version 1.6.0 `NETStandard.Library`de.

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a>Propriétés du package

Vous pouvez spécifier des propriétés telles `PackageId`que `PackageVersion`, `PackageIcon`, `Title`, et `Description` pour décrire le package qui est créé à partir de votre projet. Pour plus d’informations sur ces propriétés et d’autres, consultez [package Target](/nuget/reference/msbuild-targets#pack-target).

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties"></a>Propriétés de publication

- [RuntimeIdentifier](#runtimeidentifier)
- [RuntimeIdentifiers](#runtimeidentifiers)
- [TrimmerRootAssembly](#trimmerrootassembly)
- [UseAppHost](#useapphost)

### <a name="runtimeidentifier"></a>RuntimeIdentifier

La `RuntimeIdentifier` propriété vous permet de spécifier un [identificateur de Runtime unique (RID)](../rid-catalog.md) pour le projet. Le RID permet de publier un déploiement autonome.

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

La `RuntimeIdentifiers` propriété vous permet de spécifier une liste délimitée par des points-virgules des [identificateurs de Runtime (RID)](../rid-catalog.md) pour le projet. Utilisez cette propriété si vous devez publier pour plusieurs runtimes. `RuntimeIdentifiers`est utilisé au moment de la restauration pour s’assurer que les ressources appropriées sont dans le graphique.

> [!TIP]
> `RuntimeIdentifier`(singulier) peut fournir des builds plus rapides quand un seul Runtime est requis.

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a>TrimmerRootAssembly

L' `TrimmerRootAssembly` élément vous permet d’exclure un assembly du [*découpage*](../deploying/trim-self-contained.md). Le découpage est le processus qui consiste à supprimer des parties inutilisées du runtime d’une application empaquetée. Dans certains cas, la suppression peut supprimer incorrectement les références requises.

Le code XML suivant exclut `System.Security` de la suppression de l’assembly.

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a>UseAppHost

La `UseAppHost` propriété a été introduite dans la version 2.1.400 de l’kit SDK .net core. Il contrôle si un exécutable natif est créé ou non pour un déploiement. Un exécutable natif est requis pour les déploiements autonomes.

Dans .NET Core 3,0 et versions ultérieures, un fichier exécutable dépendant du Framework est créé par défaut. Affectez `UseAppHost` à la `false` propriété la valeur pour désactiver la génération de l’exécutable.

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

Pour plus d’informations sur le déploiement, consultez [déploiement d’applications .net Core](../deploying/index.md).

## <a name="compile-properties"></a>Propriétés de compilation

- [LangVersion](#langversion)

### <a name="langversion"></a>LangVersion

La `LangVersion` propriété vous permet de spécifier une version du langage de programmation spécifique. Par exemple, si vous souhaitez accéder aux fonctionnalités de la version préliminaire `LangVersion` de `preview`C#, affectez à la valeur.

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
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
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a>InvariantGlobalization

La `InvariantGlobalization` propriété configure si l’application s’exécute en mode de *globalisation invariant* , ce qui signifie qu’elle n’a pas accès aux données spécifiques à la culture. Affectez à la `true` valeur la valeur pour qu’elle s’exécute en mode de globalisation-indifférent. Pour plus d’informations, consultez [mode indifférent](../run-time-config/globalization.md#invariant-mode).

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a>RetainVMGarbageCollection

La `RetainVMGarbageCollection` propriété configure le garbage collector pour placer les segments de mémoire supprimés sur une liste d’attente pour une utilisation ultérieure ou les libérer. La définition de `true` la valeur indique au garbage collector de placer les segments sur une liste d’attente. Pour plus d’informations, consultez [System. gc. RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a>ServerGarbageCollection

La `ServerGarbageCollection` propriété configure si l’application utilise des [garbage collection de station de travail ou des garbage collection de serveur](../../standard/garbage-collection/workstation-server-gc.md). Définissez la valeur sur `true` sur utiliser le garbage collection serveur. Pour plus d’informations, consultez [System. gc. Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a>ThreadPoolMaxThreads

La `ThreadPoolMaxThreads` propriété configure le nombre maximal de threads pour le pool de threads de travail. Pour plus d’informations, consultez [nombre maximal de threads](../run-time-config/threading.md#maximum-threads).

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a>ThreadPoolMinThreads

La `ThreadPoolMinThreads` propriété configure le nombre minimal de threads pour le pool de threads de travail. Pour plus d’informations, consultez [minimum threads](../run-time-config/threading.md#minimum-threads).

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a>TieredCompilation

La `TieredCompilation` propriété configure si le compilateur juste-à-temps (JIT) utilise la [compilation à plusieurs niveaux](../whats-new/dotnet-core-3-0.md#tiered-compilation). Définissez la valeur sur `false` pour désactiver la compilation à plusieurs niveaux. Pour plus d’informations, consultez compilation à plusieurs [niveaux](../run-time-config/compilation.md#tiered-compilation).

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a>TieredCompilationQuickJit

La `TieredCompilationQuickJit` propriété configure si le compilateur JIT utilise Quick JIT. Définissez la valeur sur `false` pour désactiver le JIT rapide. Pour plus d’informations, consultez [Quick JIT](../run-time-config/compilation.md#quick-jit).

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a>TieredCompilationQuickJitForLoops

La `TieredCompilationQuickJitForLoops` propriété configure si le compilateur JIT utilise le JIT rapide sur les méthodes qui contiennent des boucles. Affectez la valeur `true` à pour activer le JIT rapide sur les méthodes qui contiennent des boucles. Pour plus d’informations, consultez [Quick JIT for Loops](../run-time-config/compilation.md#quick-jit-for-loops).

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties"></a>Propriétés de référence

- [AssetTargetFallback](#assettargetfallback)
- [PackageReference](#packagereference)
- [ProjectReference](#projectreference)
- [Référence](#reference)
- [Propriétés de restauration](#restore-properties)

### <a name="assettargetfallback"></a>AssetTargetFallback

La `AssetTargetFallback` propriété vous permet de spécifier des versions de Framework compatibles supplémentaires pour les références de projet et les packages NuGet. Par exemple, si vous spécifiez une dépendance de `PackageReference` package à l’aide de mais que ce package ne contient pas de `TargetFramework`ressources compatibles `AssetTargetFallback` avec les projets, la propriété entre en lecture. La compatibilité du package référencé est revérifiée à l’aide de chaque version cible de .NET Framework `AssetTargetFallback`spécifiée dans.

Vous pouvez définir la `AssetTargetFallback` propriété sur une ou plusieurs [versions du Framework cible](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a>PackageReference

`PackageReference` Définit une référence à un package NuGet. Par exemple, vous souhaiterez peut-être référencer un package unique au lieu d’un sous- [package](../packages.md#metapackages).

L’attribut `Include` spécifie l’ID du package. L' `Version` attribut spécifie la version ou la plage de versions. Pour plus d’informations sur la spécification d’une version minimale, d’une version maximale, d’une plage ou d’une correspondance exacte, consultez [plages de versions](/nuget/concepts/package-versioning#version-ranges). Vous pouvez également ajouter les métadonnées suivantes à une référence de `IncludeAssets`projet `ExcludeAssets`:, `PrivateAssets`et.

L’extrait de code du fichier projet dans l’exemple suivant référence le package [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

Pour plus d’informations, consultez [références de package dans les fichiers projet](/nuget/consume-packages/package-references-in-project-files).

### <a name="projectreference"></a>ProjectReference

L' `ProjectReference` élément définit une référence à un autre projet. Le projet référencé est ajouté en tant que dépendance de package NuGet, autrement dit, il est traité de la même `PackageReference`façon qu’un.

L' `Include` attribut spécifie le chemin d’accès au projet. Vous pouvez également ajouter les métadonnées suivantes à une référence de `IncludeAssets`projet `ExcludeAssets`:, `PrivateAssets`et.

L’extrait de code du fichier projet dans l’exemple suivant fait `Project2`référence à un projet nommé.

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a>Informations de référence

L' `Reference` élément définit une référence à un fichier d’assembly.

L' `Include` attribut spécifie le nom du fichier et l' `HintPath` élément enfant spécifie le chemin d’accès à l’assembly.

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a>Propriétés de restauration

La restauration d’un package référencé installe toutes ses dépendances directes et toutes les dépendances de ces dépendances. Vous pouvez personnaliser la restauration des packages en spécifiant `RestorePackagesPath` des `RestoreIgnoreFailedSources`propriétés telles que et. Pour plus d’informations sur ces propriétés et d’autres, consultez [restaurer la cible](/nuget/reference/msbuild-targets#restore-target).

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="see-also"></a>Voir aussi

- [Référence du schéma MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [Propriétés MSBuild communes](/visualstudio/msbuild/common-msbuild-project-properties)
- [Propriétés MSBuild pour le Pack NuGet](/nuget/reference/msbuild-targets#pack-target)
- [Propriétés MSBuild pour la restauration NuGet](/nuget/reference/msbuild-targets#restore-properties)
- [Personnaliser une build](/visualstudio/msbuild/customize-your-build)
