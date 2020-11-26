---
title: 1041 - WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: 9995823753fc78ca3f278cd635fcf6c7d2b84325
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238936"
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="b51b1-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="b51b1-102">1041 - WorkflowApplicationPersistableIdle</span></span>

## <a name="properties"></a><span data-ttu-id="b51b1-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="b51b1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b51b1-104">id</span><span class="sxs-lookup"><span data-stu-id="b51b1-104">ID</span></span>|<span data-ttu-id="b51b1-105">1041</span><span class="sxs-lookup"><span data-stu-id="b51b1-105">1041</span></span>|  
|<span data-ttu-id="b51b1-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="b51b1-106">Keywords</span></span>|<span data-ttu-id="b51b1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b51b1-107">WFRuntime</span></span>|  
|<span data-ttu-id="b51b1-108">Level</span><span class="sxs-lookup"><span data-stu-id="b51b1-108">Level</span></span>|<span data-ttu-id="b51b1-109">Informations</span><span class="sxs-lookup"><span data-stu-id="b51b1-109">Information</span></span>|  
|<span data-ttu-id="b51b1-110">Channel</span><span class="sxs-lookup"><span data-stu-id="b51b1-110">Channel</span></span>|<span data-ttu-id="b51b1-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="b51b1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b51b1-112">Description</span><span class="sxs-lookup"><span data-stu-id="b51b1-112">Description</span></span>  

 <span data-ttu-id="b51b1-113">Indique qu'une application de workflow est inactive et persistante.</span><span class="sxs-lookup"><span data-stu-id="b51b1-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="b51b1-114">L'application de workflow sera inactive ou persistante.</span><span class="sxs-lookup"><span data-stu-id="b51b1-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b51b1-115">Message</span><span class="sxs-lookup"><span data-stu-id="b51b1-115">Message</span></span>  

 <span data-ttu-id="b51b1-116">ID WorkflowApplication : « %1 » est inactif et persistable.</span><span class="sxs-lookup"><span data-stu-id="b51b1-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="b51b1-117">L’action suivante sera effectuée : %2.</span><span class="sxs-lookup"><span data-stu-id="b51b1-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b51b1-118">Détails</span><span class="sxs-lookup"><span data-stu-id="b51b1-118">Details</span></span>  
  
|<span data-ttu-id="b51b1-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="b51b1-119">Data Item Name</span></span>|<span data-ttu-id="b51b1-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="b51b1-120">Data Item Type</span></span>|<span data-ttu-id="b51b1-121">Description</span><span class="sxs-lookup"><span data-stu-id="b51b1-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b51b1-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="b51b1-122">WorkflowApplicationId</span></span>|<span data-ttu-id="b51b1-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="b51b1-123">xs:string</span></span>|<span data-ttu-id="b51b1-124">ID d'application de flux de travail</span><span class="sxs-lookup"><span data-stu-id="b51b1-124">The workflow application id</span></span>|  
|<span data-ttu-id="b51b1-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="b51b1-125">ActionTaken</span></span>|<span data-ttu-id="b51b1-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="b51b1-126">xs:string</span></span>|<span data-ttu-id="b51b1-127">Mesure qui sera prise sur l'application de workflow.</span><span class="sxs-lookup"><span data-stu-id="b51b1-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="b51b1-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b51b1-128">AppDomain</span></span>|<span data-ttu-id="b51b1-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="b51b1-129">xs:string</span></span>|<span data-ttu-id="b51b1-130">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b51b1-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
