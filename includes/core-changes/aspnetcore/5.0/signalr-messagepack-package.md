---
ms.openlocfilehash: ca0792a3fd05d28cecceac1d644e3e4bf64722bc
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345218"
---
### <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a><span data-ttu-id="a0851-101">SignalR: MessagePack Hub Protocol déplacé à MessagePack 2.x paquet</span><span class="sxs-lookup"><span data-stu-id="a0851-101">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>

<span data-ttu-id="a0851-102">Le protocole ASP.NET Core SignalR [MessagePack Hub](/aspnet/core/signalr/messagepackhubprotocol) utilise le [paquet MessagePack NuGet](https://www.nuget.org/packages/MessagePack) pour la sérialisation De MessagePack.</span><span class="sxs-lookup"><span data-stu-id="a0851-102">The ASP.NET Core SignalR [MessagePack Hub Protocol](/aspnet/core/signalr/messagepackhubprotocol) uses the [MessagePack NuGet package](https://www.nuget.org/packages/MessagePack) for MessagePack serialization.</span></span> <span data-ttu-id="a0851-103">ASP.NET Core 5.0 met à niveau le paquet de 1.x à la dernière version de paquet 2.x.</span><span class="sxs-lookup"><span data-stu-id="a0851-103">ASP.NET Core 5.0 upgrades the package from 1.x to the latest 2.x package version.</span></span>

<span data-ttu-id="a0851-104">Pour discussion sur cette question, voir [dotnet/aspnetcore 18692](https://github.com/dotnet/aspnetcore/issues/18692).</span><span class="sxs-lookup"><span data-stu-id="a0851-104">For discussion on this issue, see [dotnet/aspnetcore#18692](https://github.com/dotnet/aspnetcore/issues/18692).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a0851-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="a0851-105">Version introduced</span></span>

<span data-ttu-id="a0851-106">5.0 Aperçu 1</span><span class="sxs-lookup"><span data-stu-id="a0851-106">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a0851-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="a0851-107">Old behavior</span></span>

<span data-ttu-id="a0851-108">ASP.NET Core SignalR a utilisé le paquet MessagePack 1.x pour sérialiser et déséialiser les messages MessagePack.</span><span class="sxs-lookup"><span data-stu-id="a0851-108">ASP.NET Core SignalR used the MessagePack 1.x package to serialize and deserialize MessagePack messages.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a0851-109">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="a0851-109">New behavior</span></span>

<span data-ttu-id="a0851-110">ASP.NET Core SignalR utilise le paquet MessagePack 2.x pour sérialiser et déséialiser les messages MessagePack.</span><span class="sxs-lookup"><span data-stu-id="a0851-110">ASP.NET Core SignalR uses the MessagePack 2.x package to serialize and deserialize MessagePack messages.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a0851-111">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="a0851-111">Reason for change</span></span>

<span data-ttu-id="a0851-112">Les dernières améliorations apportées au paquet MessagePack 2.x ajoutent des fonctionnalités utiles.</span><span class="sxs-lookup"><span data-stu-id="a0851-112">The latest improvements in the MessagePack 2.x package add useful functionality.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a0851-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="a0851-113">Recommended action</span></span>

<span data-ttu-id="a0851-114">Ce changement de rupture s’applique lorsque :</span><span class="sxs-lookup"><span data-stu-id="a0851-114">This breaking change applies when:</span></span>

* <span data-ttu-id="a0851-115">Définir ou configurer <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>des valeurs sur .</span><span class="sxs-lookup"><span data-stu-id="a0851-115">Setting or configuring values on <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span></span>
* <span data-ttu-id="a0851-116">Utiliser directement les API MessagePack et utiliser le protocole ASP.NET Core SignalR MessagePack Hub dans le même projet.</span><span class="sxs-lookup"><span data-stu-id="a0851-116">Using the MessagePack APIs directly and using the ASP.NET Core SignalR MessagePack Hub Protocol in the same project.</span></span> <span data-ttu-id="a0851-117">La version la plus récente sera chargée au lieu de la version précédente.</span><span class="sxs-lookup"><span data-stu-id="a0851-117">The newer version will be loaded instead of the previous version.</span></span>

<span data-ttu-id="a0851-118">Pour les conseils de migration des auteurs du paquet, voir [Migrating de MessagePack v1.x à MessagePack v2.x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md).</span><span class="sxs-lookup"><span data-stu-id="a0851-118">For migration guidance from the package authors, see [Migrating from MessagePack v1.x to MessagePack v2.x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md).</span></span> <span data-ttu-id="a0851-119">Certains aspects de la sérialisation des messages et de la désétération sont affectés.</span><span class="sxs-lookup"><span data-stu-id="a0851-119">Some aspects of message serialization and deserialization are affected.</span></span> <span data-ttu-id="a0851-120">Plus précisément, il ya [des changements de comportement à la façon dont les valeurs DateTime sont sérialisés](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).</span><span class="sxs-lookup"><span data-stu-id="a0851-120">Specifically, there are [behavioral changes to how DateTime values are serialized](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).</span></span>

#### <a name="category"></a><span data-ttu-id="a0851-121">Category</span><span class="sxs-lookup"><span data-stu-id="a0851-121">Category</span></span>

<span data-ttu-id="a0851-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a0851-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a0851-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="a0851-123">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
