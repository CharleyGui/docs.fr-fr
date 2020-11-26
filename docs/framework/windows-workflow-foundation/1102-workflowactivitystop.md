---
title: 1102 - WorkflowActivityStop
ms.date: 03/30/2017
ms.assetid: 285e5cb8-e90d-4914-ac06-e9b176ffefa2
ms.openlocfilehash: 7b5c7874946ae494f41e73f3e7c90f3944a3521d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238689"
---
# <a name="1102---workflowactivitystop"></a><span data-ttu-id="edbfd-102">1102 - WorkflowActivityStop</span><span class="sxs-lookup"><span data-stu-id="edbfd-102">1102 - WorkflowActivityStop</span></span>

## <a name="properties"></a><span data-ttu-id="edbfd-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="edbfd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="edbfd-104">id</span><span class="sxs-lookup"><span data-stu-id="edbfd-104">ID</span></span>|<span data-ttu-id="edbfd-105">1102</span><span class="sxs-lookup"><span data-stu-id="edbfd-105">1102</span></span>|  
|<span data-ttu-id="edbfd-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="edbfd-106">Keywords</span></span>|<span data-ttu-id="edbfd-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="edbfd-107">WFRuntime</span></span>|  
|<span data-ttu-id="edbfd-108">Level</span><span class="sxs-lookup"><span data-stu-id="edbfd-108">Level</span></span>|<span data-ttu-id="edbfd-109">Informations</span><span class="sxs-lookup"><span data-stu-id="edbfd-109">Information</span></span>|  
|<span data-ttu-id="edbfd-110">Channel</span><span class="sxs-lookup"><span data-stu-id="edbfd-110">Channel</span></span>|<span data-ttu-id="edbfd-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="edbfd-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="edbfd-112">Description</span><span class="sxs-lookup"><span data-stu-id="edbfd-112">Description</span></span>  

 <span data-ttu-id="edbfd-113">Indique qu'une activité du flux de travail s'est arrêtée.</span><span class="sxs-lookup"><span data-stu-id="edbfd-113">Indicates a workflow activity has stopped.</span></span>  
  
## <a name="message"></a><span data-ttu-id="edbfd-114">Message</span><span class="sxs-lookup"><span data-stu-id="edbfd-114">Message</span></span>  

 <span data-ttu-id="edbfd-115">ID WorkflowInstance : « %1 » Activité E2E</span><span class="sxs-lookup"><span data-stu-id="edbfd-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="edbfd-116">Détails</span><span class="sxs-lookup"><span data-stu-id="edbfd-116">Details</span></span>  
  
|<span data-ttu-id="edbfd-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="edbfd-117">Data Item Name</span></span>|<span data-ttu-id="edbfd-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="edbfd-118">Data Item Type</span></span>|<span data-ttu-id="edbfd-119">Description</span><span class="sxs-lookup"><span data-stu-id="edbfd-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="edbfd-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="edbfd-120">WorkflowInstanceId</span></span>|<span data-ttu-id="edbfd-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="edbfd-121">xs:string</span></span>|<span data-ttu-id="edbfd-122">ID de l'instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="edbfd-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="edbfd-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="edbfd-123">AppDomain</span></span>|<span data-ttu-id="edbfd-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="edbfd-124">xs:string</span></span>|<span data-ttu-id="edbfd-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="edbfd-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
