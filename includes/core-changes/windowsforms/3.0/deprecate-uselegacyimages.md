---
ms.openlocfilehash: 3eab49acd3eaa5b6d5802af5f4e6f0fe2699ee97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937123"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a>Commutateur de compatibilité UseLegacyImages non pris en charge

Le `Switch.System.Windows.Forms.UseLegacyImages` commutateur de compatibilité, qui a été introduit dans .NET Framework 4,8, n’est pas pris en charge dans Windows Forms sur .net Core 3,0.

#### <a name="change-description"></a>Description de la modification

À partir de la .NET Framework 4,8, `Switch.System.Windows.Forms.UseLegacyImages` le commutateur de compatibilité a résolu les problèmes de mise à l’échelle des images dans les scénarios ClickOnce dans les environnements haute résolution. Lorsque la valeur `true`est définie sur, le commutateur permet à l’utilisateur de restaurer la mise à l’échelle des images héritées sur des affichages haute résolution dont l’échelle est supérieure à 100%. Pour plus d’informations, consultez les [notes de publication de .NET Framework 4,8](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) sur GitHub.

Dans .NET Core, le `Switch.System.Windows.Forms.UseLegacyImages` commutateur n’est pas pris en charge.

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
