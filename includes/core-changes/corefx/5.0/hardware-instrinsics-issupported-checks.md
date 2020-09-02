---
ms.openlocfilehash: bba9659b92e5aabc276c585929c99898316036c5
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359131"
---
### <a name="hardware-intrinsic-issupported-checks-may-differ-for-nested-types"></a><span data-ttu-id="18dd4-101">Les contrôles de IsSupported intrinsèques matériels peuvent être différents pour les types imbriqués</span><span class="sxs-lookup"><span data-stu-id="18dd4-101">Hardware intrinsic IsSupported checks may differ for nested types</span></span>

<span data-ttu-id="18dd4-102">`<Isa>.X64.IsSupported`La vérification, où `<Isa>` fait référence aux classes de l' <xref:System.Runtime.Intrinsics.X86?displayProperty=nameWithType> espace de noms, peut à présent produire un résultat différent pour les versions précédentes de .net.</span><span class="sxs-lookup"><span data-stu-id="18dd4-102">Checking `<Isa>.X64.IsSupported`, where `<Isa>` refers to the classes in the <xref:System.Runtime.Intrinsics.X86?displayProperty=nameWithType> namespace, may now produce a different result to previous versions of .NET.</span></span>

> [!TIP]
> <span data-ttu-id="18dd4-103">*ISA* est l’acronyme de l’architecture standard de l’industrie.</span><span class="sxs-lookup"><span data-stu-id="18dd4-103">*ISA* stands for industry standard architecture.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="18dd4-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="18dd4-104">Version introduced</span></span>

<span data-ttu-id="18dd4-105">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="18dd4-105">5.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="18dd4-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="18dd4-106">Change description</span></span>

<span data-ttu-id="18dd4-107">Dans les versions précédentes de .NET, certains des <xref:System.Runtime.Intrinsics.X86> types intrinsèques du matériel, par exemple, <xref:System.Runtime.Intrinsics.X86.Aes?displayProperty=nameWithType> , n’exposent pas une classe imbriquée `X64` .</span><span class="sxs-lookup"><span data-stu-id="18dd4-107">In previous versions of .NET, some of the <xref:System.Runtime.Intrinsics.X86> hardware-intrinsic types, for example, <xref:System.Runtime.Intrinsics.X86.Aes?displayProperty=nameWithType>, didn't expose a nested `X64` class.</span></span> <span data-ttu-id="18dd4-108">Pour ces types, l’appel de `<Isa>.X64.IsSupported` résolu à une `IsSupported` propriété sur une `X64` classe imbriquée d’une classe parente de `<Isa>` .</span><span class="sxs-lookup"><span data-stu-id="18dd4-108">For these types, calling `<Isa>.X64.IsSupported` resolved to an `IsSupported` property on a nested `X64` class of a parent class of `<Isa>`.</span></span> <span data-ttu-id="18dd4-109">Cela signifiait que la propriété pouvait retourner `true` même lorsque `<Isa>.IsSupported` retourne `false` .</span><span class="sxs-lookup"><span data-stu-id="18dd4-109">This meant that the property could return `true` even when `<Isa>.IsSupported` returns `false`.</span></span>

<span data-ttu-id="18dd4-110">Dans .NET 5,0 et versions ultérieures, tous les <xref:System.Runtime.Intrinsics.X86> types exposent une `X64` classe imbriquée qui signale correctement la prise en charge.</span><span class="sxs-lookup"><span data-stu-id="18dd4-110">In .NET 5.0 and later versions, all of the <xref:System.Runtime.Intrinsics.X86> types expose a nested `X64` class that appropriately reports support.</span></span> <span data-ttu-id="18dd4-111">Cela garantit que la hiérarchie générale reste correcte, et que si `<Isa>.X64.IsSupported` a la valeur `true` , `<Isa>.IsSupported` peut également être supposé être `true` .</span><span class="sxs-lookup"><span data-stu-id="18dd4-111">This ensures that the general hierarchy remains correct, and that if `<Isa>.X64.IsSupported` is `true`, then `<Isa>.IsSupported` can also be assumed to be `true`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="18dd4-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="18dd4-112">Reason for change</span></span>

<span data-ttu-id="18dd4-113">Il a été prévu que si `<Isa>.X64.IsSupported` a la valeur `true` , `<Isa>.IsSupported` est également supposé être `true` .</span><span class="sxs-lookup"><span data-stu-id="18dd4-113">It was intended that if `<Isa>.X64.IsSupported` is `true`, `<Isa>.IsSupported` is also implied to be `true`.</span></span> <span data-ttu-id="18dd4-114">Toutefois, en raison du fonctionnement de la résolution des membres en C#, les classes qui n’ont pas de classe imbriquée `X64` exposaient une situation où cela n’était pas toujours le cas et ont conduit à des bogues dans le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="18dd4-114">However, due to how member resolution works in C#, classes that didn't have a nested `X64` class exposed a situation where this wasn't always the case and led to bugs in user code.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="18dd4-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="18dd4-115">Recommended action</span></span>

<span data-ttu-id="18dd4-116">Si nécessaire, ajustez le code qui vérifie si `IsSupported` le ISA approprié est vérifié.</span><span class="sxs-lookup"><span data-stu-id="18dd4-116">If necessary, adjust code that checks `IsSupported` to check for the appropriate ISA.</span></span>

#### <a name="category"></a><span data-ttu-id="18dd4-117">Category</span><span class="sxs-lookup"><span data-stu-id="18dd4-117">Category</span></span>

<span data-ttu-id="18dd4-118">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="18dd4-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="18dd4-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="18dd4-119">Affected APIs</span></span>

- <xref:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported`

-->
