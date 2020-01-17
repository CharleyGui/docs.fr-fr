---
ms.openlocfilehash: 95a4c807f5c1077cf52f54b196e904ebc98c32f8
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116365"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft. VisualBasic. constants. vbNewLine est obsolète

La constante <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> est marquée comme [\[obsolète\]](xref:System.ObsoleteAttribute) à compter de .net Core 3,0 Preview 8.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 8

#### <a name="change-description"></a>Description des modifications

À compter de .NET Core 3,0 Preview 8, l’attribut [Obsolete](xref:System.ObsoleteAttribute) a été appliqué à la constante <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>. L’utilisation de la constante produit un avertissement du compilateur. Dans .NET Framework et les versions précédentes de .NET Core, il n’était pas marqué comme obsolète.

Cette modification a été apportée pour prendre en charge les Visual Basic en tant que langage pour le développement multiplateforme. La constante <xref:Microsoft.VisualBasic.Constants.vbNewLine> est équivalente à `\r\n`, la séquence de caractères de saut de ligne sur Windows. Sur les systèmes basés sur UNIX, le caractère de saut de ligne est `\n`.

#### <a name="recommended-action"></a>Action recommandée

Le message d’attribut [obsolète](xref:System.ObsoleteAttribute) pour <xref:Microsoft.VisualBasic.Constants.vbNewLine> comprend la recommandation suivante :

Pour un retour chariot et un saut de ligne, utilisez <xref:Microsoft.VisualBasic.Constants.vbCrLf>. Pour la nouvelle ligne de la plateforme actuelle, utilisez <xref:System.Environment.NewLine?displayProperty=nameWithType>.

#### <a name="category"></a>Catégorie

Visual Basic

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
