---
ms.openlocfilehash: 5aca2b8b3ca6572194692888eae3c5614245b481
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937043"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a><span data-ttu-id="6e8f8-101">Commutateur de compatibilité UseLegacyContextMenuStripSourceControlValue non pris en charge</span><span class="sxs-lookup"><span data-stu-id="6e8f8-101">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>

<span data-ttu-id="6e8f8-102">Le commutateur de compatibilité `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`, qui a été introduit dans .NET Framework 4.7.2, n’est pas pris en charge dans Windows Forms sur .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="6e8f8-102">The `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch, which was introduced in .NET Framework 4.7.2, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6e8f8-103">Description des modifications</span><span class="sxs-lookup"><span data-stu-id="6e8f8-103">Change description</span></span>

<span data-ttu-id="6e8f8-104">À partir de la .NET Framework 4.7.2, le commutateur de compatibilité `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` permet au développeur de refuser le nouveau comportement de la propriété <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>, qui retourne à présent une référence au contrôle de code source.</span><span class="sxs-lookup"><span data-stu-id="6e8f8-104">Starting with the .NET Framework 4.7.2, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` compatibility switch allows the developer to opt out of the new behavior of the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property, which now returns a reference to the source control.</span></span> <span data-ttu-id="6e8f8-105">Le comportement précédent de la propriété consistait à retourner `null`.</span><span class="sxs-lookup"><span data-stu-id="6e8f8-105">The previous behavior of the property was to return `null`.</span></span> <span data-ttu-id="6e8f8-106">Pour plus d’informations, consultez [\<élément AppContextSwitchOverrides >](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="6e8f8-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="6e8f8-107">Dans .NET Core, le commutateur `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="6e8f8-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6e8f8-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="6e8f8-108">Version introduced</span></span>

<span data-ttu-id="6e8f8-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="6e8f8-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6e8f8-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="6e8f8-110">Recommended action</span></span>

<span data-ttu-id="6e8f8-111">Supprimez le commutateur.</span><span class="sxs-lookup"><span data-stu-id="6e8f8-111">Remove the switch.</span></span> <span data-ttu-id="6e8f8-112">Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="6e8f8-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="6e8f8-113">Catégorie</span><span class="sxs-lookup"><span data-stu-id="6e8f8-113">Category</span></span>

<span data-ttu-id="6e8f8-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6e8f8-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6e8f8-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="6e8f8-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
