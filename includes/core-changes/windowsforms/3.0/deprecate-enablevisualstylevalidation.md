---
ms.openlocfilehash: 75baa4f23eae838defafd3ce9b3907a187982a18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937121"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a>Commutateur de compatibilité EnableVisualStyleValidation non pris en charge

Le `Switch.System.Windows.Forms.EnableVisualStyleValidation` commutateur de compatibilité n’est pas pris en charge dans Windows Forms sur .net Core 3,0.

#### <a name="change-description"></a>Description de la modification

Dans .NET Framework, le `Switch.System.Windows.Forms.EnableVisualStyleValidation` commutateur de compatibilité permettait à une application de refuser la validation des styles visuels fournis sous forme numérique.

Dans .NET Core, le `Switch.System.Windows.Forms.EnableVisualStyleValidation` commutateur n’est pas pris en charge.

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
