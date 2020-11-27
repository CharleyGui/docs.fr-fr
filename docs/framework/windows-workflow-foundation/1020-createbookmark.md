---
title: 1020 - CreateBookmark
ms.date: 03/30/2017
ms.assetid: 4bee948d-816f-4803-85cc-3883b5e23d10
ms.openlocfilehash: 8c9c20fd4fb74f80779c1d2ef8f29ac3d44050d9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275373"
---
# <a name="1020---createbookmark"></a><span data-ttu-id="ed0fc-102">1020 - CreateBookmark</span><span class="sxs-lookup"><span data-stu-id="ed0fc-102">1020 - CreateBookmark</span></span>

## <a name="properties"></a><span data-ttu-id="ed0fc-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="ed0fc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ed0fc-104">id</span><span class="sxs-lookup"><span data-stu-id="ed0fc-104">ID</span></span>|<span data-ttu-id="ed0fc-105">1020</span><span class="sxs-lookup"><span data-stu-id="ed0fc-105">1020</span></span>|  
|<span data-ttu-id="ed0fc-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="ed0fc-106">Keywords</span></span>|<span data-ttu-id="ed0fc-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ed0fc-107">WFRuntime</span></span>|  
|<span data-ttu-id="ed0fc-108">Level</span><span class="sxs-lookup"><span data-stu-id="ed0fc-108">Level</span></span>|<span data-ttu-id="ed0fc-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="ed0fc-109">Verbose</span></span>|  
|<span data-ttu-id="ed0fc-110">Channel</span><span class="sxs-lookup"><span data-stu-id="ed0fc-110">Channel</span></span>|<span data-ttu-id="ed0fc-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="ed0fc-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ed0fc-112">Description</span><span class="sxs-lookup"><span data-stu-id="ed0fc-112">Description</span></span>  

 <span data-ttu-id="ed0fc-113">Indique qu'un signet a été créé pour une activité.</span><span class="sxs-lookup"><span data-stu-id="ed0fc-113">Indicates a bookmark has been created for an activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ed0fc-114">Message</span><span class="sxs-lookup"><span data-stu-id="ed0fc-114">Message</span></span>  

 <span data-ttu-id="ed0fc-115">Un signet a été créé pour l’activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="ed0fc-115">A Bookmark has been created for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="ed0fc-116">BookmarkName : %4, BookmarkScope : %5.</span><span class="sxs-lookup"><span data-stu-id="ed0fc-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ed0fc-117">Détails</span><span class="sxs-lookup"><span data-stu-id="ed0fc-117">Details</span></span>  
  
|<span data-ttu-id="ed0fc-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="ed0fc-118">Data Item Name</span></span>|<span data-ttu-id="ed0fc-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="ed0fc-119">Data Item Type</span></span>|<span data-ttu-id="ed0fc-120">Description</span><span class="sxs-lookup"><span data-stu-id="ed0fc-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ed0fc-121">Activité</span><span class="sxs-lookup"><span data-stu-id="ed0fc-121">Activity</span></span>|<span data-ttu-id="ed0fc-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="ed0fc-122">xs:string</span></span>|<span data-ttu-id="ed0fc-123">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="ed0fc-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="ed0fc-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ed0fc-124">DisplayName</span></span>|<span data-ttu-id="ed0fc-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="ed0fc-125">xs:string</span></span>|<span data-ttu-id="ed0fc-126">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="ed0fc-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="ed0fc-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="ed0fc-127">InstanceId</span></span>|<span data-ttu-id="ed0fc-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="ed0fc-128">xs:string</span></span>|<span data-ttu-id="ed0fc-129">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="ed0fc-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="ed0fc-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="ed0fc-130">BookmarkName</span></span>|<span data-ttu-id="ed0fc-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="ed0fc-131">xs:string</span></span>|<span data-ttu-id="ed0fc-132">Nom du signet.</span><span class="sxs-lookup"><span data-stu-id="ed0fc-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="ed0fc-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="ed0fc-133">BookmarkScope</span></span>|<span data-ttu-id="ed0fc-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="ed0fc-134">xs:string</span></span>|<span data-ttu-id="ed0fc-135">Portée du signet.</span><span class="sxs-lookup"><span data-stu-id="ed0fc-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="ed0fc-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ed0fc-136">AppDomain</span></span>|<span data-ttu-id="ed0fc-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="ed0fc-137">xs:string</span></span>|<span data-ttu-id="ed0fc-138">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ed0fc-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
