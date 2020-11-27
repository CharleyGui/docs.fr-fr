---
title: 1017 - ScheduleCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 864546ab-d65c-4989-8fcb-537ba03a3cdd
ms.openlocfilehash: 6aed9773aa45251075520a0f955e9d71234f1357
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275617"
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="7f61e-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="7f61e-102">1017 - ScheduleCancelActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="7f61e-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="7f61e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7f61e-104">id</span><span class="sxs-lookup"><span data-stu-id="7f61e-104">ID</span></span>|<span data-ttu-id="7f61e-105">1017</span><span class="sxs-lookup"><span data-stu-id="7f61e-105">1017</span></span>|  
|<span data-ttu-id="7f61e-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="7f61e-106">Keywords</span></span>|<span data-ttu-id="7f61e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7f61e-107">WFRuntime</span></span>|  
|<span data-ttu-id="7f61e-108">Level</span><span class="sxs-lookup"><span data-stu-id="7f61e-108">Level</span></span>|<span data-ttu-id="7f61e-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="7f61e-109">Verbose</span></span>|  
|<span data-ttu-id="7f61e-110">Channel</span><span class="sxs-lookup"><span data-stu-id="7f61e-110">Channel</span></span>|<span data-ttu-id="7f61e-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="7f61e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7f61e-112">Description</span><span class="sxs-lookup"><span data-stu-id="7f61e-112">Description</span></span>  

 <span data-ttu-id="7f61e-113">Indique qu'un CancelActivityWorkItem a été planifié.</span><span class="sxs-lookup"><span data-stu-id="7f61e-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7f61e-114">Message</span><span class="sxs-lookup"><span data-stu-id="7f61e-114">Message</span></span>  

 <span data-ttu-id="7f61e-115">CancelActivityWorkItem a été planifié pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="7f61e-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7f61e-116">Détails</span><span class="sxs-lookup"><span data-stu-id="7f61e-116">Details</span></span>  
  
|<span data-ttu-id="7f61e-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="7f61e-117">Data Item Name</span></span>|<span data-ttu-id="7f61e-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="7f61e-118">Data Item Type</span></span>|<span data-ttu-id="7f61e-119">Description</span><span class="sxs-lookup"><span data-stu-id="7f61e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7f61e-120">Activité</span><span class="sxs-lookup"><span data-stu-id="7f61e-120">Activity</span></span>|<span data-ttu-id="7f61e-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="7f61e-121">xs:string</span></span>|<span data-ttu-id="7f61e-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="7f61e-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="7f61e-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="7f61e-123">DisplayName</span></span>|<span data-ttu-id="7f61e-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="7f61e-124">xs:string</span></span>|<span data-ttu-id="7f61e-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="7f61e-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="7f61e-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="7f61e-126">InstanceId</span></span>|<span data-ttu-id="7f61e-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="7f61e-127">xs:string</span></span>|<span data-ttu-id="7f61e-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="7f61e-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="7f61e-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7f61e-129">AppDomain</span></span>|<span data-ttu-id="7f61e-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="7f61e-130">xs:string</span></span>|<span data-ttu-id="7f61e-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7f61e-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
