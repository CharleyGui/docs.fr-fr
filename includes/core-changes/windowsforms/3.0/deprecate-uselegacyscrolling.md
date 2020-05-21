---
ms.openlocfilehash: dd850e83540ffed4dc95b00f807f49b0dd3725e9
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721310"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>Commutateur de compatibilité DomainUpDown. UseLegacyScrolling non pris en charge

Le `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.7.1, n’est pas pris en charge dans Windows Forms sur .net Core 3,0.

#### <a name="change-description"></a>Description de la modification

À partir du .NET Framework 4.7.1, le `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` commutateur de compatibilité permettait aux développeurs de refuser les <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> actions indépendantes et <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> . Le commutateur a restauré le comportement hérité, dans lequel <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> est ignoré si le texte de contexte est présent et que le développeur doit utiliser l' <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action sur le contrôle avant l' <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action. Pour plus d’informations, consultez [ \< AppContextSwitchOverrides>, élément](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

Dans .NET Core, le `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` commutateur n’est pas pris en charge.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 9

#### <a name="recommended-action"></a>Action recommandée

Supprimez le commutateur. Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
