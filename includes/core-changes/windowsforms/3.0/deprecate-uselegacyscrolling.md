---
ms.openlocfilehash: 80fc75d0736e2ae17699073a025e79b52b340613
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937056"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>Commutateur de compatibilité DomainUpDown. UseLegacyScrolling non pris en charge

Le `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.7.1, n’est pas pris en charge dans Windows Forms sur .net Core 3,0.

#### <a name="change-description"></a>Description de la modification

À partir du .NET Framework 4.7.1, le `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` commutateur de compatibilité permettait aux développeurs de refuser les <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> actions <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> indépendantes et. Le commutateur <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> a restauré le comportement hérité, dans lequel est ignoré si le texte de contexte est présent et que le développeur doit utiliser <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> l’action sur le contrôle avant <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> l’action. Pour plus d’informations, consultez [ \<AppContextSwitchOverrides>, élément](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

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

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
