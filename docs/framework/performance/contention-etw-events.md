---
title: Événements ETW de conflit-.NET
description: Obtenir des détails sur les événements ETW de conflit, qui sont déclenchés à chaque contention pour les verrous System. Threading. Monitor ou les verrous natifs utilisés par le Runtime.
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
ms.openlocfilehash: a36b091e0896562fffdb66e895d70049ce0667d7
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309597"
---
# <a name="contention-etw-events"></a><span data-ttu-id="3f174-103">Événements ETW de conflit</span><span class="sxs-lookup"><span data-stu-id="3f174-103">Contention ETW events</span></span>

<span data-ttu-id="3f174-104">Les événements de conflit sont déclenchés chaque fois qu’il existe un conflit sur les verrous <xref:System.Threading.Monitor?displayProperty=nameWithType> ou les verrous natifs utilisés par le runtime.</span><span class="sxs-lookup"><span data-stu-id="3f174-104">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="3f174-105">Le conflit se produit quand un thread attend un verrou alors qu’un autre thread possède ce verrou.</span><span class="sxs-lookup"><span data-stu-id="3f174-105">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>

<span data-ttu-id="3f174-106">Le tableau suivant montre le mot clé sous lequel les événements de conflit sont déclenchés, ainsi que le niveau des événements.</span><span class="sxs-lookup"><span data-stu-id="3f174-106">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="3f174-107">Pour plus d’informations, consultez [niveaux et Mots clés ETW du CLR](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3f174-107">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="3f174-108">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="3f174-108">Keyword for raising the event</span></span>|<span data-ttu-id="3f174-109">Level</span><span class="sxs-lookup"><span data-stu-id="3f174-109">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3f174-110">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="3f174-110">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="3f174-111">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="3f174-111">Informational (4)</span></span>|

<span data-ttu-id="3f174-112">Le tableau suivant présente des informations sur les événements :</span><span class="sxs-lookup"><span data-stu-id="3f174-112">The following table shows event information:</span></span>

|<span data-ttu-id="3f174-113">Événement</span><span class="sxs-lookup"><span data-stu-id="3f174-113">Event</span></span>|<span data-ttu-id="3f174-114">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="3f174-114">Event ID</span></span>|<span data-ttu-id="3f174-115">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="3f174-115">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|<span data-ttu-id="3f174-116">81</span><span class="sxs-lookup"><span data-stu-id="3f174-116">81</span></span>|<span data-ttu-id="3f174-117">Le conflit démarre.</span><span class="sxs-lookup"><span data-stu-id="3f174-117">Contention starts.</span></span> <span data-ttu-id="3f174-118">Cet événement n’inclut pas le temps qui s’écoule avant qu’un thread ne commence à attendre l’acquisition d’un verrou. Il est déclenché uniquement quand l’attente commence.</span><span class="sxs-lookup"><span data-stu-id="3f174-118">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|
|`ContentionStop`|<span data-ttu-id="3f174-119">91</span><span class="sxs-lookup"><span data-stu-id="3f174-119">91</span></span>|<span data-ttu-id="3f174-120">Le conflit se termine.</span><span class="sxs-lookup"><span data-stu-id="3f174-120">Contention ends.</span></span>|

<span data-ttu-id="3f174-121">Le tableau suivant présente les données d’événement :</span><span class="sxs-lookup"><span data-stu-id="3f174-121">The following table shows event data:</span></span>

|<span data-ttu-id="3f174-122">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="3f174-122">Field name</span></span>|<span data-ttu-id="3f174-123">Type de données</span><span class="sxs-lookup"><span data-stu-id="3f174-123">Data type</span></span>|<span data-ttu-id="3f174-124">Description</span><span class="sxs-lookup"><span data-stu-id="3f174-124">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="3f174-125">Indicateurs</span><span class="sxs-lookup"><span data-stu-id="3f174-125">Flags</span></span>|<span data-ttu-id="3f174-126">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="3f174-126">win:UInt8</span></span>|<span data-ttu-id="3f174-127">0 pour managé ; 1 pour natif.</span><span class="sxs-lookup"><span data-stu-id="3f174-127">0 for managed; 1 for native.</span></span>|
|<span data-ttu-id="3f174-128">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="3f174-128">ClrInstanceID</span></span>|<span data-ttu-id="3f174-129">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3f174-129">win:UInt16</span></span>|<span data-ttu-id="3f174-130">ID unique de l’instance de CLR.</span><span class="sxs-lookup"><span data-stu-id="3f174-130">Unique ID for the instance of CLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="3f174-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f174-131">See also</span></span>

- [<span data-ttu-id="3f174-132">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="3f174-132">CLR ETW Events</span></span>](clr-etw-events.md)
