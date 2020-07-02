---
ms.openlocfilehash: 26a001ec2009a1a66dd9038b9bd3a42d7bcefb73
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619985"
---
### <a name="missing-target-framework-moniker-results-in-40-behavior"></a>Un moniker de framework cible manquant a pour effet de restaurer le comportement de la version 4.0

#### <a name="details"></a>Détails

Les applications dans lesquelles un <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> n’est pas appliqué au niveau de l’assembly sont automatiquement exécutées à l’aide de la sémantique (Quirks) de .NET Framework 4.0. Pour garantir une haute qualité, il est recommandé d’attribuer explicitement à tous les fichiers binaires un <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> indiquant la version du .NET Framework avec laquelle ils ont été créés. Si vous utilisez un moniker de framework cible dans un fichier projet, MSBuild applique automatiquement un <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>.

#### <a name="suggestion"></a>Suggestion

Un <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> doit être fourni, soit en ajoutant directement l’attribut à l’assembly, soit en spécifiant une version cible de .Net Framework dans le [fichier projet ou par le biais de l’interface graphique utilisateur des propriétés du projet de Visual Studio](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/).

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Majeure|
|Version|4,5|
|Type|Runtime|
