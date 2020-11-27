---
title: 1031 - CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: 557155fab35a37bdbaa45efb26d6bc025ad825c4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281831"
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="587d6-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="587d6-102">1031 - CompleteFaultWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="587d6-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="587d6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="587d6-104">id</span><span class="sxs-lookup"><span data-stu-id="587d6-104">ID</span></span>|<span data-ttu-id="587d6-105">1031</span><span class="sxs-lookup"><span data-stu-id="587d6-105">1031</span></span>|  
|<span data-ttu-id="587d6-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="587d6-106">Keywords</span></span>|<span data-ttu-id="587d6-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="587d6-107">WFRuntime</span></span>|  
|<span data-ttu-id="587d6-108">Level</span><span class="sxs-lookup"><span data-stu-id="587d6-108">Level</span></span>|<span data-ttu-id="587d6-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="587d6-109">Verbose</span></span>|  
|<span data-ttu-id="587d6-110">Channel</span><span class="sxs-lookup"><span data-stu-id="587d6-110">Channel</span></span>|<span data-ttu-id="587d6-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="587d6-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="587d6-112">Description</span><span class="sxs-lookup"><span data-stu-id="587d6-112">Description</span></span>  

 <span data-ttu-id="587d6-113">Indique qu'un FaultWorkItem est terminé.</span><span class="sxs-lookup"><span data-stu-id="587d6-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="587d6-114">Message</span><span class="sxs-lookup"><span data-stu-id="587d6-114">Message</span></span>  

 <span data-ttu-id="587d6-115">Un FaultWorkItem est achevé pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="587d6-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="587d6-116">L'exception a été propagée à partir de l'activité « %4 », DisplayName : « %5 », InstanceId : « %6 ».</span><span class="sxs-lookup"><span data-stu-id="587d6-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="587d6-117">Détails</span><span class="sxs-lookup"><span data-stu-id="587d6-117">Details</span></span>  
  
|<span data-ttu-id="587d6-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="587d6-118">Data Item Name</span></span>|<span data-ttu-id="587d6-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="587d6-119">Data Item Type</span></span>|<span data-ttu-id="587d6-120">Description</span><span class="sxs-lookup"><span data-stu-id="587d6-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="587d6-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="587d6-121">FaultActivity</span></span>|<span data-ttu-id="587d6-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="587d6-122">xs:string</span></span>|<span data-ttu-id="587d6-123">Nom de type de l'activité d'erreur.</span><span class="sxs-lookup"><span data-stu-id="587d6-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="587d6-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="587d6-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="587d6-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="587d6-125">xs:string</span></span>|<span data-ttu-id="587d6-126">Nom complet de l'activité d'erreur.</span><span class="sxs-lookup"><span data-stu-id="587d6-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="587d6-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="587d6-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="587d6-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="587d6-128">xs:string</span></span>|<span data-ttu-id="587d6-129">ID d'instance de l'activité d'erreur.</span><span class="sxs-lookup"><span data-stu-id="587d6-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="587d6-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="587d6-130">ExceptionActivity</span></span>|<span data-ttu-id="587d6-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="587d6-131">xs:string</span></span>|<span data-ttu-id="587d6-132">Nom de type de l'activité qui a levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="587d6-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="587d6-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="587d6-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="587d6-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="587d6-134">xs:string</span></span>|<span data-ttu-id="587d6-135">Nom complet de l'activité qui a levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="587d6-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="587d6-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="587d6-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="587d6-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="587d6-137">xs:string</span></span>|<span data-ttu-id="587d6-138">ID d'instance de l'activité ayant levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="587d6-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="587d6-139">Exception</span><span class="sxs-lookup"><span data-stu-id="587d6-139">Exception</span></span>|<span data-ttu-id="587d6-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="587d6-140">xs:string</span></span>|<span data-ttu-id="587d6-141">Détails de l'exception</span><span class="sxs-lookup"><span data-stu-id="587d6-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="587d6-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="587d6-142">AppDomain</span></span>|<span data-ttu-id="587d6-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="587d6-143">xs:string</span></span>|<span data-ttu-id="587d6-144">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="587d6-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
