---
title: 1036 - RuntimeTransactionCompletionRequested
ms.date: 03/30/2017
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
ms.openlocfilehash: 96ea253fd61652a3719eaf8b1a4d31aa88337eeb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294259"
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="23413-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="23413-102">1036 - RuntimeTransactionCompletionRequested</span></span>

## <a name="properties"></a><span data-ttu-id="23413-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="23413-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="23413-104">id</span><span class="sxs-lookup"><span data-stu-id="23413-104">ID</span></span>|<span data-ttu-id="23413-105">1036</span><span class="sxs-lookup"><span data-stu-id="23413-105">1036</span></span>|  
|<span data-ttu-id="23413-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="23413-106">Keywords</span></span>|<span data-ttu-id="23413-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="23413-107">WFRuntime</span></span>|  
|<span data-ttu-id="23413-108">Level</span><span class="sxs-lookup"><span data-stu-id="23413-108">Level</span></span>|<span data-ttu-id="23413-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="23413-109">Verbose</span></span>|  
|<span data-ttu-id="23413-110">Channel</span><span class="sxs-lookup"><span data-stu-id="23413-110">Channel</span></span>|<span data-ttu-id="23413-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="23413-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="23413-112">Description</span><span class="sxs-lookup"><span data-stu-id="23413-112">Description</span></span>  

 <span data-ttu-id="23413-113">Indique qu’une activité a planifié la fin de la transaction runtime.</span><span class="sxs-lookup"><span data-stu-id="23413-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="23413-114">Message</span><span class="sxs-lookup"><span data-stu-id="23413-114">Message</span></span>  

 <span data-ttu-id="23413-115">L’activité « %1 », DisplayName : « %2 », InstanceId : « %3 » a planifié la fin de la transaction runtime.</span><span class="sxs-lookup"><span data-stu-id="23413-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="23413-116">Détails</span><span class="sxs-lookup"><span data-stu-id="23413-116">Details</span></span>  
  
|<span data-ttu-id="23413-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="23413-117">Data Item Name</span></span>|<span data-ttu-id="23413-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="23413-118">Data Item Type</span></span>|<span data-ttu-id="23413-119">Description</span><span class="sxs-lookup"><span data-stu-id="23413-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="23413-120">Activité</span><span class="sxs-lookup"><span data-stu-id="23413-120">Activity</span></span>|<span data-ttu-id="23413-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="23413-121">xs:string</span></span>|<span data-ttu-id="23413-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="23413-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="23413-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="23413-123">DisplayName</span></span>|<span data-ttu-id="23413-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="23413-124">xs:string</span></span>|<span data-ttu-id="23413-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="23413-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="23413-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="23413-126">InstanceId</span></span>|<span data-ttu-id="23413-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="23413-127">xs:string</span></span>|<span data-ttu-id="23413-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="23413-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="23413-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="23413-129">AppDomain</span></span>|<span data-ttu-id="23413-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="23413-130">xs:string</span></span>|<span data-ttu-id="23413-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="23413-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
