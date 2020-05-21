---
ms.openlocfilehash: 55c13aa70a03bcc548ce1d096cca8f40de6cda84
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721242"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a><span data-ttu-id="ccd7c-101">Commutateur de compatibilité DontSupportReentrantFilterMessage non pris en charge</span><span class="sxs-lookup"><span data-stu-id="ccd7c-101">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>

<span data-ttu-id="ccd7c-102">Le `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.6.1, n’est pas pris en charge dans Windows Forms sur .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="ccd7c-102">The `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ccd7c-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="ccd7c-103">Change description</span></span>

<span data-ttu-id="ccd7c-104">À partir du .NET Framework 4.6.1, le `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` commutateur de compatibilité résout les <xref:System.IndexOutOfRangeException> exceptions possibles lorsque le <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message est appelé avec une <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implémentation personnalisée.</span><span class="sxs-lookup"><span data-stu-id="ccd7c-104">Starting with the .NET Framework 4.6.1, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch addresses possible <xref:System.IndexOutOfRangeException> exceptions when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message is called with a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="ccd7c-105">Pour plus d’informations, consultez [Atténuation : implémentations IMessageFilter.PreFilterMessage personnalisées](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span><span class="sxs-lookup"><span data-stu-id="ccd7c-105">For more information, see [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span></span>

<span data-ttu-id="ccd7c-106">Dans .NET Core, le `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` commutateur n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ccd7c-106">In .NET Core, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ccd7c-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ccd7c-107">Version introduced</span></span>

<span data-ttu-id="ccd7c-108">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="ccd7c-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ccd7c-109">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="ccd7c-109">Recommended action</span></span>

<span data-ttu-id="ccd7c-110">Supprimez le commutateur.</span><span class="sxs-lookup"><span data-stu-id="ccd7c-110">Remove the switch.</span></span> <span data-ttu-id="ccd7c-111">Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="ccd7c-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="ccd7c-112">Category</span><span class="sxs-lookup"><span data-stu-id="ccd7c-112">Category</span></span>

<span data-ttu-id="ccd7c-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ccd7c-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ccd7c-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="ccd7c-114">Affected APIs</span></span>

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
