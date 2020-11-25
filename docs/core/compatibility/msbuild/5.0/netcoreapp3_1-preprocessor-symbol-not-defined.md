---
title: 'Modification avec rupture : le symbole de préprocesseur NETCOREAPP3_1 n’est pas défini lors du ciblage de .NET 5'
description: Découvrez la modification avec rupture dans .NET 5,0 où les projets ne définissent plus de symboles de préprocesseur pour les versions antérieures.
ms.date: 09/17/2020
ms.openlocfilehash: 61a5e4fce258d2be3d584318e154bb752b88ebe1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760940"
---
# <a name="netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5"></a><span data-ttu-id="3c0a1-103">NETCOREAPP3_1 symbole de préprocesseur n’est pas défini lors du ciblage de .NET 5</span><span class="sxs-lookup"><span data-stu-id="3c0a1-103">NETCOREAPP3_1 preprocessor symbol is not defined when targeting .NET 5</span></span>

<span data-ttu-id="3c0a1-104">Dans .NET 5,0 RC2 et versions ultérieures, les projets ne définissent plus les symboles de préprocesseur pour les versions antérieures, mais uniquement pour la version qu’ils ciblent.</span><span class="sxs-lookup"><span data-stu-id="3c0a1-104">In .NET 5.0 RC2 and later versions, projects no longer define preprocessor symbols for earlier versions, but only for the version that they target.</span></span> <span data-ttu-id="3c0a1-105">Il s’agit du même comportement que .NET Core 1,0-3,1.</span><span class="sxs-lookup"><span data-stu-id="3c0a1-105">This is the same behavior as .NET Core 1.0 - 3.1.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="3c0a1-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="3c0a1-106">Version introduced</span></span>

<span data-ttu-id="3c0a1-107">5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="3c0a1-107">5.0 RC2</span></span>

## <a name="change-description"></a><span data-ttu-id="3c0a1-108">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="3c0a1-108">Change description</span></span>

<span data-ttu-id="3c0a1-109">Dans .NET 5,0 Preview 7 à RC1, les projets qui ciblent `net5.0` définissent à la fois les `NETCOREAPP3_1` `NET5_0` symboles de préprocesseur et.</span><span class="sxs-lookup"><span data-stu-id="3c0a1-109">In .NET 5.0 preview 7 through RC1, projects that target `net5.0` define both `NETCOREAPP3_1` and `NET5_0` preprocessor symbols.</span></span> <span data-ttu-id="3c0a1-110">L’objectif de ce changement de comportement était que depuis .NET 5,0, les symboles de compilation conditionnelle [seraient cumulatifs](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md#preprocessor-symbols).</span><span class="sxs-lookup"><span data-stu-id="3c0a1-110">The intent behind this behavior change was that starting with .NET 5.0, conditional compilation [symbols would be cumulative](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md#preprocessor-symbols).</span></span>

<span data-ttu-id="3c0a1-111">Dans .NET 5,0 RC2 et versions ultérieures, les projets ne définissent que des symboles pour les monikers du Framework cible (TFM) qu’il cible et non pour les versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="3c0a1-111">In .NET 5.0 RC2 and later, projects only define symbols for the target framework monikers (TFM) that it targets and not for any earlier versions.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="3c0a1-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="3c0a1-112">Reason for change</span></span>

<span data-ttu-id="3c0a1-113">La modification de Preview 7 a été annulée en raison de commentaires des clients.</span><span class="sxs-lookup"><span data-stu-id="3c0a1-113">The change from preview 7 was reverted due to customer feedback.</span></span> <span data-ttu-id="3c0a1-114">En définissant des symboles pour les versions antérieures, les clients sont surpris et confus, et certains supposés qu’il s’agissait d’un bogue dans le compilateur C#.</span><span class="sxs-lookup"><span data-stu-id="3c0a1-114">Defining symbols for earlier versions surprised and confused customers, and some assumed it was a bug in the C# compiler.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="3c0a1-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="3c0a1-115">Recommended action</span></span>

<span data-ttu-id="3c0a1-116">Assurez-vous que votre `#if` logique ne suppose pas que `NETCOREAPP3_1` est défini lorsque le projet cible `net5.0` ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="3c0a1-116">Make sure that your `#if` logic doesn't assume that `NETCOREAPP3_1` is defined when the project targets `net5.0` or higher.</span></span> <span data-ttu-id="3c0a1-117">Au lieu de cela, supposons que `NETCOREAPP3_1` est défini uniquement lorsque le projet est explicitement ciblé `netcoreapp3.1` .</span><span class="sxs-lookup"><span data-stu-id="3c0a1-117">Instead, assume that `NETCOREAPP3_1` is only defined when the project explicitly targets `netcoreapp3.1`.</span></span>

<span data-ttu-id="3c0a1-118">Par exemple, si votre projet est multiciblé pour .NET Core 2,1 et .NET Core 3,1 et que vous appelez des API qui ont été introduites dans .NET Core 3,1, votre `#if` logique doit ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="3c0a1-118">For example, if your project multitargets for .NET Core 2.1 and .NET Core 3.1 and you call APIs that were introduced in .NET Core 3.1, your `#if` logic should look as follows:</span></span>

```csharp
#if NETCOREAPP2_1 || NETCOREAPP3_0
    // Fallback behavior for old versions.
#elif NETCOREAPP
    // Behavior for .NET Core 3.1 and later.
#endif
```

## <a name="affected-apis"></a><span data-ttu-id="3c0a1-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="3c0a1-119">Affected APIs</span></span>

<span data-ttu-id="3c0a1-120">N/A</span><span class="sxs-lookup"><span data-stu-id="3c0a1-120">N/A</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
