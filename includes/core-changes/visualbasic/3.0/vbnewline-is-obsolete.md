---
ms.openlocfilehash: 95a4c807f5c1077cf52f54b196e904ebc98c32f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116365"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft.VisualBasic.Constants.vbNewLine est obsolète

La <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constante est marquée comme [ \[obsolète\] ](xref:System.ObsoleteAttribute) à partir de .NET Core 3.0 Aperçu 8.

#### <a name="version-introduced"></a>Version introduite

3.0 Aperçu 8

#### <a name="change-description"></a>Description de la modification

En commençant par .NET Core 3.0 Aperçu 8, <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> l’attribut [Obsolète](xref:System.ObsoleteAttribute) a été appliqué à la constante. L’utilisation de la constante produit un avertissement de compilateur. Dans .NET Framework et les versions précédentes de .NET Core, il n’a pas été marqué comme obsolète.

Ce changement a été apporté pour soutenir Visual Basic comme langue pour le développement multiplateforme. La <xref:Microsoft.VisualBasic.Constants.vbNewLine> constante est `\r\n`équivalente à , la séquence de caractères newline sur Windows. Sur les systèmes basés sur Unix, le caractère newline est `\n`.

#### <a name="recommended-action"></a>Action recommandée

Le message [d’attribut obsolète](xref:System.ObsoleteAttribute) pour <xref:Microsoft.VisualBasic.Constants.vbNewLine> comprend la recommandation suivante:

Pour un retour de chariot <xref:Microsoft.VisualBasic.Constants.vbCrLf>et un alimentation en ligne, utilisez . Pour la nouvelle ligne de <xref:System.Environment.NewLine?displayProperty=nameWithType>la plate-forme actuelle, utilisez .

#### <a name="category"></a>Category

Visual Basic

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
