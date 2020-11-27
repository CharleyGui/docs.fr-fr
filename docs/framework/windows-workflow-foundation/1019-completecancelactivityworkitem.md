---
title: 1019 - CompleteCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 75a4a1ab-e5a3-4f4e-88e4-d19806e671d7
ms.openlocfilehash: 903b497fb3f244fd40c6888829ef71dddd455251
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275477"
---
# <a name="1019---completecancelactivityworkitem"></a><span data-ttu-id="4a620-102">1019 - CompleteCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="4a620-102">1019 - CompleteCancelActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="4a620-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="4a620-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4a620-104">id</span><span class="sxs-lookup"><span data-stu-id="4a620-104">ID</span></span>|<span data-ttu-id="4a620-105">1019</span><span class="sxs-lookup"><span data-stu-id="4a620-105">1019</span></span>|  
|<span data-ttu-id="4a620-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="4a620-106">Keywords</span></span>|<span data-ttu-id="4a620-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4a620-107">WFRuntime</span></span>|  
|<span data-ttu-id="4a620-108">Level</span><span class="sxs-lookup"><span data-stu-id="4a620-108">Level</span></span>|<span data-ttu-id="4a620-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="4a620-109">Verbose</span></span>|  
|<span data-ttu-id="4a620-110">Channel</span><span class="sxs-lookup"><span data-stu-id="4a620-110">Channel</span></span>|<span data-ttu-id="4a620-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="4a620-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4a620-112">Description</span><span class="sxs-lookup"><span data-stu-id="4a620-112">Description</span></span>  

 <span data-ttu-id="4a620-113">Indique qu'un CancelActivityWorkItem est terminé.</span><span class="sxs-lookup"><span data-stu-id="4a620-113">Indicates a CancelActivityWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4a620-114">Message</span><span class="sxs-lookup"><span data-stu-id="4a620-114">Message</span></span>  

 <span data-ttu-id="4a620-115">CancelActivityWorkItem est terminé pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="4a620-115">A CancelActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4a620-116">Détails</span><span class="sxs-lookup"><span data-stu-id="4a620-116">Details</span></span>  
  
|<span data-ttu-id="4a620-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="4a620-117">Data Item Name</span></span>|<span data-ttu-id="4a620-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="4a620-118">Data Item Type</span></span>|<span data-ttu-id="4a620-119">Description</span><span class="sxs-lookup"><span data-stu-id="4a620-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4a620-120">Activité</span><span class="sxs-lookup"><span data-stu-id="4a620-120">Activity</span></span>|<span data-ttu-id="4a620-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="4a620-121">xs:string</span></span>|<span data-ttu-id="4a620-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="4a620-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="4a620-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="4a620-123">DisplayName</span></span>|<span data-ttu-id="4a620-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="4a620-124">xs:string</span></span>|<span data-ttu-id="4a620-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="4a620-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="4a620-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="4a620-126">InstanceId</span></span>|<span data-ttu-id="4a620-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="4a620-127">xs:string</span></span>|<span data-ttu-id="4a620-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="4a620-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="4a620-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4a620-129">AppDomain</span></span>|<span data-ttu-id="4a620-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="4a620-130">xs:string</span></span>|<span data-ttu-id="4a620-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4a620-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
