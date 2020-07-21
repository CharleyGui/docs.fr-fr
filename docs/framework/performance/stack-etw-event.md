---
title: Événement ETW de pile
description: En savoir plus sur l’événement ETW de pile, qui doit être utilisé conjointement avec d’autres événements pour générer des traces de pile après le déclenchement d’un événement.
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
ms.openlocfilehash: cab496615c4ef17831895b72c8987917e3c06e77
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474135"
---
# <a name="stack-etw-event"></a><span data-ttu-id="b84d5-103">Événement ETW de pile</span><span class="sxs-lookup"><span data-stu-id="b84d5-103">Stack ETW Event</span></span>
<span data-ttu-id="b84d5-104">L’événement de pile doit être utilisé conjointement avec d’autres événements pour générer des arborescences d’appels de procédure après le déclenchement d’un événement.</span><span class="sxs-lookup"><span data-stu-id="b84d5-104">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="b84d5-105">Il est enregistré quand le fournisseur du runtime est activé.</span><span class="sxs-lookup"><span data-stu-id="b84d5-105">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="b84d5-106">Il s’agit d’un événement très fréquent, car il est déclenché à chaque déclenchement d’un autre événement runtime.</span><span class="sxs-lookup"><span data-stu-id="b84d5-106">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="b84d5-107">Pour cette raison, nous vous recommandons d’utiliser cet événement avec précaution.</span><span class="sxs-lookup"><span data-stu-id="b84d5-107">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="b84d5-108">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="b84d5-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="b84d5-109">(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="b84d5-109">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="b84d5-110">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="b84d5-110">Keyword for raising the event</span></span>|<span data-ttu-id="b84d5-111">Level</span><span class="sxs-lookup"><span data-stu-id="b84d5-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="b84d5-112">`StackKeyword` (0x40000000)</span><span class="sxs-lookup"><span data-stu-id="b84d5-112">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="b84d5-113">LogAlways(0)</span><span class="sxs-lookup"><span data-stu-id="b84d5-113">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="b84d5-114">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="b84d5-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="b84d5-115">Événement</span><span class="sxs-lookup"><span data-stu-id="b84d5-115">Event</span></span>|<span data-ttu-id="b84d5-116">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="b84d5-116">Event ID</span></span>|<span data-ttu-id="b84d5-117">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="b84d5-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="b84d5-118">82</span><span class="sxs-lookup"><span data-stu-id="b84d5-118">82</span></span>|<span data-ttu-id="b84d5-119">Conjointement avec d’autres événements pour générer les arborescences des appels de procédure après un événement.</span><span class="sxs-lookup"><span data-stu-id="b84d5-119">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="b84d5-120">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="b84d5-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="b84d5-121">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="b84d5-121">Field name</span></span>|<span data-ttu-id="b84d5-122">Type de données</span><span class="sxs-lookup"><span data-stu-id="b84d5-122">Data Type</span></span>|<span data-ttu-id="b84d5-123">Description</span><span class="sxs-lookup"><span data-stu-id="b84d5-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="b84d5-124">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b84d5-124">ClrInstanceID</span></span>|<span data-ttu-id="b84d5-125">win:Uint16</span><span class="sxs-lookup"><span data-stu-id="b84d5-125">win:Uint16</span></span>|<span data-ttu-id="b84d5-126">Identificateur de runtime unique.</span><span class="sxs-lookup"><span data-stu-id="b84d5-126">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="b84d5-127">Reserved1</span><span class="sxs-lookup"><span data-stu-id="b84d5-127">Reserved1</span></span>|<span data-ttu-id="b84d5-128">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="b84d5-128">win:UInt8</span></span>|<span data-ttu-id="b84d5-129">Réservé.</span><span class="sxs-lookup"><span data-stu-id="b84d5-129">Reserved.</span></span>|  
|<span data-ttu-id="b84d5-130">Reserved2</span><span class="sxs-lookup"><span data-stu-id="b84d5-130">Reserved2</span></span>|<span data-ttu-id="b84d5-131">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="b84d5-131">win:UInt8</span></span>|<span data-ttu-id="b84d5-132">Réservé.</span><span class="sxs-lookup"><span data-stu-id="b84d5-132">Reserved.</span></span>|  
|<span data-ttu-id="b84d5-133">FrameCount</span><span class="sxs-lookup"><span data-stu-id="b84d5-133">FrameCount</span></span>|<span data-ttu-id="b84d5-134">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="b84d5-134">win:UInt32</span></span>|<span data-ttu-id="b84d5-135">Nombre de frames dans l’arborescence des appels de procédure.</span><span class="sxs-lookup"><span data-stu-id="b84d5-135">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="b84d5-136">Pile</span><span class="sxs-lookup"><span data-stu-id="b84d5-136">Stack</span></span>|<span data-ttu-id="b84d5-137">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="b84d5-137">win:Pointer</span></span>|<span data-ttu-id="b84d5-138">Colonnes de pointeurs d’instruction.</span><span class="sxs-lookup"><span data-stu-id="b84d5-138">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b84d5-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b84d5-139">See also</span></span>

- [<span data-ttu-id="b84d5-140">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="b84d5-140">CLR ETW Events</span></span>](clr-etw-events.md)
