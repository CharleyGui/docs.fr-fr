---
ms.openlocfilehash: 8de70b0c445aa48fc4c3249ccfc8c095890fb14c
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050515"
---
### <a name="socketlocalendpoint-is-updated-after-calling-sendtoasync"></a><span data-ttu-id="1c138-101">Socket. LocalEndPoint est mis à jour après l’appel de SendToAsync</span><span class="sxs-lookup"><span data-stu-id="1c138-101">Socket.LocalEndPoint is updated after calling SendToAsync</span></span>

<span data-ttu-id="1c138-102"><xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> met à jour la valeur de la <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> propriété avec l’adresse locale du Socket.</span><span class="sxs-lookup"><span data-stu-id="1c138-102"><xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> now updates the value of the <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> property to the socket's local address.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1c138-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="1c138-103">Version introduced</span></span>

<span data-ttu-id="1c138-104">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="1c138-104">5.0 RC1</span></span>

#### <a name="change-description"></a><span data-ttu-id="1c138-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="1c138-105">Change description</span></span>

<span data-ttu-id="1c138-106">Dans les versions précédentes de .NET, <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> ne modifie pas la valeur de la <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> propriété sur l’instance de Socket.</span><span class="sxs-lookup"><span data-stu-id="1c138-106">In previous .NET versions, <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> does not alter the value of the <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> property on the socket instance.</span></span> <span data-ttu-id="1c138-107">À compter de .NET 5,0, lorsque <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> se termine avec succès, la valeur de <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> est l’adresse locale du socket lié implicitement.</span><span class="sxs-lookup"><span data-stu-id="1c138-107">Starting in .NET 5.0, when <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> successfully completes, the value of <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> is the implicitly bound socket's local address.</span></span> <span data-ttu-id="1c138-108">Ce nouveau comportement est cohérent avec le comportement de <xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> et <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)> / <xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)> .</span><span class="sxs-lookup"><span data-stu-id="1c138-108">This new behavior is consistent with the behavior of <xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> and <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)>/<xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1c138-109">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="1c138-109">Reason for change</span></span>

<span data-ttu-id="1c138-110">Cette modification [corrige un bogue](https://github.com/dotnet/runtime/issues/915) et rend le comportement cohérent entre les `SendTo` variantes.</span><span class="sxs-lookup"><span data-stu-id="1c138-110">This change [fixes a bug](https://github.com/dotnet/runtime/issues/915) and makes the behavior consistent across `SendTo` variants.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1c138-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="1c138-111">Recommended action</span></span>

<span data-ttu-id="1c138-112">Modifiez le code qui suppose que <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> ne modifiera pas la valeur de <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1c138-112">Alter any code that assumes that <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> won't alter the value of <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="1c138-113">Category</span><span class="sxs-lookup"><span data-stu-id="1c138-113">Category</span></span>

<span data-ttu-id="1c138-114">Mise en réseau</span><span class="sxs-lookup"><span data-stu-id="1c138-114">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1c138-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="1c138-115">Affected APIs</span></span>

- <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)`

-->
