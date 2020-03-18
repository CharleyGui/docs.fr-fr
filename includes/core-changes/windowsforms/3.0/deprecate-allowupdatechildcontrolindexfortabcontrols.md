---
ms.openlocfilehash: 7e76c32ddeb50eaf1ee93d7cf3cac7469187cc41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937089"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>Commutateur de compatibilité AllowUpdateChildControlIndexForTabControls non pris en charge

Le `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` commutateur de compatibilité est pris en charge dans les formulaires Windows sur .NET Framework 4.6 et les versions ultérieures, mais n’est pas pris en charge dans les formulaires Windows à partir de .NET Core 3.0.

#### <a name="change-description"></a>Description de la modification

Dans .NET Framework 4.6 et les versions ultérieures, la sélection d’un onglet réorganise sa collection de contrôle. Le `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` commutateur de compatibilité permet à une application de sauter cette réorganisation lorsque ce comportement n’est pas souhaitable.

Dans .NET Core, le commutateur n’est `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` pas pris en charge.

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
