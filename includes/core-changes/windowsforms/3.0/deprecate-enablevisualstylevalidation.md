---
ms.openlocfilehash: 75baa4f23eae838defafd3ce9b3907a187982a18
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937121"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a>Commutateur de compatibilité EnableVisualStyleValidation non pris en charge

Le commutateur de compatibilité `Switch.System.Windows.Forms.EnableVisualStyleValidation` n’est pas pris en charge dans Windows Forms sur .NET Core 3,0.

#### <a name="change-description"></a>Description des modifications

Dans .NET Framework, le commutateur de compatibilité `Switch.System.Windows.Forms.EnableVisualStyleValidation` permettait à une application de refuser la validation des styles visuels fournis sous forme numérique.

Dans .NET Core, le commutateur `Switch.System.Windows.Forms.EnableVisualStyleValidation` n’est pas pris en charge.

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
