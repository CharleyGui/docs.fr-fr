---
ms.openlocfilehash: 9631e64bb403a3fe7b1b91e8ac592b57ce8068d9
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937044"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>Commutateur de compatibilité DoNotSupportSelectAllShortcutInMultilineTextBox non pris en charge

Le commutateur de compatibilité `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`, qui a été introduit dans .NET Framework 4.6.1, n’est pas pris en charge dans Windows Forms sur .NET Core 3,0.

#### <a name="change-description"></a>Description des modifications

À partir de .NET Framework 4.6.1, si vous sélectionnez la touche <kbd>Ctrl</kbd> + <kbd>une</kbd> touche de raccourci dans un contrôle <xref:System.Windows.Forms.TextBox> sélectionné tout le texte. Dans .NET Framework 4,6 et versions antérieures, le fait de sélectionner la touche <kbd>Ctrl</kbd> + <kbd>une</kbd> touche de raccourci n’a pas pu sélectionner tout le texte si les propriétés [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) et <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> ont toutes les deux la valeur `true`. Le commutateur de compatibilité `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` a été introduit dans .NET Framework 4.6.1 pour conserver le comportement d’origine. Pour plus d'informations, consultez <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.

Dans .NET Core, le commutateur `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` n’est pas pris en charge.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 9

#### <a name="recommended-action"></a>Action recommandée

Supprimez le commutateur. Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.

#### <a name="category"></a>Catégorie

Windows Forms

#### <a name="affected-apis"></a>API affectées

- Aucun

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
