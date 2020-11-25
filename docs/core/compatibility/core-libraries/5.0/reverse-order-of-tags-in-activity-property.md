---
title: 'Modification avec rupture : ordre des balises dans Activity. les balises sont inversées'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où Activity. Tags stocke désormais les éléments dans la liste en fonction de l’ordre dans lequel ils sont ajoutés.
ms.date: 11/01/2020
ms.openlocfilehash: 1ff14dc1a4f7a0bf8cf9e79f3750b819f4d4a5ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760984"
---
# <a name="order-of-tags-in-activitytags-is-reversed"></a><span data-ttu-id="18fee-103">Ordre des balises dans Activity. les balises sont inversées</span><span class="sxs-lookup"><span data-stu-id="18fee-103">Order of tags in Activity.Tags is reversed</span></span>

<span data-ttu-id="18fee-104"><xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> stocke désormais les éléments dans la liste en fonction de l’ordre dans lequel ils sont ajoutés, c’est-à-dire que le premier élément ajouté est tout d’abord dans la liste.</span><span class="sxs-lookup"><span data-stu-id="18fee-104"><xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> now stores items in the list according to the order they are added, that is, the first item that's added is first in the list.</span></span> <span data-ttu-id="18fee-105">Cette modification a été apportée pour correspondre à la [spécification des attributs OpenTelemetry](https://github.com/open-telemetry/opentelemetry-specification/blob/master/specification/common/common.md#attributes).</span><span class="sxs-lookup"><span data-stu-id="18fee-105">This change was made to match the [OpenTelemetry Attributes specification](https://github.com/open-telemetry/opentelemetry-specification/blob/master/specification/common/common.md#attributes).</span></span>

## <a name="change-description"></a><span data-ttu-id="18fee-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="18fee-106">Change description</span></span>

<span data-ttu-id="18fee-107">Dans les versions précédentes de .NET, <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> stocke les éléments dans l’ordre inverse à partir duquel ils sont ajoutés.</span><span class="sxs-lookup"><span data-stu-id="18fee-107">In previous .NET versions, <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> stores items in the reverse order from which they're added.</span></span> <span data-ttu-id="18fee-108">Autrement dit, le premier élément ajouté est le dernier de la liste.</span><span class="sxs-lookup"><span data-stu-id="18fee-108">That is, the first item added is last in the list.</span></span> <span data-ttu-id="18fee-109">À compter de .NET 5,0, l’ordre des éléments est inversé et le premier élément ajouté est toujours en premier dans la liste.</span><span class="sxs-lookup"><span data-stu-id="18fee-109">Starting in .NET 5.0, the order of the items is reversed, and the first item added is always first in the list.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="18fee-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="18fee-110">Version introduced</span></span>

<span data-ttu-id="18fee-111">5.0</span><span class="sxs-lookup"><span data-stu-id="18fee-111">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="18fee-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="18fee-112">Recommended action</span></span>

<span data-ttu-id="18fee-113">Si votre application dépend de l’ordre de la <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> liste et que vous effectuez une mise à niveau vers .net 5,0 ou une version ultérieure, vous devez modifier cette partie de votre code.</span><span class="sxs-lookup"><span data-stu-id="18fee-113">If your app has a dependency on the <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> list order and you're upgrading to .NET 5.0 or later, you'll need to change this part of your code.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="18fee-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="18fee-114">Affected APIs</span></span>

- <xref:System.Diagnostics.Activity.Tags?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `P:System.Diagnostics.Activity.Tags`

-->
