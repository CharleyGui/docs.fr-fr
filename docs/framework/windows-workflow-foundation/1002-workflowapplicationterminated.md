---
title: 1002 - WorkflowApplicationTerminated
ms.date: 03/30/2017
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
ms.openlocfilehash: e7c92dcc9ce472c50af6f0aa26c59f55d62fbb9f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239937"
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="f9344-102">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="f9344-102">1002 - WorkflowApplicationTerminated</span></span>

## <a name="properties"></a><span data-ttu-id="f9344-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="f9344-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f9344-104">id</span><span class="sxs-lookup"><span data-stu-id="f9344-104">ID</span></span>|<span data-ttu-id="f9344-105">1002</span><span class="sxs-lookup"><span data-stu-id="f9344-105">1002</span></span>|  
|<span data-ttu-id="f9344-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="f9344-106">Keywords</span></span>|<span data-ttu-id="f9344-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f9344-107">WFRuntime</span></span>|  
|<span data-ttu-id="f9344-108">Level</span><span class="sxs-lookup"><span data-stu-id="f9344-108">Level</span></span>|<span data-ttu-id="f9344-109">Informations</span><span class="sxs-lookup"><span data-stu-id="f9344-109">Information</span></span>|  
|<span data-ttu-id="f9344-110">Channel</span><span class="sxs-lookup"><span data-stu-id="f9344-110">Channel</span></span>|<span data-ttu-id="f9344-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="f9344-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f9344-112">Description</span><span class="sxs-lookup"><span data-stu-id="f9344-112">Description</span></span>  

 <span data-ttu-id="f9344-113">Indique qu'une application de workflow s'est arrêtée en l'état Faulted avec une exception.</span><span class="sxs-lookup"><span data-stu-id="f9344-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f9344-114">Message</span><span class="sxs-lookup"><span data-stu-id="f9344-114">Message</span></span>  

 <span data-ttu-id="f9344-115">Identificateur de WorkflowApplication : « %1 » a été arrêté.</span><span class="sxs-lookup"><span data-stu-id="f9344-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="f9344-116">Il s'est terminé dans l'état Faulted avec une exception.</span><span class="sxs-lookup"><span data-stu-id="f9344-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f9344-117">Détails</span><span class="sxs-lookup"><span data-stu-id="f9344-117">Details</span></span>  
  
|<span data-ttu-id="f9344-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="f9344-118">Data Item Name</span></span>|<span data-ttu-id="f9344-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="f9344-119">Data Item Type</span></span>|<span data-ttu-id="f9344-120">Description</span><span class="sxs-lookup"><span data-stu-id="f9344-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f9344-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="f9344-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="f9344-122">ID d'application de flux de travail</span><span class="sxs-lookup"><span data-stu-id="f9344-122">The workflow application id</span></span>|  
|<span data-ttu-id="f9344-123">Exception</span><span class="sxs-lookup"><span data-stu-id="f9344-123">Exception</span></span>|`xs:string`|<span data-ttu-id="f9344-124">Détails de l'exception</span><span class="sxs-lookup"><span data-stu-id="f9344-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="f9344-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f9344-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f9344-126">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f9344-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
