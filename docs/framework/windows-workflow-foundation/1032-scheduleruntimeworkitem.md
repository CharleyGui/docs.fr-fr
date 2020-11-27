---
title: 1032 - ScheduleRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
ms.openlocfilehash: da35201f2b3e3bc07e0b9139b0584ce37011e168
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294311"
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="2d192-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="2d192-102">1032 - ScheduleRuntimeWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="2d192-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="2d192-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2d192-104">id</span><span class="sxs-lookup"><span data-stu-id="2d192-104">ID</span></span>|<span data-ttu-id="2d192-105">1032</span><span class="sxs-lookup"><span data-stu-id="2d192-105">1032</span></span>|  
|<span data-ttu-id="2d192-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="2d192-106">Keywords</span></span>|<span data-ttu-id="2d192-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2d192-107">WFRuntime</span></span>|  
|<span data-ttu-id="2d192-108">Level</span><span class="sxs-lookup"><span data-stu-id="2d192-108">Level</span></span>|<span data-ttu-id="2d192-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="2d192-109">Verbose</span></span>|  
|<span data-ttu-id="2d192-110">Channel</span><span class="sxs-lookup"><span data-stu-id="2d192-110">Channel</span></span>|<span data-ttu-id="2d192-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="2d192-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2d192-112">Description</span><span class="sxs-lookup"><span data-stu-id="2d192-112">Description</span></span>  

 <span data-ttu-id="2d192-113">Indique qu'un RuntimeWorkItem a été planifié.</span><span class="sxs-lookup"><span data-stu-id="2d192-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2d192-114">Message</span><span class="sxs-lookup"><span data-stu-id="2d192-114">Message</span></span>  

 <span data-ttu-id="2d192-115">Un élément de travail runtime a été planifié pour l’activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="2d192-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2d192-116">Détails</span><span class="sxs-lookup"><span data-stu-id="2d192-116">Details</span></span>  
  
|<span data-ttu-id="2d192-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="2d192-117">Data Item Name</span></span>|<span data-ttu-id="2d192-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="2d192-118">Data Item Type</span></span>|<span data-ttu-id="2d192-119">Description</span><span class="sxs-lookup"><span data-stu-id="2d192-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2d192-120">Activité</span><span class="sxs-lookup"><span data-stu-id="2d192-120">Activity</span></span>|<span data-ttu-id="2d192-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="2d192-121">xs:string</span></span>|<span data-ttu-id="2d192-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="2d192-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="2d192-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="2d192-123">DisplayName</span></span>|<span data-ttu-id="2d192-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="2d192-124">xs:string</span></span>|<span data-ttu-id="2d192-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="2d192-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="2d192-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="2d192-126">InstanceId</span></span>|<span data-ttu-id="2d192-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="2d192-127">xs:string</span></span>|<span data-ttu-id="2d192-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="2d192-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="2d192-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2d192-129">AppDomain</span></span>|<span data-ttu-id="2d192-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="2d192-130">xs:string</span></span>|<span data-ttu-id="2d192-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2d192-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
