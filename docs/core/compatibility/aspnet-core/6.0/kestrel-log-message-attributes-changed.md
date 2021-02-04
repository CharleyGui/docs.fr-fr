---
title: 'Modification avec rupture : Kestrel : les attributs du message de journal ont été modifiés'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 6,0 intitulée Kestrel : attributs de message de journal modifiés'
author: scottaddie
ms.author: scaddie
ms.date: 02/01/2021
ms.openlocfilehash: 30b03c22a6c85623fec7db14b58b169f887395a0
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2021
ms.locfileid: "99551559"
---
# <a name="kestrel-log-message-attributes-changed"></a><span data-ttu-id="aa269-103">Kestrel : les attributs de message de journal ont été modifiés</span><span class="sxs-lookup"><span data-stu-id="aa269-103">Kestrel: Log message attributes changed</span></span>

<span data-ttu-id="aa269-104">Les ID et les noms des messages du journal Kestrel sont associés.</span><span class="sxs-lookup"><span data-stu-id="aa269-104">Kestrel log messages have associated IDs and names.</span></span> <span data-ttu-id="aa269-105">Ces attributs identifient de manière unique différents types de messages de journal.</span><span class="sxs-lookup"><span data-stu-id="aa269-105">These attributes uniquely identify different kinds of log messages.</span></span> <span data-ttu-id="aa269-106">Certains de ces ID et noms n’ont pas été dupliqués correctement.</span><span class="sxs-lookup"><span data-stu-id="aa269-106">Some of those IDs and names were incorrectly duplicated.</span></span> <span data-ttu-id="aa269-107">Ce problème de duplication est résolu dans ASP.NET Core 6,0.</span><span class="sxs-lookup"><span data-stu-id="aa269-107">This duplication problem is fixed in ASP.NET Core 6.0.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="aa269-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="aa269-108">Version introduced</span></span>

<span data-ttu-id="aa269-109">6.0</span><span class="sxs-lookup"><span data-stu-id="aa269-109">6.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="aa269-110">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="aa269-110">Old behavior</span></span>

<span data-ttu-id="aa269-111">Le tableau suivant indique l’état des messages du journal affectés avant ASP.NET Core 6,0.</span><span class="sxs-lookup"><span data-stu-id="aa269-111">The following table shows the state of the affected log messages before ASP.NET Core 6.0.</span></span>

| <span data-ttu-id="aa269-112">Description du message</span><span class="sxs-lookup"><span data-stu-id="aa269-112">Message description</span></span>                   | <span data-ttu-id="aa269-113">Nom</span><span class="sxs-lookup"><span data-stu-id="aa269-113">Name</span></span>                    | <span data-ttu-id="aa269-114">id</span><span class="sxs-lookup"><span data-stu-id="aa269-114">ID</span></span> |
|---------------------------------------|-------------------------|----|
| <span data-ttu-id="aa269-115">Messages du journal des connexions HTTP/2 fermées</span><span class="sxs-lookup"><span data-stu-id="aa269-115">HTTP/2 connection closed log messages</span></span> | `Http2ConnectionClosed` | <span data-ttu-id="aa269-116">36</span><span class="sxs-lookup"><span data-stu-id="aa269-116">36</span></span> |
| <span data-ttu-id="aa269-117">Images HTTP/2 envoyant des messages de journal</span><span class="sxs-lookup"><span data-stu-id="aa269-117">HTTP/2 frame sending log messages</span></span>     | `Http2FrameReceived`    | <span data-ttu-id="aa269-118">37</span><span class="sxs-lookup"><span data-stu-id="aa269-118">37</span></span> |

## <a name="new-behavior"></a><span data-ttu-id="aa269-119">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="aa269-119">New behavior</span></span>

<span data-ttu-id="aa269-120">Le tableau suivant indique l’état des messages de journal affectés dans ASP.NET Core 6,0.</span><span class="sxs-lookup"><span data-stu-id="aa269-120">The following table shows the state of the affected log messages in ASP.NET Core 6.0.</span></span>

| <span data-ttu-id="aa269-121">Description du message</span><span class="sxs-lookup"><span data-stu-id="aa269-121">Message description</span></span>                   | <span data-ttu-id="aa269-122">Nom</span><span class="sxs-lookup"><span data-stu-id="aa269-122">Name</span></span>                    | <span data-ttu-id="aa269-123">id</span><span class="sxs-lookup"><span data-stu-id="aa269-123">ID</span></span> |
|---------------------------------------|-------------------------|----|
| <span data-ttu-id="aa269-124">Messages du journal des connexions HTTP/2 fermées</span><span class="sxs-lookup"><span data-stu-id="aa269-124">HTTP/2 connection closed log messages</span></span> | `Http2ConnectionClosed` | <span data-ttu-id="aa269-125">48</span><span class="sxs-lookup"><span data-stu-id="aa269-125">48</span></span> |
| <span data-ttu-id="aa269-126">Images HTTP/2 envoyant des messages de journal</span><span class="sxs-lookup"><span data-stu-id="aa269-126">HTTP/2 frame sending log messages</span></span>     | `Http2FrameSending`     | <span data-ttu-id="aa269-127">49</span><span class="sxs-lookup"><span data-stu-id="aa269-127">49</span></span> |

## <a name="reason-for-change"></a><span data-ttu-id="aa269-128">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="aa269-128">Reason for change</span></span>

<span data-ttu-id="aa269-129">Les ID de journal et les noms doivent être uniques afin que différents types de messages puissent être identifiés.</span><span class="sxs-lookup"><span data-stu-id="aa269-129">Log IDs and names should be unique so different message types can be identified.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="aa269-130">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="aa269-130">Recommended action</span></span>

<span data-ttu-id="aa269-131">Si vous avez du code ou une configuration qui fait référence aux anciens ID et noms, mettez à jour ces références pour utiliser les nouveaux ID et noms.</span><span class="sxs-lookup"><span data-stu-id="aa269-131">If you have code or configuration that references the old IDs and names, update those references to use the new IDs and names.</span></span>

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
