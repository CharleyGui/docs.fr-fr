---
title: Propriétés MSBuild pour Microsoft. NET. Sdk
description: Référence pour les propriétés et les éléments MSBuild compris par le kit de développement logiciel (SDK) .NET.
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: faa0dc0e94800a49b56af8810562ee0540f118d2
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247568"
---
# <a name="msbuild-reference-for-net-sdk-projects"></a>Référence MSBuild pour les projets SDK .NET

Cette page est une référence pour les propriétés et les éléments MSBuild que vous pouvez utiliser pour configurer des projets .NET.

> [!NOTE]
> Cette page est un travail en cours et ne répertorie pas toutes les propriétés MSBuild utiles pour le kit de développement logiciel (SDK) .NET. Pour obtenir la liste des propriétés MSBuild courantes, consultez [propriétés MSBuild communes](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="framework-properties"></a>Propriétés du Framework

- [TargetFramework](#targetframework)
- [TargetFrameworks](#targetframeworks)
- [NetStandardImplicitPackageVersion](#netstandardimplicitpackageversion)

### <a name="targetframework"></a>TargetFramework

La `TargetFramework` propriété spécifie la version cible de .NET Framework pour l’application. Pour obtenir la liste des monikers du Framework cible valides, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md#supported-target-frameworks).

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

Pour plus d’informations, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md).

### <a name="targetframeworks"></a>TargetFrameworks

Utilisez la `TargetFrameworks` propriété lorsque vous souhaitez que votre application cible plusieurs plateformes. Pour obtenir la liste des monikers du Framework cible valides, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md#supported-target-frameworks).

> [!NOTE]
> Cette propriété est ignorée si `TargetFramework` (singulier) est spécifié.

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

Pour plus d’informations, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md).

### <a name="netstandardimplicitpackageversion"></a>NetStandardImplicitPackageVersion

> [!NOTE]
> Cette propriété s’applique uniquement aux projets qui utilisent `netstandard1.x` . Elle ne s’applique pas aux projets qui utilisent `netstandard2.x` .

Utilisez la `NetStandardImplicitPackageVersion` propriété lorsque vous souhaitez spécifier une version de Framework inférieure à la version de l’ensemble de packages. Le fichier projet dans l’exemple suivant cible, `netstandard1.3` mais utilise la version 1.6.0 de `NETStandard.Library` .

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a>Propriétés du package

Vous pouvez spécifier des propriétés telles que `PackageId` , `PackageVersion` ,, `PackageIcon` `Title` et `Description` pour décrire le package qui est créé à partir de votre projet. Pour plus d’informations sur ces propriétés et d’autres, consultez [package Target](/nuget/reference/msbuild-targets#pack-target).

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-and-items"></a>Publier les propriétés et les éléments

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

La `RuntimeIdentifiers` propriété vous permet de spécifier une liste délimitée par des points-virgules des [identificateurs de Runtime (RID)](../rid-catalog.md) pour le projet. Utilisez cette propriété si vous devez publier pour plusieurs runtimes. `RuntimeIdentifiers` est utilisé au moment de la restauration pour s’assurer que les ressources appropriées sont dans le graphique.

> [!TIP]
> `RuntimeIdentifier` (singulier) peut fournir des builds plus rapides quand un seul Runtime est requis.

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

La `UseAppHost` propriété a été introduite dans la version 2.1.400 du kit de développement logiciel (SDK) .net. Il contrôle si un exécutable natif est créé ou non pour un déploiement. Un exécutable natif est requis pour les déploiements autonomes.

Dans .NET Core 3,0 et versions ultérieures, un fichier exécutable dépendant du Framework est créé par défaut. Affectez à la propriété la valeur `UseAppHost` `false` pour désactiver la génération de l’exécutable.

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

Pour plus d’informations sur le déploiement, consultez [déploiement d’applications .net](../deploying/index.md).

## <a name="compile-properties"></a>Propriétés de compilation

- [EmbeddedResourceUseDependentUponConvention](#embeddedresourceusedependentuponconvention)
- [LangVersion](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a>EmbeddedResourceUseDependentUponConvention

La `EmbeddedResourceUseDependentUponConvention` propriété définit si les noms des fichiers manifestes de ressources sont générés à partir des informations de type dans les fichiers sources qui sont colocalisés avec les fichiers de ressources. Par exemple, si *Form1. resx* se trouve dans le même dossier que *Form1.cs*et que `EmbeddedResourceUseDependentUponConvention` a la valeur `true` , le fichier *. Resources* généré prend son nom dans le premier type défini dans *Form1.cs*. Par exemple, si `MyNamespace.Form1` est le premier type défini dans *Form1.cs*, le nom de fichier généré est *MyNamespace. Form1. Resources*.

> [!NOTE]
> Si `LogicalName` `ManifestResourceName` `DependentUpon` les métadonnées, ou sont spécifiées pour un `EmbeddedResource` élément, le nom de fichier manifeste généré pour ce fichier de ressources est basé sur ces métadonnées à la place.

Par défaut, dans un nouveau projet .NET, cette propriété a la valeur `true` . Si la valeur `false` est définie sur, et si aucune `LogicalName` `ManifestResourceName` `DependentUpon` métadonnée n’est spécifiée pour l' `EmbeddedResource` élément dans le fichier projet, le nom du fichier manifeste de la ressource est basé sur l’espace de noms racine du projet et le chemin d’accès relatif au fichier *. resx* . Pour plus d’informations, consultez [Comment les fichiers manifestes de ressources sont nommés](../resources/manifest-file-names.md).

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a>LangVersion

La `LangVersion` propriété vous permet de spécifier une version du langage de programmation spécifique. Par exemple, si vous souhaitez accéder aux fonctionnalités de la version préliminaire de C#, affectez à la valeur `LangVersion` `preview` .

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Pour plus d’informations, consultez contrôle de [version du langage C#](../../csharp/language-reference/configure-language-version.md#override-a-default).

## <a name="code-analysis-properties"></a>Propriétés de l’analyse du code

### <a name="analysislevel"></a>AnalysisLevel

La `AnalysisLevel` propriété vous permet de spécifier un niveau d’analyse du code. Par exemple, si vous souhaitez accéder à l’aperçu des analyseurs de code, affectez à la valeur `AnalysisLevel` `preview` . La valeur par défaut est `latest`.

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

Le tableau suivant présente les options disponibles.

| Value | Signification |
|-|-|
| `latest` | Les derniers analyseurs de code qui ont été publiés sont utilisés. Il s’agit de la valeur par défaut. |
| `preview` | Les derniers analyseurs de code sont utilisés, même s’ils sont en version préliminaire. |
| `5.0` | L’ensemble de règles activé pour la version .NET 5,0 est utilisé, même si des règles plus récentes sont disponibles. |
| `5` | L’ensemble de règles activé pour la version .NET 5,0 est utilisé, même si des règles plus récentes sont disponibles. |

### <a name="analysismode"></a>AnalysisMode

À compter de .NET 5,0 RC2, le kit de développement logiciel (SDK) .NET est fourni avec toutes les [règles de qualité du code « ca »](../../fundamentals/code-analysis/rules/quality-rules-reference.md). Par défaut, seules [certaines règles sont activées](../../fundamentals/code-analysis/overview.md#enabled-rules) en tant qu’avertissements de génération. La `AnalysisMode` propriété vous permet de personnaliser l’ensemble des règles qui sont activées par défaut. Vous pouvez basculer vers un mode d’analyse plus agressif ou un mode d’analyse plus prudent (abonnement). Par exemple, si vous souhaitez activer toutes les règles par défaut en tant qu’avertissements de build, affectez la valeur à `AllEnabledByDefault` .

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
</PropertyGroup>
```

Le tableau suivant présente les options disponibles.

| Value | Signification |
|-|-|
| `Default` | Mode par défaut, où certaines règles sont activées en tant qu’avertissements de build, certaines règles sont activées en tant que suggestions de l’IDE Visual Studio, et le reste est désactivé. |
| `AllEnabledByDefault` | Mode agressif ou opt-out, où toutes les règles sont activées par défaut en tant qu’avertissements de génération. Vous pouvez [choisir](../../fundamentals/code-analysis/configuration-options.md) de désactiver les règles individuelles de manière sélective pour les désactiver. |
| `AllDisabledByDefault` | Mode conservateur ou opt-in, où toutes les règles sont désactivées par défaut. Vous pouvez [choisir](../../fundamentals/code-analysis/configuration-options.md) des règles individuelles pour les activer. |

### <a name="codeanalysistreatwarningsaserrors"></a>CodeAnalysisTreatWarningsAsErrors

La `CodeAnalysisTreatWarningsAsErrors` propriété vous permet de configurer si les avertissements d’analyse de la qualité du code (CAXXXX) doivent être traités comme des avertissements et rompre la génération. Si vous utilisez l' `-warnaserror` indicateur lorsque vous générez vos projets, les avertissements de l’analyse de la [qualité du code .net](../../fundamentals/code-analysis/overview.md#code-quality-analysis) sont également traités comme des erreurs. Si vous ne souhaitez pas que les avertissements d’analyse de la qualité du code soient traités comme des erreurs, vous pouvez définir la `CodeAnalysisTreatWarningsAsErrors` propriété MSBuild sur `false` dans votre fichier projet.

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a>EnableNETAnalyzers

L’analyse de la [qualité du code .net](../../fundamentals/code-analysis/overview.md#code-quality-analysis) est activée, par défaut, pour les projets qui ciblent .net 5,0 ou une version ultérieure. Vous pouvez activer l’analyse du code .NET pour les projets qui ciblent des versions antérieures de .NET en affectant à la propriété la valeur `EnableNETAnalyzers` `true` . Pour désactiver l’analyse du code dans un projet, affectez la valeur à cette propriété `false` .

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!TIP]
> Une autre façon d’activer l’analyse du code .NET sur les projets qui ciblent les versions .NET antérieures à .NET 5,0 consiste à définir la propriété [AnalysisLevel](#analysislevel) sur `latest` .

### <a name="enforcecodestyleinbuild"></a>EnforceCodeStyleInBuild

L' [analyse du style de code .net](../../fundamentals/code-analysis/overview.md#code-style-analysis) est désactivée, par défaut, à la génération pour tous les projets .net. Vous pouvez activer l’analyse de style de code pour les projets .NET en affectant à la propriété la valeur `EnforceCodeStyleInBuild` `true` .

```xml
<PropertyGroup>
  <EnforceCodeStyleInBuild>true</EnforceCodeStyleInBuild>
</PropertyGroup>
```

Toutes les règles de style de code qui sont [configurées](../../fundamentals/code-analysis/overview.md#code-style-analysis) pour être des avertissements ou des erreurs sont exécutées lors des violations de la build et des rapports.

## <a name="run-time-configuration-properties"></a>Propriétés de configuration au moment de l’exécution

Vous pouvez configurer certains comportements au moment de l’exécution en spécifiant des propriétés MSBuild dans le fichier projet de l’application. Pour plus d’informations sur les autres méthodes de configuration du comportement au moment de l’exécution, consultez [paramètres de configuration](../run-time-config/index.md)de l’exécution.

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

La `ConcurrentGarbageCollection` propriété configure si l' [garbage collection d’arrière-plan (simultané)](../../standard/garbage-collection/background-gc.md) est activée. Affectez la valeur `false` à pour désactiver les garbage collection d’arrière-plan. Pour plus d’informations, consultez [Background gc](../run-time-config/garbage-collector.md#background-gc).

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a>InvariantGlobalization

La `InvariantGlobalization` propriété configure si l’application s’exécute en mode de *globalisation invariant* , ce qui signifie qu’elle n’a pas accès aux données spécifiques à la culture. Affectez à la valeur la valeur `true` pour qu’elle s’exécute en mode de globalisation-indifférent. Pour plus d’informations, consultez [mode indifférent](../run-time-config/globalization.md#invariant-mode).

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a>RetainVMGarbageCollection

La `RetainVMGarbageCollection` propriété configure le garbage collector pour placer les segments de mémoire supprimés sur une liste d’attente pour une utilisation ultérieure ou les libérer. La définition de la valeur `true` indique au garbage collector de placer les segments sur une liste d’attente. Pour plus d’informations, consultez [conserver la machine virtuelle](../run-time-config/garbage-collector.md#retain-vm).

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a>ServerGarbageCollection

La `ServerGarbageCollection` propriété configure si l’application utilise des [garbage collection de station de travail ou des garbage collection de serveur](../../standard/garbage-collection/workstation-server-gc.md). Définissez la valeur sur `true` sur utiliser le garbage collection serveur. Pour plus d’informations, consultez [station de travail et serveur](../run-time-config/garbage-collector.md#workstation-vs-server).

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

## <a name="reference-properties-and-items"></a>Propriétés et éléments de référence

- [AssetTargetFallback](#assettargetfallback)
- [PackageReference](#packagereference)
- [ProjectReference](#projectreference)
- [Référence](#reference)
- [Propriétés de restauration](#restore-properties)

### <a name="assettargetfallback"></a>AssetTargetFallback

La `AssetTargetFallback` propriété vous permet de spécifier des versions de Framework compatibles supplémentaires pour les références de projet et les packages NuGet. Par exemple, si vous spécifiez une dépendance de package à l’aide de `PackageReference` mais que ce package ne contient pas de ressources compatibles avec les projets `TargetFramework` , la `AssetTargetFallback` propriété entre en lecture. La compatibilité du package référencé est revérifiée à l’aide de chaque version cible de .NET Framework spécifiée dans `AssetTargetFallback` .

Vous pouvez définir la `AssetTargetFallback` propriété sur une ou plusieurs [versions du Framework cible](../../standard/frameworks.md#supported-target-frameworks).

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a>PackageReference

L' `PackageReference` élément définit une référence à un package NuGet.

L’attribut `Include` spécifie l’ID du package. L' `Version` attribut spécifie la version ou la plage de versions. Pour plus d’informations sur la spécification d’une version minimale, d’une version maximale, d’une plage ou d’une correspondance exacte, consultez [plages de versions](/nuget/concepts/package-versioning#version-ranges). Vous pouvez également ajouter les métadonnées suivantes à une référence de projet : `IncludeAssets` , `ExcludeAssets` et `PrivateAssets` .

L’extrait de code du fichier projet dans l’exemple suivant référence le package [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

Pour plus d’informations, consultez [références de package dans les fichiers projet](/nuget/consume-packages/package-references-in-project-files).

### <a name="projectreference"></a>ProjectReference

L' `ProjectReference` élément définit une référence à un autre projet. Le projet référencé est ajouté en tant que dépendance de package NuGet, autrement dit, il est traité de la même façon qu’un `PackageReference` .

L' `Include` attribut spécifie le chemin d’accès au projet. Vous pouvez également ajouter les métadonnées suivantes à une référence de projet : `IncludeAssets` , `ExcludeAssets` et `PrivateAssets` .

L’extrait de code du fichier projet dans l’exemple suivant fait référence à un projet nommé `Project2` .

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a>Informations de référence

L' `Reference` élément définit une référence à un fichier d’assembly.

L' `Include` attribut spécifie le nom du fichier, et les `HintPath` métadonnées spécifient le chemin d’accès à l’assembly.

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a>Propriétés de restauration

La restauration d’un package référencé installe toutes ses dépendances directes et toutes les dépendances de ces dépendances. Vous pouvez personnaliser la restauration des packages en spécifiant des propriétés telles que `RestorePackagesPath` et `RestoreIgnoreFailedSources` . Pour plus d’informations sur ces propriétés et d’autres, consultez [restaurer la cible](/nuget/reference/msbuild-targets#restore-target).

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
