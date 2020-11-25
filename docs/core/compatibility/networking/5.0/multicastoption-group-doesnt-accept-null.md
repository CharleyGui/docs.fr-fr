---
title: 'Modification avec rupture : MulticastOption. Group n’accepte pas de valeur null'
description: Découvrez la modification avec rupture dans .NET 5,0 où MulticastOption. Group n’accepte plus de valeur null.
ms.date: 08/18/2020
ms.openlocfilehash: 164ac8c2c8dd14f9e0758017e54eeb377f88a7e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760927"
---
# <a name="multicastoptiongroup-doesnt-accept-a-null-value"></a><span data-ttu-id="69f78-103">MulticastOption. Group n’accepte pas de valeur null</span><span class="sxs-lookup"><span data-stu-id="69f78-103">MulticastOption.Group doesn't accept a null value</span></span>

<span data-ttu-id="69f78-104"><xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> n’accepte plus la valeur `null` .</span><span class="sxs-lookup"><span data-stu-id="69f78-104"><xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> no longer accepts a value of `null`.</span></span> <span data-ttu-id="69f78-105">Si vous affectez à la propriété la valeur `null` , une <xref:System.ArgumentNullException> exception est levée.</span><span class="sxs-lookup"><span data-stu-id="69f78-105">If you set the property to `null`, an <xref:System.ArgumentNullException> is thrown.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="69f78-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="69f78-106">Version introduced</span></span>

<span data-ttu-id="69f78-107">5.0</span><span class="sxs-lookup"><span data-stu-id="69f78-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="69f78-108">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="69f78-108">Change description</span></span>

<span data-ttu-id="69f78-109">Dans les versions précédentes de .NET, vous pouvez affecter <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> à la propriété la valeur `null` .</span><span class="sxs-lookup"><span data-stu-id="69f78-109">In previous versions of .NET, you can set the <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> property to `null`.</span></span> <span data-ttu-id="69f78-110">Si le <xref:System.Net.Sockets.MulticastOption> est passé par la suite à <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> , le runtime lève une exception <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="69f78-110">If the <xref:System.Net.Sockets.MulticastOption> is later passed to <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType>, the runtime throws a <xref:System.NullReferenceException>.</span></span>

<span data-ttu-id="69f78-111">Dans .NET 5,0 et versions ultérieures, une <xref:System.ArgumentNullException> exception est levée si vous affectez à la propriété la valeur `null` .</span><span class="sxs-lookup"><span data-stu-id="69f78-111">In .NET 5.0 and later, an <xref:System.ArgumentNullException> is thrown if you set the property to `null`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="69f78-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="69f78-112">Reason for change</span></span>

<span data-ttu-id="69f78-113">Pour être cohérente avec les règles de conception de l’infrastructure, la propriété a été mise à jour pour lever une <xref:System.ArgumentNullException> si la valeur est `null` .</span><span class="sxs-lookup"><span data-stu-id="69f78-113">To be consistent with the Framework Design Guidelines, the property has been updated to throw an <xref:System.ArgumentNullException> if the value is `null`.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="69f78-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="69f78-114">Recommended action</span></span>

<span data-ttu-id="69f78-115">Assurez-vous que vous n’affectez pas la valeur <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> `null` .</span><span class="sxs-lookup"><span data-stu-id="69f78-115">Make sure that you don't set <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> to `null`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="69f78-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="69f78-116">Affected APIs</span></span>

- <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Net.Sockets.MulticastOption.Group`

### Category

Networking

-->
