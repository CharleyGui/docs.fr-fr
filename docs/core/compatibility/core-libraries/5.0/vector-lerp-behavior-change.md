---
title: 'Modification avec rupture : modification du comportement pour Vector2. Lerp et Vector4. Lerp'
description: En savoir plus sur le changement critique .NET 5,0 dans les bibliothèques .NET de base où l’implémentation de Vector2. Lerp et Vector4. Lerp a été modifiée pour prendre en compte correctement une erreur d’arrondi à virgule flottante.
ms.date: 11/01/2020
ms.openlocfilehash: 8e363a559dba8b7563c40637c47f101d59951216
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760899"
---
# <a name="behavior-change-for-vector2lerp-and-vector4lerp"></a><span data-ttu-id="edfc6-103">Changement de comportement pour Vector2. Lerp et Vector4. Lerp</span><span class="sxs-lookup"><span data-stu-id="edfc6-103">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>

<span data-ttu-id="edfc6-104">L’implémentation de <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> et <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> a changé pour tenir compte d’une erreur d’arrondi à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="edfc6-104">The implementation of <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> and <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> changed to correctly account for a floating-point rounding error.</span></span>

## <a name="change-description"></a><span data-ttu-id="edfc6-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="edfc6-105">Change description</span></span>

<span data-ttu-id="edfc6-106">Précédemment, <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> et <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> étaient implémentées en tant que `value1 + (value2 - value1) * amount` .</span><span class="sxs-lookup"><span data-stu-id="edfc6-106">Previously, <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> and <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> were implemented as `value1 + (value2 - value1) * amount`.</span></span> <span data-ttu-id="edfc6-107">Toutefois, en raison d’une erreur d’arrondi à virgule flottante, cet algorithme ne retourne pas toujours `value2` lorsque `amount` est `1.0f` .</span><span class="sxs-lookup"><span data-stu-id="edfc6-107">However, due to a floating-point rounding error, this algorithm doesn't always return `value2` when `amount` is `1.0f`.</span></span>

<span data-ttu-id="edfc6-108">Dans .NET 5,0 et versions ultérieures, l’implémentation utilise le même algorithme que <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType> , qui est `(value1 * (1.0f - amount)) + (value2 * amount)` .</span><span class="sxs-lookup"><span data-stu-id="edfc6-108">In .NET 5.0 and later, the implementation uses the same algorithm as <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType>, which is `(value1 * (1.0f - amount)) + (value2 * amount)`.</span></span> <span data-ttu-id="edfc6-109">Cet algorithme gère correctement l’erreur d’arrondi.</span><span class="sxs-lookup"><span data-stu-id="edfc6-109">This algorithm correctly accounts for the rounding error.</span></span> <span data-ttu-id="edfc6-110">Désormais, lorsque `amount` a `1.0f` la valeur, le résultat est exact `value2` .</span><span class="sxs-lookup"><span data-stu-id="edfc6-110">Now, when `amount` is `1.0f`, the result is precisely `value2`.</span></span> <span data-ttu-id="edfc6-111">L’algorithme mis à jour permet également à l’algorithme d’être optimisé librement à l’aide <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> de lorsqu’il est disponible.</span><span class="sxs-lookup"><span data-stu-id="edfc6-111">The updated algorithm also allows the algorithm to be freely optimized using <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> when it's available.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="edfc6-112">Version introduite</span><span class="sxs-lookup"><span data-stu-id="edfc6-112">Version introduced</span></span>

<span data-ttu-id="edfc6-113">5.0</span><span class="sxs-lookup"><span data-stu-id="edfc6-113">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="edfc6-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="edfc6-114">Recommended action</span></span>

<span data-ttu-id="edfc6-115">Aucune action n'est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="edfc6-115">No action is necessary.</span></span> <span data-ttu-id="edfc6-116">Toutefois, si vous souhaitez conserver l’ancien comportement, vous pouvez implémenter votre propre `Lerp` fonction qui utilise l’algorithme précédent de `value1 + (value2 - value1) * amount` .</span><span class="sxs-lookup"><span data-stu-id="edfc6-116">However, if you want to maintain the old behavior, you can implement your own `Lerp` function that uses the previous algorithm of `value1 + (value2 - value1) * amount`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="edfc6-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="edfc6-117">Affected APIs</span></span>

- <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=fullName>
- <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)`
- `M:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)`

-->
