---
title: 1015 - StartCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
ms.openlocfilehash: c0d8572f192a8faa22327fd671cd9ea49c5054ca
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275542"
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="87881-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="87881-102">1015 - StartCompletionWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="87881-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="87881-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="87881-104">id</span><span class="sxs-lookup"><span data-stu-id="87881-104">ID</span></span>|<span data-ttu-id="87881-105">1015</span><span class="sxs-lookup"><span data-stu-id="87881-105">1015</span></span>|  
|<span data-ttu-id="87881-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="87881-106">Keywords</span></span>|<span data-ttu-id="87881-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="87881-107">WFRuntime</span></span>|  
|<span data-ttu-id="87881-108">Level</span><span class="sxs-lookup"><span data-stu-id="87881-108">Level</span></span>|<span data-ttu-id="87881-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="87881-109">Verbose</span></span>|  
|<span data-ttu-id="87881-110">Channel</span><span class="sxs-lookup"><span data-stu-id="87881-110">Channel</span></span>|<span data-ttu-id="87881-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="87881-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="87881-112">Description</span><span class="sxs-lookup"><span data-stu-id="87881-112">Description</span></span>  

 <span data-ttu-id="87881-113">Indique qu'un CompletionWorkItem démarre l'exécution.</span><span class="sxs-lookup"><span data-stu-id="87881-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="87881-114">Message</span><span class="sxs-lookup"><span data-stu-id="87881-114">Message</span></span>  

 <span data-ttu-id="87881-115">Début de l'exécution d'un CompletionWorkItem pour l'activité parente « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="87881-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="87881-116">Activité terminée « %4 », DisplayName : « %5 », InstanceId : « %6 ».</span><span class="sxs-lookup"><span data-stu-id="87881-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="87881-117">Détails</span><span class="sxs-lookup"><span data-stu-id="87881-117">Details</span></span>  
  
|<span data-ttu-id="87881-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="87881-118">Data Item Name</span></span>|<span data-ttu-id="87881-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="87881-119">Data Item Type</span></span>|<span data-ttu-id="87881-120">Description</span><span class="sxs-lookup"><span data-stu-id="87881-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="87881-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="87881-121">ParentActivity</span></span>|<span data-ttu-id="87881-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="87881-122">xs:string</span></span>|<span data-ttu-id="87881-123">Nom de type de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="87881-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="87881-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="87881-124">ParentDisplayName</span></span>|<span data-ttu-id="87881-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="87881-125">xs:string</span></span>|<span data-ttu-id="87881-126">Nom complet de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="87881-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="87881-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="87881-127">ParentInstanceId</span></span>|<span data-ttu-id="87881-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="87881-128">xs:string</span></span>|<span data-ttu-id="87881-129">ID d'instance de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="87881-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="87881-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="87881-130">CompletedActivity</span></span>|<span data-ttu-id="87881-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="87881-131">xs:string</span></span>|<span data-ttu-id="87881-132">Nom de type de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="87881-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="87881-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="87881-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="87881-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="87881-134">xs:string</span></span>|<span data-ttu-id="87881-135">Nom complet de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="87881-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="87881-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="87881-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="87881-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="87881-137">xs:string</span></span>|<span data-ttu-id="87881-138">ID d'instance de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="87881-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="87881-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="87881-139">AppDomain</span></span>|<span data-ttu-id="87881-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="87881-140">xs:string</span></span>|<span data-ttu-id="87881-141">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="87881-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
