---
ms.openlocfilehash: 4c47b95e98aca727d9f0eda54a167a71fd53afb9
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198412"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a><span data-ttu-id="0e538-101">Types dans l’espace de noms Microsoft. VisualBasic. Devices non disponible</span><span class="sxs-lookup"><span data-stu-id="0e538-101">Types in Microsoft.VisualBasic.Devices namespace not available</span></span>

<span data-ttu-id="0e538-102">Les types de l’espace de noms <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> ne sont pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="0e538-102">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0e538-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="0e538-103">Version introduced</span></span>

<span data-ttu-id="0e538-104">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="0e538-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="0e538-105">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="0e538-105">Change description</span></span>

<span data-ttu-id="0e538-106">Les types de l’espace de noms <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> étaient disponibles dans certaines versions préliminaires de .NET Core 3,0,.</span><span class="sxs-lookup"><span data-stu-id="0e538-106">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="0e538-107">Ils ne sont plus disponibles à partir de .NET Core 3,0 Preview 9.</span><span class="sxs-lookup"><span data-stu-id="0e538-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="0e538-108">Les types ont été supprimés pour éviter les dépendances d’assembly inutiles ou les modifications importantes dans les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="0e538-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0e538-109">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="0e538-109">Recommended action</span></span>

<span data-ttu-id="0e538-110">Si votre code dépend de l’utilisation de <xref:Microsoft.VisualBasic.Devices> types et de leurs membres, vous pourrez peut-être utiliser un type ou un membre correspondant dans la bibliothèque de classes .NET.</span><span class="sxs-lookup"><span data-stu-id="0e538-110">If your code depends on the use of <xref:Microsoft.VisualBasic.Devices> types and their members, you may be able to use a corresponding type or member in the .NET class library.</span></span> <span data-ttu-id="0e538-111">Par exemple, les fonctionnalités équivalentes à la classe <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> sont fournies par les types <xref:System.DateTime?displayProperty=nameWithType> et <xref:System.Environment?displayProperty=nameWithType>, et les fonctionnalités équivalentes à la classe <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> sont fournies par les types dans l’espace de noms <xref:System.IO.Ports?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0e538-111">For example, equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> class is provided by the <xref:System.DateTime?displayProperty=nameWithType> and <xref:System.Environment?displayProperty=nameWithType> types, and equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> class is provided by types in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span>

#### <a name="category"></a><span data-ttu-id="0e538-112">Category</span><span class="sxs-lookup"><span data-stu-id="0e538-112">Category</span></span>

<span data-ttu-id="0e538-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0e538-113">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0e538-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="0e538-114">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >

