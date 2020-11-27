---
title: 1030 - StartFaultWorkItem
ms.date: 03/30/2017
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
ms.openlocfilehash: 52034f7cc7c6f6749fbbbf06db9267ecb6279ee1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281857"
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="0e96f-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="0e96f-102">1030 - StartFaultWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="0e96f-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="0e96f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0e96f-104">id</span><span class="sxs-lookup"><span data-stu-id="0e96f-104">ID</span></span>|<span data-ttu-id="0e96f-105">1030</span><span class="sxs-lookup"><span data-stu-id="0e96f-105">1030</span></span>|  
|<span data-ttu-id="0e96f-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="0e96f-106">Keywords</span></span>|<span data-ttu-id="0e96f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0e96f-107">WFRuntime</span></span>|  
|<span data-ttu-id="0e96f-108">Level</span><span class="sxs-lookup"><span data-stu-id="0e96f-108">Level</span></span>|<span data-ttu-id="0e96f-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="0e96f-109">Verbose</span></span>|  
|<span data-ttu-id="0e96f-110">Channel</span><span class="sxs-lookup"><span data-stu-id="0e96f-110">Channel</span></span>|<span data-ttu-id="0e96f-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="0e96f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0e96f-112">Description</span><span class="sxs-lookup"><span data-stu-id="0e96f-112">Description</span></span>  

 <span data-ttu-id="0e96f-113">Indique qu'un FaultWorkItem démarre l'exécution.</span><span class="sxs-lookup"><span data-stu-id="0e96f-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0e96f-114">Message</span><span class="sxs-lookup"><span data-stu-id="0e96f-114">Message</span></span>  

 <span data-ttu-id="0e96f-115">Début de l’exécution d’un FaultWorkItem pour l’activité' %1 ', DisplayName : ' %2 ', InstanceId : ' %3 '.</span><span class="sxs-lookup"><span data-stu-id="0e96f-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="0e96f-116">L'exception a été propagée à partir de l'activité « %4 », DisplayName : « %5 », InstanceId : « %6 ».</span><span class="sxs-lookup"><span data-stu-id="0e96f-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0e96f-117">Détails</span><span class="sxs-lookup"><span data-stu-id="0e96f-117">Details</span></span>  
  
|<span data-ttu-id="0e96f-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="0e96f-118">Data Item Name</span></span>|<span data-ttu-id="0e96f-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="0e96f-119">Data Item Type</span></span>|<span data-ttu-id="0e96f-120">Description</span><span class="sxs-lookup"><span data-stu-id="0e96f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0e96f-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="0e96f-121">FaultActivity</span></span>|<span data-ttu-id="0e96f-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="0e96f-122">xs:string</span></span>|<span data-ttu-id="0e96f-123">Nom de type de l'activité d'erreur.</span><span class="sxs-lookup"><span data-stu-id="0e96f-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="0e96f-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="0e96f-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="0e96f-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="0e96f-125">xs:string</span></span>|<span data-ttu-id="0e96f-126">Nom complet de l'activité d'erreur.</span><span class="sxs-lookup"><span data-stu-id="0e96f-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="0e96f-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="0e96f-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="0e96f-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="0e96f-128">xs:string</span></span>|<span data-ttu-id="0e96f-129">ID d'instance de l'activité d'erreur.</span><span class="sxs-lookup"><span data-stu-id="0e96f-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="0e96f-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="0e96f-130">ExceptionActivity</span></span>|<span data-ttu-id="0e96f-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="0e96f-131">xs:string</span></span>|<span data-ttu-id="0e96f-132">Nom de type de l'activité qui a levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="0e96f-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="0e96f-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="0e96f-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="0e96f-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="0e96f-134">xs:string</span></span>|<span data-ttu-id="0e96f-135">Nom complet de l'activité qui a levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="0e96f-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="0e96f-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="0e96f-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="0e96f-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="0e96f-137">xs:string</span></span>|<span data-ttu-id="0e96f-138">ID d'instance de l'activité ayant levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="0e96f-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="0e96f-139">Exception</span><span class="sxs-lookup"><span data-stu-id="0e96f-139">Exception</span></span>|<span data-ttu-id="0e96f-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="0e96f-140">xs:string</span></span>|<span data-ttu-id="0e96f-141">Détails de l'exception</span><span class="sxs-lookup"><span data-stu-id="0e96f-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="0e96f-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0e96f-142">AppDomain</span></span>|<span data-ttu-id="0e96f-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="0e96f-143">xs:string</span></span>|<span data-ttu-id="0e96f-144">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0e96f-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
