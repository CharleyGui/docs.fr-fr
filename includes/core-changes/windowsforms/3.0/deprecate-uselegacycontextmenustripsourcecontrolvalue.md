---
ms.openlocfilehash: 5c1dc42a451d2c6a82e2c2429115db023c610334
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644018"
---
### <a name="switchsystemwindowsformsuselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="14233-101">Commutateur de compatibilité Switch. System. Windows. Forms. UseLegacyContextMenuStripSourceControlValue non pris en charge</span><span class="sxs-lookup"><span data-stu-id="14233-101">Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="14233-102">Le commutateur de compatibilité `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`, qui a été introduit dans .NET Framework 4.7.2, n’est pas pris en charge dans Windows Forms sur .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="14233-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="14233-103">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="14233-103">Change description</span></span>

<span data-ttu-id="14233-104">À partir de la .NET Framework 4.7.2, le commutateur de compatibilité `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` permet au développeur de refuser le nouveau comportement de la propriété <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>, qui retourne à présent une référence au contrôle de code source.</span><span class="sxs-lookup"><span data-stu-id="14233-104">Starting with the .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="14233-105">Le comportement précédent de la propriété consistait à retourner `null`.</span><span class="sxs-lookup"><span data-stu-id="14233-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="14233-106">Pour plus d’informations, consultez [\<élément AppContextSwitchOverrides >](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="14233-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="14233-107">Dans .NET Core, le commutateur `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="14233-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="14233-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="14233-108">Version introduced</span></span>

<span data-ttu-id="14233-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="14233-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="14233-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="14233-110">Recommended action</span></span>

<span data-ttu-id="14233-111">Supprimez le commutateur.</span><span class="sxs-lookup"><span data-stu-id="14233-111">Remove the switch.</span></span> <span data-ttu-id="14233-112">Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="14233-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="14233-113">Category</span><span class="sxs-lookup"><span data-stu-id="14233-113">Category</span></span>

<span data-ttu-id="14233-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="14233-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="14233-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="14233-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
