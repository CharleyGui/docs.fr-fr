---
ms.openlocfilehash: 7e76c32ddeb50eaf1ee93d7cf3cac7469187cc41
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937089"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>Commutateur de compatibilité AllowUpdateChildControlIndexForTabControls non pris en charge

Le commutateur de compatibilité `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` est pris en charge dans Windows Forms sur .NET Framework 4,6 et versions ultérieures, mais n’est pas pris en charge dans Windows Forms à partir de .NET Core 3,0.

#### <a name="change-description"></a>Description des modifications

Dans .NET Framework 4,6 et versions ultérieures, la sélection d’un onglet réorganise sa collection de contrôles. Le commutateur de compatibilité `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` permet à une application d’ignorer cette réorganisation lorsque ce comportement n’est pas souhaitable.

Dans .NET Core, le commutateur `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` n’est pas pris en charge.

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
