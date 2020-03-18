---
ms.openlocfilehash: 1d8bcaf68d44f27642048c1c207b52c55b604690
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902062"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a><span data-ttu-id="f90a1-101">SignalR: HandshakeProtocol.SuccessHandshakeData remplacé</span><span class="sxs-lookup"><span data-stu-id="f90a1-101">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>

<span data-ttu-id="f90a1-102">Le champ [HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) a été enlevé et remplacé par une méthode d’aide `IHubProtocol`qui génère une réponse de poignée de main réussie étant donné un spécifique .</span><span class="sxs-lookup"><span data-stu-id="f90a1-102">The [HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) field was removed and replaced with a helper method that generates a successful handshake response given a specific `IHubProtocol`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f90a1-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f90a1-103">Version introduced</span></span>

<span data-ttu-id="f90a1-104">3.0</span><span class="sxs-lookup"><span data-stu-id="f90a1-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f90a1-105">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="f90a1-105">Old behavior</span></span>

<span data-ttu-id="f90a1-106">`HandshakeProtocol.SuccessHandshakeData`était `public static ReadOnlyMemory<byte>` un champ.</span><span class="sxs-lookup"><span data-stu-id="f90a1-106">`HandshakeProtocol.SuccessHandshakeData` was a `public static ReadOnlyMemory<byte>` field.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f90a1-107">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="f90a1-107">New behavior</span></span>

<span data-ttu-id="f90a1-108">`HandshakeProtocol.SuccessHandshakeData`a été remplacé `static` `GetSuccessfulHandshake(IHubProtocol protocol)` par une `ReadOnlyMemory<byte>` méthode qui renvoie un basé sur le protocole spécifié.</span><span class="sxs-lookup"><span data-stu-id="f90a1-108">`HandshakeProtocol.SuccessHandshakeData` has been replaced by a `static` `GetSuccessfulHandshake(IHubProtocol protocol)` method that returns a `ReadOnlyMemory<byte>` based on the specified protocol.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f90a1-109">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="f90a1-109">Reason for change</span></span>

<span data-ttu-id="f90a1-110">D’autres champs ont été ajoutés à la _réponse_ de poignée de main qui ne sont pas constantes et changent selon le protocole choisi.</span><span class="sxs-lookup"><span data-stu-id="f90a1-110">Additional fields were added to the handshake _response_ that are non-constant and change depending on the selected protocol.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f90a1-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="f90a1-111">Recommended action</span></span>

<span data-ttu-id="f90a1-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f90a1-112">None.</span></span> <span data-ttu-id="f90a1-113">Ce type n’est pas conçu pour une utilisation à partir du code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f90a1-113">This type isn't designed for use from user code.</span></span> <span data-ttu-id="f90a1-114">C’est, `public`de sorte qu’il peut être partagé entre le serveur SignalR et le client.</span><span class="sxs-lookup"><span data-stu-id="f90a1-114">It's `public`, so it can be shared between the SignalR server and client.</span></span> <span data-ttu-id="f90a1-115">Il peut également être utilisé par les clients SignalR client écrit en .NET.</span><span class="sxs-lookup"><span data-stu-id="f90a1-115">It may also be used by customer SignalR clients written in .NET.</span></span> <span data-ttu-id="f90a1-116">**Les utilisateurs** de SignalR ne devraient pas être affectés par ce changement.</span><span class="sxs-lookup"><span data-stu-id="f90a1-116">**Users** of SignalR shouldn't be affected by this change.</span></span>

#### <a name="category"></a><span data-ttu-id="f90a1-117">Category</span><span class="sxs-lookup"><span data-stu-id="f90a1-117">Category</span></span>

<span data-ttu-id="f90a1-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f90a1-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f90a1-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="f90a1-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
