---
title: 1014 - ScheduleCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
ms.openlocfilehash: 7fd93683851c5a8c4ab253272c3f2129b3f0bb49
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275555"
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="581df-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="581df-102">1014 - ScheduleCompletionWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="581df-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="581df-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="581df-104">id</span><span class="sxs-lookup"><span data-stu-id="581df-104">ID</span></span>|<span data-ttu-id="581df-105">1014</span><span class="sxs-lookup"><span data-stu-id="581df-105">1014</span></span>|  
|<span data-ttu-id="581df-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="581df-106">Keywords</span></span>|<span data-ttu-id="581df-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="581df-107">WFRuntime</span></span>|  
|<span data-ttu-id="581df-108">Level</span><span class="sxs-lookup"><span data-stu-id="581df-108">Level</span></span>|<span data-ttu-id="581df-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="581df-109">Verbose</span></span>|  
|<span data-ttu-id="581df-110">Channel</span><span class="sxs-lookup"><span data-stu-id="581df-110">Channel</span></span>|<span data-ttu-id="581df-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="581df-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="581df-112">Description</span><span class="sxs-lookup"><span data-stu-id="581df-112">Description</span></span>  

 <span data-ttu-id="581df-113">Indique qu'un CompletionWorkItem a été planifié.</span><span class="sxs-lookup"><span data-stu-id="581df-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="581df-114">Message</span><span class="sxs-lookup"><span data-stu-id="581df-114">Message</span></span>  

 <span data-ttu-id="581df-115">Un CompletionWorkItem a été planifié pour l’activité parente « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="581df-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="581df-116">Activité terminée « %4 », DisplayName : « %5 », InstanceId : « %6 ».</span><span class="sxs-lookup"><span data-stu-id="581df-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="581df-117">Détails</span><span class="sxs-lookup"><span data-stu-id="581df-117">Details</span></span>  
  
|<span data-ttu-id="581df-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="581df-118">Data Item Name</span></span>|<span data-ttu-id="581df-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="581df-119">Data Item Type</span></span>|<span data-ttu-id="581df-120">Description</span><span class="sxs-lookup"><span data-stu-id="581df-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="581df-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="581df-121">ParentActivity</span></span>|<span data-ttu-id="581df-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="581df-122">xs:string</span></span>|<span data-ttu-id="581df-123">Nom de type de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="581df-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="581df-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="581df-124">ParentDisplayName</span></span>|<span data-ttu-id="581df-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="581df-125">xs:string</span></span>|<span data-ttu-id="581df-126">Nom complet de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="581df-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="581df-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="581df-127">ParentInstanceId</span></span>|<span data-ttu-id="581df-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="581df-128">xs:string</span></span>|<span data-ttu-id="581df-129">ID d'instance de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="581df-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="581df-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="581df-130">CompletedActivity</span></span>|<span data-ttu-id="581df-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="581df-131">xs:string</span></span>|<span data-ttu-id="581df-132">Nom de type de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="581df-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="581df-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="581df-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="581df-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="581df-134">xs:string</span></span>|<span data-ttu-id="581df-135">Nom complet de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="581df-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="581df-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="581df-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="581df-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="581df-137">xs:string</span></span>|<span data-ttu-id="581df-138">ID d'instance de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="581df-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="581df-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="581df-139">AppDomain</span></span>|<span data-ttu-id="581df-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="581df-140">xs:string</span></span>|<span data-ttu-id="581df-141">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="581df-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
