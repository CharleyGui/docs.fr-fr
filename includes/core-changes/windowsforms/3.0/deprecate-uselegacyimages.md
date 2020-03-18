---
ms.openlocfilehash: 3eab49acd3eaa5b6d5802af5f4e6f0fe2699ee97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937123"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a>Commutateur de compatibilité UseLegacyImages non pris en charge

Le `Switch.System.Windows.Forms.UseLegacyImages` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.8, n’est pas pris en charge dans windows Forms sur .NET Core 3.0.

#### <a name="change-description"></a>Description de la modification

En commençant par le cadre .NET `Switch.System.Windows.Forms.UseLegacyImages` 4.8, le commutateur de compatibilité a abordé les problèmes possibles de mise à l’échelle des images dans les scénarios ClickOnce dans des environnements DPI élevés. Lorsqu’il `true`est configuré, le commutateur permet à l’utilisateur de restaurer l’échelle d’image héritée sur les écrans DPI élevés dont l’échelle est définie à plus de 100%. Pour plus d’informations, voir [.NET Framework 4.8 Notes de sortie](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) sur GitHub.

Dans .NET Core, le commutateur n’est `Switch.System.Windows.Forms.UseLegacyImages` pas pris en charge.

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
