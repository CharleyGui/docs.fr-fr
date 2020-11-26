---
title: 1010 - ActivityCompleted
ms.date: 03/30/2017
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
ms.openlocfilehash: d0ebf32ec1d5fe5b34ffe650d5547891be0eb665
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239911"
---
# <a name="1010---activitycompleted"></a><span data-ttu-id="675a4-102">1010 - ActivityCompleted</span><span class="sxs-lookup"><span data-stu-id="675a4-102">1010 - ActivityCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="675a4-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="675a4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="675a4-104">id</span><span class="sxs-lookup"><span data-stu-id="675a4-104">ID</span></span>|<span data-ttu-id="675a4-105">1010</span><span class="sxs-lookup"><span data-stu-id="675a4-105">1010</span></span>|  
|<span data-ttu-id="675a4-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="675a4-106">Keywords</span></span>|<span data-ttu-id="675a4-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="675a4-107">WFRuntime</span></span>|  
|<span data-ttu-id="675a4-108">Level</span><span class="sxs-lookup"><span data-stu-id="675a4-108">Level</span></span>|<span data-ttu-id="675a4-109">Informations</span><span class="sxs-lookup"><span data-stu-id="675a4-109">Information</span></span>|  
|<span data-ttu-id="675a4-110">Channel</span><span class="sxs-lookup"><span data-stu-id="675a4-110">Channel</span></span>|<span data-ttu-id="675a4-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="675a4-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="675a4-112">Description</span><span class="sxs-lookup"><span data-stu-id="675a4-112">Description</span></span>  

 <span data-ttu-id="675a4-113">Indique que l'exécution d'une activité est terminée.</span><span class="sxs-lookup"><span data-stu-id="675a4-113">Indicates an activity has completed execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="675a4-114">Message</span><span class="sxs-lookup"><span data-stu-id="675a4-114">Message</span></span>  

 <span data-ttu-id="675a4-115">L'activité « %1 », DisplayName : « %2 », InstanceId : « %3 » s'est terminée à l'état « %4 ».</span><span class="sxs-lookup"><span data-stu-id="675a4-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has completed in the '%4' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="675a4-116">Détails</span><span class="sxs-lookup"><span data-stu-id="675a4-116">Details</span></span>  
  
|<span data-ttu-id="675a4-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="675a4-117">Data Item Name</span></span>|<span data-ttu-id="675a4-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="675a4-118">Data Item Type</span></span>|<span data-ttu-id="675a4-119">Description</span><span class="sxs-lookup"><span data-stu-id="675a4-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="675a4-120">Activité</span><span class="sxs-lookup"><span data-stu-id="675a4-120">Activity</span></span>|<span data-ttu-id="675a4-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="675a4-121">xs:string</span></span>|<span data-ttu-id="675a4-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="675a4-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="675a4-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="675a4-123">DisplayName</span></span>|<span data-ttu-id="675a4-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="675a4-124">xs:string</span></span>|<span data-ttu-id="675a4-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="675a4-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="675a4-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="675a4-126">InstanceId</span></span>|<span data-ttu-id="675a4-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="675a4-127">xs:string</span></span>|<span data-ttu-id="675a4-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="675a4-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="675a4-129">State</span><span class="sxs-lookup"><span data-stu-id="675a4-129">State</span></span>|<span data-ttu-id="675a4-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="675a4-130">xs:string</span></span>|<span data-ttu-id="675a4-131">État de l'activité.</span><span class="sxs-lookup"><span data-stu-id="675a4-131">The state of the activity.</span></span>|  
|<span data-ttu-id="675a4-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="675a4-132">AppDomain</span></span>|<span data-ttu-id="675a4-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="675a4-133">xs:string</span></span>|<span data-ttu-id="675a4-134">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="675a4-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
