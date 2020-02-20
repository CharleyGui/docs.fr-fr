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
# <a name="msbuild-properties-for-net-core-sdk-projects"></a>Propriétés MSBuild pour les projets kit SDK .NET Core

Cette page décrit les propriétés MSBuild pour la configuration des projets .NET Core.

> [!NOTE]
> Cette page est un travail en cours et ne répertorie pas toutes les propriétés MSBuild utiles pour le kit SDK .NET Core. Pour obtenir la liste des propriétés MSBuild courantes, consultez [propriétés MSBuild communes](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="framework-properties"></a>Propriétés du Framework

- [NetStandardImplicitPackageVersion](#netstandardimplicitpackageversion)
- [TargetFramework](#targetframework)
- [TargetFrameworks](#targetframeworks)

### <a name="netstandardimplicitpackageversion"></a>NetStandardImplicitPackageVersion

> [!NOTE]
> Cette propriété s’applique uniquement aux projets qui utilisent `netstandard1.x`. Elle ne s’applique pas aux projets qui utilisent `netstandard2` et versions ultérieures.

Utilisez la propriété `NetStandardImplicitPackageVersion` lorsque vous souhaitez spécifier une version de Framework inférieure à la version de l' [ensemble de packages](../packages.md#metapackages) . Le fichier projet dans l’exemple suivant cible `netstandard1.3` mais utilise la version 1.6.0 de `NETStandard.Library`.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

### <a name="targetframework"></a>TargetFramework

La propriété `TargetFramework` spécifie la version cible de .NET Framework pour l’application, qui référence implicitement un [repackage](../packages.md#metapackages). Pour obtenir la liste des monikers du Framework cible valides, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

Pour plus d’informations, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md).

### <a name="targetframeworks"></a>TargetFrameworks

Utilisez la propriété `TargetFrameworks` lorsque vous souhaitez que votre application cible plusieurs plateformes. Pour obtenir la liste des monikers du Framework cible valides, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md#supported-target-framework-versions).

> [!NOTE]
> Cette propriété est ignorée si `TargetFramework` (singulier) est spécifié.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

Pour plus d’informations, consultez [frameworks cibles dans les projets de type SDK](../../standard/frameworks.md).

## <a name="publish-properties"></a>Propriétés de publication

- [RuntimeIdentifier](#runtimeidentifier)
- [RuntimeIdentifiers](#runtimeidentifiers)
- [UseAppHost](#useapphost)

### <a name="runtimeidentifier"></a>RuntimeIdentifier

La propriété `RuntimeIdentifier` vous permet de spécifier un [identificateur de Runtime unique (RID)](../rid-catalog.md) pour le projet. Le RID permet de publier un déploiement autonome.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

La propriété `RuntimeIdentifiers` vous permet de spécifier une liste délimitée par des points-virgules des [identificateurs de Runtime (RID)](../rid-catalog.md) pour le projet. Utilisez cette propriété si vous devez publier pour plusieurs runtimes. `RuntimeIdentifiers` est utilisé au moment de la restauration pour s’assurer que les ressources appropriées sont dans le graphique.

> [!TIP]
> `RuntimeIdentifier` (singulier) peut fournir des builds plus rapides quand un seul Runtime est requis.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a>UseAppHost

La propriété `UseAppHost` a été introduite dans la version 2.1.400 de l’kit SDK .NET Core. Il contrôle si un exécutable natif est créé ou non pour un déploiement. Un exécutable natif est requis pour les déploiements autonomes.

Dans .NET Core 3,0 et versions ultérieures, un fichier exécutable dépendant du Framework est créé par défaut. Affectez à la propriété `UseAppHost` la valeur `false` pour désactiver la génération du fichier exécutable.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

Pour plus d’informations sur le déploiement, consultez [déploiement d’applications .net Core](../deploying/index.md).

## <a name="compile-properties"></a>Propriétés de compilation

### <a name="langversion"></a>LangVersion

La propriété `LangVersion` vous permet de spécifier une version spécifique du langage de programmation. Par exemple, si vous souhaitez accéder aux C# fonctionnalités en version préliminaire, définissez `LangVersion` sur `preview`.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

Pour plus d’informations, [ C# ](../../csharp/language-reference/configure-language-version.md#override-a-default)consultez contrôle de version de langage.

## <a name="nuget-packages"></a>Packages NuGet

- [PackageReference](#packagereference)

### <a name="packagereference"></a>PackageReference

L’élément `PackageReference` vous permet de spécifier une dépendance NuGet. Par exemple, vous souhaiterez peut-être référencer un package unique au lieu d’un sous- [package](../packages.md#metapackages). L’attribut `Include` spécifie l’ID du package. L’extrait de code du fichier projet dans l’exemple suivant référence le package [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

Pour plus d’informations, consultez [références de package dans les fichiers projet](/nuget/consume-packages/package-references-in-project-files).

### <a name="pack-and-restore-targets"></a>Cibles de Pack et de restauration

MSBuild 15,1 a introduit `pack` et `restore` cibles pour la création et la restauration de packages NuGet dans le cadre d’une build. Pour plus d’informations sur les propriétés MSBuild pour ces cibles, y compris `PackageTargetFallback`, consultez [NuGet Pack et Restore en tant que cibles MSBuild](/nuget/reference/msbuild-targets).

## <a name="see-also"></a>Voir aussi

- [Référence du schéma MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [Propriétés MSBuild communes](/visualstudio/msbuild/common-msbuild-project-properties)
- [Propriétés MSBuild pour le Pack NuGet](/nuget/reference/msbuild-targets#pack-target)
- [Propriétés MSBuild pour la restauration NuGet](/nuget/reference/msbuild-targets#restore-properties)
- [Personnaliser une build](/visualstudio/msbuild/customize-your-build)
