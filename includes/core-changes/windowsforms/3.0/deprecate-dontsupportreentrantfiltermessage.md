---
ms.openlocfilehash: 3272dc562981269b868df4ca9d3a5806918aba5f
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937037"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a><span data-ttu-id="d7da8-101">Commutateur de compatibilité DontSupportReentrantFilterMessage non pris en charge</span><span class="sxs-lookup"><span data-stu-id="d7da8-101">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>

<span data-ttu-id="d7da8-102">Le commutateur de compatibilité `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`, qui a été introduit dans .NET Framework 4.6.1, n’est pas pris en charge dans Windows Forms sur .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="d7da8-102">The `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d7da8-103">Description des modifications</span><span class="sxs-lookup"><span data-stu-id="d7da8-103">Change description</span></span>

<span data-ttu-id="d7da8-104">À partir de la .NET Framework 4.6.1, le commutateur de compatibilité `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` résout les exceptions <xref:System.IndexOutOfRangeException> possibles lorsque le <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message est appelé avec une implémentation de <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> personnalisée.</span><span class="sxs-lookup"><span data-stu-id="d7da8-104">Starting with the .NET Framework 4.6.1, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch addresses possible <xref:System.IndexOutOfRangeException> exceptions when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message is called with a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="d7da8-105">Pour plus d’informations, consultez [Atténuation : implémentations IMessageFilter.PreFilterMessage personnalisées](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span><span class="sxs-lookup"><span data-stu-id="d7da8-105">For more information, see [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span></span>

<span data-ttu-id="d7da8-106">Dans .NET Core, le commutateur `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d7da8-106">In .NET Core, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d7da8-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d7da8-107">Version introduced</span></span>

<span data-ttu-id="d7da8-108">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="d7da8-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d7da8-109">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d7da8-109">Recommended action</span></span>

<span data-ttu-id="d7da8-110">Supprimez le commutateur.</span><span class="sxs-lookup"><span data-stu-id="d7da8-110">Remove the switch.</span></span> <span data-ttu-id="d7da8-111">Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="d7da8-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="d7da8-112">Catégorie</span><span class="sxs-lookup"><span data-stu-id="d7da8-112">Category</span></span>

<span data-ttu-id="d7da8-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d7da8-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d7da8-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="d7da8-114">Affected APIs</span></span>

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
