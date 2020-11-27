---
title: 1016 - CompleteCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
ms.openlocfilehash: a192ffe19777ca3e2e9784f6506a0c2929ced000
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275529"
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="86f4d-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="86f4d-102">1016 - CompleteCompletionWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="86f4d-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="86f4d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="86f4d-104">id</span><span class="sxs-lookup"><span data-stu-id="86f4d-104">ID</span></span>|<span data-ttu-id="86f4d-105">1016</span><span class="sxs-lookup"><span data-stu-id="86f4d-105">1016</span></span>|  
|<span data-ttu-id="86f4d-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="86f4d-106">Keywords</span></span>|<span data-ttu-id="86f4d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="86f4d-107">WFRuntime</span></span>|  
|<span data-ttu-id="86f4d-108">Level</span><span class="sxs-lookup"><span data-stu-id="86f4d-108">Level</span></span>|<span data-ttu-id="86f4d-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="86f4d-109">Verbose</span></span>|  
|<span data-ttu-id="86f4d-110">Channel</span><span class="sxs-lookup"><span data-stu-id="86f4d-110">Channel</span></span>|<span data-ttu-id="86f4d-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="86f4d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="86f4d-112">Description</span><span class="sxs-lookup"><span data-stu-id="86f4d-112">Description</span></span>  

 <span data-ttu-id="86f4d-113">Indique qu'un CompletionWorkItem est terminé.</span><span class="sxs-lookup"><span data-stu-id="86f4d-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="86f4d-114">Message</span><span class="sxs-lookup"><span data-stu-id="86f4d-114">Message</span></span>  

 <span data-ttu-id="86f4d-115">Un CompletionWorkItem est achevé pour l'activité parente « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="86f4d-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="86f4d-116">Activité terminée « %4 », DisplayName : « %5 », InstanceId : « %6 ».</span><span class="sxs-lookup"><span data-stu-id="86f4d-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="86f4d-117">Détails</span><span class="sxs-lookup"><span data-stu-id="86f4d-117">Details</span></span>  
  
|<span data-ttu-id="86f4d-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="86f4d-118">Data Item Name</span></span>|<span data-ttu-id="86f4d-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="86f4d-119">Data Item Type</span></span>|<span data-ttu-id="86f4d-120">Description</span><span class="sxs-lookup"><span data-stu-id="86f4d-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="86f4d-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="86f4d-121">ParentActivity</span></span>|<span data-ttu-id="86f4d-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="86f4d-122">xs:string</span></span>|<span data-ttu-id="86f4d-123">Nom de type de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="86f4d-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="86f4d-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="86f4d-124">ParentDisplayName</span></span>|<span data-ttu-id="86f4d-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="86f4d-125">xs:string</span></span>|<span data-ttu-id="86f4d-126">Nom complet de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="86f4d-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="86f4d-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="86f4d-127">ParentInstanceId</span></span>|<span data-ttu-id="86f4d-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="86f4d-128">xs:string</span></span>|<span data-ttu-id="86f4d-129">ID d'instance de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="86f4d-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="86f4d-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="86f4d-130">CompletedActivity</span></span>|<span data-ttu-id="86f4d-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="86f4d-131">xs:string</span></span>|<span data-ttu-id="86f4d-132">Nom de type de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="86f4d-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="86f4d-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="86f4d-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="86f4d-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="86f4d-134">xs:string</span></span>|<span data-ttu-id="86f4d-135">Nom complet de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="86f4d-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="86f4d-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="86f4d-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="86f4d-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="86f4d-137">xs:string</span></span>|<span data-ttu-id="86f4d-138">ID d'instance de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="86f4d-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="86f4d-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="86f4d-139">AppDomain</span></span>|<span data-ttu-id="86f4d-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="86f4d-140">xs:string</span></span>|<span data-ttu-id="86f4d-141">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="86f4d-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
