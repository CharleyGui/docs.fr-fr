---
ms.openlocfilehash: 4bc060f991501b81db0cb7c521e55996a2b5e91e
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281297"
---
### <a name="behavior-change-for-vector2lerp-and-vector4lerp"></a><span data-ttu-id="86738-101">Changement de comportement pour Vector2. Lerp et Vector4. Lerp</span><span class="sxs-lookup"><span data-stu-id="86738-101">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>

<span data-ttu-id="86738-102">L’implémentation de <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> et <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> a changé pour tenir compte d’une erreur d’arrondi à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="86738-102">The implementation of <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> and <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> changed to correctly account for a floating-point rounding error.</span></span>

#### <a name="change-description"></a><span data-ttu-id="86738-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="86738-103">Change description</span></span>

<span data-ttu-id="86738-104">Précédemment, <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> et <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> étaient implémentées en tant que `value1 + (value2 - value1) * amount` .</span><span class="sxs-lookup"><span data-stu-id="86738-104">Previously, <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> and <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> were implemented as `value1 + (value2 - value1) * amount`.</span></span> <span data-ttu-id="86738-105">Toutefois, en raison d’une erreur d’arrondi à virgule flottante, cet algorithme ne retourne pas toujours `value2` lorsque `amount` est `1.0f` .</span><span class="sxs-lookup"><span data-stu-id="86738-105">However, due to a floating-point rounding error, this algorithm doesn't always return `value2` when `amount` is `1.0f`.</span></span>

<span data-ttu-id="86738-106">Dans .NET 5,0 et versions ultérieures, l’implémentation utilise le même algorithme que <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType> , qui est `(value1 * (1.0f - amount)) + (value2 * amount)` .</span><span class="sxs-lookup"><span data-stu-id="86738-106">In .NET 5.0 and later, the implementation uses the same algorithm as <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType>, which is `(value1 * (1.0f - amount)) + (value2 * amount)`.</span></span> <span data-ttu-id="86738-107">Cet algorithme gère correctement l’erreur d’arrondi.</span><span class="sxs-lookup"><span data-stu-id="86738-107">This algorithm correctly accounts for the rounding error.</span></span> <span data-ttu-id="86738-108">Désormais, lorsque `amount` a `1.0f` la valeur, le résultat est exact `value2` .</span><span class="sxs-lookup"><span data-stu-id="86738-108">Now, when `amount` is `1.0f`, the result is precisely `value2`.</span></span> <span data-ttu-id="86738-109">L’algorithme mis à jour permet également à l’algorithme d’être optimisé librement à l’aide <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> de lorsqu’il est disponible.</span><span class="sxs-lookup"><span data-stu-id="86738-109">The updated algorithm also allows the algorithm to be freely optimized using <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> when it's available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="86738-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="86738-110">Version introduced</span></span>

<span data-ttu-id="86738-111">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="86738-111">5.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="86738-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="86738-112">Recommended action</span></span>

<span data-ttu-id="86738-113">Aucune action n'est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="86738-113">No action is necessary.</span></span> <span data-ttu-id="86738-114">Toutefois, si vous souhaitez conserver l’ancien comportement, vous pouvez implémenter votre propre `Lerp` fonction qui utilise l’algorithme précédent de `value1 + (value2 - value1) * amount` .</span><span class="sxs-lookup"><span data-stu-id="86738-114">However, if you want to maintain the old behavior, you can implement your own `Lerp` function that uses the previous algorithm of `value1 + (value2 - value1) * amount`.</span></span>

#### <a name="category"></a><span data-ttu-id="86738-115">Category</span><span class="sxs-lookup"><span data-stu-id="86738-115">Category</span></span>

<span data-ttu-id="86738-116">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="86738-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="86738-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="86738-117">Affected APIs</span></span>

- <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=fullName>
- <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)`
- `M:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)`

-->
