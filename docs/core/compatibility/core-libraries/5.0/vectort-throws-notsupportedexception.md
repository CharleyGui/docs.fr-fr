---
title: 'Modification avec rupture : le vecteur <T> lève une exception NotSupportedException'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où Vector <T> lève toujours une exception pour les paramètres de type non pris en charge.
ms.date: 11/01/2020
ms.openlocfilehash: 63db7c6b720735b180ed11098227b31a14008f74
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761004"
---
# <a name="vectort-always-throws-notsupportedexception-for-unsupported-types"></a><span data-ttu-id="bb33a-103">Vector \<T> lève toujours l’exception NotSupportedException pour les types non pris en charge</span><span class="sxs-lookup"><span data-stu-id="bb33a-103">Vector\<T> always throws NotSupportedException for unsupported types</span></span>

<span data-ttu-id="bb33a-104"><xref:System.Numerics.Vector%601?displayProperty=nameWithType> lève à présent toujours un <xref:System.NotSupportedException> pour les paramètres de type non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="bb33a-104"><xref:System.Numerics.Vector%601?displayProperty=nameWithType> now always throws a <xref:System.NotSupportedException> for unsupported type parameters.</span></span>

## <a name="change-description"></a><span data-ttu-id="bb33a-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="bb33a-105">Change description</span></span>

<span data-ttu-id="bb33a-106">Auparavant, les membres de <xref:System.Numerics.Vector%601> ne lèvent pas toujours une exception <xref:System.NotSupportedException> quand `T` était un [type non pris en charge](#unsupported-types).</span><span class="sxs-lookup"><span data-stu-id="bb33a-106">Previously, members of <xref:System.Numerics.Vector%601> would not always throw a <xref:System.NotSupportedException> when `T` was an [unsupported type](#unsupported-types).</span></span> <span data-ttu-id="bb33a-107">L’exception n’a pas toujours été levée en raison des chemins de code qui ont pris en charge l’accélération matérielle.</span><span class="sxs-lookup"><span data-stu-id="bb33a-107">The exception wasn't always thrown because of code paths that supported hardware acceleration.</span></span> <span data-ttu-id="bb33a-108">Par exemple, `Vector<bool> + Vector<bool>` retourné `default` au lieu de lever une exception sur les plateformes qui n’ont pas d’accélération matérielle, telles que ARM32.</span><span class="sxs-lookup"><span data-stu-id="bb33a-108">For example, `Vector<bool> + Vector<bool>` returned `default` instead of throwing an exception on platforms that have no hardware acceleration, such as ARM32.</span></span> <span data-ttu-id="bb33a-109">Pour les types non pris en charge, <xref:System.Numerics.Vector%601> les membres présentent un comportement incohérent sur différentes plateformes et configurations matérielles.</span><span class="sxs-lookup"><span data-stu-id="bb33a-109">For unsupported types, <xref:System.Numerics.Vector%601> members exhibited inconsistent behavior across different platforms and hardware configurations.</span></span>

<span data-ttu-id="bb33a-110">À compter de .NET 5,0, <xref:System.Numerics.Vector%601> les membres lèvent toujours une <xref:System.NotSupportedException> sur toutes les configurations matérielles lorsque `T` n’est pas un type pris en charge.</span><span class="sxs-lookup"><span data-stu-id="bb33a-110">Starting in .NET 5.0, <xref:System.Numerics.Vector%601> members always throw a <xref:System.NotSupportedException> on all hardware configurations when `T` is not a supported type.</span></span>

### <a name="unsupported-types"></a><span data-ttu-id="bb33a-111">Types non pris en charge</span><span class="sxs-lookup"><span data-stu-id="bb33a-111">Unsupported types</span></span>

<span data-ttu-id="bb33a-112">Les types pris en charge pour le paramètre de type de <xref:System.Numerics.Vector%601> sont :</span><span class="sxs-lookup"><span data-stu-id="bb33a-112">The supported types for the type parameter of <xref:System.Numerics.Vector%601> are:</span></span>

- `byte`
- `sbyte`
- `short`
- `ushort`
- `int`
- `uint`
- `long`
- `ulong`
- `float`
- `double`

<span data-ttu-id="bb33a-113">Les types pris en charge n’ont pas changé, toutefois, ils peuvent changer à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="bb33a-113">The supported types have not changed, however, they may change in the future.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="bb33a-114">Version introduite</span><span class="sxs-lookup"><span data-stu-id="bb33a-114">Version introduced</span></span>

<span data-ttu-id="bb33a-115">5.0</span><span class="sxs-lookup"><span data-stu-id="bb33a-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="bb33a-116">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="bb33a-116">Recommended action</span></span>

<span data-ttu-id="bb33a-117">N’utilisez pas un type non pris en charge pour le paramètre de type de <xref:System.Numerics.Vector%601> .</span><span class="sxs-lookup"><span data-stu-id="bb33a-117">Don't use an unsupported type for the type parameter of <xref:System.Numerics.Vector%601>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="bb33a-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="bb33a-118">Affected APIs</span></span>

- <span data-ttu-id="bb33a-119"><xref:System.Numerics.Vector%601?displayProperty=fullName> et tous ses membres</span><span class="sxs-lookup"><span data-stu-id="bb33a-119"><xref:System.Numerics.Vector%601?displayProperty=fullName> and all its members</span></span>

<!--

#### Category

Core .NET libraries

### Affected APIs

- ``T:System.Numerics.Vector`1``

-->
