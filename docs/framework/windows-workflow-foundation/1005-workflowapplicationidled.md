---
title: 1005 - WorkflowApplicationIdled
ms.date: 03/30/2017
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
ms.openlocfilehash: 3b7210246b7fb754145c8aa6128da3183cea9f91
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239859"
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="5f582-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="5f582-102">1005 - WorkflowApplicationIdled</span></span>

## <a name="properties"></a><span data-ttu-id="5f582-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="5f582-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5f582-104">id</span><span class="sxs-lookup"><span data-stu-id="5f582-104">ID</span></span>|<span data-ttu-id="5f582-105">1005</span><span class="sxs-lookup"><span data-stu-id="5f582-105">1005</span></span>|  
|<span data-ttu-id="5f582-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="5f582-106">Keywords</span></span>|<span data-ttu-id="5f582-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="5f582-107">WFRuntime</span></span>|  
|<span data-ttu-id="5f582-108">Level</span><span class="sxs-lookup"><span data-stu-id="5f582-108">Level</span></span>|<span data-ttu-id="5f582-109">Informations</span><span class="sxs-lookup"><span data-stu-id="5f582-109">Information</span></span>|  
|<span data-ttu-id="5f582-110">Channel</span><span class="sxs-lookup"><span data-stu-id="5f582-110">Channel</span></span>|<span data-ttu-id="5f582-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="5f582-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5f582-112">Description</span><span class="sxs-lookup"><span data-stu-id="5f582-112">Description</span></span>  

 <span data-ttu-id="5f582-113">Indique qu'une application de workflow a été inactive.</span><span class="sxs-lookup"><span data-stu-id="5f582-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5f582-114">Message</span><span class="sxs-lookup"><span data-stu-id="5f582-114">Message</span></span>  

 <span data-ttu-id="5f582-115">ID WorkflowApplication : « %1 » est devenu inactif.</span><span class="sxs-lookup"><span data-stu-id="5f582-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5f582-116">Détails</span><span class="sxs-lookup"><span data-stu-id="5f582-116">Details</span></span>  
  
|<span data-ttu-id="5f582-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="5f582-117">Data Item Name</span></span>|<span data-ttu-id="5f582-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="5f582-118">Data Item Type</span></span>|<span data-ttu-id="5f582-119">Description</span><span class="sxs-lookup"><span data-stu-id="5f582-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5f582-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="5f582-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="5f582-121">ID d'application de flux de travail</span><span class="sxs-lookup"><span data-stu-id="5f582-121">The workflow application id</span></span>|  
|<span data-ttu-id="5f582-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5f582-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="5f582-123">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5f582-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
