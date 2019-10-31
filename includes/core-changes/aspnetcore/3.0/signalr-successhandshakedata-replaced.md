---
ms.openlocfilehash: e9278320ee3fdf9e6b89698d187f047c309ea791
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198423"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a><span data-ttu-id="7a927-101">Signalr : HandshakeProtocol. SuccessHandshakeData remplacé</span><span class="sxs-lookup"><span data-stu-id="7a927-101">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>

<span data-ttu-id="7a927-102">Le champ [HandshakeProtocol. SuccessHandshakeData](https://github.com/aspnet/AspNetCore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) a été supprimé et remplacé par une méthode d’assistance qui génère une réponse de négociation réussie en fonction d’un `IHubProtocol`spécifique.</span><span class="sxs-lookup"><span data-stu-id="7a927-102">The [HandshakeProtocol.SuccessHandshakeData](https://github.com/aspnet/AspNetCore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) field was removed and replaced with a helper method that generates a successful handshake response given a specific `IHubProtocol`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7a927-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="7a927-103">Version introduced</span></span>

<span data-ttu-id="7a927-104">3,0</span><span class="sxs-lookup"><span data-stu-id="7a927-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="7a927-105">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="7a927-105">Old behavior</span></span>

<span data-ttu-id="7a927-106">`HandshakeProtocol.SuccessHandshakeData` était un champ `public static ReadOnlyMemory<byte>`.</span><span class="sxs-lookup"><span data-stu-id="7a927-106">`HandshakeProtocol.SuccessHandshakeData` was a `public static ReadOnlyMemory<byte>` field.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="7a927-107">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="7a927-107">New behavior</span></span>

<span data-ttu-id="7a927-108">`HandshakeProtocol.SuccessHandshakeData` a été remplacé par une méthode `static` `GetSuccessfulHandshake(IHubProtocol protocol)` qui retourne un `ReadOnlyMemory<byte>` basé sur le protocole spécifié.</span><span class="sxs-lookup"><span data-stu-id="7a927-108">`HandshakeProtocol.SuccessHandshakeData` has been replaced by a `static` `GetSuccessfulHandshake(IHubProtocol protocol)` method that returns a `ReadOnlyMemory<byte>` based on the specified protocol.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7a927-109">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="7a927-109">Reason for change</span></span>

<span data-ttu-id="7a927-110">Des champs supplémentaires ont été ajoutés à la _réponse_ de négociation qui sont non constantes et changent selon le protocole sélectionné.</span><span class="sxs-lookup"><span data-stu-id="7a927-110">Additional fields were added to the handshake _response_ that are non-constant and change depending on the selected protocol.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7a927-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="7a927-111">Recommended action</span></span>

<span data-ttu-id="7a927-112">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="7a927-112">None.</span></span> <span data-ttu-id="7a927-113">Ce type n’est pas conçu pour être utilisé à partir du code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7a927-113">This type isn't designed for use from user code.</span></span> <span data-ttu-id="7a927-114">`public`, il peut être partagé entre le serveur Signalr et le client.</span><span class="sxs-lookup"><span data-stu-id="7a927-114">It's `public`, so it can be shared between the SignalR server and client.</span></span> <span data-ttu-id="7a927-115">Il peut également être utilisé par les clients Signalr de clients écrits en .NET.</span><span class="sxs-lookup"><span data-stu-id="7a927-115">It may also be used by customer SignalR clients written in .NET.</span></span> <span data-ttu-id="7a927-116">**Les utilisateurs** de signalr ne doivent pas être affectés par cette modification.</span><span class="sxs-lookup"><span data-stu-id="7a927-116">**Users** of SignalR shouldn't be affected by this change.</span></span>

#### <a name="category"></a><span data-ttu-id="7a927-117">Category</span><span class="sxs-lookup"><span data-stu-id="7a927-117">Category</span></span>

<span data-ttu-id="7a927-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7a927-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7a927-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="7a927-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
