---
ms.openlocfilehash: 3272dc562981269b868df4ca9d3a5806918aba5f
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937037"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>Commutateur de compatibilité DontSupportReentrantFilterMessage non pris en charge

Le commutateur de compatibilité `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`, qui a été introduit dans .NET Framework 4.6.1, n’est pas pris en charge dans Windows Forms sur .NET Core 3,0.

#### <a name="change-description"></a>Description des modifications

À partir de la .NET Framework 4.6.1, le commutateur de compatibilité `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` résout les exceptions <xref:System.IndexOutOfRangeException> possibles lorsque le <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message est appelé avec une implémentation de <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> personnalisée. Pour plus d’informations, consultez [Atténuation : implémentations IMessageFilter.PreFilterMessage personnalisées](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).

Dans .NET Core, le commutateur `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` n’est pas pris en charge.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 9

#### <a name="recommended-action"></a>Action recommandée

Supprimez le commutateur. Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.

#### <a name="category"></a>Catégorie

Windows Forms

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
