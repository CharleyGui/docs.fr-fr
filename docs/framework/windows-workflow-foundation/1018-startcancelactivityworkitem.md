---
title: 1018 - StartCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
ms.openlocfilehash: c1558e19b0de2dc5d22d4356b0f80c35e5b4fbc1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275503"
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="7555c-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="7555c-102">1018 - StartCancelActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="7555c-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="7555c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7555c-104">id</span><span class="sxs-lookup"><span data-stu-id="7555c-104">ID</span></span>|<span data-ttu-id="7555c-105">1018</span><span class="sxs-lookup"><span data-stu-id="7555c-105">1018</span></span>|  
|<span data-ttu-id="7555c-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="7555c-106">Keywords</span></span>|<span data-ttu-id="7555c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7555c-107">WFRuntime</span></span>|  
|<span data-ttu-id="7555c-108">Level</span><span class="sxs-lookup"><span data-stu-id="7555c-108">Level</span></span>|<span data-ttu-id="7555c-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="7555c-109">Verbose</span></span>|  
|<span data-ttu-id="7555c-110">Channel</span><span class="sxs-lookup"><span data-stu-id="7555c-110">Channel</span></span>|<span data-ttu-id="7555c-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="7555c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7555c-112">Description</span><span class="sxs-lookup"><span data-stu-id="7555c-112">Description</span></span>  

 <span data-ttu-id="7555c-113">Indique qu'un CancelActivityWorkItem démarre l'exécution.</span><span class="sxs-lookup"><span data-stu-id="7555c-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7555c-114">Message</span><span class="sxs-lookup"><span data-stu-id="7555c-114">Message</span></span>  

 <span data-ttu-id="7555c-115">Début de l'exécution d'un CancelActivityWorkItem pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="7555c-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7555c-116">Détails</span><span class="sxs-lookup"><span data-stu-id="7555c-116">Details</span></span>  
  
|<span data-ttu-id="7555c-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="7555c-117">Data Item Name</span></span>|<span data-ttu-id="7555c-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="7555c-118">Data Item Type</span></span>|<span data-ttu-id="7555c-119">Description</span><span class="sxs-lookup"><span data-stu-id="7555c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7555c-120">Activité</span><span class="sxs-lookup"><span data-stu-id="7555c-120">Activity</span></span>|<span data-ttu-id="7555c-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="7555c-121">xs:string</span></span>|<span data-ttu-id="7555c-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="7555c-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="7555c-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="7555c-123">DisplayName</span></span>|<span data-ttu-id="7555c-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="7555c-124">xs:string</span></span>|<span data-ttu-id="7555c-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="7555c-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="7555c-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="7555c-126">InstanceId</span></span>|<span data-ttu-id="7555c-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="7555c-127">xs:string</span></span>|<span data-ttu-id="7555c-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="7555c-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="7555c-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7555c-129">AppDomain</span></span>|<span data-ttu-id="7555c-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="7555c-130">xs:string</span></span>|<span data-ttu-id="7555c-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7555c-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
