---
ms.openlocfilehash: de35df21d1887bc95a3106edba312c53daad8b68
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654734"
---
### <a name="netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5"></a><span data-ttu-id="d349d-101">NETCOREAPP3_1 symbole de préprocesseur n’est pas défini lors du ciblage de .NET 5</span><span class="sxs-lookup"><span data-stu-id="d349d-101">NETCOREAPP3_1 preprocessor symbol is not defined when targeting .NET 5</span></span>

<span data-ttu-id="d349d-102">Dans .NET 5,0 RC2 et versions ultérieures, les projets ne définissent plus les symboles de préprocesseur pour les versions antérieures, mais uniquement pour la version qu’ils ciblent.</span><span class="sxs-lookup"><span data-stu-id="d349d-102">In .NET 5.0 RC2 and later versions, projects no longer define preprocessor symbols for earlier versions, but only for the version that they target.</span></span> <span data-ttu-id="d349d-103">Il s’agit du même comportement que .NET Core 1,0-3,1.</span><span class="sxs-lookup"><span data-stu-id="d349d-103">This is the same behavior as .NET Core 1.0 - 3.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d349d-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d349d-104">Version introduced</span></span>

<span data-ttu-id="d349d-105">5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="d349d-105">5.0 RC2</span></span>

#### <a name="change-description"></a><span data-ttu-id="d349d-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="d349d-106">Change description</span></span>

<span data-ttu-id="d349d-107">Dans .NET 5,0 Preview 7 à RC1, les projets qui ciblent `net5.0` définissent à la fois les `NETCOREAPP3_1` `NET5_0` symboles de préprocesseur et.</span><span class="sxs-lookup"><span data-stu-id="d349d-107">In .NET 5.0 preview 7 through RC1, projects that target `net5.0` define both `NETCOREAPP3_1` and `NET5_0` preprocessor symbols.</span></span> <span data-ttu-id="d349d-108">L’objectif de ce changement de comportement était que depuis .NET 5,0, les symboles de compilation conditionnelle [seraient cumulatifs](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md#preprocessor-symbols).</span><span class="sxs-lookup"><span data-stu-id="d349d-108">The intent behind this behavior change was that starting with .NET 5.0, conditional compilation [symbols would be cumulative](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md#preprocessor-symbols).</span></span>

<span data-ttu-id="d349d-109">Dans .NET 5,0 RC2 et versions ultérieures, les projets ne définissent que des symboles pour les monikers du Framework cible (TFM) qu’il cible et non pour les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="d349d-109">In .NET 5.0 RC2 and later, projects only define symbols for the target framework monikers (TFM) that it targets and not for any earlier versions.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d349d-110">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="d349d-110">Reason for change</span></span>

<span data-ttu-id="d349d-111">La modification de Preview 7 a été annulée en raison de commentaires des clients.</span><span class="sxs-lookup"><span data-stu-id="d349d-111">The change from preview 7 was reverted due to customer feedback.</span></span> <span data-ttu-id="d349d-112">En définissant des symboles pour les versions antérieures, les clients sont surpris et confus, et certains supposés qu’il s’agissait d’un bogue dans le compilateur C#.</span><span class="sxs-lookup"><span data-stu-id="d349d-112">Defining symbols for earlier versions surprised and confused customers, and some assumed it was a bug in the C# compiler.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d349d-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d349d-113">Recommended action</span></span>

<span data-ttu-id="d349d-114">Assurez-vous que votre `#if` logique ne suppose pas que `NETCOREAPP3_1` est défini lorsque le projet cible `net5.0` ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="d349d-114">Make sure that your `#if` logic doesn't assume that `NETCOREAPP3_1` is defined when the project targets `net5.0` or higher.</span></span> <span data-ttu-id="d349d-115">Au lieu de cela, supposons que `NETCOREAPP3_1` est défini uniquement lorsque le projet est explicitement ciblé `netcoreapp3.1` .</span><span class="sxs-lookup"><span data-stu-id="d349d-115">Instead, assume that `NETCOREAPP3_1` is only defined when the project explicitly targets `netcoreapp3.1`.</span></span>

<span data-ttu-id="d349d-116">Par exemple, si votre projet est multiciblé pour .NET Core 2,1 et .NET Core 3,1 et que vous appelez des API qui ont été introduites dans .NET Core 3,1, votre `#if` logique doit ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="d349d-116">For example, if your project multitargets for .NET Core 2.1 and .NET Core 3.1 and you call APIs that were introduced in .NET Core 3.1, your `#if` logic should look as follows:</span></span>

```csharp
#if NETCOREAPP2_1 || NETCOREAPP3_0
    // Fallback behavior for old versions.
#elif NETCOREAPP
    // Behavior for .NET Core 3.1 and later.
#endif
```

#### <a name="category"></a><span data-ttu-id="d349d-117">Category</span><span class="sxs-lookup"><span data-stu-id="d349d-117">Category</span></span>

<span data-ttu-id="d349d-118">MSBuild</span><span class="sxs-lookup"><span data-stu-id="d349d-118">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d349d-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="d349d-119">Affected APIs</span></span>

<span data-ttu-id="d349d-120">N/A</span><span class="sxs-lookup"><span data-stu-id="d349d-120">N/A</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
