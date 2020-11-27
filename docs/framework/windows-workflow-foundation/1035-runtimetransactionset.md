---
title: 1035 - RuntimeTransactionSet
ms.date: 03/30/2017
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
ms.openlocfilehash: b8bf8431c4e2b82c6aac95820eb45de2a404e976
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294272"
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="b8130-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="b8130-102">1035 - RuntimeTransactionSet</span></span>

## <a name="properties"></a><span data-ttu-id="b8130-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="b8130-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b8130-104">id</span><span class="sxs-lookup"><span data-stu-id="b8130-104">ID</span></span>|<span data-ttu-id="b8130-105">1035</span><span class="sxs-lookup"><span data-stu-id="b8130-105">1035</span></span>|  
|<span data-ttu-id="b8130-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="b8130-106">Keywords</span></span>|<span data-ttu-id="b8130-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b8130-107">WFRuntime</span></span>|  
|<span data-ttu-id="b8130-108">Level</span><span class="sxs-lookup"><span data-stu-id="b8130-108">Level</span></span>|<span data-ttu-id="b8130-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="b8130-109">Verbose</span></span>|  
|<span data-ttu-id="b8130-110">Channel</span><span class="sxs-lookup"><span data-stu-id="b8130-110">Channel</span></span>|<span data-ttu-id="b8130-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="b8130-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b8130-112">Description</span><span class="sxs-lookup"><span data-stu-id="b8130-112">Description</span></span>  

 <span data-ttu-id="b8130-113">Indique qu'une activité a défini la transaction d'exécution.</span><span class="sxs-lookup"><span data-stu-id="b8130-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b8130-114">Message</span><span class="sxs-lookup"><span data-stu-id="b8130-114">Message</span></span>  

 <span data-ttu-id="b8130-115">La transaction d’exécution a été définie par l’activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="b8130-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="b8130-116">Exécution isolée de l’activité' %4 ', DisplayName : ' %5 ', InstanceId : ' %6 '.</span><span class="sxs-lookup"><span data-stu-id="b8130-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b8130-117">Détails</span><span class="sxs-lookup"><span data-stu-id="b8130-117">Details</span></span>  
  
|<span data-ttu-id="b8130-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="b8130-118">Data Item Name</span></span>|<span data-ttu-id="b8130-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="b8130-119">Data Item Type</span></span>|<span data-ttu-id="b8130-120">Description</span><span class="sxs-lookup"><span data-stu-id="b8130-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b8130-121">Activité</span><span class="sxs-lookup"><span data-stu-id="b8130-121">Activity</span></span>|<span data-ttu-id="b8130-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="b8130-122">xs:string</span></span>|<span data-ttu-id="b8130-123">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="b8130-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="b8130-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="b8130-124">DisplayName</span></span>|<span data-ttu-id="b8130-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="b8130-125">xs:string</span></span>|<span data-ttu-id="b8130-126">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="b8130-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="b8130-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="b8130-127">InstanceId</span></span>|<span data-ttu-id="b8130-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="b8130-128">xs:string</span></span>|<span data-ttu-id="b8130-129">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="b8130-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="b8130-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="b8130-130">IsolatedActivity</span></span>|<span data-ttu-id="b8130-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="b8130-131">xs:string</span></span>|<span data-ttu-id="b8130-132">Nom de type de l’activité dans laquelle la transaction est isolée.</span><span class="sxs-lookup"><span data-stu-id="b8130-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="b8130-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="b8130-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="b8130-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="b8130-134">xs:string</span></span>|<span data-ttu-id="b8130-135">Nom complet de l’activité dans laquelle la transaction est isolée.</span><span class="sxs-lookup"><span data-stu-id="b8130-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="b8130-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="b8130-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="b8130-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="b8130-137">xs:string</span></span>|<span data-ttu-id="b8130-138">ID d’instance de l’activité dans laquelle la transaction est isolée.</span><span class="sxs-lookup"><span data-stu-id="b8130-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="b8130-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b8130-139">AppDomain</span></span>|<span data-ttu-id="b8130-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="b8130-140">xs:string</span></span>|<span data-ttu-id="b8130-141">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b8130-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
