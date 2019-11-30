---
ms.openlocfilehash: 459e7e1f0b5543f069682dadf60668e94b472377
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643969"
---
### <a name="switchsystemwindowsformsdomainupdownuselegacyscrolling-compatibility-switch-not-supported"></a><span data-ttu-id="d7379-101">Commutateur de compatibilité Switch. System. Windows. Forms. DomainUpDown. UseLegacyScrolling non pris en charge</span><span class="sxs-lookup"><span data-stu-id="d7379-101">Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>

<span data-ttu-id="d7379-102">Le commutateur de compatibilité `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`, qui a été introduit dans .NET Framework 4.7.1, n’est pas pris en charge dans Windows Forms sur .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="d7379-102">The `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d7379-103">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="d7379-103">Change description</span></span>

<span data-ttu-id="d7379-104">À partir du .NET Framework 4.7.1, le commutateur de compatibilité `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` permettait aux développeurs de refuser les actions <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> et <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> indépendantes.</span><span class="sxs-lookup"><span data-stu-id="d7379-104">Starting with the .NET Framework 4.7.1, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch allowed developers to opt-out of independent <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> actions.</span></span> <span data-ttu-id="d7379-105">Le commutateur a restauré le comportement hérité, dans lequel la <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> est ignorée si le texte de contexte est présent et que le développeur doit utiliser <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action sur le contrôle avant l’action <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d7379-105">The switch restored the legacy behavior, in which the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> is ignored if context text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="d7379-106">Pour plus d’informations, consultez [\<élément AppContextSwitchOverrides >](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="d7379-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="d7379-107">Dans .NET Core, le commutateur `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d7379-107">In .NET Core, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d7379-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d7379-108">Version introduced</span></span>

<span data-ttu-id="d7379-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="d7379-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d7379-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d7379-110">Recommended action</span></span>

<span data-ttu-id="d7379-111">Supprimez le commutateur.</span><span class="sxs-lookup"><span data-stu-id="d7379-111">Remove the switch.</span></span> <span data-ttu-id="d7379-112">Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="d7379-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="d7379-113">Category</span><span class="sxs-lookup"><span data-stu-id="d7379-113">Category</span></span>

<span data-ttu-id="d7379-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d7379-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d7379-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="d7379-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
