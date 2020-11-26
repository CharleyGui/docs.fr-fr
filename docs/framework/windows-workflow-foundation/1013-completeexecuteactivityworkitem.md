---
title: 1013 - CompleteExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
ms.openlocfilehash: 654f961088c371ab53e4a81f40e3c63335efb1a8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239586"
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="e5316-102">1013 - CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="e5316-102">1013 - CompleteExecuteActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="e5316-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="e5316-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e5316-104">id</span><span class="sxs-lookup"><span data-stu-id="e5316-104">ID</span></span>|<span data-ttu-id="e5316-105">1013</span><span class="sxs-lookup"><span data-stu-id="e5316-105">1013</span></span>|  
|<span data-ttu-id="e5316-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="e5316-106">Keywords</span></span>|<span data-ttu-id="e5316-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e5316-107">WFRuntime</span></span>|  
|<span data-ttu-id="e5316-108">Level</span><span class="sxs-lookup"><span data-stu-id="e5316-108">Level</span></span>|<span data-ttu-id="e5316-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="e5316-109">Verbose</span></span>|  
|<span data-ttu-id="e5316-110">Channel</span><span class="sxs-lookup"><span data-stu-id="e5316-110">Channel</span></span>|<span data-ttu-id="e5316-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="e5316-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e5316-112">Description</span><span class="sxs-lookup"><span data-stu-id="e5316-112">Description</span></span>  

 <span data-ttu-id="e5316-113">Indique qu'un ExecuteActivityWorkItem est terminé.</span><span class="sxs-lookup"><span data-stu-id="e5316-113">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="e5316-114">Message</span><span class="sxs-lookup"><span data-stu-id="e5316-114">Message</span></span>  

 <span data-ttu-id="e5316-115">ExecuteActivityWorkItem est terminé pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="e5316-115">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e5316-116">Détails</span><span class="sxs-lookup"><span data-stu-id="e5316-116">Details</span></span>  
  
|<span data-ttu-id="e5316-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="e5316-117">Data Item Name</span></span>|<span data-ttu-id="e5316-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="e5316-118">Data Item Type</span></span>|<span data-ttu-id="e5316-119">Description</span><span class="sxs-lookup"><span data-stu-id="e5316-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e5316-120">Activité</span><span class="sxs-lookup"><span data-stu-id="e5316-120">Activity</span></span>|<span data-ttu-id="e5316-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="e5316-121">xs:string</span></span>|<span data-ttu-id="e5316-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="e5316-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="e5316-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e5316-123">DisplayName</span></span>|<span data-ttu-id="e5316-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e5316-124">xs:string</span></span>|<span data-ttu-id="e5316-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="e5316-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="e5316-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="e5316-126">InstanceId</span></span>|<span data-ttu-id="e5316-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="e5316-127">xs:string</span></span>|<span data-ttu-id="e5316-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="e5316-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="e5316-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e5316-129">AppDomain</span></span>|<span data-ttu-id="e5316-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="e5316-130">xs:string</span></span>|<span data-ttu-id="e5316-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e5316-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
