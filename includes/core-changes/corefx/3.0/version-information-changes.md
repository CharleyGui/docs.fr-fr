---
ms.openlocfilehash: 5612ebce67946e22aaeeba861115ce4f8967e1f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344455"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a>API qui signalent la version signalent maintenant le produit et ne fichier pas la version

Bon nombre des API qui retournent les versions dans .NET Core retournent maintenant la version du produit plutôt que la version de fichier.

#### <a name="change-description"></a>Description de la modification

Dans .NET Core 2.2 et les <xref:System.Environment.Version?displayProperty=nameWithType>versions précédentes, les méthodes telles que , <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>et les propriétés de fichier dialogue pour les assemblages .NET Core reflètent la version de fichier. En commençant par .NET Core 3.0, ils reflètent la version du produit.

Le chiffre suivant illustre la différence d’informations de version pour *l’assemblage System.Runtime.dll* pour .NET Core 2.2 (à gauche) et .NET Core 3.0 (à droite) tel qu’affiché par le dialogue des propriétés de fichiers **Windows Explorer.**

![Différence dans les informations sur la version du produit](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Aucun. Ce changement devrait rendre la détection de version intuitive plutôt que obtus.

#### <a name="category"></a>Category

CoreFx

#### <a name="affected-apis"></a>API affectées

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
