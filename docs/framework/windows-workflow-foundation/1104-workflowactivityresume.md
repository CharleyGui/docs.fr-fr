---
title: 1104 - WorkflowActivityResume
ms.date: 03/30/2017
ms.assetid: 7fe95d1e-34bd-43ca-b92e-587d2d248fff
ms.openlocfilehash: 2a9c40e2c403d43dc980af116e4b6e98b3b2090b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243558"
---
# <a name="1104---workflowactivityresume"></a><span data-ttu-id="c71d8-102">1104 - WorkflowActivityResume</span><span class="sxs-lookup"><span data-stu-id="c71d8-102">1104 - WorkflowActivityResume</span></span>

## <a name="properties"></a><span data-ttu-id="c71d8-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="c71d8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c71d8-104">id</span><span class="sxs-lookup"><span data-stu-id="c71d8-104">ID</span></span>|<span data-ttu-id="c71d8-105">1104</span><span class="sxs-lookup"><span data-stu-id="c71d8-105">1104</span></span>|  
|<span data-ttu-id="c71d8-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="c71d8-106">Keywords</span></span>|<span data-ttu-id="c71d8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c71d8-107">WFRuntime</span></span>|  
|<span data-ttu-id="c71d8-108">Level</span><span class="sxs-lookup"><span data-stu-id="c71d8-108">Level</span></span>|<span data-ttu-id="c71d8-109">Informations</span><span class="sxs-lookup"><span data-stu-id="c71d8-109">Information</span></span>|  
|<span data-ttu-id="c71d8-110">Channel</span><span class="sxs-lookup"><span data-stu-id="c71d8-110">Channel</span></span>|<span data-ttu-id="c71d8-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="c71d8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c71d8-112">Description</span><span class="sxs-lookup"><span data-stu-id="c71d8-112">Description</span></span>  

 <span data-ttu-id="c71d8-113">Indique qu'une activité du flux de travail a été reprise.</span><span class="sxs-lookup"><span data-stu-id="c71d8-113">Indicates a workflow activity has been resumed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c71d8-114">Message</span><span class="sxs-lookup"><span data-stu-id="c71d8-114">Message</span></span>  

 <span data-ttu-id="c71d8-115">ID WorkflowInstance : « %1 » Activité E2E</span><span class="sxs-lookup"><span data-stu-id="c71d8-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="c71d8-116">Détails</span><span class="sxs-lookup"><span data-stu-id="c71d8-116">Details</span></span>  
  
|<span data-ttu-id="c71d8-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c71d8-117">Data Item Name</span></span>|<span data-ttu-id="c71d8-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c71d8-118">Data Item Type</span></span>|<span data-ttu-id="c71d8-119">Description</span><span class="sxs-lookup"><span data-stu-id="c71d8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c71d8-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="c71d8-120">WorkflowInstanceId</span></span>|<span data-ttu-id="c71d8-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c71d8-121">xs:string</span></span>|<span data-ttu-id="c71d8-122">ID de l'instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="c71d8-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="c71d8-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c71d8-123">AppDomain</span></span>|<span data-ttu-id="c71d8-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c71d8-124">xs:string</span></span>|<span data-ttu-id="c71d8-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c71d8-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
