---
ms.openlocfilehash: 3ada05a13ec7acde1d8374ed733d0d51cdfb408c
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720911"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="3c68a-101">Commutateur de compatibilité UseLegacyContextMenuStripSourceControlValue non pris en charge</span><span class="sxs-lookup"><span data-stu-id="3c68a-101">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="3c68a-102">Le `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.7.2, n’est pas pris en charge dans Windows Forms sur .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="3c68a-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3c68a-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="3c68a-103">Change description</span></span>

<span data-ttu-id="3c68a-104">À partir de la .NET Framework 4.7.2, le `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` commutateur de compatibilité permet au développeur de refuser le nouveau comportement de la <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> propriété, qui retourne à présent une référence au contrôle de code source.</span><span class="sxs-lookup"><span data-stu-id="3c68a-104">Starting with the .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="3c68a-105">Le comportement précédent de la propriété consistait à retourner `null` .</span><span class="sxs-lookup"><span data-stu-id="3c68a-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="3c68a-106">Pour plus d’informations, consultez [ \< AppContextSwitchOverrides>, élément](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="3c68a-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="3c68a-107">Dans .NET Core, le `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` commutateur n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="3c68a-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3c68a-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="3c68a-108">Version introduced</span></span>

<span data-ttu-id="3c68a-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="3c68a-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3c68a-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="3c68a-110">Recommended action</span></span>

<span data-ttu-id="3c68a-111">Supprimez le commutateur.</span><span class="sxs-lookup"><span data-stu-id="3c68a-111">Remove the switch.</span></span> <span data-ttu-id="3c68a-112">Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="3c68a-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="3c68a-113">Category</span><span class="sxs-lookup"><span data-stu-id="3c68a-113">Category</span></span>

<span data-ttu-id="3c68a-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3c68a-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3c68a-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="3c68a-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
