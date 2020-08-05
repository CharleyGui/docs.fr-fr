---
ms.openlocfilehash: 43ebb37124b8efe077b9f81fe5351bd7db2c72f7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302706"
---
### <a name="vectort-always-throws-notsupportedexception-for-unsupported-types"></a><span data-ttu-id="93662-101">Vector \<T> lève toujours l’exception NotSupportedException pour les types non pris en charge</span><span class="sxs-lookup"><span data-stu-id="93662-101">Vector\<T> always throws NotSupportedException for unsupported types</span></span>

<span data-ttu-id="93662-102"><xref:System.Numerics.Vector%601?displayProperty=nameWithType>lève à présent toujours un <xref:System.NotSupportedException> pour les paramètres de type non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="93662-102"><xref:System.Numerics.Vector%601?displayProperty=nameWithType> now always throws a <xref:System.NotSupportedException> for unsupported type parameters.</span></span>

#### <a name="change-description"></a><span data-ttu-id="93662-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="93662-103">Change description</span></span>

<span data-ttu-id="93662-104">Auparavant, les membres de <xref:System.Numerics.Vector%601> ne lèvent pas toujours une exception <xref:System.NotSupportedException> quand `T` était un [type non pris en charge](#unsupported-types).</span><span class="sxs-lookup"><span data-stu-id="93662-104">Previously, members of <xref:System.Numerics.Vector%601> would not always throw a <xref:System.NotSupportedException> when `T` was an [unsupported type](#unsupported-types).</span></span> <span data-ttu-id="93662-105">L’exception n’a pas toujours été levée en raison des chemins de code qui ont pris en charge l’accélération matérielle.</span><span class="sxs-lookup"><span data-stu-id="93662-105">The exception wasn't always thrown because of code paths that supported hardware acceleration.</span></span> <span data-ttu-id="93662-106">Par exemple, `Vector<bool> + Vector<bool>` retourné `default` au lieu de lever une exception sur les plateformes qui n’ont pas d’accélération matérielle, telles que ARM32.</span><span class="sxs-lookup"><span data-stu-id="93662-106">For example, `Vector<bool> + Vector<bool>` returned `default` instead of throwing an exception on platforms that have no hardware acceleration, such as ARM32.</span></span> <span data-ttu-id="93662-107">Pour les types non pris en charge, <xref:System.Numerics.Vector%601> les membres présentent un comportement incohérent sur différentes plateformes et configurations matérielles.</span><span class="sxs-lookup"><span data-stu-id="93662-107">For unsupported types, <xref:System.Numerics.Vector%601> members exhibited inconsistent behavior across different platforms and hardware configurations.</span></span>

<span data-ttu-id="93662-108">À compter de .NET 5,0, <xref:System.Numerics.Vector%601> les membres lèvent toujours une <xref:System.NotSupportedException> sur toutes les configurations matérielles lorsque `T` n’est pas un type pris en charge.</span><span class="sxs-lookup"><span data-stu-id="93662-108">Starting in .NET 5.0, <xref:System.Numerics.Vector%601> members always throw a <xref:System.NotSupportedException> on all hardware configurations when `T` is not a supported type.</span></span>

##### <a name="unsupported-types"></a><span data-ttu-id="93662-109">Types non pris en charge</span><span class="sxs-lookup"><span data-stu-id="93662-109">Unsupported types</span></span>

<span data-ttu-id="93662-110">Les types pris en charge pour le paramètre de type de <xref:System.Numerics.Vector%601> sont :</span><span class="sxs-lookup"><span data-stu-id="93662-110">The supported types for the type parameter of <xref:System.Numerics.Vector%601> are:</span></span>

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

<span data-ttu-id="93662-111">Les types pris en charge n’ont pas changé, toutefois, ils peuvent changer à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="93662-111">The supported types have not changed, however, they may change in the future.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="93662-112">Version introduite</span><span class="sxs-lookup"><span data-stu-id="93662-112">Version introduced</span></span>

<span data-ttu-id="93662-113">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="93662-113">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="93662-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="93662-114">Recommended action</span></span>

<span data-ttu-id="93662-115">N’utilisez pas un type non pris en charge pour le paramètre de type de <xref:System.Numerics.Vector%601> .</span><span class="sxs-lookup"><span data-stu-id="93662-115">Don't use an unsupported type for the type parameter of <xref:System.Numerics.Vector%601>.</span></span>

#### <a name="category"></a><span data-ttu-id="93662-116">Category</span><span class="sxs-lookup"><span data-stu-id="93662-116">Category</span></span>

<span data-ttu-id="93662-117">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="93662-117">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="93662-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="93662-118">Affected APIs</span></span>

- <span data-ttu-id="93662-119"><xref:System.Numerics.Vector%601?displayProperty=fullName>et tous ses membres</span><span class="sxs-lookup"><span data-stu-id="93662-119"><xref:System.Numerics.Vector%601?displayProperty=fullName> and all its members</span></span>

<!--

#### Affected APIs

- ``T:System.Numerics.Vector`1``

-->
