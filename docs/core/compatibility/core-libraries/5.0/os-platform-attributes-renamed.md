---
title: 'Modification avec rupture : attributs OSPlatform renommés ou supprimés'
description: En savoir plus sur le changement critique .NET 5,0 dans les bibliothèques .NET de base où les attributs de plateforme de système d’exploitation qui ont été introduits dans une version préliminaire ont été supprimés ou renommés.
ms.date: 11/01/2020
ms.openlocfilehash: 80eba790a607a01e0588c067cdc6105d5f3b20a7
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437881"
---
# <a name="osplatform-attributes-renamed-or-removed"></a>Les attributs OSPlatform ont été renommés ou supprimés

Les attributs suivants qui ont été introduits dans .NET 5,0 Preview 8 ont été supprimés ou renommés : `MinimumOSPlatformAttribute` , `RemovedInOSPlatformAttribute` et `ObsoletedInOSPlatformAttribute` .

## <a name="change-description"></a>Description de la modification

.NET 5,0 Preview 8 a introduit les attributs suivants dans l' <xref:System.Runtime.Versioning> espace de noms :

- `MinimumOSPlatformAttribute`
- `RemovedInOSPlatformAttribute`
- `ObsoletedInOSPlatformAttribute`

Dans .NET 5,0 Preview 8, lorsqu’un projet cible une version spécifique du système d’exploitation de .NET 5 à l’aide d’un [moniker de Framework cible](../../../../standard/frameworks.md) tel que `net5.0-windows` , la génération ajoute un attribut de niveau assembly `System.Runtime.Versioning.MinimumOSPlatformAttribute` .

Dans .NET 5,0 RC1, `ObsoletedInOSPlatformAttribute` a été supprimé et `MinimumOSPlatformAttribute` et et `RemovedInOSPlatformAttribute` ont été renommés comme suit :

| Nom de l’aperçu 8 | RC1 et nom ultérieur |
| - | - |
| `MinimumOSPlatformAttribute` | <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> |
| `RemovedInOSPlatformAttribute` | <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> |

Dans .NET 5,0 RC1 et versions ultérieures, quand un projet cible une version spécifique du système d’exploitation de .NET 5 à l’aide d’un [moniker de Framework cible](../../../../standard/frameworks.md) tel que `net5.0-windows` , la génération ajoute un attribut de niveau assembly <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> .

## <a name="reason-for-change"></a>Motif de modification

.NET 5,0 Preview 8 a introduit des attributs dans <xref:System.Runtime.Versioning> pour spécifier les plateformes prises en charge pour les API. Les attributs sont consommés par l' [Analyseur de compatibilité](../../code-analysis/5.0/ca1416-platform-compatibility-analyzer.md) de la plateforme pour produire des avertissements de génération lorsque des API spécifiques à la plateforme sont consommées sur des plateformes qui ne sont pas prises en charge par ces API.

Pour .NET 5,0 RC1, une fonctionnalité supplémentaire a été ajoutée à l’analyseur de compatibilité de plateforme pour l’exclusion de la plateforme. Cette fonctionnalité permet aux API d’être marquées comme étant entièrement non prises en charge sur les plateformes de système d’exploitation. Cette fonctionnalité vous invite à modifier les attributs, notamment en utilisant des noms plus appropriés. `ObsoletedInOSPlatformAttribute`A été supprimé, car il n’était plus nécessaire.

## <a name="version-introduced"></a>Version introduite

5,0 RC1

## <a name="recommended-action"></a>Action recommandée

Lorsque vous reciblez votre projet de .NET 5,0 Preview 8 vers .NET 5,0 RC1, vous pouvez rencontrer des erreurs de build ou d’exécution en raison de ces modifications. Par exemple, le changement de nom de `MinimumOSPlatformAttribute` est susceptible de générer des erreurs, car l’attribut est appliqué aux assemblys spécifiques à la plateforme au moment de la génération, et les anciens artefacts de build feront toujours référence à l’ancien nom de l’API.

Exemples d’erreurs de génération :

- **erreur CS0246 : le nom du type ou de l’espace de noms’MinimumOSPlatformAttribute’est introuvable (une directive using ou une référence d’assembly est-elle manquante ?)**
- **erreur CS0246 : le nom du type ou de l’espace de noms’RemovedInOSPlatformAttribute’est introuvable (une directive using ou une référence d’assembly est-elle manquante ?)**
- **erreur CS0246 : le nom du type ou de l’espace de noms’ObsoletedInOSPlatformAttribute’est introuvable (une directive using ou une référence d’assembly est-elle manquante ?)**

Exemple d’erreur au moment de l’exécution :

**Exception non gérée. System. TypeLoadException : impossible de charger le type’System. Runtime. Versioning. MinimumOSPlatformAttribute’à partir de l’assembly’System. Runtime, version = 5.0.0.0, culture = neutral, PublicKeyToken = b03f5f7f11d50a3a'.**

Pour résoudre ces erreurs :

- Met à jour toutes les références de `MinimumOSPlatformAttribute` à <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> .
- Met à jour toutes les références de `RemovedInOSPlatformAttribute` à <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> .
- Supprimez toutes les références à `ObsoletedInOSPlatformAttribute` .
- Régénérez votre projet (ou effectuez une génération + Build) pour supprimer les anciens artefacts de Build.

## <a name="affected-apis"></a>API affectées

- `System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `System.Runtime.Versioning.RemovedInOSPlatformAttribute`

<!--

### Category

Core .NET libraries

### Affected APIs

- `T:System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `T:System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `T:System.Runtime.Versioning.RemovedInOSPlatformAttribute`

-->
