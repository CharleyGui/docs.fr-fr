---
ms.openlocfilehash: 07527c247e6ccd53d2a77793946ffc796c3e1cbb
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644032"
---
### <a name="switchsystemwindowsformsuselegacyimages-compatibility-switch-not-supported"></a>Commutateur de compatibilité Switch. System. Windows. Forms. UseLegacyImages non pris en charge

Le commutateur de compatibilité `Switch.System.Windows.Forms.UseLegacyImages`, qui a été introduit dans .NET Framework 4,8, n’est pas pris en charge dans Windows Forms sur .NET Core 3,0.

#### <a name="change-description"></a>Modifier la description

À partir de la .NET Framework 4,8, le commutateur de compatibilité `Switch.System.Windows.Forms.UseLegacyImages` a pris en charge les problèmes de mise à l’échelle des images dans les scénarios ClickOnce dans les environnements haute résolution. Lorsque cette option est définie sur `true`, le commutateur permet à l’utilisateur de restaurer la mise à l’échelle des images héritées sur les affichages à haute résolution, dont l’échelle est définie sur une valeur supérieure à 100%. Pour plus d’informations, consultez les [notes de publication de .NET Framework 4,8](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) sur GitHub.

Dans .NET Core, le commutateur `Switch.System.Windows.Forms.UseLegacyImages` n’est pas pris en charge.

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
