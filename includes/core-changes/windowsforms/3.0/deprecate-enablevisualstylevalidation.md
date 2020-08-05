---
ms.openlocfilehash: 196a26bd235e5e2556baa7fac979b3316ff81e1f
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556163"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a><span data-ttu-id="6ba62-101">Commutateur de compatibilité EnableVisualStyleValidation non pris en charge</span><span class="sxs-lookup"><span data-stu-id="6ba62-101">EnableVisualStyleValidation compatibility switch not supported</span></span>

<span data-ttu-id="6ba62-102">Le `Switch.System.Windows.Forms.EnableVisualStyleValidation` commutateur de compatibilité n’est pas pris en charge dans les Windows Forms sur .net Core ou .net 5,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6ba62-102">The `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch is not supported in Windows Forms on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6ba62-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="6ba62-103">Change description</span></span>

<span data-ttu-id="6ba62-104">Dans .NET Framework, le `Switch.System.Windows.Forms.EnableVisualStyleValidation` commutateur de compatibilité permettait à une application de refuser la validation des styles visuels fournis sous forme numérique.</span><span class="sxs-lookup"><span data-stu-id="6ba62-104">In .NET Framework, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch allowed an application to opt out of validation of visual styles supplied in a numeric form.</span></span>

<span data-ttu-id="6ba62-105">Dans .NET Core et .NET 5,0 et versions ultérieures, le `Switch.System.Windows.Forms.EnableVisualStyleValidation` commutateur n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="6ba62-105">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6ba62-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="6ba62-106">Version introduced</span></span>

<span data-ttu-id="6ba62-107">3.0</span><span class="sxs-lookup"><span data-stu-id="6ba62-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6ba62-108">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="6ba62-108">Recommended action</span></span>

<span data-ttu-id="6ba62-109">Supprimez le commutateur.</span><span class="sxs-lookup"><span data-stu-id="6ba62-109">Remove the switch.</span></span> <span data-ttu-id="6ba62-110">Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.</span><span class="sxs-lookup"><span data-stu-id="6ba62-110">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="6ba62-111">Category</span><span class="sxs-lookup"><span data-stu-id="6ba62-111">Category</span></span>

<span data-ttu-id="6ba62-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6ba62-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6ba62-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="6ba62-113">Affected APIs</span></span>

- <span data-ttu-id="6ba62-114">Aucun</span><span class="sxs-lookup"><span data-stu-id="6ba62-114">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
