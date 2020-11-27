---
title: 1023 - CompleteBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: fc5dac57-b3eb-4826-b505-c6d269e4774d
ms.openlocfilehash: cb99fd72165182788955021fbedd2aa657b3a098
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275321"
---
# <a name="1023---completebookmarkworkitem"></a><span data-ttu-id="4d29f-102">1023 - CompleteBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="4d29f-102">1023 - CompleteBookmarkWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="4d29f-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="4d29f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4d29f-104">id</span><span class="sxs-lookup"><span data-stu-id="4d29f-104">ID</span></span>|<span data-ttu-id="4d29f-105">1023</span><span class="sxs-lookup"><span data-stu-id="4d29f-105">1023</span></span>|  
|<span data-ttu-id="4d29f-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="4d29f-106">Keywords</span></span>|<span data-ttu-id="4d29f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4d29f-107">WFRuntime</span></span>|  
|<span data-ttu-id="4d29f-108">Level</span><span class="sxs-lookup"><span data-stu-id="4d29f-108">Level</span></span>|<span data-ttu-id="4d29f-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="4d29f-109">Verbose</span></span>|  
|<span data-ttu-id="4d29f-110">Channel</span><span class="sxs-lookup"><span data-stu-id="4d29f-110">Channel</span></span>|<span data-ttu-id="4d29f-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="4d29f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4d29f-112">Description</span><span class="sxs-lookup"><span data-stu-id="4d29f-112">Description</span></span>  

 <span data-ttu-id="4d29f-113">Indique qu'un BookmarkWorkItem est terminé.</span><span class="sxs-lookup"><span data-stu-id="4d29f-113">Indicates a BookmarkWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4d29f-114">Message</span><span class="sxs-lookup"><span data-stu-id="4d29f-114">Message</span></span>  

 <span data-ttu-id="4d29f-115">Un BookmarkWorkItem est achevé pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="4d29f-115">A BookmarkWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="4d29f-116">BookmarkName : %4, BookmarkScope : %5.</span><span class="sxs-lookup"><span data-stu-id="4d29f-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4d29f-117">Détails</span><span class="sxs-lookup"><span data-stu-id="4d29f-117">Details</span></span>  
  
|<span data-ttu-id="4d29f-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="4d29f-118">Data Item Name</span></span>|<span data-ttu-id="4d29f-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="4d29f-119">Data Item Type</span></span>|<span data-ttu-id="4d29f-120">Description</span><span class="sxs-lookup"><span data-stu-id="4d29f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4d29f-121">Activité</span><span class="sxs-lookup"><span data-stu-id="4d29f-121">Activity</span></span>|<span data-ttu-id="4d29f-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="4d29f-122">xs:string</span></span>|<span data-ttu-id="4d29f-123">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="4d29f-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="4d29f-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="4d29f-124">DisplayName</span></span>|<span data-ttu-id="4d29f-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="4d29f-125">xs:string</span></span>|<span data-ttu-id="4d29f-126">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="4d29f-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="4d29f-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="4d29f-127">InstanceId</span></span>|<span data-ttu-id="4d29f-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="4d29f-128">xs:string</span></span>|<span data-ttu-id="4d29f-129">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="4d29f-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="4d29f-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="4d29f-130">BookmarkName</span></span>|<span data-ttu-id="4d29f-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="4d29f-131">xs:string</span></span>|<span data-ttu-id="4d29f-132">Nom du signet.</span><span class="sxs-lookup"><span data-stu-id="4d29f-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="4d29f-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="4d29f-133">BookmarkScope</span></span>|<span data-ttu-id="4d29f-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="4d29f-134">xs:string</span></span>|<span data-ttu-id="4d29f-135">Portée du signet.</span><span class="sxs-lookup"><span data-stu-id="4d29f-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="4d29f-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4d29f-136">AppDomain</span></span>|<span data-ttu-id="4d29f-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="4d29f-137">xs:string</span></span>|<span data-ttu-id="4d29f-138">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4d29f-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
