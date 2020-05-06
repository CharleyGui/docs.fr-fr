---
ms.openlocfilehash: 3272dc562981269b868df4ca9d3a5806918aba5f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937037"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>Commutateur de compatibilité DontSupportReentrantFilterMessage non pris en charge

Le `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.6.1, n’est pas pris en charge dans Windows Forms sur .net Core 3,0.

#### <a name="change-description"></a>Description de la modification

À partir du .NET Framework 4.6.1, le `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` commutateur de compatibilité résout les <xref:System.IndexOutOfRangeException> exceptions <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> possibles lorsque le message est appelé <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> avec une implémentation personnalisée. Pour plus d’informations, consultez [Atténuation : implémentations IMessageFilter.PreFilterMessage personnalisées](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).

Dans .NET Core, le `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` commutateur n’est pas pris en charge.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 9

#### <a name="recommended-action"></a>Action recommandée

Supprimez le commutateur. Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
