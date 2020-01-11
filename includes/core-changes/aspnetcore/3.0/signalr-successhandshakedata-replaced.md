---
ms.openlocfilehash: 1d8bcaf68d44f27642048c1c207b52c55b604690
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75902062"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a><span data-ttu-id="a8d0f-101">Signalr : HandshakeProtocol. SuccessHandshakeData remplacé</span><span class="sxs-lookup"><span data-stu-id="a8d0f-101">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>

<span data-ttu-id="a8d0f-102">Le champ [HandshakeProtocol. SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) a été supprimé et remplacé par une méthode d’assistance qui génère une réponse de négociation réussie en fonction d’un `IHubProtocol`spécifique.</span><span class="sxs-lookup"><span data-stu-id="a8d0f-102">The [HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) field was removed and replaced with a helper method that generates a successful handshake response given a specific `IHubProtocol`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a8d0f-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="a8d0f-103">Version introduced</span></span>

<span data-ttu-id="a8d0f-104">3.0</span><span class="sxs-lookup"><span data-stu-id="a8d0f-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a8d0f-105">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="a8d0f-105">Old behavior</span></span>

<span data-ttu-id="a8d0f-106">`HandshakeProtocol.SuccessHandshakeData` était un champ de `public static ReadOnlyMemory<byte>`.</span><span class="sxs-lookup"><span data-stu-id="a8d0f-106">`HandshakeProtocol.SuccessHandshakeData` was a `public static ReadOnlyMemory<byte>` field.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a8d0f-107">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="a8d0f-107">New behavior</span></span>

<span data-ttu-id="a8d0f-108">`HandshakeProtocol.SuccessHandshakeData` a été remplacé par une méthode de `GetSuccessfulHandshake(IHubProtocol protocol)` `static` qui retourne une `ReadOnlyMemory<byte>` basée sur le protocole spécifié.</span><span class="sxs-lookup"><span data-stu-id="a8d0f-108">`HandshakeProtocol.SuccessHandshakeData` has been replaced by a `static` `GetSuccessfulHandshake(IHubProtocol protocol)` method that returns a `ReadOnlyMemory<byte>` based on the specified protocol.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a8d0f-109">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="a8d0f-109">Reason for change</span></span>

<span data-ttu-id="a8d0f-110">Des champs supplémentaires ont été ajoutés à la _réponse_ de négociation qui sont non constantes et changent selon le protocole sélectionné.</span><span class="sxs-lookup"><span data-stu-id="a8d0f-110">Additional fields were added to the handshake _response_ that are non-constant and change depending on the selected protocol.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a8d0f-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="a8d0f-111">Recommended action</span></span>

<span data-ttu-id="a8d0f-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a8d0f-112">None.</span></span> <span data-ttu-id="a8d0f-113">Ce type n’est pas conçu pour être utilisé à partir du code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a8d0f-113">This type isn't designed for use from user code.</span></span> <span data-ttu-id="a8d0f-114">`public`, il peut être partagé entre le serveur Signalr et le client.</span><span class="sxs-lookup"><span data-stu-id="a8d0f-114">It's `public`, so it can be shared between the SignalR server and client.</span></span> <span data-ttu-id="a8d0f-115">Il peut également être utilisé par les clients Signalr de clients écrits en .NET.</span><span class="sxs-lookup"><span data-stu-id="a8d0f-115">It may also be used by customer SignalR clients written in .NET.</span></span> <span data-ttu-id="a8d0f-116">**Les utilisateurs** de signalr ne doivent pas être affectés par cette modification.</span><span class="sxs-lookup"><span data-stu-id="a8d0f-116">**Users** of SignalR shouldn't be affected by this change.</span></span>

#### <a name="category"></a><span data-ttu-id="a8d0f-117">Catégorie</span><span class="sxs-lookup"><span data-stu-id="a8d0f-117">Category</span></span>

<span data-ttu-id="a8d0f-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a8d0f-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a8d0f-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="a8d0f-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
