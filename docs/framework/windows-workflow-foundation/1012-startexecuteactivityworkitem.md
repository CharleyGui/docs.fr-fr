---
title: 1012 - StartExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 29e9b1c6-c5d7-4b58-b59d-a06a923d3c80
ms.openlocfilehash: b9cfceb12d56f93c0f9726849e34f4333f1399ac
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239638"
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="80bbe-102">1012 - StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="80bbe-102">1012 - StartExecuteActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="80bbe-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="80bbe-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="80bbe-104">id</span><span class="sxs-lookup"><span data-stu-id="80bbe-104">ID</span></span>|<span data-ttu-id="80bbe-105">1012</span><span class="sxs-lookup"><span data-stu-id="80bbe-105">1012</span></span>|  
|<span data-ttu-id="80bbe-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="80bbe-106">Keywords</span></span>|<span data-ttu-id="80bbe-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="80bbe-107">WFRuntime</span></span>|  
|<span data-ttu-id="80bbe-108">Level</span><span class="sxs-lookup"><span data-stu-id="80bbe-108">Level</span></span>|<span data-ttu-id="80bbe-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="80bbe-109">Verbose</span></span>|  
|<span data-ttu-id="80bbe-110">Channel</span><span class="sxs-lookup"><span data-stu-id="80bbe-110">Channel</span></span>|<span data-ttu-id="80bbe-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="80bbe-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="80bbe-112">Description</span><span class="sxs-lookup"><span data-stu-id="80bbe-112">Description</span></span>  

 <span data-ttu-id="80bbe-113">Indique qu'un ExecuteActivityWorkItem démarre l'exécution.</span><span class="sxs-lookup"><span data-stu-id="80bbe-113">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="80bbe-114">Message</span><span class="sxs-lookup"><span data-stu-id="80bbe-114">Message</span></span>  

 <span data-ttu-id="80bbe-115">Début de l'exécution d'un ExecuteActivityWorkItem pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="80bbe-115">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="80bbe-116">Détails</span><span class="sxs-lookup"><span data-stu-id="80bbe-116">Details</span></span>  
  
|<span data-ttu-id="80bbe-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="80bbe-117">Data Item Name</span></span>|<span data-ttu-id="80bbe-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="80bbe-118">Data Item Type</span></span>|<span data-ttu-id="80bbe-119">Description</span><span class="sxs-lookup"><span data-stu-id="80bbe-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="80bbe-120">Activité</span><span class="sxs-lookup"><span data-stu-id="80bbe-120">Activity</span></span>|<span data-ttu-id="80bbe-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="80bbe-121">xs:string</span></span>|<span data-ttu-id="80bbe-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="80bbe-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="80bbe-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="80bbe-123">DisplayName</span></span>|<span data-ttu-id="80bbe-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="80bbe-124">xs:string</span></span>|<span data-ttu-id="80bbe-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="80bbe-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="80bbe-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="80bbe-126">InstanceId</span></span>|<span data-ttu-id="80bbe-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="80bbe-127">xs:string</span></span>|<span data-ttu-id="80bbe-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="80bbe-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="80bbe-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="80bbe-129">AppDomain</span></span>|<span data-ttu-id="80bbe-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="80bbe-130">xs:string</span></span>|<span data-ttu-id="80bbe-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="80bbe-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
