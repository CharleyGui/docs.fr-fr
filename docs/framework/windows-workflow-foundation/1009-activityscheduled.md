---
title: 1009 - ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 812531d4206dfee20f183b9461330e71263b0bf8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239768"
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="5bbdd-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="5bbdd-102">1009 - ActivityScheduled</span></span>

## <a name="properties"></a><span data-ttu-id="5bbdd-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="5bbdd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5bbdd-104">id</span><span class="sxs-lookup"><span data-stu-id="5bbdd-104">ID</span></span>|<span data-ttu-id="5bbdd-105">1009</span><span class="sxs-lookup"><span data-stu-id="5bbdd-105">1009</span></span>|  
|<span data-ttu-id="5bbdd-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="5bbdd-106">Keywords</span></span>|<span data-ttu-id="5bbdd-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="5bbdd-107">WFRuntime</span></span>|  
|<span data-ttu-id="5bbdd-108">Level</span><span class="sxs-lookup"><span data-stu-id="5bbdd-108">Level</span></span>|<span data-ttu-id="5bbdd-109">Informations</span><span class="sxs-lookup"><span data-stu-id="5bbdd-109">Information</span></span>|  
|<span data-ttu-id="5bbdd-110">Channel</span><span class="sxs-lookup"><span data-stu-id="5bbdd-110">Channel</span></span>|<span data-ttu-id="5bbdd-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="5bbdd-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5bbdd-112">Description</span><span class="sxs-lookup"><span data-stu-id="5bbdd-112">Description</span></span>  

 <span data-ttu-id="5bbdd-113">Indique qu'une activité est planifiée en vue de son exécution.</span><span class="sxs-lookup"><span data-stu-id="5bbdd-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5bbdd-114">Message</span><span class="sxs-lookup"><span data-stu-id="5bbdd-114">Message</span></span>  

 <span data-ttu-id="5bbdd-115">L'activité parent « %1 », DisplayName : « %2 », InstanceId : « %3 » a planifié l'activité enfant « %4 », DisplayName : « %5 », InstanceId : « %6 ».</span><span class="sxs-lookup"><span data-stu-id="5bbdd-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5bbdd-116">Détails</span><span class="sxs-lookup"><span data-stu-id="5bbdd-116">Details</span></span>  
  
|<span data-ttu-id="5bbdd-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="5bbdd-117">Data Item Name</span></span>|<span data-ttu-id="5bbdd-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="5bbdd-118">Data Item Type</span></span>|<span data-ttu-id="5bbdd-119">Description</span><span class="sxs-lookup"><span data-stu-id="5bbdd-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5bbdd-120">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="5bbdd-120">ParentActivity</span></span>|<span data-ttu-id="5bbdd-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="5bbdd-121">xs:string</span></span>|<span data-ttu-id="5bbdd-122">Nom de type de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="5bbdd-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="5bbdd-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="5bbdd-123">ParentDisplayName</span></span>|<span data-ttu-id="5bbdd-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="5bbdd-124">xs:string</span></span>|<span data-ttu-id="5bbdd-125">Nom complet de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="5bbdd-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="5bbdd-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="5bbdd-126">ParentInstanceId</span></span>|<span data-ttu-id="5bbdd-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="5bbdd-127">xs:string</span></span>|<span data-ttu-id="5bbdd-128">ID d'instance de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="5bbdd-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="5bbdd-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="5bbdd-129">ChildActivity</span></span>|<span data-ttu-id="5bbdd-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="5bbdd-130">xs:string</span></span>|<span data-ttu-id="5bbdd-131">Nom de type de l'activité enfant planifiée.</span><span class="sxs-lookup"><span data-stu-id="5bbdd-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="5bbdd-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="5bbdd-132">ChildDisplayName</span></span>|<span data-ttu-id="5bbdd-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="5bbdd-133">xs:string</span></span>|<span data-ttu-id="5bbdd-134">Nom complet de l'activité enfant planifiée.</span><span class="sxs-lookup"><span data-stu-id="5bbdd-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="5bbdd-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="5bbdd-135">ChildInstanceId</span></span>|<span data-ttu-id="5bbdd-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="5bbdd-136">xs:string</span></span>|<span data-ttu-id="5bbdd-137">ID d'instance de l'activité enfant planifiée.</span><span class="sxs-lookup"><span data-stu-id="5bbdd-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="5bbdd-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5bbdd-138">AppDomain</span></span>|<span data-ttu-id="5bbdd-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="5bbdd-139">xs:string</span></span>|<span data-ttu-id="5bbdd-140">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5bbdd-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
