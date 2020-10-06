---
ms.openlocfilehash: 24b88b3ba1b6cfe9fb9fb1f6398a6daeb57596a9
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756106"
---
### <a name="order-of-tags-in-activitytags-is-reversed"></a><span data-ttu-id="adff6-101">Ordre des balises dans Activity. les balises sont inversées</span><span class="sxs-lookup"><span data-stu-id="adff6-101">Order of tags in Activity.Tags is reversed</span></span>

<span data-ttu-id="adff6-102"><xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> stocke désormais les éléments dans la liste en fonction de l’ordre dans lequel ils sont ajoutés, c’est-à-dire que le premier élément ajouté est tout d’abord dans la liste.</span><span class="sxs-lookup"><span data-stu-id="adff6-102"><xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> now stores items in the list according to the order they are added, that is, the first item that's added is first in the list.</span></span> <span data-ttu-id="adff6-103">Cette modification a été apportée pour correspondre à la [spécification des attributs OpenTelemetry](https://github.com/open-telemetry/opentelemetry-specification/blob/master/specification/common/common.md#attributes).</span><span class="sxs-lookup"><span data-stu-id="adff6-103">This change was made to match the [OpenTelemetry Attributes specification](https://github.com/open-telemetry/opentelemetry-specification/blob/master/specification/common/common.md#attributes).</span></span>

#### <a name="change-description"></a><span data-ttu-id="adff6-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="adff6-104">Change description</span></span>

<span data-ttu-id="adff6-105">Dans les versions précédentes de .NET, <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> stocke les éléments dans l’ordre inverse à partir duquel ils sont ajoutés.</span><span class="sxs-lookup"><span data-stu-id="adff6-105">In previous .NET versions, <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> stores items in the reverse order from which they're added.</span></span> <span data-ttu-id="adff6-106">Autrement dit, le premier élément ajouté est le dernier de la liste.</span><span class="sxs-lookup"><span data-stu-id="adff6-106">That is, the first item added is last in the list.</span></span> <span data-ttu-id="adff6-107">À compter de .NET 5,0, l’ordre des éléments est inversé et le premier élément ajouté est toujours en premier dans la liste.</span><span class="sxs-lookup"><span data-stu-id="adff6-107">Starting in .NET 5.0, the order of the items is reversed, and the first item added is always first in the list.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="adff6-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="adff6-108">Version introduced</span></span>

<span data-ttu-id="adff6-109">5.0</span><span class="sxs-lookup"><span data-stu-id="adff6-109">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="adff6-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="adff6-110">Recommended action</span></span>

<span data-ttu-id="adff6-111">Si votre application dépend de l’ordre de la <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> liste et que vous effectuez une mise à niveau vers .net 5,0 ou une version ultérieure, vous devez modifier cette partie de votre code.</span><span class="sxs-lookup"><span data-stu-id="adff6-111">If your app has a dependency on the <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> list order and you're upgrading to .NET 5.0 or later, you'll need to change this part of your code.</span></span>

#### <a name="category"></a><span data-ttu-id="adff6-112">Category</span><span class="sxs-lookup"><span data-stu-id="adff6-112">Category</span></span>

<span data-ttu-id="adff6-113">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="adff6-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="adff6-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="adff6-114">Affected APIs</span></span>

- <xref:System.Diagnostics.Activity.Tags?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Activity.Tags`

-->
