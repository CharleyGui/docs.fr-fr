---
ms.openlocfilehash: 80d13609f1b02ae0ac875b2028e745670bb8f503
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050562"
---
### <a name="frameworkdescriptions-value-is-net-instead-of-net-core"></a><span data-ttu-id="b3be5-101">La valeur de FrameworkDescription est .NET au lieu de .NET Core</span><span class="sxs-lookup"><span data-stu-id="b3be5-101">FrameworkDescription's value is .NET instead of .NET Core</span></span>

<span data-ttu-id="b3be5-102"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> retourne désormais « .NET » au lieu de « .NET Core ».</span><span class="sxs-lookup"><span data-stu-id="b3be5-102"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> now returns ".NET" instead of ".NET Core".</span></span>

#### <a name="change-description"></a><span data-ttu-id="b3be5-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="b3be5-103">Change description</span></span>

<span data-ttu-id="b3be5-104">Dans les versions précédentes de .NET, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> retourne « .net core » dans le cadre de la chaîne de description, par exemple `.NET Core 3.1.1` .</span><span class="sxs-lookup"><span data-stu-id="b3be5-104">In previous .NET versions, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> returns ".NET Core" as part of the description string, for example, `.NET Core 3.1.1`.</span></span>

<span data-ttu-id="b3be5-105">À compter de .NET 5,0, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> retourne « .net » dans le cadre de la chaîne de description, par exemple `.NET 5.0.0` .</span><span class="sxs-lookup"><span data-stu-id="b3be5-105">Starting in .NET 5.0, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> returns ".NET" as part of the description string, for example, `.NET 5.0.0`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b3be5-106">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="b3be5-106">Reason for change</span></span>

<span data-ttu-id="b3be5-107">Avec .NET 5, `netcoreapp` est remplacé par `net` comme moniker de Framework cible courts.</span><span class="sxs-lookup"><span data-stu-id="b3be5-107">With .NET 5, `netcoreapp` is replaced by `net` as the short target-framework moniker.</span></span> <span data-ttu-id="b3be5-108">Pour des fins de cohérence, la description de l’infrastructure a également été mise à jour.</span><span class="sxs-lookup"><span data-stu-id="b3be5-108">For consistency, the framework's description has also been updated.</span></span> <span data-ttu-id="b3be5-109">La modification est cosmétique, car `FrameworkName` n’est pas encodé ailleurs que dans la <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="b3be5-109">The change is cosmetic, as the `FrameworkName` isn't encoded anywhere else than in the <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> property.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b3be5-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="b3be5-110">Version introduced</span></span>

<span data-ttu-id="b3be5-111">5.0</span><span class="sxs-lookup"><span data-stu-id="b3be5-111">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b3be5-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="b3be5-112">Recommended action</span></span>

<span data-ttu-id="b3be5-113">Mettez à jour le code qui recherche « .NET Core » dans la chaîne retournée par <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription> .</span><span class="sxs-lookup"><span data-stu-id="b3be5-113">Update any code that searches for ".NET Core" in the string returned by <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription>.</span></span>

#### <a name="category"></a><span data-ttu-id="b3be5-114">Category</span><span class="sxs-lookup"><span data-stu-id="b3be5-114">Category</span></span>

<span data-ttu-id="b3be5-115">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="b3be5-115">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b3be5-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="b3be5-116">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
