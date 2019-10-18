---
ms.openlocfilehash: 86cdb845c436f424bbcc70e0736568031143b204
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522706"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft. VisualBasic. constants. vbNewLine est obsolète

La constante <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> est marquée comme [obsolète](xref:System.ObsoleteAttribute) à partir de .net Core 3,0 Preview 8.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 8

#### <a name="change-description"></a>Modifier la description

À compter de .NET Core 3,0 Preview 8, l’attribut [Obsolete](xref:System.ObsoleteAttribute) a été appliqué à la constante <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>. L’utilisation de la constante produit un avertissement du compilateur. Dans les versions précédentes de .NET Core et .NET Framework, il n’était pas marqué comme obsolète.

Cette modification a été apportée pour prendre en charge les Visual Basic en tant que langage pour le développement multiplateforme. La constante `vbNewLine` est équivalente à `\r\n`, la séquence de caractères de saut de ligne sur Windows. Sur les systèmes basés sur UNIX, le caractère de saut de ligne est `\n`.

#### <a name="recommended-action"></a>Action recommandée

Le message d’attribut [obsolète](xref:System.ObsoleteAttribute) pour `vbNewLine` comprend la recommandation suivante :

> Pour un retour chariot et un saut de ligne, utilisez [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf). Pour la nouvelle ligne de la plateforme actuelle, utilisez <xref:System.Environment.NewLine?displayProperty=nameWithType>.

#### <a name="category"></a>Category

Visual Basic

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
