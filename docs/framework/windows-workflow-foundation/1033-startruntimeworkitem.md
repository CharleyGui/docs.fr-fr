---
title: 1033 - StartRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
ms.openlocfilehash: 46a3dc8d313ec72ac90abc2e2e333b274dad2e4c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294298"
---
# <a name="1033---startruntimeworkitem"></a><span data-ttu-id="c07a0-102">1033 - StartRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="c07a0-102">1033 - StartRuntimeWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="c07a0-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="c07a0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c07a0-104">id</span><span class="sxs-lookup"><span data-stu-id="c07a0-104">ID</span></span>|<span data-ttu-id="c07a0-105">1033</span><span class="sxs-lookup"><span data-stu-id="c07a0-105">1033</span></span>|  
|<span data-ttu-id="c07a0-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="c07a0-106">Keywords</span></span>|<span data-ttu-id="c07a0-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c07a0-107">WFRuntime</span></span>|  
|<span data-ttu-id="c07a0-108">Level</span><span class="sxs-lookup"><span data-stu-id="c07a0-108">Level</span></span>|<span data-ttu-id="c07a0-109">Commentaires</span><span class="sxs-lookup"><span data-stu-id="c07a0-109">Verbose</span></span>|  
|<span data-ttu-id="c07a0-110">Channel</span><span class="sxs-lookup"><span data-stu-id="c07a0-110">Channel</span></span>|<span data-ttu-id="c07a0-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="c07a0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c07a0-112">Description</span><span class="sxs-lookup"><span data-stu-id="c07a0-112">Description</span></span>  

 <span data-ttu-id="c07a0-113">Indique qu'un RuntimeWorkItem démarre l'exécution.</span><span class="sxs-lookup"><span data-stu-id="c07a0-113">Indicates a RuntimeWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c07a0-114">Message</span><span class="sxs-lookup"><span data-stu-id="c07a0-114">Message</span></span>  

 <span data-ttu-id="c07a0-115">Début de l’exécution d’un élément de travail runtime pour l’activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="c07a0-115">Starting execution of a runtime work item for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c07a0-116">Détails</span><span class="sxs-lookup"><span data-stu-id="c07a0-116">Details</span></span>  
  
|<span data-ttu-id="c07a0-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c07a0-117">Data Item Name</span></span>|<span data-ttu-id="c07a0-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c07a0-118">Data Item Type</span></span>|<span data-ttu-id="c07a0-119">Description</span><span class="sxs-lookup"><span data-stu-id="c07a0-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c07a0-120">Activité</span><span class="sxs-lookup"><span data-stu-id="c07a0-120">Activity</span></span>|<span data-ttu-id="c07a0-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c07a0-121">xs:string</span></span>|<span data-ttu-id="c07a0-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="c07a0-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="c07a0-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c07a0-123">DisplayName</span></span>|<span data-ttu-id="c07a0-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c07a0-124">xs:string</span></span>|<span data-ttu-id="c07a0-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="c07a0-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="c07a0-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="c07a0-126">InstanceId</span></span>|<span data-ttu-id="c07a0-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="c07a0-127">xs:string</span></span>|<span data-ttu-id="c07a0-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="c07a0-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c07a0-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c07a0-129">AppDomain</span></span>|<span data-ttu-id="c07a0-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="c07a0-130">xs:string</span></span>|<span data-ttu-id="c07a0-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c07a0-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
