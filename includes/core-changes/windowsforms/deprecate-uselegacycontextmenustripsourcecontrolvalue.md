---
ms.openlocfilehash: 5c1dc42a451d2c6a82e2c2429115db023c610334
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181780"
---
### <a name="switchsystemwindowsformsuselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a>Commutateur de compatibilité Switch. System. Windows. Forms. UseLegacyContextMenuStripSourceControlValue non pris en charge

Le `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.7.2, n’est pas pris en charge dans Windows Forms sur .net Core 3,0.

#### <a name="change-description"></a>Modifier la description

À partir de la .NET Framework 4.7.2, `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` le commutateur de compatibilité permet au développeur de refuser le nouveau comportement de la <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> propriété, qui retourne à présent une référence au contrôle de code source. Le comportement précédent de la propriété consistait à `null`retourner. Pour plus d’informations, consultez [ \<AppContextSwitchOverrides >, élément](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

Dans .net Core, le `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` commutateur n’est pas pris en charge.

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
