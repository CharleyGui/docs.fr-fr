---
title: 1026 - ScheduleTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 0d5f86ba-ec21-4129-a726-5432e425384c
ms.openlocfilehash: 7ba2ada1fbd5217592b4e4e3cffd813ffbe978ac
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275243"
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="96832-102">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="96832-102">1026 - ScheduleTransactionContextWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="96832-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="96832-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="96832-104">id</span><span class="sxs-lookup"><span data-stu-id="96832-104">ID</span></span>|<span data-ttu-id="96832-105">1026</span><span class="sxs-lookup"><span data-stu-id="96832-105">1026</span></span>|  
|<span data-ttu-id="96832-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="96832-106">Keywords</span></span>|<span data-ttu-id="96832-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="96832-107">WFRuntime</span></span>|  
|<span data-ttu-id="96832-108">Level</span><span class="sxs-lookup"><span data-stu-id="96832-108">Level</span></span>|<span data-ttu-id="96832-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="96832-109">Verbose</span></span>|  
|<span data-ttu-id="96832-110">Channel</span><span class="sxs-lookup"><span data-stu-id="96832-110">Channel</span></span>|<span data-ttu-id="96832-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="96832-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="96832-112">Description</span><span class="sxs-lookup"><span data-stu-id="96832-112">Description</span></span>  

 <span data-ttu-id="96832-113">Indique qu’un TransactionContextWorkItem a été planifié.</span><span class="sxs-lookup"><span data-stu-id="96832-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="96832-114">Message</span><span class="sxs-lookup"><span data-stu-id="96832-114">Message</span></span>  

 <span data-ttu-id="96832-115">TransactionContextWorkItem a été planifié pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="96832-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="96832-116">Détails</span><span class="sxs-lookup"><span data-stu-id="96832-116">Details</span></span>  
  
|<span data-ttu-id="96832-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="96832-117">Data Item Name</span></span>|<span data-ttu-id="96832-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="96832-118">Data Item Type</span></span>|<span data-ttu-id="96832-119">Description</span><span class="sxs-lookup"><span data-stu-id="96832-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="96832-120">Activité</span><span class="sxs-lookup"><span data-stu-id="96832-120">Activity</span></span>|<span data-ttu-id="96832-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="96832-121">xs:string</span></span>|<span data-ttu-id="96832-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="96832-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="96832-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="96832-123">DisplayName</span></span>|<span data-ttu-id="96832-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="96832-124">xs:string</span></span>|<span data-ttu-id="96832-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="96832-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="96832-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="96832-126">InstanceId</span></span>|<span data-ttu-id="96832-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="96832-127">xs:string</span></span>|<span data-ttu-id="96832-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="96832-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="96832-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="96832-129">AppDomain</span></span>|<span data-ttu-id="96832-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="96832-130">xs:string</span></span>|<span data-ttu-id="96832-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="96832-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
