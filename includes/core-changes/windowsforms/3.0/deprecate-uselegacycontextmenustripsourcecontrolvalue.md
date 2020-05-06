---
ms.openlocfilehash: 5aca2b8b3ca6572194692888eae3c5614245b481
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937043"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="f2f01-101">Commutateur de compatibilité UseLegacyContextMenuStripSourceControlValue non pris en charge</span><span class="sxs-lookup"><span data-stu-id="f2f01-101">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="f2f01-102">Le `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.7.2, n’est pas pris en charge dans Windows Forms sur .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="f2f01-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f2f01-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="f2f01-103">Change description</span></span>

<span data-ttu-id="f2f01-104">À partir de la .NET Framework 4.7.2, `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` le commutateur de compatibilité permet au développeur de refuser le nouveau comportement de la <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> propriété, qui retourne à présent une référence au contrôle de code source.</span><span class="sxs-lookup"><span data-stu-id="f2f01-104">Starting with the .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="f2f01-105">Le comportement précédent de la propriété consistait à `null`retourner.</span><span class="sxs-lookup"><span data-stu-id="f2f01-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="f2f01-106">Pour plus d’informations, consultez [ \<AppContextSwitchOverrides>, élément](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="f2f01-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="f2f01-107">Dans .NET Core, le `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` commutateur n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="f2f01-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f2f01-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f2f01-108">Version introduced</span></span>

<span data-ttu-id="f2f01-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="f2f01-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f2f01-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="f2f01-110">Recommended action</span></span>

<span data-ttu-id="f2f01-111">Supprimez le commutateur.</span><span class="sxs-lookup"><span data-stu-id="f2f01-111">Remove the switch.</span></span> <span data-ttu-id="f2f01-112">Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="f2f01-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="f2f01-113">Category</span><span class="sxs-lookup"><span data-stu-id="f2f01-113">Category</span></span>

<span data-ttu-id="f2f01-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f2f01-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f2f01-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="f2f01-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
