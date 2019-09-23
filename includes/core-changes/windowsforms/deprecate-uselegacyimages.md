---
ms.openlocfilehash: 07527c247e6ccd53d2a77793946ffc796c3e1cbb
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71181759"
---
### <a name="switchsystemwindowsformsuselegacyimages-compatibility-switch-not-supported"></a>Commutateur de compatibilité Switch. System. Windows. Forms. UseLegacyImages non pris en charge

Le `Switch.System.Windows.Forms.UseLegacyImages` commutateur de compatibilité, qui a été introduit dans .NET Framework 4,8, n’est pas pris en charge dans Windows Forms sur .net Core 3,0.

#### <a name="change-description"></a>Modifier la description

À partir de la .NET Framework 4,8, `Switch.System.Windows.Forms.UseLegacyImages` le commutateur de compatibilité a résolu les problèmes de mise à l’échelle des images dans les scénarios ClickOnce dans les environnements haute résolution. Lorsque la valeur `true`est définie sur, le commutateur permet à l’utilisateur de restaurer la mise à l’échelle des images héritées sur des affichages haute résolution dont l’échelle est supérieure à 100%. Pour plus d’informations, consultez les [notes de publication de .NET Framework 4,8](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) sur GitHub.

Dans .net Core, le `Switch.System.Windows.Forms.UseLegacyImages` commutateur n’est pas pris en charge.

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
