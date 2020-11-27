---
title: 1022 - StartBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
ms.openlocfilehash: ca1f4244fb1a5144cb2d86eaacb9b31137d317c2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275334"
---
# <a name="1022---startbookmarkworkitem"></a><span data-ttu-id="8b8c3-102">1022 - StartBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="8b8c3-102">1022 - StartBookmarkWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="8b8c3-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="8b8c3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8b8c3-104">id</span><span class="sxs-lookup"><span data-stu-id="8b8c3-104">ID</span></span>|<span data-ttu-id="8b8c3-105">1022</span><span class="sxs-lookup"><span data-stu-id="8b8c3-105">1022</span></span>|  
|<span data-ttu-id="8b8c3-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="8b8c3-106">Keywords</span></span>|<span data-ttu-id="8b8c3-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8b8c3-107">WFRuntime</span></span>|  
|<span data-ttu-id="8b8c3-108">Level</span><span class="sxs-lookup"><span data-stu-id="8b8c3-108">Level</span></span>|<span data-ttu-id="8b8c3-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="8b8c3-109">Verbose</span></span>|  
|<span data-ttu-id="8b8c3-110">Channel</span><span class="sxs-lookup"><span data-stu-id="8b8c3-110">Channel</span></span>|<span data-ttu-id="8b8c3-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="8b8c3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8b8c3-112">Description</span><span class="sxs-lookup"><span data-stu-id="8b8c3-112">Description</span></span>  

 <span data-ttu-id="8b8c3-113">Indique qu'un BookmarkWorkItem démarre l'exécution.</span><span class="sxs-lookup"><span data-stu-id="8b8c3-113">Indicates a BookmarkWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8b8c3-114">Message</span><span class="sxs-lookup"><span data-stu-id="8b8c3-114">Message</span></span>  

 <span data-ttu-id="8b8c3-115">Début de l’exécution d’un BookmarkWorkItem pour l’activité' %1 ', DisplayName : ' %2 ', InstanceId : ' %3 '.</span><span class="sxs-lookup"><span data-stu-id="8b8c3-115">Starting execution of a BookmarkWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="8b8c3-116">BookmarkName : %4, BookmarkScope : %5.</span><span class="sxs-lookup"><span data-stu-id="8b8c3-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8b8c3-117">Détails</span><span class="sxs-lookup"><span data-stu-id="8b8c3-117">Details</span></span>  
  
|<span data-ttu-id="8b8c3-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="8b8c3-118">Data Item Name</span></span>|<span data-ttu-id="8b8c3-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="8b8c3-119">Data Item Type</span></span>|<span data-ttu-id="8b8c3-120">Description</span><span class="sxs-lookup"><span data-stu-id="8b8c3-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8b8c3-121">Activité</span><span class="sxs-lookup"><span data-stu-id="8b8c3-121">Activity</span></span>|<span data-ttu-id="8b8c3-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="8b8c3-122">xs:string</span></span>|<span data-ttu-id="8b8c3-123">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="8b8c3-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="8b8c3-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="8b8c3-124">DisplayName</span></span>|<span data-ttu-id="8b8c3-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="8b8c3-125">xs:string</span></span>|<span data-ttu-id="8b8c3-126">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="8b8c3-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="8b8c3-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="8b8c3-127">InstanceId</span></span>|<span data-ttu-id="8b8c3-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="8b8c3-128">xs:string</span></span>|<span data-ttu-id="8b8c3-129">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="8b8c3-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="8b8c3-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="8b8c3-130">BookmarkName</span></span>|<span data-ttu-id="8b8c3-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="8b8c3-131">xs:string</span></span>|<span data-ttu-id="8b8c3-132">Nom du signet.</span><span class="sxs-lookup"><span data-stu-id="8b8c3-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="8b8c3-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="8b8c3-133">BookmarkScope</span></span>|<span data-ttu-id="8b8c3-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="8b8c3-134">xs:string</span></span>|<span data-ttu-id="8b8c3-135">Portée du signet.</span><span class="sxs-lookup"><span data-stu-id="8b8c3-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="8b8c3-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8b8c3-136">AppDomain</span></span>|<span data-ttu-id="8b8c3-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="8b8c3-137">xs:string</span></span>|<span data-ttu-id="8b8c3-138">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8b8c3-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
