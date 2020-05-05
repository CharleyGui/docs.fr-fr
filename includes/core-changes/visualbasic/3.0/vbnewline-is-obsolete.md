---
ms.openlocfilehash: 95a4c807f5c1077cf52f54b196e904ebc98c32f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116365"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft. VisualBasic. constants. vbNewLine est obsolète

La <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constante est marquée comme [ \[obsolète\] ](xref:System.ObsoleteAttribute) à partir de .net Core 3,0 Preview 8.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 8

#### <a name="change-description"></a>Description de la modification

À compter de .NET Core 3,0 Preview 8, l’attribut [Obsolete](xref:System.ObsoleteAttribute) a été appliqué à <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> la constante. L’utilisation de la constante produit un avertissement du compilateur. Dans .NET Framework et les versions précédentes de .NET Core, il n’était pas marqué comme obsolète.

Cette modification a été apportée pour prendre en charge les Visual Basic en tant que langage pour le développement multiplateforme. La <xref:Microsoft.VisualBasic.Constants.vbNewLine> constante équivaut à `\r\n`, la séquence de caractères de saut de ligne sur Windows. Sur les systèmes basés sur UNIX, le caractère de `\n`saut de ligne est.

#### <a name="recommended-action"></a>Action recommandée

Le [Obsolete](xref:System.ObsoleteAttribute) message d’attribut obsolète <xref:Microsoft.VisualBasic.Constants.vbNewLine> pour comprend la recommandation suivante :

Pour un retour chariot et un saut de ligne <xref:Microsoft.VisualBasic.Constants.vbCrLf>, utilisez. Pour la nouvelle ligne de la plateforme actuelle <xref:System.Environment.NewLine?displayProperty=nameWithType>, utilisez.

#### <a name="category"></a>Category

Visual Basic

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
