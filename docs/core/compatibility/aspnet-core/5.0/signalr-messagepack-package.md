---
title: 'Modification avec rupture : Signalr : protocole MessagePack Hub déplacé vers le package MessagePack 2. x'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 Signalr : le protocole MessagePack Hub a été déplacé vers le package MessagePack 2. x'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 1e666c40d7046233c9fb06af819b901fd1251b06
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761261"
---
# <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a><span data-ttu-id="d9226-103">Signalr : protocole MessagePack Hub déplacé vers le package MessagePack 2. x</span><span class="sxs-lookup"><span data-stu-id="d9226-103">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>

<span data-ttu-id="d9226-104">Le Protocole ASP.NET Core Signalr [MessagePack Hub](/aspnet/core/signalr/messagepackhubprotocol) utilise le [package NuGet MessagePack](https://www.nuget.org/packages/MessagePack) pour la sérialisation MessagePack.</span><span class="sxs-lookup"><span data-stu-id="d9226-104">The ASP.NET Core SignalR [MessagePack Hub Protocol](/aspnet/core/signalr/messagepackhubprotocol) uses the [MessagePack NuGet package](https://www.nuget.org/packages/MessagePack) for MessagePack serialization.</span></span> <span data-ttu-id="d9226-105">ASP.NET Core 5,0 met à niveau le package de 1. x vers la dernière version du package 2. x.</span><span class="sxs-lookup"><span data-stu-id="d9226-105">ASP.NET Core 5.0 upgrades the package from 1.x to the latest 2.x package version.</span></span>

<span data-ttu-id="d9226-106">Pour plus d’informations sur ce problème, consultez [dotnet/aspnetcore # 18692](https://github.com/dotnet/aspnetcore/issues/18692).</span><span class="sxs-lookup"><span data-stu-id="d9226-106">For discussion on this issue, see [dotnet/aspnetcore#18692](https://github.com/dotnet/aspnetcore/issues/18692).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="d9226-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d9226-107">Version introduced</span></span>

<span data-ttu-id="d9226-108">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="d9226-108">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="d9226-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="d9226-109">Old behavior</span></span>

<span data-ttu-id="d9226-110">ASP.NET Core Signalr a utilisé le package MessagePack 1. x pour sérialiser et désérialiser les messages MessagePack.</span><span class="sxs-lookup"><span data-stu-id="d9226-110">ASP.NET Core SignalR used the MessagePack 1.x package to serialize and deserialize MessagePack messages.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="d9226-111">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="d9226-111">New behavior</span></span>

<span data-ttu-id="d9226-112">ASP.NET Core Signalr utilise le package MessagePack 2. x pour sérialiser et désérialiser les messages MessagePack.</span><span class="sxs-lookup"><span data-stu-id="d9226-112">ASP.NET Core SignalR uses the MessagePack 2.x package to serialize and deserialize MessagePack messages.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="d9226-113">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="d9226-113">Reason for change</span></span>

<span data-ttu-id="d9226-114">Les dernières améliorations du package MessagePack 2. x ajoutent des fonctionnalités utiles.</span><span class="sxs-lookup"><span data-stu-id="d9226-114">The latest improvements in the MessagePack 2.x package add useful functionality.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d9226-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d9226-115">Recommended action</span></span>

<span data-ttu-id="d9226-116">Cette modification avec rupture s’applique dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="d9226-116">This breaking change applies when:</span></span>

* <span data-ttu-id="d9226-117">Définition ou configuration des valeurs sur <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions> .</span><span class="sxs-lookup"><span data-stu-id="d9226-117">Setting or configuring values on <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span></span>
* <span data-ttu-id="d9226-118">Utilisation directe des API MessagePack et utilisation du Protocole ASP.NET Core Signalr MessagePack Hub dans le même projet.</span><span class="sxs-lookup"><span data-stu-id="d9226-118">Using the MessagePack APIs directly and using the ASP.NET Core SignalR MessagePack Hub Protocol in the same project.</span></span> <span data-ttu-id="d9226-119">La version la plus récente sera chargée à la place de la version précédente.</span><span class="sxs-lookup"><span data-stu-id="d9226-119">The newer version will be loaded instead of the previous version.</span></span>

<span data-ttu-id="d9226-120">Pour obtenir des conseils sur la migration à partir des auteurs de package, consultez [migration de MessagePack v1. x vers MessagePack v2. x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md).</span><span class="sxs-lookup"><span data-stu-id="d9226-120">For migration guidance from the package authors, see [Migrating from MessagePack v1.x to MessagePack v2.x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md).</span></span> <span data-ttu-id="d9226-121">Certains aspects de la sérialisation et de la désérialisation des messages sont affectés.</span><span class="sxs-lookup"><span data-stu-id="d9226-121">Some aspects of message serialization and deserialization are affected.</span></span> <span data-ttu-id="d9226-122">Plus précisément, il existe des [changements de comportement dans la manière dont les valeurs DateTime sont sérialisées](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).</span><span class="sxs-lookup"><span data-stu-id="d9226-122">Specifically, there are [behavioral changes to how DateTime values are serialized](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="d9226-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="d9226-123">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
