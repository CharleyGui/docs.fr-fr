---
title: 1101 - WorkflowActivityStart
ms.date: 03/30/2017
ms.assetid: 831cd386-b9b5-47a9-9690-aff6292ff348
ms.openlocfilehash: 6e43b0ab1e2d35657bae43e7239a677643154fa9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238728"
---
# <a name="1101---workflowactivitystart"></a><span data-ttu-id="c34ec-102">1101 - WorkflowActivityStart</span><span class="sxs-lookup"><span data-stu-id="c34ec-102">1101 - WorkflowActivityStart</span></span>

## <a name="properties"></a><span data-ttu-id="c34ec-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="c34ec-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c34ec-104">id</span><span class="sxs-lookup"><span data-stu-id="c34ec-104">ID</span></span>|<span data-ttu-id="c34ec-105">1101</span><span class="sxs-lookup"><span data-stu-id="c34ec-105">1101</span></span>|  
|<span data-ttu-id="c34ec-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="c34ec-106">Keywords</span></span>|<span data-ttu-id="c34ec-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c34ec-107">WFRuntime</span></span>|  
|<span data-ttu-id="c34ec-108">Level</span><span class="sxs-lookup"><span data-stu-id="c34ec-108">Level</span></span>|<span data-ttu-id="c34ec-109">Informations</span><span class="sxs-lookup"><span data-stu-id="c34ec-109">Information</span></span>|  
|<span data-ttu-id="c34ec-110">Channel</span><span class="sxs-lookup"><span data-stu-id="c34ec-110">Channel</span></span>|<span data-ttu-id="c34ec-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="c34ec-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c34ec-112">Description</span><span class="sxs-lookup"><span data-stu-id="c34ec-112">Description</span></span>  

 <span data-ttu-id="c34ec-113">Indique qu'une activité du flux de travail a démarré.</span><span class="sxs-lookup"><span data-stu-id="c34ec-113">Indicates a workflow activity has started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c34ec-114">Message</span><span class="sxs-lookup"><span data-stu-id="c34ec-114">Message</span></span>  

 <span data-ttu-id="c34ec-115">ID WorkflowInstance : « %1 » Activité E2E</span><span class="sxs-lookup"><span data-stu-id="c34ec-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="c34ec-116">Détails</span><span class="sxs-lookup"><span data-stu-id="c34ec-116">Details</span></span>  
  
|<span data-ttu-id="c34ec-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c34ec-117">Data Item Name</span></span>|<span data-ttu-id="c34ec-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c34ec-118">Data Item Type</span></span>|<span data-ttu-id="c34ec-119">Description</span><span class="sxs-lookup"><span data-stu-id="c34ec-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c34ec-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="c34ec-120">WorkflowInstanceId</span></span>|<span data-ttu-id="c34ec-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c34ec-121">xs:string</span></span>|<span data-ttu-id="c34ec-122">ID de l'instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="c34ec-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="c34ec-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c34ec-123">AppDomain</span></span>|<span data-ttu-id="c34ec-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c34ec-124">xs:string</span></span>|<span data-ttu-id="c34ec-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c34ec-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
