---
ms.openlocfilehash: bba74f26eafd52b966928835d5003d03af1eabdc
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721054"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>Commutateur de compatibilité DoNotSupportSelectAllShortcutInMultilineTextBox non pris en charge

Le `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.6.1, n’est pas pris en charge dans Windows Forms sur .net Core 3,0.

#### <a name="change-description"></a>Description de la modification

À partir de .NET Framework 4.6.1, la sélection de la touche de raccourci <kbd>CTRL</kbd>  +  <kbd>a</kbd> dans un <xref:System.Windows.Forms.TextBox> contrôle sélectionne tout le texte. Dans .NET Framework 4,6 et versions antérieures, la sélection de la touche de raccourci <kbd>CTRL</kbd>  +  <kbd>A</kbd> a échoué pour sélectionner tout le texte si les propriétés [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) et <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> sont toutes deux définies sur `true` . Le `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` commutateur de compatibilité a été introduit dans .NET Framework 4.6.1 pour conserver le comportement d’origine. Pour plus d'informations, consultez <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.

Dans .NET Core, le `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` commutateur n’est pas pris en charge.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 9

#### <a name="recommended-action"></a>Action recommandée

Supprimez le commutateur. Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- Aucune

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
