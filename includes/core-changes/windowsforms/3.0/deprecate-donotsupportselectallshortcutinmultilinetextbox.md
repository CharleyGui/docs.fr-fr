---
ms.openlocfilehash: 9631e64bb403a3fe7b1b91e8ac592b57ce8068d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937044"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>Commutateur de compatibilité DoNotSupportSelectAllShortcutInMultilineTextBox non pris en charge

Le `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.6.1, n’est pas pris en charge dans windows Forms sur .NET Core 3.0.

#### <a name="change-description"></a>Description de la modification

En commençant par .NET Framework 4.6.1, en sélectionnant <xref:System.Windows.Forms.TextBox> la clé de raccourci <kbd>Ctrl</kbd> + <kbd>A</kbd> dans un contrôle sélectionné tout le texte. Dans .NET Framework 4.6 et les versions précédentes, la sélection de la clé de raccourci <kbd>Ctrl</kbd> + <kbd>A</kbd> n’a pas réussi à sélectionner tout le texte si le [Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) et <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> les propriétés ont été mis à `true`. Le `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` commutateur de compatibilité a été introduit dans .NET Framework 4.6.1 pour conserver le comportement original. Pour plus d'informations, consultez <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.

Dans .NET Core, le commutateur n’est `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` pas pris en charge.

#### <a name="version-introduced"></a>Version introduite

3.0 Aperçu 9

#### <a name="recommended-action"></a>Action recommandée

Retirez l’interrupteur. Le commutateur n’est pas pris en charge, et aucune fonctionnalité alternative n’est disponible.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- None

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
