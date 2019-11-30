---
ms.openlocfilehash: 1d01de4b978309e05a6036953f2a6909628a2480
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643997"
---
### <a name="switchsystemwindowsformsallowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>Commutateur de compatibilité Switch. System. Windows. Forms. AllowUpdateChildControlIndexForTabControls non pris en charge

Le commutateur de compatibilité `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` est pris en charge dans Windows Forms sur .NET Framework 4,6 et versions ultérieures, mais n’est pas pris en charge dans Windows Forms à partir de .NET Core 3,0.

#### <a name="change-description"></a>Modifier la description

Dans .NET Framework 4,6 et versions ultérieures, la sélection d’un onglet réorganise sa collection de contrôles. Le commutateur de compatibilité `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` permet à une application d’ignorer cette réorganisation lorsque ce comportement n’est pas souhaitable.

Dans .NET Core, le commutateur `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` n’est pas pris en charge.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 9

#### <a name="recommended-action"></a>Action recommandée

Supprimez le commutateur. Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- Aucun

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
