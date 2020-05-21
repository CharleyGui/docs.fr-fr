---
ms.openlocfilehash: 97e38685777c7c418c0ccd91f4c433501ecf3aaa
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721301"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a><span data-ttu-id="bf34a-101">Commutateur de compatibilité EnableVisualStyleValidation non pris en charge</span><span class="sxs-lookup"><span data-stu-id="bf34a-101">EnableVisualStyleValidation compatibility switch not supported</span></span>

<span data-ttu-id="bf34a-102">Le `Switch.System.Windows.Forms.EnableVisualStyleValidation` commutateur de compatibilité n’est pas pris en charge dans Windows Forms sur .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="bf34a-102">The `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="bf34a-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="bf34a-103">Change description</span></span>

<span data-ttu-id="bf34a-104">Dans .NET Framework, le `Switch.System.Windows.Forms.EnableVisualStyleValidation` commutateur de compatibilité permettait à une application de refuser la validation des styles visuels fournis sous forme numérique.</span><span class="sxs-lookup"><span data-stu-id="bf34a-104">In .NET Framework, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch allowed an application to opt out of validation of visual styles supplied in a numeric form.</span></span>

<span data-ttu-id="bf34a-105">Dans .NET Core, le `Switch.System.Windows.Forms.EnableVisualStyleValidation` commutateur n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="bf34a-105">In .NET Core, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bf34a-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="bf34a-106">Version introduced</span></span>

<span data-ttu-id="bf34a-107">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="bf34a-107">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bf34a-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="bf34a-108">Recommended action</span></span>

<span data-ttu-id="bf34a-109">Supprimez le commutateur.</span><span class="sxs-lookup"><span data-stu-id="bf34a-109">Remove the switch.</span></span> <span data-ttu-id="bf34a-110">Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="bf34a-110">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="bf34a-111">Category</span><span class="sxs-lookup"><span data-stu-id="bf34a-111">Category</span></span>

<span data-ttu-id="bf34a-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bf34a-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bf34a-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="bf34a-113">Affected APIs</span></span>

- <span data-ttu-id="bf34a-114">Aucune</span><span class="sxs-lookup"><span data-stu-id="bf34a-114">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
