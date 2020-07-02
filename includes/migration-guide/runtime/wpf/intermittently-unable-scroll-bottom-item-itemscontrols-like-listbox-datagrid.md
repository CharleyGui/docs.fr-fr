---
ms.openlocfilehash: b92dc8a1c48e83846c3d9a1d86e66629f31b7722
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622019"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a><span data-ttu-id="35376-101">Impossibilité intermittente de faire défiler jusqu’à l’élément du bas dans les ItemsControls (comme ListBox et DataGrid) lors de l’utilisation de DataTemplates personnalisés</span><span class="sxs-lookup"><span data-stu-id="35376-101">Intermittently unable to scroll to bottom item in ItemsControls (like ListBox and DataGrid) when using custom DataTemplates</span></span>

#### <a name="details"></a><span data-ttu-id="35376-102">Détails</span><span class="sxs-lookup"><span data-stu-id="35376-102">Details</span></span>

<span data-ttu-id="35376-103">Dans certains cas, un bogue du .NET Framework 4.5 empêche le défilement des ItemsControls (comme <xref:System.Windows.Controls.ListBox?displayProperty=fullName>, <xref:System.Windows.Controls.ComboBox?displayProperty=fullName>, <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>, etc.) jusqu’au dernier élément quand vous utilisez des DataTemplates personnalisés.</span><span class="sxs-lookup"><span data-stu-id="35376-103">In some instances, a bug in the .NET Framework 4.5 is causing ItemsControls (like <xref:System.Windows.Controls.ListBox?displayProperty=fullName>, <xref:System.Windows.Controls.ComboBox?displayProperty=fullName>, <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>, etc.) to not scroll to their bottom item when using custom DataTemplates.</span></span> <span data-ttu-id="35376-104">Si le défilement est tenté une deuxième fois (après avoir fait défiler jusqu’en haut), il fonctionnera.</span><span class="sxs-lookup"><span data-stu-id="35376-104">If the scrolling is attempted a second time (after scrolling back up), it will work then.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="35376-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="35376-105">Suggestion</span></span>

<span data-ttu-id="35376-106">Étant donné que ce problème a été résolu dans le .NET Framework 4.5.2, vous pouvez également mettre à niveau votre version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="35376-106">This issue has been fixed in the .NET Framework 4.5.2 and may be addressed by upgrading to that version (or a later version) of the .NET Framework.</span></span> <span data-ttu-id="35376-107">Vous pouvez également faire glisser les barres de défilement jusqu’au dernier élément de la collection, mais aurez peut-être à recommencer l’opération une deuxième fois pour y arriver.</span><span class="sxs-lookup"><span data-stu-id="35376-107">Alternatively, users can still drag scroll bars to the final items in these collections, but may need to try twice to do so successfully.</span></span>

| <span data-ttu-id="35376-108">Nom</span><span class="sxs-lookup"><span data-stu-id="35376-108">Name</span></span>    | <span data-ttu-id="35376-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="35376-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="35376-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="35376-110">Scope</span></span>   |<span data-ttu-id="35376-111">Secondaire</span><span class="sxs-lookup"><span data-stu-id="35376-111">Minor</span></span>|
|<span data-ttu-id="35376-112">Version</span><span class="sxs-lookup"><span data-stu-id="35376-112">Version</span></span>|<span data-ttu-id="35376-113">4,5</span><span class="sxs-lookup"><span data-stu-id="35376-113">4.5</span></span>|
|<span data-ttu-id="35376-114">Type</span><span class="sxs-lookup"><span data-stu-id="35376-114">Type</span></span>|<span data-ttu-id="35376-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="35376-115">Runtime</span></span>|
