---
title: 'Modification avec rupture : Socket. LocalEndPoint est mis à jour après l’appel de SendToAsync'
description: Découvrez la modification avec rupture dans .NET 5,0 où SendToAsync met à jour la valeur de la propriété de point de terminaison local à l’adresse locale du Socket.
ms.date: 10/18/2020
ms.openlocfilehash: 53d7da350eac6e65832012331044427fd90fe796
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760931"
---
# <a name="socketlocalendpoint-is-updated-after-calling-sendtoasync"></a><span data-ttu-id="7ca3b-103">Socket. LocalEndPoint est mis à jour après l’appel de SendToAsync</span><span class="sxs-lookup"><span data-stu-id="7ca3b-103">Socket.LocalEndPoint is updated after calling SendToAsync</span></span>

<span data-ttu-id="7ca3b-104"><xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> met à jour la valeur de la <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> propriété avec l’adresse locale du Socket.</span><span class="sxs-lookup"><span data-stu-id="7ca3b-104"><xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> now updates the value of the <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> property to the socket's local address.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="7ca3b-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="7ca3b-105">Version introduced</span></span>

<span data-ttu-id="7ca3b-106">5.0</span><span class="sxs-lookup"><span data-stu-id="7ca3b-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="7ca3b-107">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="7ca3b-107">Change description</span></span>

<span data-ttu-id="7ca3b-108">Dans les versions précédentes de .NET, <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> ne modifie pas la valeur de la <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> propriété sur l’instance de Socket.</span><span class="sxs-lookup"><span data-stu-id="7ca3b-108">In previous .NET versions, <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> does not alter the value of the <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> property on the socket instance.</span></span> <span data-ttu-id="7ca3b-109">À compter de .NET 5,0, lorsque <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> se termine avec succès, la valeur de <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> est l’adresse locale du socket lié implicitement.</span><span class="sxs-lookup"><span data-stu-id="7ca3b-109">Starting in .NET 5.0, when <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> successfully completes, the value of <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> is the implicitly bound socket's local address.</span></span> <span data-ttu-id="7ca3b-110">Ce nouveau comportement est cohérent avec le comportement de <xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> et <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)> / <xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)> .</span><span class="sxs-lookup"><span data-stu-id="7ca3b-110">This new behavior is consistent with the behavior of <xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> and <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)>/<xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)>.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="7ca3b-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="7ca3b-111">Reason for change</span></span>

<span data-ttu-id="7ca3b-112">Cette modification [corrige un bogue](https://github.com/dotnet/runtime/issues/915) et rend le comportement cohérent entre les `SendTo` variantes.</span><span class="sxs-lookup"><span data-stu-id="7ca3b-112">This change [fixes a bug](https://github.com/dotnet/runtime/issues/915) and makes the behavior consistent across `SendTo` variants.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="7ca3b-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="7ca3b-113">Recommended action</span></span>

<span data-ttu-id="7ca3b-114">Modifiez le code qui suppose que <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> ne modifiera pas la valeur de <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7ca3b-114">Alter any code that assumes that <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> won't alter the value of <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="7ca3b-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="7ca3b-115">Affected APIs</span></span>

- <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)`

### Category

Networking

-->
