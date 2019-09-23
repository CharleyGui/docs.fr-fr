---
ms.openlocfilehash: e6bb1d53cbe1883b8faef75bd22942bd4f65a5e6
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71181790"
---
### <a name="switchsystemwindowsformsenablevisualstylevalidation-compatibility-switch-not-supported"></a><span data-ttu-id="ca9bf-101">Commutateur de compatibilité Switch. System. Windows. Forms. EnableVisualStyleValidation non pris en charge</span><span class="sxs-lookup"><span data-stu-id="ca9bf-101">Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported</span></span>

<span data-ttu-id="ca9bf-102">Le `Switch.System.Windows.Forms.EnableVisualStyleValidation` commutateur de compatibilité n’est pas pris en charge dans Windows Forms sur .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="ca9bf-102">The `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ca9bf-103">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="ca9bf-103">Change description</span></span>

<span data-ttu-id="ca9bf-104">Dans .NET Framework, le `Switch.System.Windows.Forms.EnableVisualStyleValidation` commutateur de compatibilité permettait à une application de refuser la validation des styles visuels fournis sous forme numérique.</span><span class="sxs-lookup"><span data-stu-id="ca9bf-104">In .NET Framework, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch allowed an application to opt out of validation of visual styles supplied in a numeric form.</span></span> 

<span data-ttu-id="ca9bf-105">Dans .net Core, le `Switch.System.Windows.Forms.EnableVisualStyleValidation` commutateur n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ca9bf-105">In .NET Core, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ca9bf-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ca9bf-106">Version introduced</span></span>

<span data-ttu-id="ca9bf-107">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="ca9bf-107">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ca9bf-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="ca9bf-108">Recommended action</span></span>

<span data-ttu-id="ca9bf-109">Supprimez le commutateur.</span><span class="sxs-lookup"><span data-stu-id="ca9bf-109">Remove the switch.</span></span> <span data-ttu-id="ca9bf-110">Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="ca9bf-110">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="ca9bf-111">Category</span><span class="sxs-lookup"><span data-stu-id="ca9bf-111">Category</span></span>

<span data-ttu-id="ca9bf-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ca9bf-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ca9bf-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="ca9bf-113">Affected APIs</span></span>

- <span data-ttu-id="ca9bf-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ca9bf-114">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
