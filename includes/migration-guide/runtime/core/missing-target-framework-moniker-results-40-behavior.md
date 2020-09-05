---
ms.openlocfilehash: 49740d3b1890d72935e6e329a4f4be836ed70b25
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496541"
---
### <a name="missing-target-framework-moniker-results-in-40-behavior"></a>Un moniker de framework cible manquant a pour effet de restaurer le comportement de la version 4.0

#### <a name="details"></a>Détails

Les applications dans lesquelles un <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> n’est pas appliqué au niveau de l’assembly sont automatiquement exécutées à l’aide de la sémantique (Quirks) de .NET Framework 4.0. Pour garantir une haute qualité, il est recommandé d’attribuer explicitement à tous les fichiers binaires un <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> indiquant la version du .NET Framework avec laquelle ils ont été créés. Si vous utilisez un moniker de framework cible dans un fichier projet, MSBuild applique automatiquement un <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>.

#### <a name="suggestion"></a>Suggestion

Un <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> doit être fourni, soit en ajoutant directement l’attribut à l’assembly, soit en spécifiant une version cible de .Net Framework dans le [fichier projet ou par le biais de l’interface graphique utilisateur des propriétés du projet de Visual Studio](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/).

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Majeure|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
