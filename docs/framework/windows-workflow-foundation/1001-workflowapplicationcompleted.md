---
title: 1001 - WorkflowApplicationCompleted
ms.date: 03/30/2017
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
ms.openlocfilehash: be97991be9b61908a23486da0ef255ebfbdc5485
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239950"
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="20e74-102">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="20e74-102">1001 - WorkflowApplicationCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="20e74-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="20e74-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="20e74-104">id</span><span class="sxs-lookup"><span data-stu-id="20e74-104">ID</span></span>|<span data-ttu-id="20e74-105">1001</span><span class="sxs-lookup"><span data-stu-id="20e74-105">1001</span></span>|  
|<span data-ttu-id="20e74-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="20e74-106">Keywords</span></span>|<span data-ttu-id="20e74-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="20e74-107">WFRuntime</span></span>|  
|<span data-ttu-id="20e74-108">Level</span><span class="sxs-lookup"><span data-stu-id="20e74-108">Level</span></span>|<span data-ttu-id="20e74-109">Informations</span><span class="sxs-lookup"><span data-stu-id="20e74-109">Information</span></span>|  
|<span data-ttu-id="20e74-110">Channel</span><span class="sxs-lookup"><span data-stu-id="20e74-110">Channel</span></span>|<span data-ttu-id="20e74-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="20e74-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="20e74-112">Description</span><span class="sxs-lookup"><span data-stu-id="20e74-112">Description</span></span>  

 <span data-ttu-id="20e74-113">Indique qu'une application de workflow s'est terminée à l'état Closed.</span><span class="sxs-lookup"><span data-stu-id="20e74-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="20e74-114">Message</span><span class="sxs-lookup"><span data-stu-id="20e74-114">Message</span></span>  

 <span data-ttu-id="20e74-115">ID WorkflowInstance : « %1 » s'est terminé à l'état Closed.</span><span class="sxs-lookup"><span data-stu-id="20e74-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="20e74-116">Détails</span><span class="sxs-lookup"><span data-stu-id="20e74-116">Details</span></span>  
  
|<span data-ttu-id="20e74-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="20e74-117">Data Item Name</span></span>|<span data-ttu-id="20e74-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="20e74-118">Data Item Type</span></span>|<span data-ttu-id="20e74-119">Description</span><span class="sxs-lookup"><span data-stu-id="20e74-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="20e74-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="20e74-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="20e74-121">ID d'instance pour le workflow</span><span class="sxs-lookup"><span data-stu-id="20e74-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="20e74-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="20e74-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="20e74-123">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="20e74-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
