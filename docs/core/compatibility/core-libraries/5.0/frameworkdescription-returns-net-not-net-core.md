---
title: 'Modification avec rupture : la valeur de FrameworkDescription est .NET au lieu de .NET Core'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où RuntimeInformation. FrameworkDescription retourne désormais « .NET » au lieu de « .NET Core ».
ms.date: 11/01/2020
ms.openlocfilehash: 3925fb092135c26291e1e60b99f359974d21553c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761069"
---
# <a name="frameworkdescriptions-value-is-net-instead-of-net-core"></a><span data-ttu-id="f409c-103">La valeur de FrameworkDescription est .NET au lieu de .NET Core</span><span class="sxs-lookup"><span data-stu-id="f409c-103">FrameworkDescription's value is .NET instead of .NET Core</span></span>

<span data-ttu-id="f409c-104"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> retourne désormais « .NET » au lieu de « .NET Core ».</span><span class="sxs-lookup"><span data-stu-id="f409c-104"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> now returns ".NET" instead of ".NET Core".</span></span>

## <a name="change-description"></a><span data-ttu-id="f409c-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="f409c-105">Change description</span></span>

<span data-ttu-id="f409c-106">Dans les versions précédentes de .NET, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> retourne « .net core » dans le cadre de la chaîne de description, par exemple `.NET Core 3.1.1` .</span><span class="sxs-lookup"><span data-stu-id="f409c-106">In previous .NET versions, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> returns ".NET Core" as part of the description string, for example, `.NET Core 3.1.1`.</span></span>

<span data-ttu-id="f409c-107">À compter de .NET 5,0, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> retourne « .net » dans le cadre de la chaîne de description, par exemple `.NET 5.0.0` .</span><span class="sxs-lookup"><span data-stu-id="f409c-107">Starting in .NET 5.0, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> returns ".NET" as part of the description string, for example, `.NET 5.0.0`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="f409c-108">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="f409c-108">Reason for change</span></span>

<span data-ttu-id="f409c-109">Avec .NET 5, `netcoreapp` est remplacé par `net` comme moniker de Framework cible courts.</span><span class="sxs-lookup"><span data-stu-id="f409c-109">With .NET 5, `netcoreapp` is replaced by `net` as the short target-framework moniker.</span></span> <span data-ttu-id="f409c-110">Pour des fins de cohérence, la description de l’infrastructure a également été mise à jour.</span><span class="sxs-lookup"><span data-stu-id="f409c-110">For consistency, the framework's description has also been updated.</span></span> <span data-ttu-id="f409c-111">La modification est cosmétique, car `FrameworkName` n’est pas encodé ailleurs que dans la <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="f409c-111">The change is cosmetic, as the `FrameworkName` isn't encoded anywhere else than in the <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> property.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="f409c-112">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f409c-112">Version introduced</span></span>

<span data-ttu-id="f409c-113">5.0</span><span class="sxs-lookup"><span data-stu-id="f409c-113">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f409c-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="f409c-114">Recommended action</span></span>

<span data-ttu-id="f409c-115">Mettez à jour le code qui recherche « .NET Core » dans la chaîne retournée par <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription> .</span><span class="sxs-lookup"><span data-stu-id="f409c-115">Update any code that searches for ".NET Core" in the string returned by <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f409c-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="f409c-116">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
