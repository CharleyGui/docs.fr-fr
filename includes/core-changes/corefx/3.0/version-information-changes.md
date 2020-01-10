---
ms.openlocfilehash: 5612ebce67946e22aaeeba861115ce4f8967e1f5
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344455"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a>API qui signalent la version du produit et non de la version du fichier

La plupart des API qui retournent des versions dans .NET Core retournent désormais la version du produit plutôt que la version du fichier.

#### <a name="change-description"></a>Description des modifications

Dans .NET Core 2,2 et versions antérieures, les méthodes telles que <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>et la boîte de dialogue des propriétés de fichier pour les assemblys .NET Core reflètent la version du fichier. À compter de .NET Core 3,0, ils reflètent la version du produit.

La figure suivante illustre la différence dans les informations de version de l’assembly *System. Runtime. dll* pour .net Core 2,2 (à gauche) et .net Core 3,0 (à droite), tel qu’affiché dans la boîte de dialogue des propriétés du fichier de l' **Explorateur Windows** .

![Différence dans les informations sur la version du produit](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Aucun. Cette modification doit rendre la détection de version intuitive plutôt que abstruse.

#### <a name="category"></a>Catégorie

CoreFx

#### <a name="affected-apis"></a>API affectées

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
