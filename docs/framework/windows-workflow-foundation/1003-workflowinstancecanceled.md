---
title: 1003 - WorkflowInstanceCanceled
ms.date: 03/30/2017
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
ms.openlocfilehash: bd8abf173ab6588d4a35ba59c6cd14fb53445e9f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239898"
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="e0be9-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="e0be9-102">1003 - WorkflowInstanceCanceled</span></span>

## <a name="properties"></a><span data-ttu-id="e0be9-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="e0be9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e0be9-104">id</span><span class="sxs-lookup"><span data-stu-id="e0be9-104">ID</span></span>|<span data-ttu-id="e0be9-105">1003</span><span class="sxs-lookup"><span data-stu-id="e0be9-105">1003</span></span>|  
|<span data-ttu-id="e0be9-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="e0be9-106">Keywords</span></span>|<span data-ttu-id="e0be9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e0be9-107">WFRuntime</span></span>|  
|<span data-ttu-id="e0be9-108">Level</span><span class="sxs-lookup"><span data-stu-id="e0be9-108">Level</span></span>|<span data-ttu-id="e0be9-109">Informations</span><span class="sxs-lookup"><span data-stu-id="e0be9-109">Information</span></span>|  
|<span data-ttu-id="e0be9-110">Channel</span><span class="sxs-lookup"><span data-stu-id="e0be9-110">Channel</span></span>|<span data-ttu-id="e0be9-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="e0be9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e0be9-112">Description</span><span class="sxs-lookup"><span data-stu-id="e0be9-112">Description</span></span>  

 <span data-ttu-id="e0be9-113">Indique qu'une instance de workflow s'est terminée à l'état Canceled.</span><span class="sxs-lookup"><span data-stu-id="e0be9-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e0be9-114">Message</span><span class="sxs-lookup"><span data-stu-id="e0be9-114">Message</span></span>  

 <span data-ttu-id="e0be9-115">ID WorkflowInstance : « %1 » s'est terminé à l'état Canceled.</span><span class="sxs-lookup"><span data-stu-id="e0be9-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e0be9-116">Détails</span><span class="sxs-lookup"><span data-stu-id="e0be9-116">Details</span></span>  
  
|<span data-ttu-id="e0be9-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="e0be9-117">Data Item Name</span></span>|<span data-ttu-id="e0be9-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="e0be9-118">Data Item Type</span></span>|<span data-ttu-id="e0be9-119">Description</span><span class="sxs-lookup"><span data-stu-id="e0be9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e0be9-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="e0be9-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="e0be9-121">ID d'instance pour le workflow</span><span class="sxs-lookup"><span data-stu-id="e0be9-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="e0be9-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e0be9-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e0be9-123">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e0be9-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
