---
title: Propriétés AssemblyInfo
description: En savoir plus sur les attributs d’assembly et leur correspondance avec les propriétés MSBuild dans .NET Core 2,1 et versions ultérieures.
ms.topic: reference
ms.date: 01/08/2021
ms.openlocfilehash: a2c431b3fe3da428f21582624ca5f357887e2815
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192889"
---
# <a name="map-assemblyinfo-attributes-to-properties"></a>Mapper les attributs AssemblyInfo aux propriétés

Les [attributs d’assembly](../../standard/assembly/set-attributes.md) qui étaient généralement présents dans un fichier *AssemblyInfo* dans .net Core 2,0 et les versions antérieures sont générés automatiquement à partir des propriétés MSBuild, à partir de .net Core 2,1.

## <a name="properties-per-attribute"></a>Propriétés par attribut

Comme indiqué dans le tableau suivant, chaque attribut a une propriété correspondante qui contrôle son contenu et un autre qui désactive sa génération :

| Attribut                                                      | Propriété               | Propriété permettant de désactiver                             |
|----------------------------------------------------------------|------------------------|-------------------------------------------------|
| <xref:System.Reflection.AssemblyCompanyAttribute>              | `Company`              | `GenerateAssemblyCompanyAttribute`              |
| <xref:System.Reflection.AssemblyConfigurationAttribute>        | `Configuration`        | `GenerateAssemblyConfigurationAttribute`        |
| <xref:System.Reflection.AssemblyCopyrightAttribute>            | `Copyright`            | `GenerateAssemblyCopyrightAttribute`            |
| <xref:System.Reflection.AssemblyDescriptionAttribute>          | `Description`          | `GenerateAssemblyDescriptionAttribute`          |
| <xref:System.Reflection.AssemblyFileVersionAttribute>          | `FileVersion`          | `GenerateAssemblyFileVersionAttribute`          |
| <xref:System.Reflection.AssemblyInformationalVersionAttribute> | `InformationalVersion` | `GenerateAssemblyInformationalVersionAttribute` |
| <xref:System.Reflection.AssemblyProductAttribute>              | `Product`              | `GenerateAssemblyProductAttribute`              |
| <xref:System.Reflection.AssemblyTitleAttribute>                | `AssemblyTitle`        | `GenerateAssemblyTitleAttribute`                |
| <xref:System.Reflection.AssemblyVersionAttribute>              | `AssemblyVersion`      | `GenerateAssemblyVersionAttribute`              |
| <xref:System.Resources.NeutralResourcesLanguageAttribute>      | `NeutralLanguage`      | `GenerateNeutralResourcesLanguageAttribute`     |

Remarques :

- `AssemblyVersion` et `FileVersion` la valeur par défaut `$(Version)` sans le suffixe. Par exemple, si `$(Version)` est `1.2.3-beta.4`, alors la valeur serait `1.2.3`.
- `InformationalVersion` utilise par défaut la valeur de `$(Version)`.
- Si la `$(SourceRevisionId)` propriété est présente, elle est ajoutée à `InformationalVersion` . Vous pouvez désactiver ce comportement à l’aide de `IncludeSourceRevisionInInformationalVersion` .
- Les propriétés `Copyright` et `Description` sont également utilisées pour les métadonnées NuGet.
- `Configuration`, dont la valeur par défaut `Debug` est, est partagé avec toutes les cibles MSBuild. Vous pouvez le définir par le biais `--configuration` de l’option des `dotnet` commandes, par exemple, [dotnet Pack](../tools/dotnet-pack.md).

## <a name="generateassemblyinfo"></a>GenerateAssemblyInfo

Valeur booléenne qui active ou désactive la génération de AssemblyInfo. La valeur par défaut est `true`.

## <a name="generatedassemblyinfofile"></a>GeneratedAssemblyInfoFile

Chemin d’accès relatif ou absolu du fichier d’informations de l’assembly généré. La valeur par défaut est un fichier nommé *[Project-Name]. AssemblyInfo. [CS | VB]* dans le `$(IntermediateOutputPath)` répertoire (*obj*).
