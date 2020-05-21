---
ms.openlocfilehash: dd850e83540ffed4dc95b00f807f49b0dd3725e9
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721310"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a><span data-ttu-id="e7fa8-101">Commutateur de compatibilité DomainUpDown. UseLegacyScrolling non pris en charge</span><span class="sxs-lookup"><span data-stu-id="e7fa8-101">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>

<span data-ttu-id="e7fa8-102">Le `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.7.1, n’est pas pris en charge dans Windows Forms sur .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="e7fa8-102">The `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e7fa8-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="e7fa8-103">Change description</span></span>

<span data-ttu-id="e7fa8-104">À partir du .NET Framework 4.7.1, le `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` commutateur de compatibilité permettait aux développeurs de refuser les <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> actions indépendantes et <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e7fa8-104">Starting with the .NET Framework 4.7.1, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch allowed developers to opt-out of independent <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> actions.</span></span> <span data-ttu-id="e7fa8-105">Le commutateur a restauré le comportement hérité, dans lequel <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> est ignoré si le texte de contexte est présent et que le développeur doit utiliser l' <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action sur le contrôle avant l' <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span><span class="sxs-lookup"><span data-stu-id="e7fa8-105">The switch restored the legacy behavior, in which the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> is ignored if context text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="e7fa8-106">Pour plus d’informations, consultez [ \< AppContextSwitchOverrides>, élément](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="e7fa8-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="e7fa8-107">Dans .NET Core, le `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` commutateur n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="e7fa8-107">In .NET Core, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e7fa8-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="e7fa8-108">Version introduced</span></span>

<span data-ttu-id="e7fa8-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="e7fa8-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e7fa8-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="e7fa8-110">Recommended action</span></span>

<span data-ttu-id="e7fa8-111">Supprimez le commutateur.</span><span class="sxs-lookup"><span data-stu-id="e7fa8-111">Remove the switch.</span></span> <span data-ttu-id="e7fa8-112">Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="e7fa8-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="e7fa8-113">Category</span><span class="sxs-lookup"><span data-stu-id="e7fa8-113">Category</span></span>

<span data-ttu-id="e7fa8-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e7fa8-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e7fa8-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="e7fa8-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
