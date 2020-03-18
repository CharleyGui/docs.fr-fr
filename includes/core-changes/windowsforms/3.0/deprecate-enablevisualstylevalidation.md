---
ms.openlocfilehash: 75baa4f23eae838defafd3ce9b3907a187982a18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937121"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a>Commutateur de compatibilité EnableVisualStyleValidation non pris en charge

Le `Switch.System.Windows.Forms.EnableVisualStyleValidation` commutateur de compatibilité n’est pas pris en charge dans Windows Forms sur .NET Core 3.0.

#### <a name="change-description"></a>Description de la modification

Dans .NET Framework, le `Switch.System.Windows.Forms.EnableVisualStyleValidation` commutateur de compatibilité a permis à une application de se retirer de la validation des styles visuels fournis sous forme numérique.

Dans .NET Core, le commutateur n’est `Switch.System.Windows.Forms.EnableVisualStyleValidation` pas pris en charge.

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
