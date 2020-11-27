---
title: 1029 - ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: 5c109607b2d353d3d4a5a693f29ab66bb76c8398
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275087"
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="7be7d-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="7be7d-102">1029 - ScheduleFaultWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="7be7d-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="7be7d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7be7d-104">id</span><span class="sxs-lookup"><span data-stu-id="7be7d-104">ID</span></span>|<span data-ttu-id="7be7d-105">1029</span><span class="sxs-lookup"><span data-stu-id="7be7d-105">1029</span></span>|  
|<span data-ttu-id="7be7d-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="7be7d-106">Keywords</span></span>|<span data-ttu-id="7be7d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7be7d-107">WFRuntime</span></span>|  
|<span data-ttu-id="7be7d-108">Level</span><span class="sxs-lookup"><span data-stu-id="7be7d-108">Level</span></span>|<span data-ttu-id="7be7d-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="7be7d-109">Verbose</span></span>|  
|<span data-ttu-id="7be7d-110">Channel</span><span class="sxs-lookup"><span data-stu-id="7be7d-110">Channel</span></span>|<span data-ttu-id="7be7d-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="7be7d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7be7d-112">Description</span><span class="sxs-lookup"><span data-stu-id="7be7d-112">Description</span></span>  

 <span data-ttu-id="7be7d-113">Indique qu'un FaultWorkItem a été planifié.</span><span class="sxs-lookup"><span data-stu-id="7be7d-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7be7d-114">Message</span><span class="sxs-lookup"><span data-stu-id="7be7d-114">Message</span></span>  

 <span data-ttu-id="7be7d-115">Un FaultWorkItem a été planifié pour l’activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="7be7d-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="7be7d-116">L'exception a été propagée à partir de l'activité « %4 », DisplayName : « %5 », InstanceId : « %6 ».</span><span class="sxs-lookup"><span data-stu-id="7be7d-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7be7d-117">Détails</span><span class="sxs-lookup"><span data-stu-id="7be7d-117">Details</span></span>  
  
|<span data-ttu-id="7be7d-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="7be7d-118">Data Item Name</span></span>|<span data-ttu-id="7be7d-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="7be7d-119">Data Item Type</span></span>|<span data-ttu-id="7be7d-120">Description</span><span class="sxs-lookup"><span data-stu-id="7be7d-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7be7d-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="7be7d-121">FaultActivity</span></span>|<span data-ttu-id="7be7d-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="7be7d-122">xs:string</span></span>|<span data-ttu-id="7be7d-123">Nom de type de l'activité d'erreur.</span><span class="sxs-lookup"><span data-stu-id="7be7d-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="7be7d-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="7be7d-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="7be7d-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="7be7d-125">xs:string</span></span>|<span data-ttu-id="7be7d-126">Nom complet de l'activité d'erreur.</span><span class="sxs-lookup"><span data-stu-id="7be7d-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="7be7d-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="7be7d-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="7be7d-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="7be7d-128">xs:string</span></span>|<span data-ttu-id="7be7d-129">ID d'instance de l'activité d'erreur.</span><span class="sxs-lookup"><span data-stu-id="7be7d-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="7be7d-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="7be7d-130">ExceptionActivity</span></span>|<span data-ttu-id="7be7d-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="7be7d-131">xs:string</span></span>|<span data-ttu-id="7be7d-132">Nom de type de l'activité qui a levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="7be7d-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="7be7d-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="7be7d-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="7be7d-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="7be7d-134">xs:string</span></span>|<span data-ttu-id="7be7d-135">Nom complet de l'activité qui a levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="7be7d-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="7be7d-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="7be7d-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="7be7d-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="7be7d-137">xs:string</span></span>|<span data-ttu-id="7be7d-138">ID d'instance de l'activité ayant levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="7be7d-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="7be7d-139">Exception</span><span class="sxs-lookup"><span data-stu-id="7be7d-139">Exception</span></span>|<span data-ttu-id="7be7d-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="7be7d-140">xs:string</span></span>|<span data-ttu-id="7be7d-141">Détails de l'exception</span><span class="sxs-lookup"><span data-stu-id="7be7d-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="7be7d-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7be7d-142">AppDomain</span></span>|<span data-ttu-id="7be7d-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="7be7d-143">xs:string</span></span>|<span data-ttu-id="7be7d-144">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7be7d-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
