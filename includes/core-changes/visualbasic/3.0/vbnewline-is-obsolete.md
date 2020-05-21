---
ms.openlocfilehash: 535a73c6b748166a1e4a4661a6bab0671c653278
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721588"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft. VisualBasic. constants. vbNewLine est obsolète

La <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constante est marquée comme [ \[ obsolète \] ](xref:System.ObsoleteAttribute) à partir de .net Core 3,0 Preview 8.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 8

#### <a name="change-description"></a>Description de la modification

À compter de .NET Core 3,0 Preview 8, l’attribut [Obsolete](xref:System.ObsoleteAttribute) a été appliqué à la <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constante. L’utilisation de la constante produit un avertissement du compilateur. Dans .NET Framework et les versions précédentes de .NET Core, il n’était pas marqué comme obsolète.

Cette modification a été apportée pour prendre en charge les Visual Basic en tant que langage pour le développement multiplateforme. La <xref:Microsoft.VisualBasic.Constants.vbNewLine> constante équivaut à `\r\n` , la séquence de caractères de saut de ligne sur Windows. Sur les systèmes basés sur UNIX, le caractère de saut de ligne est `\n` .

#### <a name="recommended-action"></a>Action recommandée

Le message d’attribut [obsolète](xref:System.ObsoleteAttribute) pour <xref:Microsoft.VisualBasic.Constants.vbNewLine> comprend la recommandation suivante :

Pour un retour chariot et un saut de ligne, utilisez <xref:Microsoft.VisualBasic.Constants.vbCrLf> . Pour la nouvelle ligne de la plateforme actuelle, utilisez <xref:System.Environment.NewLine?displayProperty=nameWithType> .

#### <a name="category"></a>Category

Visual Basic

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

#### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
