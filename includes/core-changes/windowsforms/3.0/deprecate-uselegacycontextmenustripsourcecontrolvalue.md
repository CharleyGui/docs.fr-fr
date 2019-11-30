---
ms.openlocfilehash: 5c1dc42a451d2c6a82e2c2429115db023c610334
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644018"
---
### <a name="switchsystemwindowsformsuselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a>Commutateur de compatibilité Switch. System. Windows. Forms. UseLegacyContextMenuStripSourceControlValue non pris en charge

Le commutateur de compatibilité `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`, qui a été introduit dans .NET Framework 4.7.2, n’est pas pris en charge dans Windows Forms sur .NET Core 3,0.

#### <a name="change-description"></a>Modifier la description

À partir de la .NET Framework 4.7.2, le commutateur de compatibilité `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` permet au développeur de refuser le nouveau comportement de la propriété <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>, qui retourne à présent une référence au contrôle de code source. Le comportement précédent de la propriété consistait à retourner `null`. Pour plus d’informations, consultez [\<élément AppContextSwitchOverrides >](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

Dans .NET Core, le commutateur `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` n’est pas pris en charge.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 9

#### <a name="recommended-action"></a>Action recommandée

Supprimez le commutateur. Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
