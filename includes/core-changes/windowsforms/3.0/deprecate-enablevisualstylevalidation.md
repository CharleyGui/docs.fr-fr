---
ms.openlocfilehash: 75baa4f23eae838defafd3ce9b3907a187982a18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937121"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a><span data-ttu-id="40d25-101">Commutateur de compatibilité EnableVisualStyleValidation non pris en charge</span><span class="sxs-lookup"><span data-stu-id="40d25-101">EnableVisualStyleValidation compatibility switch not supported</span></span>

<span data-ttu-id="40d25-102">Le `Switch.System.Windows.Forms.EnableVisualStyleValidation` commutateur de compatibilité n’est pas pris en charge dans Windows Forms sur .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="40d25-102">The `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="40d25-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="40d25-103">Change description</span></span>

<span data-ttu-id="40d25-104">Dans .NET Framework, le `Switch.System.Windows.Forms.EnableVisualStyleValidation` commutateur de compatibilité a permis à une application de se retirer de la validation des styles visuels fournis sous forme numérique.</span><span class="sxs-lookup"><span data-stu-id="40d25-104">In .NET Framework, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch allowed an application to opt out of validation of visual styles supplied in a numeric form.</span></span>

<span data-ttu-id="40d25-105">Dans .NET Core, le commutateur n’est `Switch.System.Windows.Forms.EnableVisualStyleValidation` pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="40d25-105">In .NET Core, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="40d25-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="40d25-106">Version introduced</span></span>

<span data-ttu-id="40d25-107">3.0 Aperçu 9</span><span class="sxs-lookup"><span data-stu-id="40d25-107">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="40d25-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="40d25-108">Recommended action</span></span>

<span data-ttu-id="40d25-109">Retirez l’interrupteur.</span><span class="sxs-lookup"><span data-stu-id="40d25-109">Remove the switch.</span></span> <span data-ttu-id="40d25-110">Le commutateur n’est pas pris en charge, et aucune fonctionnalité alternative n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="40d25-110">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="40d25-111">Category</span><span class="sxs-lookup"><span data-stu-id="40d25-111">Category</span></span>

<span data-ttu-id="40d25-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40d25-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="40d25-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="40d25-113">Affected APIs</span></span>

- <span data-ttu-id="40d25-114">None</span><span class="sxs-lookup"><span data-stu-id="40d25-114">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
