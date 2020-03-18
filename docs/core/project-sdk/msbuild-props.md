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
# <a name="msbuild-properties-for-net-core-sdk-projects"></a>Propriétés MSBuild pour les projets SDK de base .NET

Cette page décrit les propriétés MSBuild pour configurer des projets .NET Core.

> [!NOTE]
> Cette page est un travail en cours et n’énumère pas toutes les propriétés utiles MSBuild pour le .NET Core SDK. Pour une liste des propriétés COMMUNES MSBuild, voir [propriétés communes MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="framework-properties"></a>Propriétés-cadres

- [TargetFramework (TargetFramework)](#targetframework)
- [TargetFrameworks (TargetFrameworks)](#targetframeworks)
- [NetStandardImplicitPackageVersion](#netstandardimplicitpackageversion)

### <a name="targetframework"></a>TargetFramework (TargetFramework)

La `TargetFramework` propriété spécifie la version cadre cible de l’application, qui fait implicitement référence à un [métapackage](../packages.md#metapackages). Pour une liste de nom-cadre cible valide, voir [les cadres Target dans les projets de type SDK](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

Pour plus d’informations, voir [les cadres Target dans les projets de style SDK](../../standard/frameworks.md).

### <a name="targetframeworks"></a>TargetFrameworks (TargetFrameworks)

Utilisez `TargetFrameworks` la propriété lorsque vous souhaitez que votre application cible plusieurs plates-formes. Pour une liste de nom-cadre cible valide, voir [les cadres Target dans les projets de type SDK](../../standard/frameworks.md#supported-target-framework-versions).

> [!NOTE]
> Cette propriété est `TargetFramework` ignorée si (singulier) est spécifié.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

Pour plus d’informations, voir [les cadres Target dans les projets de style SDK](../../standard/frameworks.md).

### <a name="netstandardimplicitpackageversion"></a>NetStandardImplicitPackageVersion

> [!NOTE]
> Cette propriété ne s’applique qu’aux projets utilisant `netstandard1.x`. Il ne s’applique pas `netstandard2.x`aux projets qui utilisent .

Utilisez `NetStandardImplicitPackageVersion` la propriété lorsque vous souhaitez spécifier une version-cadre inférieure à la version [métapackage.](../packages.md#metapackages) Le fichier de projet `netstandard1.3` dans l’exemple suivant vise mais utilise `NETStandard.Library`la version 1.6.0 de .

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
- [UtiliserAppHost](#useapphost)

### <a name="runtimeidentifier"></a>RuntimeIdentifier

La `RuntimeIdentifier` propriété vous permet de spécifier un [identifiant d’exécution unique (RID)](../rid-catalog.md) pour le projet. Le RID permet de publier un déploiement autonome.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

La `RuntimeIdentifiers` propriété vous permet de spécifier une liste d’identifiants de [temps d’exécution (RID)](../rid-catalog.md) pour le projet. Utilisez cette propriété si vous avez besoin de publier pour plusieurs runtimes. `RuntimeIdentifiers`est utilisé au moment de la restauration pour s’assurer que les bons actifs sont dans le graphique.

> [!TIP]
> `RuntimeIdentifier`(singulier) peut fournir des constructions plus rapides quand un seul temps d’exécution est nécessaire.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a>UtiliserAppHost

La `UseAppHost` propriété a été introduite dans la version 2.1.400 du .NET Core SDK. Il contrôle si un natif exécutable est créé pour un déploiement. Un autochtone exécutable est nécessaire pour les déploiements autonomes.

Dans .NET Core 3.0 et les versions ultérieures, un cadre dépendant exécutable est créé par défaut. Définissez `UseAppHost` la `false` propriété pour désactiver la génération de l’exécutable.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

Pour plus d’informations sur le déploiement, voir [déploiement d’applications .NET Core](../deploying/index.md).

## <a name="compile-properties"></a>Propriétés Compile

### <a name="langversion"></a>LangVersion (LangVersion)

La `LangVersion` propriété vous permet de spécifier une version linguistique de programmation spécifique. Par exemple, si vous souhaitez accéder aux `LangVersion` `preview`fonctionnalités d’aperçu de C, définissez pour .

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

Pour plus d’informations, voir [la version linguistique C .](../../csharp/language-reference/configure-language-version.md#override-a-default)

## <a name="nuget-packages"></a>Packages NuGet

- [PackageReference](#packagereference)
- [AssetTargetFallback (en)](#assettargetfallback)

### <a name="packagereference"></a>PackageReference

L’article `PackageReference` vous permet de spécifier une dépendance NuGet. Par exemple, vous pouvez faire référence à un seul paquet au lieu d’un [métapackage](../packages.md#metapackages). L’attribut `Include` spécifie l’ID du package. L’extrait de fichier de projet dans l’exemple suivant fait référence au paquet [System.Runtime.](https://www.nuget.org/packages/System.Runtime/)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

Pour plus d’informations, voir [références Paquet dans les fichiers de projet](/nuget/consume-packages/package-references-in-project-files).

### <a name="assettargetfallback"></a>AssetTargetFallback (en)

La `AssetTargetFallback` propriété vous permet de spécifier des versions-cadres compatibles supplémentaires pour les projets que vos références de projet et les forfaits NuGet que votre projet consomme. Par exemple, si vous spécifiez une dépendance au forfait à l’aide de l’emballage, `PackageReference` mais que ce paquet ne contient pas d’actifs `TargetFramework`compatibles avec vos projets, la `AssetTargetFallback` propriété entre en jeu. La compatibilité du paquet référencé est revérifié à `AssetTargetFallback`l’aide de chaque cadre cible spécifié dans .

Vous pouvez `AssetTargetFallback` définir la propriété à une ou plusieurs [versions de cadre cible](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <PropertyGroup>
    <AssetTargetFallback>net461</AssetTargetFallback>
  </PropertyGroup>
</Project>
```

### <a name="pack-and-restore-targets"></a>Emballez et rétablissez les cibles

MSBuild 15.1 `pack` `restore` introduit et des objectifs pour la création et la restauration des paquets NuGet dans le cadre d’une construction. Pour plus d’informations sur les propriétés `PackageTargetFallback`MSBuild pour ces cibles, y compris , voir [NuGet pack et restaurer comme cibles MSBuild](/nuget/reference/msbuild-targets).

## <a name="see-also"></a>Voir aussi

- [Référence du schéma MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [Propriétés MSBuild communes](/visualstudio/msbuild/common-msbuild-project-properties)
- [Propriétés MSBuild pour Pack NuGet](/nuget/reference/msbuild-targets#pack-target)
- [Propriétés MSBuild pour la restauration NuGet](/nuget/reference/msbuild-targets#restore-properties)
- [Personnaliser une build](/visualstudio/msbuild/customize-your-build)
