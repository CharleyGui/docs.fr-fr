---
ms.openlocfilehash: 84b6bfc32f5a73597b227098e5aee1e3450cf85b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198415"
---
### <a name="switchsystemwindowsformsenablevisualstylevalidation-compatibility-switch-not-supported"></a>Commutateur de compatibilité Switch. System. Windows. Forms. EnableVisualStyleValidation non pris en charge

Le commutateur de compatibilité `Switch.System.Windows.Forms.EnableVisualStyleValidation` n’est pas pris en charge dans Windows Forms sur .NET Core 3,0.

#### <a name="change-description"></a>Modifier la description

Dans .NET Framework, le commutateur de compatibilité `Switch.System.Windows.Forms.EnableVisualStyleValidation` permettait à une application de refuser la validation des styles visuels fournis sous forme numérique.

Dans .NET Core, le commutateur `Switch.System.Windows.Forms.EnableVisualStyleValidation` n’est pas pris en charge.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 9

#### <a name="recommended-action"></a>Action recommandée

Supprimez le commutateur. Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- aucune.

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
