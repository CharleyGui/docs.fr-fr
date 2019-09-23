---
ms.openlocfilehash: bb163d5a6eb3d926a44a83ea79572c3a497bbe8d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181843"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a><span data-ttu-id="5e8a4-101">Types dans l’espace de noms Microsoft. VisualBasic. Devices non disponible</span><span class="sxs-lookup"><span data-stu-id="5e8a4-101">Types in Microsoft.VisualBasic.Devices namespace not available</span></span>

<span data-ttu-id="5e8a4-102">Les types de l' <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> espace de noms ne sont pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="5e8a4-102">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5e8a4-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="5e8a4-103">Version introduced</span></span>

<span data-ttu-id="5e8a4-104">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="5e8a4-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="details"></a><span data-ttu-id="5e8a4-105">Détails</span><span class="sxs-lookup"><span data-stu-id="5e8a4-105">Details</span></span>

<span data-ttu-id="5e8a4-106">Les types de l' <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> espace de noms étaient disponibles dans certaines versions préliminaires de .net Core 3,0,.</span><span class="sxs-lookup"><span data-stu-id="5e8a4-106">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="5e8a4-107">Ils ne sont plus disponibles à partir de .NET Core 3,0 Preview 9.</span><span class="sxs-lookup"><span data-stu-id="5e8a4-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="5e8a4-108">Les types ont été supprimés pour éviter les dépendances d’assembly inutiles ou les modifications importantes dans les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="5e8a4-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="5e8a4-109">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="5e8a4-109">Recommended action</span></span>

<span data-ttu-id="5e8a4-110">Si votre code dépend de l’utilisation de <xref:Microsoft.VisualBasic.Devices> types et de leurs membres, vous pourrez peut-être utiliser un type ou un membre correspondant dans la bibliothèque de classes .net.</span><span class="sxs-lookup"><span data-stu-id="5e8a4-110">If your code depends on the use of <xref:Microsoft.VisualBasic.Devices> types and their members, you may be able to use a corresponding type or member in the .NET class library.</span></span> <span data-ttu-id="5e8a4-111">Par exemple, les fonctionnalités équivalentes <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> à la classe sont fournies <xref:System.DateTime?displayProperty=nameWithType> par <xref:System.Environment?displayProperty=nameWithType> les types et, et les fonctionnalités <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> équivalentes à la classe sont fournies <xref:System.IO.Ports?displayProperty=nameWithType> par les types dans l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="5e8a4-111">For example, equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> class is provided by the <xref:System.DateTime?displayProperty=nameWithType> and <xref:System.Environment?displayProperty=nameWithType> types, and equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> class is provided by types in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span>

#### <a name="category"></a><span data-ttu-id="5e8a4-112">Category</span><span class="sxs-lookup"><span data-stu-id="5e8a4-112">Category</span></span>

<span data-ttu-id="5e8a4-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5e8a4-113">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5e8a4-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="5e8a4-114">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >

