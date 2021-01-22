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

## <a name="publish-properties-items-and-metadata"></a>Publier les propriétés, les éléments et les métadonnées

- [AppendRuntimeIdentifierToOutputPath](#appendruntimeidentifiertooutputpath)
- [AppendTargetFrameworkToOutputPath](#appendtargetframeworktooutputpath)
- [CopyLocalLockFileAssemblies](#copylocallockfileassemblies)
- [CopyToPublishDirectory](#copytopublishdirectory)
- [Ressources](#linkbase)
- [PreserveCompilationContext](#preservecompilationcontext)
- [PreserveCompilationReferences](#preservecompilationreferences)
- [RuntimeIdentifier](#runtimeidentifier)
- [RuntimeIdentifiers](#runtimeidentifiers)
- [TrimmerRootAssembly](#trimmerrootassembly)
- [UseAppHost](#useapphost)

### <a name="copytopublishdirectory"></a>CopyToPublishDirectory

Les `CopyToPublishDirectory` métadonnées d’un élément MSBuild contrôlent le moment où l’élément est copié dans le répertoire de publication. Les valeurs autorisées sont `PreserveNewest` , qui copient uniquement l’élément s’il a changé, `Always` , qui copie toujours l’élément, et `Never` , qui ne copie jamais l’élément. Du point de vue des performances, `PreserveNewest` est préférable, car il permet une génération incrémentielle.

```xml
<ItemGroup>
  <None Update="appsettings.Development.json" CopyToOutputDirectory="PreserveNewest" CopyToPublishDirectory="PreserveNewest" />
</ItemGroup>
```

### <a name="linkbase"></a>Ressources

Pour un élément qui se trouve en dehors du répertoire du projet et de ses sous-répertoires, la cible de publication utilise les [métadonnées de lien](/visualstudio/msbuild/common-msbuild-item-metadata) de l’élément pour déterminer où copier l’élément. `Link` détermine également la manière dont les éléments en dehors de l’arborescence du projet s’affichent dans la fenêtre Explorateur de solutions de Visual Studio.

Si `Link` n’est pas spécifié pour un élément qui se trouve en dehors du cône du projet, la valeur par défaut est `%(LinkBase)\%(RecursiveDir)%(Filename)%(Extension)` . `LinkBase` vous permet de spécifier un dossier de base raisonnable pour les éléments en dehors du cône du projet. L’arborescence des dossiers sous le dossier de base est conservée via `RecursiveDir` . Si `LinkBase` n’est pas spécifié, il est omis du `Link` chemin d’accès.

```xml
<ItemGroup>
  <Content Include="..\Extras\**\*.cs" LinkBase="Shared"/>
</ItemGroup>
```

L’illustration suivante montre comment un fichier inclus via l’élément précédent `Include` glob s’affiche dans Explorateur de solutions.

:::image type="content" source="media/solution-explorer-linkbase.png" alt-text="Explorateur de solutions présentant l’élément avec les métadonnées de lienet.":::

### <a name="appendtargetframeworktooutputpath"></a>AppendTargetFrameworkToOutputPath

La `AppendTargetFrameworkToOutputPath` propriété détermine si le [moniker du Framework cible (TFM)](../../standard/frameworks.md) est ajouté au chemin de sortie (qui est défini par [OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)). Le kit de développement logiciel (SDK) .NET ajoute automatiquement le Framework cible et, le cas échéant, l’identificateur du Runtime au chemin de sortie. L’affectation de `AppendTargetFrameworkToOutputPath` la valeur à `false` empêche le TFM d’être ajouté au chemin de sortie. Toutefois, si le chemin de sortie n’est pas TFM, plusieurs artefacts de build peuvent se remplacer mutuellement.

Par exemple, pour une application .NET 5,0, le chemin de sortie passe de `bin\Debug\net5.0` à `bin\Debug` avec le paramètre suivant :

```xml
<PropertyGroup>
  <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
</PropertyGroup>
```

### <a name="appendruntimeidentifiertooutputpath"></a>AppendRuntimeIdentifierToOutputPath

La `AppendRuntimeIdentifierToOutputPath` propriété détermine si l' [identificateur de Runtime (RID)](../rid-catalog.md) est ajouté au chemin de sortie. Le kit de développement logiciel (SDK) .NET ajoute automatiquement le Framework cible et, le cas échéant, l’identificateur du Runtime au chemin de sortie. `AppendRuntimeIdentifierToOutputPath`La définition de `false` la valeur empêche l’ajout du RID au chemin de sortie.

Par exemple, pour une application .NET 5,0 et un RID `win10-x64` , le chemin de sortie passe de `bin\Debug\net5.0\win10-x64` à `bin\Debug\net5.0` avec le paramètre suivant :

```xml
<PropertyGroup>
  <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
</PropertyGroup>
```

### <a name="copylocallockfileassemblies"></a>CopyLocalLockFileAssemblies

La `CopyLocalLockFileAssemblies` propriété est utile pour les projets de plug-in qui ont des dépendances sur d’autres bibliothèques. Si vous affectez à cette propriété `true` la valeur, toutes les dépendances de package NuGet sont copiées dans le répertoire de sortie. Cela signifie que vous pouvez utiliser la sortie de `dotnet build` pour exécuter votre plug-in sur n’importe quel ordinateur.

```xml
<PropertyGroup>
  <CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>
</PropertyGroup>
```

> [!TIP]
> Vous pouvez également utiliser `dotnet publish` pour publier la bibliothèque de classes. Pour plus d’informations, consultez [dotnet Publish](../tools/dotnet-publish.md).

### <a name="preservecompilationcontext"></a>PreserveCompilationContext

La `PreserveCompilationContext` propriété permet à une application générée ou publiée de compiler davantage de code au moment de l’exécution en utilisant les mêmes paramètres que ceux utilisés au moment de la génération. Les assemblys référencés au moment de la génération sont copiés dans le sous-répertoire *ref* du répertoire de sortie. Les noms des assemblys de référence sont stockés dans l'.deps.jsde l’application *sur* le fichier, ainsi que les options passées au compilateur. Vous pouvez récupérer ces informations à l’aide des <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompileLibraries?displayProperty=nameWithType> <xref:Microsoft.Extensions.DependencyModel.DependencyContext.CompilationOptions?displayProperty=nameWithType> Propriétés et.

Cette fonctionnalité est principalement utilisée en interne par ASP.NET Core MVC et les pages Razor pour prendre en charge la compilation des fichiers Razor au moment de l’exécution.

```xml
<PropertyGroup>
  <PreserveCompilationContext>true</PreserveCompilationContext>
</PropertyGroup>
```

### <a name="preservecompilationreferences"></a>PreserveCompilationReferences

La `PreserveCompilationReferences` propriété est semblable à la propriété [PreserveCompilationContext](#preservecompilationcontext) , à ceci près qu’elle copie uniquement les assemblys référencés dans le répertoire publish, et non le *.deps.jsdans* le fichier.

```xml
<PropertyGroup>
  <PreserveCompilationReferences>true</PreserveCompilationReferences>
</PropertyGroup>
```

Pour plus d’informations, consultez [Propriétés du kit de développement logiciel (SDK) Razor](/aspnet/core/razor-pages/sdk#properties).

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

La `UseAppHost` propriété contrôle si un exécutable natif est créé ou non pour un déploiement. Un exécutable natif est requis pour les déploiements autonomes.

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

La `EmbeddedResourceUseDependentUponConvention` propriété définit si les noms des fichiers manifestes de ressources sont générés à partir des informations de type dans les fichiers sources qui sont colocalisés avec les fichiers de ressources. Par exemple, si *Form1. resx* se trouve dans le même dossier que *Form1.cs* et que `EmbeddedResourceUseDependentUponConvention` a la valeur `true` , le fichier *. Resources* généré prend son nom dans le premier type défini dans *Form1.cs*. Par exemple, si `MyNamespace.Form1` est le premier type défini dans *Form1.cs*, le nom de fichier généré est *MyNamespace. Form1. Resources*.

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

## <a name="default-item-inclusion-properties"></a>Propriétés d’inclusion d’élément par défaut

- [DefaultExcludesInProjectFolder](#defaultexcludesinprojectfolder)
- [DefaultItemExcludes](#defaultitemexcludes)
- [EnableDefaultCompileItems](#enabledefaultcompileitems)
- [EnableDefaultEmbeddedResourceItems](#enabledefaultembeddedresourceitems)
- [EnableDefaultItems](#enabledefaultitems)
- [EnableDefaultNoneItems](#enabledefaultnoneitems)

Pour plus d’informations, consultez [include et Exclude par défaut](overview.md#default-includes-and-excludes).

### <a name="defaultitemexcludes"></a>DefaultItemExcludes

Utilisez la `DefaultItemExcludes` propriété pour définir les modèles glob pour les fichiers et les dossiers qui doivent être exclus des modèles glob include, Exclude et Remove. Par défaut, les dossiers *./bin* et *./obj* sont exclus des modèles glob.

```xml
<PropertyGroup>
  <DefaultItemExcludes>$(DefaultItemExcludes);**/*.myextension</DefaultItemExcludes>
</PropertyGroup>
```

### <a name="defaultexcludesinprojectfolder"></a>DefaultExcludesInProjectFolder

Utilisez la `DefaultExcludesInProjectFolder` propriété pour définir les modèles glob pour les fichiers et les dossiers dans le dossier du projet qui doivent être exclus des modèles glob include, Exclude et Remove. Par défaut, les dossiers qui commencent par un point ( `.` ), tels que *. git* et *. vs*, sont exclus des modèles glob.

Cette propriété est très similaire à la `DefaultItemExcludes` propriété, sauf qu’elle considère uniquement les fichiers et les dossiers dans le dossier du projet. Quand un modèle glob correspondrait involontairement à des éléments en dehors du dossier du projet avec un chemin d’accès relatif, utilisez la propriété à la `DefaultExcludesInProjectFolder` place de la `DefaultItemExcludes` propriété.

```xml
<PropertyGroup>
  <DefaultExcludesInProjectFolder>$(DefaultExcludesInProjectFolder);**/myprefix*/**</DefaultExcludesInProjectFolder>
</PropertyGroup>
```

### <a name="enabledefaultitems"></a>EnableDefaultItems

La `EnableDefaultItems` propriété contrôle si les éléments de compilation, les éléments de ressources incorporés et les `None` éléments sont implicitement inclus dans le projet. La valeur par défaut est `true`. Affectez à la propriété la valeur `EnableDefaultItems` `false` pour désactiver toute inclusion de fichier implicite.

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="enabledefaultcompileitems"></a>EnableDefaultCompileItems

La `EnableDefaultCompileItems` propriété contrôle si les éléments de compilation sont inclus implicitement dans le projet. La valeur par défaut est `true`. Affectez à la propriété la valeur `EnableDefaultCompileItems` `false` pour désactiver l’inclusion implicite des fichiers *. cs et d’autres extensions de langage.

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

### <a name="enabledefaultembeddedresourceitems"></a>EnableDefaultEmbeddedResourceItems

La `EnableDefaultEmbeddedResourceItems` propriété contrôle si les éléments de ressources incorporés sont implicitement inclus dans le projet. La valeur par défaut est `true`. Affectez à la propriété la valeur `EnableDefaultEmbeddedResourceItems` `false` pour désactiver l’inclusion implicite des fichiers de ressources incorporés.

```xml
<PropertyGroup>
  <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
</PropertyGroup>
```

### <a name="enabledefaultnoneitems"></a>EnableDefaultNoneItems

La `EnableDefaultNoneItems` propriété contrôle si les `None` éléments (fichiers qui n’ont pas de rôle dans le processus de génération) sont implicitement inclus dans le projet. La valeur par défaut est `true`. Affectez à la propriété la valeur `EnableDefaultNoneItems` `false` pour désactiver l’inclusion implicite d' `None` éléments.

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

## <a name="code-analysis-properties"></a>Propriétés de l’analyse du code

- [AnalysisLevel](#analysislevel)
- [AnalysisMode](#analysismode)
- [CodeAnalysisTreatWarningsAsErrors](#codeanalysistreatwarningsaserrors)
- [EnableNETAnalyzers](#enablenetanalyzers)
- [EnforceCodeStyleInBuild](#enforcecodestyleinbuild)

### <a name="analysislevel"></a>AnalysisLevel

La `AnalysisLevel` propriété vous permet de spécifier un niveau d’analyse du code. Par exemple, si vous souhaitez accéder à l’aperçu des analyseurs de code, affectez à la valeur `AnalysisLevel` `preview` . La valeur par défaut est `latest`.

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

Le tableau suivant présente les options disponibles.

| Valeur | Signification |
|-|-|
| `latest` | Les derniers analyseurs de code qui ont été publiés sont utilisés. Il s’agit de la valeur par défaut. |
| `preview` | Les derniers analyseurs de code sont utilisés, même s’ils sont en version préliminaire. |
| `5.0` | L’ensemble de règles activé pour la version .NET 5,0 est utilisé, même si des règles plus récentes sont disponibles. |
| `5` | L’ensemble de règles activé pour la version .NET 5,0 est utilisé, même si des règles plus récentes sont disponibles. |

### <a name="analysismode"></a>AnalysisMode

À compter de .NET 5,0, le kit de développement logiciel (SDK) .NET est fourni avec toutes les [règles de qualité du code « ca »](../../fundamentals/code-analysis/quality-rules/index.md). Par défaut, seules [certaines règles sont activées](../../fundamentals/code-analysis/overview.md#enabled-rules) en tant qu’avertissements de génération. La `AnalysisMode` propriété vous permet de personnaliser l’ensemble des règles qui sont activées par défaut. Vous pouvez basculer vers un mode d’analyse plus agressif ou un mode d’analyse plus prudent (abonnement). Par exemple, si vous souhaitez activer toutes les règles par défaut en tant qu’avertissements de build, affectez la valeur à `AllEnabledByDefault` .

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
</PropertyGroup>
```

Le tableau suivant présente les options disponibles.

| Valeur | Signification |
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

> [!NOTE]
> Cette fonctionnalité est actuellement expérimentale et peut changer entre les versions .NET 5 et .NET 6.

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
- [DisableImplicitFrameworkReferences](#disableimplicitframeworkreferences)
- [PackageReference](#packagereference)
- [ProjectReference](#projectreference)
- [Référence](#reference)
- [Propriétés liées à la restauration](#restore-related-properties)

### <a name="assettargetfallback"></a>AssetTargetFallback

La `AssetTargetFallback` propriété vous permet de spécifier des versions de Framework compatibles supplémentaires pour les références de projet et les packages NuGet. Par exemple, si vous spécifiez une dépendance de package à l’aide de `PackageReference` mais que ce package ne contient pas de ressources compatibles avec les projets `TargetFramework` , la `AssetTargetFallback` propriété entre en lecture. La compatibilité du package référencé est revérifiée à l’aide de chaque version cible de .NET Framework spécifiée dans `AssetTargetFallback` . Cette propriété remplace la propriété déconseillée `PackageTargetFallback` .

Vous pouvez définir la `AssetTargetFallback` propriété sur une ou plusieurs [versions du Framework cible](../../standard/frameworks.md#supported-target-frameworks).

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="disableimplicitframeworkreferences"></a>DisableImplicitFrameworkReferences

La `DisableImplicitFrameworkReferences` propriété contrôle les `FrameworkReference` éléments implicites lors du ciblage de .net Core 3,0 et des versions ultérieures. Quand vous ciblez .NET Core 2,1 ou .NET Standard 2,0 et versions antérieures, il contrôle les éléments [PackageReference](#packagereference) implicites pour les packages dans un sous-package. (Un reconditionnement est un package basé sur une infrastructure qui se compose uniquement de dépendances sur d’autres packages.) Cette propriété contrôle également les références implicites telles que `System` et `System.Core` lorsque vous ciblez .NET Framework.

Affectez à cette propriété la valeur `true` pour désactiver les éléments implicites `FrameworkReference` ou [PackageReference](#packagereference) . Si vous affectez à cette propriété `true` la valeur, vous pouvez ajouter des références explicites uniquement aux frameworks ou aux packages dont vous avez besoin.

```xml
<PropertyGroup>
  <DisableImplicitFrameworkReferences>true</DisableImplicitFrameworkReferences>
</PropertyGroup>
```

### <a name="packagereference"></a>PackageReference

L' `PackageReference` élément définit une référence à un package NuGet.

L’attribut `Include` spécifie l’ID du package. L' `Version` attribut spécifie la version ou la plage de versions. Pour plus d’informations sur la spécification d’une version minimale, d’une version maximale, d’une plage ou d’une correspondance exacte, consultez [plages de versions](/nuget/concepts/package-versioning#version-ranges). Vous pouvez également ajouter des [attributs de ressource](#asset-attributes) à une référence de package.

L’extrait de code du fichier projet dans l’exemple suivant référence le package [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

Pour plus d’informations, consultez [références de package dans les fichiers projet](/nuget/consume-packages/package-references-in-project-files).

#### <a name="asset-attributes"></a>Attributs de ressource

Les `IncludeAssets` `ExcludeAssets` `PrivateAssets` métadonnées, et peuvent être ajoutées à une référence de package.

| Attribut | Description |
| - | - |
| `IncludeAssets` | Spécifie quelles ressources appartenant au package spécifié par `<PackageReference>` doivent être consommées. Par défaut, toutes les ressources du package sont incluses. |
| `ExcludeAssets`| Spécifie les ressources appartenant au package spécifié par ne `<PackageReference>` doivent pas être consommées. |
| `PrivateAssets` | Spécifie les ressources appartenant au package spécifié par `<PackageReference>` doivent être consommées, mais pas transmises au projet suivant. Les `Analyzers` `Build` ressources, et `ContentFiles` sont privées par défaut lorsque cet attribut n’est pas présent. |

Ces attributs peuvent contenir un ou plusieurs des éléments suivants, séparés par un point-virgule `;` si plus d’un élément est listé :

- `Compile` : le contenu du dossier *lib* est disponible pour la compilation.
- `Runtime` : le contenu du dossier *Runtime* est distribué.
- `ContentFiles` : Le contenu du dossier *contentfiles* est utilisé.
- `Build` : les propriétés/cibles du dossier de *génération* sont utilisées.
- `Native` : le contenu des ressources natives est copié dans le dossier de *sortie* pour l’exécution.
- `Analyzers` : Les analyseurs sont utilisés.

Sinon, l’attribut peut contenir :

- `None` : Aucune ressource n’est utilisée.
- `All` : Toutes les ressources sont utilisées.

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

### <a name="restore-related-properties"></a>Propriétés liées à la restauration

La restauration d’un package référencé installe toutes ses dépendances directes et toutes les dépendances de ces dépendances. Vous pouvez personnaliser la restauration des packages en spécifiant des propriétés telles que `RestorePackagesPath` et `RestoreIgnoreFailedSources` . Pour plus d’informations sur ces propriétés et d’autres, consultez [restaurer la cible](/nuget/reference/msbuild-targets#restore-target).

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="run-properties"></a>Propriétés d’exécution

Les propriétés suivantes sont utilisées pour lancer une application à l’aide de la [`dotnet run`](../tools/dotnet-run.md) commande :

- [RunArguments](#runarguments)
- [RunWorkingDirectory](#runworkingdirectory)

### <a name="runarguments"></a>RunArguments

La `RunArguments` propriété définit les arguments passés à l’application lorsqu’elle est exécutée.

```xml
<PropertyGroup>
  <RunArguments>-mode dryrun</RunArguments>
</PropertyGroup>
```

> [!TIP]
> Vous pouvez spécifier des arguments supplémentaires à passer à l’application à l’aide [ `--` de l' `dotnet run` option pour ](../tools/dotnet-run.md#options).

### <a name="runworkingdirectory"></a>RunWorkingDirectory

La `RunWorkingDirectory` propriété définit le répertoire de travail pour le processus d’application à démarrer dans. Il peut s’agir d’un chemin d’accès absolu ou d’un chemin d’accès relatif au répertoire du projet. Si vous ne spécifiez pas de répertoire, `OutDir` est utilisé comme répertoire de travail.

```xml
<PropertyGroup>
  <RunWorkingDirectory>c:\temp</RunWorkingDirectory>
</PropertyGroup>
```

## <a name="hosting-properties"></a>Propriétés d’hébergement

- [EnableComHosting](#enablecomhosting)
- [EnableDynamicLoading](#enabledynamicloading)

### <a name="enablecomhosting"></a>EnableComHosting

La `EnableComHosting` propriété indique qu’un assembly fournit un serveur com. Le `EnableComHosting` fait d’affecter à la valeur `true` implique également que [EnableDynamicLoading](#enabledynamicloading) est `true` .

```xml
<PropertyGroup>
  <EnableComHosting>True</EnableComHosting>
</PropertyGroup>
```

Pour plus d’informations, consultez [exposer des composants .net à com](../native-interop/expose-components-to-com.md).

### <a name="enabledynamicloading"></a>EnableDynamicLoading

La `EnableDynamicLoading` propriété indique qu’un assembly est un composant chargé dynamiquement. Le composant peut être une bibliothèque [com](/windows/win32/com/the-component-object-model) ou une bibliothèque non-com qui peut être [utilisée à partir d’un hôte natif](../tutorials/netcore-hosting.md). L’affectation de la valeur à cette propriété `true` a les effets suivants :

- Un *.runtimeconfig.jssur le* fichier est généré.
- La [restauration par progression](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) est définie sur `LatestMinor` .
- Les références NuGet sont copiées localement.

```xml
<PropertyGroup>
  <EnableDynamicLoading>true</EnableDynamicLoading>
</PropertyGroup>
```

## <a name="see-also"></a>Voir aussi

- [Référence du schéma MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [Propriétés MSBuild communes](/visualstudio/msbuild/common-msbuild-project-properties)
- [Propriétés MSBuild pour le Pack NuGet](/nuget/reference/msbuild-targets#pack-target)
- [Propriétés MSBuild pour la restauration NuGet](/nuget/reference/msbuild-targets#restore-properties)
- [Personnaliser une build](/visualstudio/msbuild/customize-your-build)
