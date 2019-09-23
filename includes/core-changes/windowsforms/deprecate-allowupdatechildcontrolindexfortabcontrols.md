---
ms.openlocfilehash: 1d01de4b978309e05a6036953f2a6909628a2480
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71181850"
---
### <a name="switchsystemwindowsformsallowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a><span data-ttu-id="19c8d-101">Commutateur de compatibilité Switch. System. Windows. Forms. AllowUpdateChildControlIndexForTabControls non pris en charge</span><span class="sxs-lookup"><span data-stu-id="19c8d-101">Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>

<span data-ttu-id="19c8d-102">Le `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` commutateur de compatibilité est pris en charge dans Windows Forms sur .NET Framework 4,6 et versions ultérieures, mais n’est pas pris en charge dans Windows Forms à compter de .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="19c8d-102">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch is supported in Windows Forms on .NET Framework 4.6 and later versions but is not supported in Windows Forms starting with .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="19c8d-103">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="19c8d-103">Change description</span></span>

<span data-ttu-id="19c8d-104">Dans .NET Framework 4,6 et versions ultérieures, la sélection d’un onglet réorganise sa collection de contrôles.</span><span class="sxs-lookup"><span data-stu-id="19c8d-104">In .NET Framework 4.6 and later versions, selecting a tab reorders its control collection.</span></span> <span data-ttu-id="19c8d-105">Le `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` commutateur de compatibilité permet à une application d’ignorer cette réorganisation lorsque ce comportement n’est pas souhaitable.</span><span class="sxs-lookup"><span data-stu-id="19c8d-105">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch allows an application to skip this reordering when this behavior is undesirable.</span></span>

<span data-ttu-id="19c8d-106">Dans .net Core, le `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` commutateur n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="19c8d-106">In .NET Core, the `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="19c8d-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="19c8d-107">Version introduced</span></span>

<span data-ttu-id="19c8d-108">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="19c8d-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="19c8d-109">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="19c8d-109">Recommended action</span></span>

<span data-ttu-id="19c8d-110">Supprimez le commutateur.</span><span class="sxs-lookup"><span data-stu-id="19c8d-110">Remove the switch.</span></span> <span data-ttu-id="19c8d-111">Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="19c8d-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="19c8d-112">Category</span><span class="sxs-lookup"><span data-stu-id="19c8d-112">Category</span></span>

<span data-ttu-id="19c8d-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="19c8d-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="19c8d-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="19c8d-114">Affected APIs</span></span>

- <span data-ttu-id="19c8d-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="19c8d-115">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
