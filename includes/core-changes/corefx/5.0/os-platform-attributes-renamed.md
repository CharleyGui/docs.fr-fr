---
ms.openlocfilehash: 8c739d8f355ffa6a6e09cbe4c531b188acede5bd
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720299"
---
### <a name="osplatform-attributes-renamed-or-removed"></a>Attributs OSPlatform renommés ou supprimés

Les attributs suivants qui ont été introduits dans .NET 5,0 Preview 8 ont été supprimés ou renommés : `MinimumOSPlatformAttribute` , `RemovedInOSPlatformAttribute` et `ObsoletedInOSPlatformAttribute` .

#### <a name="change-description"></a>Description de la modification

.NET 5,0 Preview 8 a introduit les attributs suivants dans l' <xref:System.Runtime.Versioning> espace de noms :

- `MinimumOSPlatformAttribute`
- `RemovedInOSPlatformAttribute`
- `ObsoletedInOSPlatformAttribute`

Dans .NET 5,0 Preview 8, lorsqu’un projet cible une version spécifique du système d’exploitation de .NET 5 à l’aide d’un [moniker de Framework cible](../../../../docs/standard/frameworks.md) tel que `net5.0-windows` , la génération ajoute un attribut de niveau assembly `System.Runtime.Versioning.MinimumOSPlatformAttribute` .

Dans .NET 5,0 RC1, `ObsoletedInOSPlatformAttribute` a été supprimé et `MinimumOSPlatformAttribute` et et `RemovedInOSPlatformAttribute` ont été renommés comme suit :

| Nom de l’aperçu 8 | RC1 et nom ultérieur |
| - | - |
| `MinimumOSPlatformAttribute` | <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> |
| `RemovedInOSPlatformAttribute` | <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> |

Dans .NET 5,0 RC1 et versions ultérieures, quand un projet cible une version spécifique du système d’exploitation de .NET 5 à l’aide d’un [moniker de Framework cible](../../../../docs/standard/frameworks.md) tel que `net5.0-windows` , la génération ajoute un attribut de niveau assembly <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> .

#### <a name="reason-for-change"></a>Motif de modification

.NET 5,0 Preview 8 a introduit des attributs dans <xref:System.Runtime.Versioning> pour spécifier les plateformes prises en charge pour les API. Les attributs sont consommés par l' [Analyseur de compatibilité](../../../../docs/core/compatibility/code-analysis.md#ca1416-platform-compatibility) de la plateforme pour produire des avertissements de génération lorsque des API spécifiques à la plateforme sont consommées sur des plateformes qui ne sont pas prises en charge par ces API.

Pour .NET 5,0 RC1, une fonctionnalité supplémentaire a été ajoutée à l’analyseur de compatibilité de plateforme pour l’exclusion de la plateforme. Cette fonctionnalité permet aux API d’être marquées comme étant entièrement non prises en charge sur les plateformes de système d’exploitation. Cette fonctionnalité vous invite à modifier les attributs, notamment en utilisant des noms plus appropriés. `ObsoletedInOSPlatformAttribute`A été supprimé, car il n’était plus nécessaire.

#### <a name="version-introduced"></a>Version introduite

5,0 RC1

#### <a name="recommended-action"></a>Action recommandée

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

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- `System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `System.Runtime.Versioning.RemovedInOSPlatformAttribute`

<!--

#### Affected APIs

- `T:System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `T:System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `T:System.Runtime.Versioning.RemovedInOSPlatformAttribute`

-->
