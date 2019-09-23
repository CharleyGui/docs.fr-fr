---
ms.openlocfilehash: cb72e1b92172b8989ce99b47181c13561a7ccd76
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181744"
---
### <a name="switchsystemwindowsformsdontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>Commutateur de compatibilité Switch. System. Windows. Forms. DontSupportReentrantFilterMessage non pris en charge

Le `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.6.1, n’est pas pris en charge dans Windows Forms sur .net Core 3,0.

#### <a name="change-description"></a>Modifier la description

À partir du .NET Framework 4.6.1, le `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` commutateur de compatibilité résout les exceptions <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> possibles <xref:System.IndexOutOfRangeException> lorsque le message est appelé <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> avec une implémentation personnalisée. Pour plus d’informations, consultez [Atténuation : Implémentations de IMessageFilter. PreFilterMessage personnalisées](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)personnalisées.

Dans .net Core, le `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` commutateur n’est pas pris en charge.

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
