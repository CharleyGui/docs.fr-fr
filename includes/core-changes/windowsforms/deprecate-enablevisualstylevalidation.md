---
ms.openlocfilehash: e6bb1d53cbe1883b8faef75bd22942bd4f65a5e6
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71181790"
---
### <a name="switchsystemwindowsformsenablevisualstylevalidation-compatibility-switch-not-supported"></a>Commutateur de compatibilité Switch. System. Windows. Forms. EnableVisualStyleValidation non pris en charge

Le `Switch.System.Windows.Forms.EnableVisualStyleValidation` commutateur de compatibilité n’est pas pris en charge dans Windows Forms sur .net Core 3,0.

#### <a name="change-description"></a>Modifier la description

Dans .NET Framework, le `Switch.System.Windows.Forms.EnableVisualStyleValidation` commutateur de compatibilité permettait à une application de refuser la validation des styles visuels fournis sous forme numérique. 

Dans .net Core, le `Switch.System.Windows.Forms.EnableVisualStyleValidation` commutateur n’est pas pris en charge.

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
