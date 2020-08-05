---
ms.openlocfilehash: 072ed716910e2e1f1f98dbddc56d5bd097b75acc
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555906"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft. VisualBasic. constants. vbNewLine est obsolète

La <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constante est marquée comme [ \[ obsolète \] ](xref:System.ObsoleteAttribute) à partir de .net Core 3,0.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="change-description"></a>Description de la modification

À compter de .NET Core 3,0, l’attribut [Obsolete](xref:System.ObsoleteAttribute) a été appliqué à la <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constante. L’utilisation de la constante produit un avertissement du compilateur. Dans .NET Framework et les versions précédentes de .NET Core, il n’était pas marqué comme obsolète.

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
