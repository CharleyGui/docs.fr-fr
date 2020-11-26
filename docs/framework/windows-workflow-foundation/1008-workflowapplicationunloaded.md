---
title: 1008 - WorkflowApplicationUnloaded
ms.date: 03/30/2017
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
ms.openlocfilehash: 6ea121e7901d877d4f0d8f9f5bfd259c2f93696d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239819"
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="c9322-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="c9322-102">1008 - WorkflowApplicationUnloaded</span></span>

## <a name="properties"></a><span data-ttu-id="c9322-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="c9322-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c9322-104">id</span><span class="sxs-lookup"><span data-stu-id="c9322-104">ID</span></span>|<span data-ttu-id="c9322-105">1008</span><span class="sxs-lookup"><span data-stu-id="c9322-105">1008</span></span>|  
|<span data-ttu-id="c9322-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="c9322-106">Keywords</span></span>|<span data-ttu-id="c9322-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c9322-107">WFRuntime</span></span>|  
|<span data-ttu-id="c9322-108">Level</span><span class="sxs-lookup"><span data-stu-id="c9322-108">Level</span></span>|<span data-ttu-id="c9322-109">Informations</span><span class="sxs-lookup"><span data-stu-id="c9322-109">Information</span></span>|  
|<span data-ttu-id="c9322-110">Channel</span><span class="sxs-lookup"><span data-stu-id="c9322-110">Channel</span></span>|<span data-ttu-id="c9322-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="c9322-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c9322-112">Description</span><span class="sxs-lookup"><span data-stu-id="c9322-112">Description</span></span>  

 <span data-ttu-id="c9322-113">Indique qu'une application de workflow a été déchargée.</span><span class="sxs-lookup"><span data-stu-id="c9322-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c9322-114">Message</span><span class="sxs-lookup"><span data-stu-id="c9322-114">Message</span></span>  

 <span data-ttu-id="c9322-115">ID WorkflowInstance : « %1 » était Unloaded.</span><span class="sxs-lookup"><span data-stu-id="c9322-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c9322-116">Détails</span><span class="sxs-lookup"><span data-stu-id="c9322-116">Details</span></span>  
  
|<span data-ttu-id="c9322-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c9322-117">Data Item Name</span></span>|<span data-ttu-id="c9322-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c9322-118">Data Item Type</span></span>|<span data-ttu-id="c9322-119">Description</span><span class="sxs-lookup"><span data-stu-id="c9322-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c9322-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="c9322-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="c9322-121">ID d'instance pour le workflow</span><span class="sxs-lookup"><span data-stu-id="c9322-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="c9322-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c9322-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c9322-123">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c9322-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
