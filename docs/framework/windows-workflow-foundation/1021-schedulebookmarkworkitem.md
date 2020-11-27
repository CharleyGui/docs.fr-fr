---
title: 1021 - ScheduleBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 2e0da311-b219-4637-9460-90cdafcc4ecd
ms.openlocfilehash: 42ed23654622e29df8ffc210c8d5ba572fa69fd4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275347"
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="6e61c-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="6e61c-102">1021 - ScheduleBookmarkWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="6e61c-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="6e61c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6e61c-104">id</span><span class="sxs-lookup"><span data-stu-id="6e61c-104">ID</span></span>|<span data-ttu-id="6e61c-105">1021</span><span class="sxs-lookup"><span data-stu-id="6e61c-105">1021</span></span>|  
|<span data-ttu-id="6e61c-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="6e61c-106">Keywords</span></span>|<span data-ttu-id="6e61c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="6e61c-107">WFRuntime</span></span>|  
|<span data-ttu-id="6e61c-108">Level</span><span class="sxs-lookup"><span data-stu-id="6e61c-108">Level</span></span>|<span data-ttu-id="6e61c-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="6e61c-109">Verbose</span></span>|  
|<span data-ttu-id="6e61c-110">Channel</span><span class="sxs-lookup"><span data-stu-id="6e61c-110">Channel</span></span>|<span data-ttu-id="6e61c-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="6e61c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6e61c-112">Description</span><span class="sxs-lookup"><span data-stu-id="6e61c-112">Description</span></span>  

 <span data-ttu-id="6e61c-113">Indique qu'un BookmarkWorkItem a été planifié.</span><span class="sxs-lookup"><span data-stu-id="6e61c-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6e61c-114">Message</span><span class="sxs-lookup"><span data-stu-id="6e61c-114">Message</span></span>  

 <span data-ttu-id="6e61c-115">Un BookmarkWorkItem a été planifié pour l’activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="6e61c-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="6e61c-116">BookmarkName : %4, BookmarkScope : %5.</span><span class="sxs-lookup"><span data-stu-id="6e61c-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6e61c-117">Détails</span><span class="sxs-lookup"><span data-stu-id="6e61c-117">Details</span></span>  
  
|<span data-ttu-id="6e61c-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="6e61c-118">Data Item Name</span></span>|<span data-ttu-id="6e61c-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="6e61c-119">Data Item Type</span></span>|<span data-ttu-id="6e61c-120">Description</span><span class="sxs-lookup"><span data-stu-id="6e61c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6e61c-121">Activité</span><span class="sxs-lookup"><span data-stu-id="6e61c-121">Activity</span></span>|<span data-ttu-id="6e61c-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="6e61c-122">xs:string</span></span>|<span data-ttu-id="6e61c-123">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="6e61c-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="6e61c-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="6e61c-124">DisplayName</span></span>|<span data-ttu-id="6e61c-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="6e61c-125">xs:string</span></span>|<span data-ttu-id="6e61c-126">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="6e61c-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="6e61c-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="6e61c-127">InstanceId</span></span>|<span data-ttu-id="6e61c-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="6e61c-128">xs:string</span></span>|<span data-ttu-id="6e61c-129">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="6e61c-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="6e61c-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="6e61c-130">BookmarkName</span></span>|<span data-ttu-id="6e61c-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="6e61c-131">xs:string</span></span>|<span data-ttu-id="6e61c-132">Nom du signet.</span><span class="sxs-lookup"><span data-stu-id="6e61c-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="6e61c-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="6e61c-133">BookmarkScope</span></span>|<span data-ttu-id="6e61c-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="6e61c-134">xs:string</span></span>|<span data-ttu-id="6e61c-135">Portée du signet.</span><span class="sxs-lookup"><span data-stu-id="6e61c-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="6e61c-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6e61c-136">AppDomain</span></span>|<span data-ttu-id="6e61c-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="6e61c-137">xs:string</span></span>|<span data-ttu-id="6e61c-138">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6e61c-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
