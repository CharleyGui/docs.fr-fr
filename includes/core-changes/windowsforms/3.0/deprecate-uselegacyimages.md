---
ms.openlocfilehash: 3eab49acd3eaa5b6d5802af5f4e6f0fe2699ee97
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937123"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a>Commutateur de compatibilité UseLegacyImages non pris en charge

Le commutateur de compatibilité `Switch.System.Windows.Forms.UseLegacyImages`, qui a été introduit dans .NET Framework 4,8, n’est pas pris en charge dans Windows Forms sur .NET Core 3,0.

#### <a name="change-description"></a>Description des modifications

À partir de la .NET Framework 4,8, le commutateur de compatibilité `Switch.System.Windows.Forms.UseLegacyImages` a pris en charge les problèmes de mise à l’échelle des images dans les scénarios ClickOnce dans les environnements haute résolution. Lorsque cette option est définie sur `true`, le commutateur permet à l’utilisateur de restaurer la mise à l’échelle des images héritées sur les affichages à haute résolution, dont l’échelle est définie sur une valeur supérieure à 100%. Pour plus d’informations, consultez les [notes de publication de .NET Framework 4,8](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) sur GitHub.

Dans .NET Core, le commutateur `Switch.System.Windows.Forms.UseLegacyImages` n’est pas pris en charge.

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
