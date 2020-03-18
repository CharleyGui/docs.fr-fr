---
ms.openlocfilehash: 7f528510e4158dad71280a7b1f269a231b8c60f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116338"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a><span data-ttu-id="38375-101">Types dans Microsoft.VisualBasic.Devices namespace non disponible</span><span class="sxs-lookup"><span data-stu-id="38375-101">Types in Microsoft.VisualBasic.Devices namespace not available</span></span>

<span data-ttu-id="38375-102">Les types <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> dans l’espace nom ne sont pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="38375-102">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="38375-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="38375-103">Version introduced</span></span>

<span data-ttu-id="38375-104">.NET Core 3.0 Aperçu 8</span><span class="sxs-lookup"><span data-stu-id="38375-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="38375-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="38375-105">Change description</span></span>

<span data-ttu-id="38375-106">Les types <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> dans l’espace de nom étaient disponibles dans certains .NET Core 3.0 Versions aperçu,.</span><span class="sxs-lookup"><span data-stu-id="38375-106">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="38375-107">Ils ne sont plus disponibles à partir de .NET Core 3.0 Aperçu 9.</span><span class="sxs-lookup"><span data-stu-id="38375-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="38375-108">Les types ont été supprimés pour éviter des dépendances inutiles à l’assemblage ou des changements de rupture dans les rejets ultérieurs.</span><span class="sxs-lookup"><span data-stu-id="38375-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="38375-109">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="38375-109">Recommended action</span></span>

<span data-ttu-id="38375-110">Si votre code dépend <xref:Microsoft.VisualBasic.Devices> de l’utilisation des types et de leurs membres, vous pouvez être en mesure d’utiliser un type ou un membre correspondant dans la bibliothèque de classe .NET.</span><span class="sxs-lookup"><span data-stu-id="38375-110">If your code depends on the use of <xref:Microsoft.VisualBasic.Devices> types and their members, you may be able to use a corresponding type or member in the .NET class library.</span></span> <span data-ttu-id="38375-111">Par exemple, des fonctionnalités équivalentes <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> <xref:System.DateTime?displayProperty=nameWithType> à <xref:System.Environment?displayProperty=nameWithType> la classe sont fournies <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> par les types <xref:System.IO.Ports?displayProperty=nameWithType> et les types, et des fonctionnalités équivalentes à la classe sont fournies par des types dans l’espace nom.</span><span class="sxs-lookup"><span data-stu-id="38375-111">For example, equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> class is provided by the <xref:System.DateTime?displayProperty=nameWithType> and <xref:System.Environment?displayProperty=nameWithType> types, and equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> class is provided by types in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span>

#### <a name="category"></a><span data-ttu-id="38375-112">Category</span><span class="sxs-lookup"><span data-stu-id="38375-112">Category</span></span>

<span data-ttu-id="38375-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="38375-113">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="38375-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="38375-114">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->
