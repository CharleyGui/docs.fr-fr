---
title: 1150 - CompensationState
ms.date: 03/30/2017
ms.assetid: eb015842-cc5a-47be-bce5-6af39e567723
ms.openlocfilehash: 2adb317521b8659c2419e4c04aabf4cf4499b36f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96285107"
---
# <a name="1150---compensationstate"></a><span data-ttu-id="0a215-102">1150 - CompensationState</span><span class="sxs-lookup"><span data-stu-id="0a215-102">1150 - CompensationState</span></span>

## <a name="properties"></a><span data-ttu-id="0a215-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="0a215-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0a215-104">id</span><span class="sxs-lookup"><span data-stu-id="0a215-104">ID</span></span>|<span data-ttu-id="0a215-105">1150</span><span class="sxs-lookup"><span data-stu-id="0a215-105">1150</span></span>|  
|<span data-ttu-id="0a215-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="0a215-106">Keywords</span></span>|<span data-ttu-id="0a215-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="0a215-107">WFActivities</span></span>|  
|<span data-ttu-id="0a215-108">Level</span><span class="sxs-lookup"><span data-stu-id="0a215-108">Level</span></span>|<span data-ttu-id="0a215-109">Informations</span><span class="sxs-lookup"><span data-stu-id="0a215-109">Information</span></span>|  
|<span data-ttu-id="0a215-110">Channel</span><span class="sxs-lookup"><span data-stu-id="0a215-110">Channel</span></span>|<span data-ttu-id="0a215-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="0a215-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0a215-112">Description</span><span class="sxs-lookup"><span data-stu-id="0a215-112">Description</span></span>  

 <span data-ttu-id="0a215-113">Indique un changement d'état d'un CompensableActivity.</span><span class="sxs-lookup"><span data-stu-id="0a215-113">Indicates a change of state in a CompensableActivity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0a215-114">Message</span><span class="sxs-lookup"><span data-stu-id="0a215-114">Message</span></span>  

 <span data-ttu-id="0a215-115">CompensableActivity « %1 » est dans l'état « %2 ».</span><span class="sxs-lookup"><span data-stu-id="0a215-115">CompensableActivity '%1' is in the '%2' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0a215-116">Détails</span><span class="sxs-lookup"><span data-stu-id="0a215-116">Details</span></span>  
  
|<span data-ttu-id="0a215-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="0a215-117">Data Item Name</span></span>|<span data-ttu-id="0a215-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="0a215-118">Data Item Type</span></span>|<span data-ttu-id="0a215-119">Description</span><span class="sxs-lookup"><span data-stu-id="0a215-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0a215-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="0a215-120">DisplayName</span></span>|<span data-ttu-id="0a215-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="0a215-121">xs:string</span></span>|<span data-ttu-id="0a215-122">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="0a215-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="0a215-123">State</span><span class="sxs-lookup"><span data-stu-id="0a215-123">State</span></span>|<span data-ttu-id="0a215-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="0a215-124">xs:string</span></span>|<span data-ttu-id="0a215-125">État de compensation.</span><span class="sxs-lookup"><span data-stu-id="0a215-125">The compensation state.</span></span>|  
|<span data-ttu-id="0a215-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0a215-126">AppDomain</span></span>|<span data-ttu-id="0a215-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="0a215-127">xs:string</span></span>|<span data-ttu-id="0a215-128">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0a215-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
