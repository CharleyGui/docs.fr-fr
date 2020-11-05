---
ms.openlocfilehash: 56127309c5f5993ffc2e2faedd1f481e8131e094
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400632"
---
### <a name="textformatflagsmodifystring-is-obsolete"></a>TextFormatFlags. ModifyString est obsolète

Le <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> champ est obsolète, comme un avertissement, et peut être supprimé dans une prochaine version .net.

#### <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, le <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> champ d’énumération n’est pas marqué comme obsolète. Dans .NET 5,0 et versions ultérieures, il est marqué comme étant obsolète en tant qu’avertissement. Ce champ peut être supprimé dans une future version .NET.

#### <a name="reason-for-change"></a>Motif de modification

Le passage d’une chaîne à <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> avec <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> modifie la chaîne dans certaines situations. Ce comportement interrompt la promesse de la chaîne d’immuabilité et peut entraîner une altération irrécupérable de l’état du Runtime .NET.

#### <a name="version-introduced"></a>Version introduite

.NET 5,0 RC1

#### <a name="recommended-action"></a>Action recommandée

Mettez à jour le code qui s’appuie sur <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> .

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=fullName>

<!--

#### Affected APIs

- `F:System.Windows.Forms.TextFormatFlags.ModifyString`

-->
