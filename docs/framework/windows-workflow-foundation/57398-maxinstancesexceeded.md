---
title: 57398 - MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: bd490aad24fba4550bc778799cd6f836dcfd466c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289176"
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="7c337-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="7c337-102">57398 - MaxInstancesExceeded</span></span>

## <a name="properties"></a><span data-ttu-id="7c337-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="7c337-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7c337-104">id</span><span class="sxs-lookup"><span data-stu-id="7c337-104">ID</span></span>|<span data-ttu-id="7c337-105">57398</span><span class="sxs-lookup"><span data-stu-id="7c337-105">57398</span></span>|  
|<span data-ttu-id="7c337-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="7c337-106">Keywords</span></span>|<span data-ttu-id="7c337-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="7c337-107">WFServices</span></span>|  
|<span data-ttu-id="7c337-108">Level</span><span class="sxs-lookup"><span data-stu-id="7c337-108">Level</span></span>|<span data-ttu-id="7c337-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="7c337-109">Warning</span></span>|  
|<span data-ttu-id="7c337-110">Channel</span><span class="sxs-lookup"><span data-stu-id="7c337-110">Channel</span></span>|<span data-ttu-id="7c337-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="7c337-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7c337-112">Description</span><span class="sxs-lookup"><span data-stu-id="7c337-112">Description</span></span>  

 <span data-ttu-id="7c337-113">Indique que le système a atteint la limite définie pour la limitation des « MaxConcurrentInstances ».</span><span class="sxs-lookup"><span data-stu-id="7c337-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7c337-114">Message</span><span class="sxs-lookup"><span data-stu-id="7c337-114">Message</span></span>  

 <span data-ttu-id="7c337-115">Le système a atteint la limite définie pour la limitation des 'MaxConcurrentInstances'.</span><span class="sxs-lookup"><span data-stu-id="7c337-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="7c337-116">La limite a été définie sur %1.</span><span class="sxs-lookup"><span data-stu-id="7c337-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="7c337-117">La valeur de limitation peut être modifiée en modifiant l'attribut « maxConcurrentInstances » de l'élément serviceThrottle ou en modifiant la propriété « MaxConcurrentInstances » à l'aide du comportement ServiceThrottlingBehavior.</span><span class="sxs-lookup"><span data-stu-id="7c337-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7c337-118">Détails</span><span class="sxs-lookup"><span data-stu-id="7c337-118">Details</span></span>  
  
|<span data-ttu-id="7c337-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="7c337-119">Data Item Name</span></span>|<span data-ttu-id="7c337-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="7c337-120">Data Item Type</span></span>|<span data-ttu-id="7c337-121">Description</span><span class="sxs-lookup"><span data-stu-id="7c337-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7c337-122">Nom</span><span class="sxs-lookup"><span data-stu-id="7c337-122">Name</span></span>|<span data-ttu-id="7c337-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="7c337-123">xs:string</span></span>|<span data-ttu-id="7c337-124">Nom de l'élément.</span><span class="sxs-lookup"><span data-stu-id="7c337-124">The name of the item.</span></span>|  
|<span data-ttu-id="7c337-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7c337-125">AppDomain</span></span>|<span data-ttu-id="7c337-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="7c337-126">xs:string</span></span>|<span data-ttu-id="7c337-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7c337-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
