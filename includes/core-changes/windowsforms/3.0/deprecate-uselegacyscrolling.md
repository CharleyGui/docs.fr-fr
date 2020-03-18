---
ms.openlocfilehash: 80fc75d0736e2ae17699073a025e79b52b340613
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937056"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a><span data-ttu-id="ba66d-101">DomainUpDown.UseLegacyScrolling commutation compatibilité non pris en charge</span><span class="sxs-lookup"><span data-stu-id="ba66d-101">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>

<span data-ttu-id="ba66d-102">Le `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.7.1, n’est pas pris en charge dans windows Forms sur .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ba66d-102">The `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ba66d-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="ba66d-103">Change description</span></span>

<span data-ttu-id="ba66d-104">En commençant par le cadre .NET 4.7.1, le `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` commutateur de <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> compatibilité a permis aux développeurs de se retirer de l’indépendance et des actions.</span><span class="sxs-lookup"><span data-stu-id="ba66d-104">Starting with the .NET Framework 4.7.1, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch allowed developers to opt-out of independent <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> actions.</span></span> <span data-ttu-id="ba66d-105">Le commutateur a restauré le <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> comportement hérité, dans lequel le est ignoré <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> si le texte <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> de contexte est présent, et le développeur est tenu d’utiliser l’action sur le contrôle avant l’action.</span><span class="sxs-lookup"><span data-stu-id="ba66d-105">The switch restored the legacy behavior, in which the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> is ignored if context text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="ba66d-106">Pour plus d’informations, voir [ \<AppContextSwitchOverrides> élément](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="ba66d-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="ba66d-107">Dans .NET Core, le commutateur n’est `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ba66d-107">In .NET Core, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ba66d-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ba66d-108">Version introduced</span></span>

<span data-ttu-id="ba66d-109">3.0 Aperçu 9</span><span class="sxs-lookup"><span data-stu-id="ba66d-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ba66d-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="ba66d-110">Recommended action</span></span>

<span data-ttu-id="ba66d-111">Retirez l’interrupteur.</span><span class="sxs-lookup"><span data-stu-id="ba66d-111">Remove the switch.</span></span> <span data-ttu-id="ba66d-112">Le commutateur n’est pas pris en charge, et aucune fonctionnalité alternative n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="ba66d-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="ba66d-113">Category</span><span class="sxs-lookup"><span data-stu-id="ba66d-113">Category</span></span>

<span data-ttu-id="ba66d-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ba66d-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ba66d-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="ba66d-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
