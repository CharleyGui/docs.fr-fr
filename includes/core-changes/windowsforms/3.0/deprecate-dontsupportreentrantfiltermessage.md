---
ms.openlocfilehash: cb72e1b92172b8989ce99b47181c13561a7ccd76
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644004"
---
### <a name="switchsystemwindowsformsdontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>Commutateur de compatibilité Switch. System. Windows. Forms. DontSupportReentrantFilterMessage non pris en charge

Le commutateur de compatibilité `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`, qui a été introduit dans .NET Framework 4.6.1, n’est pas pris en charge dans Windows Forms sur .NET Core 3,0.

#### <a name="change-description"></a>Modifier la description

À partir de la .NET Framework 4.6.1, le commutateur de compatibilité `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` résout les exceptions <xref:System.IndexOutOfRangeException> possibles lorsque le <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message est appelé avec une implémentation de <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> personnalisée. Pour plus d’informations, consultez [Atténuation : implémentations IMessageFilter.PreFilterMessage personnalisées](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).

Dans .NET Core, le commutateur `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` n’est pas pris en charge.

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
