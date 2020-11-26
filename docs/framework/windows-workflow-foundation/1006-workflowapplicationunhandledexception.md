---
title: 1006 - WorkflowApplicationUnhandledException
ms.date: 03/30/2017
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
ms.openlocfilehash: 4bb76a93ec7a07a735def1f1d5dc79decb7792ad
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239832"
---
# <a name="1006---workflowapplicationunhandledexception"></a><span data-ttu-id="76f7f-102">1006 - WorkflowApplicationUnhandledException</span><span class="sxs-lookup"><span data-stu-id="76f7f-102">1006 - WorkflowApplicationUnhandledException</span></span>

## <a name="properties"></a><span data-ttu-id="76f7f-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="76f7f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="76f7f-104">id</span><span class="sxs-lookup"><span data-stu-id="76f7f-104">ID</span></span>|<span data-ttu-id="76f7f-105">1006</span><span class="sxs-lookup"><span data-stu-id="76f7f-105">1006</span></span>|  
|<span data-ttu-id="76f7f-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="76f7f-106">Keywords</span></span>|<span data-ttu-id="76f7f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="76f7f-107">WFRuntime</span></span>|  
|<span data-ttu-id="76f7f-108">Level</span><span class="sxs-lookup"><span data-stu-id="76f7f-108">Level</span></span>|<span data-ttu-id="76f7f-109">Error</span><span class="sxs-lookup"><span data-stu-id="76f7f-109">Error</span></span>|  
|<span data-ttu-id="76f7f-110">Channel</span><span class="sxs-lookup"><span data-stu-id="76f7f-110">Channel</span></span>|<span data-ttu-id="76f7f-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="76f7f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="76f7f-112">Description</span><span class="sxs-lookup"><span data-stu-id="76f7f-112">Description</span></span>  

 <span data-ttu-id="76f7f-113">Indique qu'une application de workflow a rencontré une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="76f7f-113">Indicates a workflow application has encountered an unhandled exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="76f7f-114">Message</span><span class="sxs-lookup"><span data-stu-id="76f7f-114">Message</span></span>  

 <span data-ttu-id="76f7f-115">WorkflowInstance ID : ' %1 'a rencontré une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="76f7f-115">WorkflowInstance Id: '%1' has encountered an unhandled exception.</span></span>  <span data-ttu-id="76f7f-116">L’exception provient de l’activité « %2 », DisplayName : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="76f7f-116">The exception originated from Activity '%2', DisplayName: '%3'.</span></span>  <span data-ttu-id="76f7f-117">L’action suivante sera effectuée : %4.</span><span class="sxs-lookup"><span data-stu-id="76f7f-117">The following action will be taken: %4.</span></span>  
  
## <a name="details"></a><span data-ttu-id="76f7f-118">Détails</span><span class="sxs-lookup"><span data-stu-id="76f7f-118">Details</span></span>  
  
|<span data-ttu-id="76f7f-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="76f7f-119">Data Item Name</span></span>|<span data-ttu-id="76f7f-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="76f7f-120">Data Item Type</span></span>|<span data-ttu-id="76f7f-121">Description</span><span class="sxs-lookup"><span data-stu-id="76f7f-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="76f7f-122">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="76f7f-122">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="76f7f-123">ID d'instance pour le workflow</span><span class="sxs-lookup"><span data-stu-id="76f7f-123">The instance id for the workflow</span></span>|  
|<span data-ttu-id="76f7f-124">Exception</span><span class="sxs-lookup"><span data-stu-id="76f7f-124">Exception</span></span>|`xs:string`|<span data-ttu-id="76f7f-125">Détails de l'exception</span><span class="sxs-lookup"><span data-stu-id="76f7f-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="76f7f-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="76f7f-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="76f7f-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="76f7f-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
