---
ms.openlocfilehash: a9d0fe3516ade04bc38b804268a9d989f6891d80
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181801"
---
### <a name="switchsystemwindowsformsdonotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>Commutateur de compatibilité Switch. System. Windows. Forms. DoNotSupportSelectAllShortcutInMultilineTextBox non pris en charge

Le `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.6.1, n’est pas pris en charge dans Windows Forms sur .net Core 3,0.

#### <a name="change-description"></a>Modifier la description

À partir de .NET Framework 4.6.1, la sélection de la touche de raccourci <xref:System.Windows.Forms.TextBox> <kbd>CTRL</kbd> + <kbd>a</kbd> dans un contrôle sélectionne tout le texte. Dans .NET Framework 4,6 et versions antérieures, la sélection de la touche<kbd>de raccourci</kbd> <kbd>CTRL</kbd> + a échoué pour sélectionner tout le texte si les <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> propriétés [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) et `true`sont toutes deux définies sur. Le `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` commutateur de compatibilité a été introduit dans .NET Framework 4.6.1 pour conserver le comportement d’origine. Pour plus d'informations, consultez <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.

Dans .net Core, le `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` commutateur n’est pas pris en charge.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 9

#### <a name="recommended-action"></a>Action recommandée

Supprimez le commutateur. Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- Aucun.

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
