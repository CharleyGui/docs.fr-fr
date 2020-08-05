---
ms.openlocfilehash: 3db4b0b42a154c5bc9296889ae9dc4b7ecf1e58e
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556166"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a><span data-ttu-id="94739-101">Commutateur de compatibilité AllowUpdateChildControlIndexForTabControls non pris en charge</span><span class="sxs-lookup"><span data-stu-id="94739-101">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>

<span data-ttu-id="94739-102">Le `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` commutateur de compatibilité est pris en charge dans Windows Forms sur .NET Framework 4,6 et versions ultérieures, mais n’est pas pris en charge sur .net Core ou .net 5,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="94739-102">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch is supported in Windows Forms on .NET Framework 4.6 and later versions but is not supported on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="94739-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="94739-103">Change description</span></span>

<span data-ttu-id="94739-104">Dans .NET Framework 4,6 et versions ultérieures, la sélection d’un onglet réorganise sa collection de contrôles.</span><span class="sxs-lookup"><span data-stu-id="94739-104">In .NET Framework 4.6 and later versions, selecting a tab reorders its control collection.</span></span> <span data-ttu-id="94739-105">Le `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` commutateur de compatibilité permet à une application d’ignorer cette réorganisation lorsque ce comportement n’est pas souhaitable.</span><span class="sxs-lookup"><span data-stu-id="94739-105">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch allows an application to skip this reordering when this behavior is undesirable.</span></span>

<span data-ttu-id="94739-106">Dans .NET Core et .NET 5,0 et versions ultérieures, le `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` commutateur n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="94739-106">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="94739-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="94739-107">Version introduced</span></span>

<span data-ttu-id="94739-108">3.0</span><span class="sxs-lookup"><span data-stu-id="94739-108">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="94739-109">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="94739-109">Recommended action</span></span>

<span data-ttu-id="94739-110">Supprimez le commutateur.</span><span class="sxs-lookup"><span data-stu-id="94739-110">Remove the switch.</span></span> <span data-ttu-id="94739-111">Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="94739-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="94739-112">Category</span><span class="sxs-lookup"><span data-stu-id="94739-112">Category</span></span>

<span data-ttu-id="94739-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94739-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="94739-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="94739-114">Affected APIs</span></span>

- <span data-ttu-id="94739-115">Aucun</span><span class="sxs-lookup"><span data-stu-id="94739-115">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
