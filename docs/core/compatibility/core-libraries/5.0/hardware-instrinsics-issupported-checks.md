---
title: 'Modification avec rupture : les vérifications de IsSupported de matériel intrinsèque peuvent être différentes pour les types imbriqués'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où la vérification de x64. IsSupported pour les intrinsèques matériels peut à présent produire un résultat différent.
ms.date: 11/01/2020
ms.openlocfilehash: 9acef15860de76a9743621cb4c5edba5aac3931c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761063"
---
# <a name="hardware-intrinsic-issupported-checks-may-differ-for-nested-types"></a><span data-ttu-id="4ef65-103">Les contrôles de IsSupported intrinsèques matériels peuvent être différents pour les types imbriqués</span><span class="sxs-lookup"><span data-stu-id="4ef65-103">Hardware intrinsic IsSupported checks may differ for nested types</span></span>

<span data-ttu-id="4ef65-104">`<Isa>.X64.IsSupported`La vérification, où `<Isa>` fait référence aux classes de l' <xref:System.Runtime.Intrinsics.X86?displayProperty=nameWithType> espace de noms, peut à présent produire un résultat différent pour les versions précédentes de .net.</span><span class="sxs-lookup"><span data-stu-id="4ef65-104">Checking `<Isa>.X64.IsSupported`, where `<Isa>` refers to the classes in the <xref:System.Runtime.Intrinsics.X86?displayProperty=nameWithType> namespace, may now produce a different result to previous versions of .NET.</span></span>

> [!TIP]
> <span data-ttu-id="4ef65-105">*ISA* est l’acronyme de l’architecture standard de l’industrie.</span><span class="sxs-lookup"><span data-stu-id="4ef65-105">*ISA* stands for industry standard architecture.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="4ef65-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="4ef65-106">Version introduced</span></span>

<span data-ttu-id="4ef65-107">5.0</span><span class="sxs-lookup"><span data-stu-id="4ef65-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="4ef65-108">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="4ef65-108">Change description</span></span>

<span data-ttu-id="4ef65-109">Dans les versions précédentes de .NET, certains des <xref:System.Runtime.Intrinsics.X86> types intrinsèques du matériel, par exemple, <xref:System.Runtime.Intrinsics.X86.Aes?displayProperty=nameWithType> , n’exposent pas une classe imbriquée `X64` .</span><span class="sxs-lookup"><span data-stu-id="4ef65-109">In previous versions of .NET, some of the <xref:System.Runtime.Intrinsics.X86> hardware-intrinsic types, for example, <xref:System.Runtime.Intrinsics.X86.Aes?displayProperty=nameWithType>, didn't expose a nested `X64` class.</span></span> <span data-ttu-id="4ef65-110">Pour ces types, l’appel de `<Isa>.X64.IsSupported` résolu à une `IsSupported` propriété sur une `X64` classe imbriquée d’une classe parente de `<Isa>` .</span><span class="sxs-lookup"><span data-stu-id="4ef65-110">For these types, calling `<Isa>.X64.IsSupported` resolved to an `IsSupported` property on a nested `X64` class of a parent class of `<Isa>`.</span></span> <span data-ttu-id="4ef65-111">Cela signifiait que la propriété pouvait retourner `true` même lorsque `<Isa>.IsSupported` retourne `false` .</span><span class="sxs-lookup"><span data-stu-id="4ef65-111">This meant that the property could return `true` even when `<Isa>.IsSupported` returns `false`.</span></span>

<span data-ttu-id="4ef65-112">Dans .NET 5,0 et versions ultérieures, tous les <xref:System.Runtime.Intrinsics.X86> types exposent une `X64` classe imbriquée qui signale correctement la prise en charge.</span><span class="sxs-lookup"><span data-stu-id="4ef65-112">In .NET 5.0 and later versions, all of the <xref:System.Runtime.Intrinsics.X86> types expose a nested `X64` class that appropriately reports support.</span></span> <span data-ttu-id="4ef65-113">Cela garantit que la hiérarchie générale reste correcte, et que si `<Isa>.X64.IsSupported` a la valeur `true` , `<Isa>.IsSupported` peut également être supposé être `true` .</span><span class="sxs-lookup"><span data-stu-id="4ef65-113">This ensures that the general hierarchy remains correct, and that if `<Isa>.X64.IsSupported` is `true`, then `<Isa>.IsSupported` can also be assumed to be `true`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="4ef65-114">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="4ef65-114">Reason for change</span></span>

<span data-ttu-id="4ef65-115">Il a été prévu que si `<Isa>.X64.IsSupported` a la valeur `true` , `<Isa>.IsSupported` est également supposé être `true` .</span><span class="sxs-lookup"><span data-stu-id="4ef65-115">It was intended that if `<Isa>.X64.IsSupported` is `true`, `<Isa>.IsSupported` is also implied to be `true`.</span></span> <span data-ttu-id="4ef65-116">Toutefois, en raison du fonctionnement de la résolution des membres en C#, les classes qui n’ont pas de classe imbriquée `X64` exposaient une situation où cela n’était pas toujours le cas et ont conduit à des bogues dans le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4ef65-116">However, due to how member resolution works in C#, classes that didn't have a nested `X64` class exposed a situation where this wasn't always the case and led to bugs in user code.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="4ef65-117">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="4ef65-117">Recommended action</span></span>

<span data-ttu-id="4ef65-118">Si nécessaire, ajustez le code qui vérifie si `IsSupported` le ISA approprié est vérifié.</span><span class="sxs-lookup"><span data-stu-id="4ef65-118">If necessary, adjust code that checks `IsSupported` to check for the appropriate ISA.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="4ef65-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="4ef65-119">Affected APIs</span></span>

- <xref:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported`

-->
