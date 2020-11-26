---
title: 1011 - ScheduleExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
ms.openlocfilehash: dc209fc41dc6b076dfb897880f753be51f7fb0ce
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239690"
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="b93d4-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="b93d4-102">1011 - ScheduleExecuteActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="b93d4-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="b93d4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b93d4-104">id</span><span class="sxs-lookup"><span data-stu-id="b93d4-104">ID</span></span>|<span data-ttu-id="b93d4-105">1010</span><span class="sxs-lookup"><span data-stu-id="b93d4-105">1011</span></span>|  
|<span data-ttu-id="b93d4-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="b93d4-106">Keywords</span></span>|<span data-ttu-id="b93d4-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b93d4-107">WFRuntime</span></span>|  
|<span data-ttu-id="b93d4-108">Level</span><span class="sxs-lookup"><span data-stu-id="b93d4-108">Level</span></span>|<span data-ttu-id="b93d4-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="b93d4-109">Verbose</span></span>|  
|<span data-ttu-id="b93d4-110">Channel</span><span class="sxs-lookup"><span data-stu-id="b93d4-110">Channel</span></span>|<span data-ttu-id="b93d4-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="b93d4-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b93d4-112">Description</span><span class="sxs-lookup"><span data-stu-id="b93d4-112">Description</span></span>  

 <span data-ttu-id="b93d4-113">Indique qu'un ExecuteActivityWorkItem a été planifié.</span><span class="sxs-lookup"><span data-stu-id="b93d4-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b93d4-114">Message</span><span class="sxs-lookup"><span data-stu-id="b93d4-114">Message</span></span>  

 <span data-ttu-id="b93d4-115">ExecuteActivityWorkItem a été planifié pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="b93d4-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b93d4-116">Détails</span><span class="sxs-lookup"><span data-stu-id="b93d4-116">Details</span></span>  
  
|<span data-ttu-id="b93d4-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="b93d4-117">Data Item Name</span></span>|<span data-ttu-id="b93d4-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="b93d4-118">Data Item Type</span></span>|<span data-ttu-id="b93d4-119">Description</span><span class="sxs-lookup"><span data-stu-id="b93d4-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b93d4-120">Activité</span><span class="sxs-lookup"><span data-stu-id="b93d4-120">Activity</span></span>|<span data-ttu-id="b93d4-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="b93d4-121">xs:string</span></span>|<span data-ttu-id="b93d4-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="b93d4-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="b93d4-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="b93d4-123">DisplayName</span></span>|<span data-ttu-id="b93d4-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="b93d4-124">xs:string</span></span>|<span data-ttu-id="b93d4-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="b93d4-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="b93d4-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="b93d4-126">InstanceId</span></span>|<span data-ttu-id="b93d4-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="b93d4-127">xs:string</span></span>|<span data-ttu-id="b93d4-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="b93d4-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="b93d4-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b93d4-129">AppDomain</span></span>|<span data-ttu-id="b93d4-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="b93d4-130">xs:string</span></span>|<span data-ttu-id="b93d4-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b93d4-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
