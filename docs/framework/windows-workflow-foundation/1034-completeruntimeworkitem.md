---
title: 1034 - CompleteRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 45620011-8b04-4f87-ab5a-65b24145e17d
ms.openlocfilehash: 837adc9e143060284f2373a049bc9ad9c8cee336
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294285"
---
# <a name="1034---completeruntimeworkitem"></a><span data-ttu-id="a6f97-102">1034 - CompleteRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="a6f97-102">1034 - CompleteRuntimeWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="a6f97-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="a6f97-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a6f97-104">id</span><span class="sxs-lookup"><span data-stu-id="a6f97-104">ID</span></span>|<span data-ttu-id="a6f97-105">1034</span><span class="sxs-lookup"><span data-stu-id="a6f97-105">1034</span></span>|  
|<span data-ttu-id="a6f97-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="a6f97-106">Keywords</span></span>|<span data-ttu-id="a6f97-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a6f97-107">WFRuntime</span></span>|  
|<span data-ttu-id="a6f97-108">Level</span><span class="sxs-lookup"><span data-stu-id="a6f97-108">Level</span></span>|<span data-ttu-id="a6f97-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="a6f97-109">Verbose</span></span>|  
|<span data-ttu-id="a6f97-110">Channel</span><span class="sxs-lookup"><span data-stu-id="a6f97-110">Channel</span></span>|<span data-ttu-id="a6f97-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="a6f97-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a6f97-112">Description</span><span class="sxs-lookup"><span data-stu-id="a6f97-112">Description</span></span>  

 <span data-ttu-id="a6f97-113">Indique qu'un RuntimeWorkItem est terminé.</span><span class="sxs-lookup"><span data-stu-id="a6f97-113">Indicates a RuntimeWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a6f97-114">Message</span><span class="sxs-lookup"><span data-stu-id="a6f97-114">Message</span></span>  

 <span data-ttu-id="a6f97-115">Un élément de travail runtime est terminé pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="a6f97-115">A runtime work item has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a6f97-116">Détails</span><span class="sxs-lookup"><span data-stu-id="a6f97-116">Details</span></span>  
  
|<span data-ttu-id="a6f97-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="a6f97-117">Data Item Name</span></span>|<span data-ttu-id="a6f97-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="a6f97-118">Data Item Type</span></span>|<span data-ttu-id="a6f97-119">Description</span><span class="sxs-lookup"><span data-stu-id="a6f97-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a6f97-120">Activité</span><span class="sxs-lookup"><span data-stu-id="a6f97-120">Activity</span></span>|<span data-ttu-id="a6f97-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="a6f97-121">xs:string</span></span>|<span data-ttu-id="a6f97-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="a6f97-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="a6f97-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="a6f97-123">DisplayName</span></span>|<span data-ttu-id="a6f97-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="a6f97-124">xs:string</span></span>|<span data-ttu-id="a6f97-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="a6f97-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="a6f97-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="a6f97-126">InstanceId</span></span>|<span data-ttu-id="a6f97-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="a6f97-127">xs:string</span></span>|<span data-ttu-id="a6f97-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="a6f97-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="a6f97-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a6f97-129">AppDomain</span></span>|<span data-ttu-id="a6f97-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="a6f97-130">xs:string</span></span>|<span data-ttu-id="a6f97-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a6f97-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
