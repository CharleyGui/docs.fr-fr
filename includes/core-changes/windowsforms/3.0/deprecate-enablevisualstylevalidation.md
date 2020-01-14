---
ms.openlocfilehash: 75baa4f23eae838defafd3ce9b3907a187982a18
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937121"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a><span data-ttu-id="060b5-101">Commutateur de compatibilité EnableVisualStyleValidation non pris en charge</span><span class="sxs-lookup"><span data-stu-id="060b5-101">EnableVisualStyleValidation compatibility switch not supported</span></span>

<span data-ttu-id="060b5-102">Le commutateur de compatibilité `Switch.System.Windows.Forms.EnableVisualStyleValidation` n’est pas pris en charge dans Windows Forms sur .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="060b5-102">The `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="060b5-103">Description des modifications</span><span class="sxs-lookup"><span data-stu-id="060b5-103">Change description</span></span>

<span data-ttu-id="060b5-104">Dans .NET Framework, le commutateur de compatibilité `Switch.System.Windows.Forms.EnableVisualStyleValidation` permettait à une application de refuser la validation des styles visuels fournis sous forme numérique.</span><span class="sxs-lookup"><span data-stu-id="060b5-104">In .NET Framework, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch allowed an application to opt out of validation of visual styles supplied in a numeric form.</span></span>

<span data-ttu-id="060b5-105">Dans .NET Core, le commutateur `Switch.System.Windows.Forms.EnableVisualStyleValidation` n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="060b5-105">In .NET Core, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="060b5-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="060b5-106">Version introduced</span></span>

<span data-ttu-id="060b5-107">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="060b5-107">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="060b5-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="060b5-108">Recommended action</span></span>

<span data-ttu-id="060b5-109">Supprimez le commutateur.</span><span class="sxs-lookup"><span data-stu-id="060b5-109">Remove the switch.</span></span> <span data-ttu-id="060b5-110">Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="060b5-110">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="060b5-111">Catégorie</span><span class="sxs-lookup"><span data-stu-id="060b5-111">Category</span></span>

<span data-ttu-id="060b5-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="060b5-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="060b5-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="060b5-113">Affected APIs</span></span>

- <span data-ttu-id="060b5-114">Aucun</span><span class="sxs-lookup"><span data-stu-id="060b5-114">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
