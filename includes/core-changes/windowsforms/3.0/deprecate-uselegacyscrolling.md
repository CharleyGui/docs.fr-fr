---
ms.openlocfilehash: 459e7e1f0b5543f069682dadf60668e94b472377
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643969"
---
### <a name="switchsystemwindowsformsdomainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>Commutateur de compatibilité Switch. System. Windows. Forms. DomainUpDown. UseLegacyScrolling non pris en charge

Le commutateur de compatibilité `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`, qui a été introduit dans .NET Framework 4.7.1, n’est pas pris en charge dans Windows Forms sur .NET Core 3,0.

#### <a name="change-description"></a>Modifier la description

À partir du .NET Framework 4.7.1, le commutateur de compatibilité `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` permettait aux développeurs de refuser les actions <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> et <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> indépendantes. Le commutateur a restauré le comportement hérité, dans lequel la <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> est ignorée si le texte de contexte est présent et que le développeur doit utiliser <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action sur le contrôle avant l’action <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>. Pour plus d’informations, consultez [\<élément AppContextSwitchOverrides >](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

Dans .NET Core, le commutateur `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` n’est pas pris en charge.

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
