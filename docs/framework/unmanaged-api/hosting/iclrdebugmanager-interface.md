---
title: ICLRDebugManager, interface
ms.date: 03/30/2017
api_name:
- ICLRDebugManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager
helpviewer_keywords:
- ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type:
- apiref
ms.openlocfilehash: 3836bd349423670a19a19dda67eba75419507a29
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724284"
---
# <a name="iclrdebugmanager-interface"></a><span data-ttu-id="7a8dc-102">ICLRDebugManager, interface</span><span class="sxs-lookup"><span data-stu-id="7a8dc-102">ICLRDebugManager Interface</span></span>

<span data-ttu-id="7a8dc-103">Fournit des méthodes qui permettent à un hôte d’associer un ensemble de tâches à un identificateur et un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="7a8dc-103">Provides methods that allow a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7a8dc-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="7a8dc-104">Methods</span></span>  
  
|<span data-ttu-id="7a8dc-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="7a8dc-105">Method</span></span>|<span data-ttu-id="7a8dc-106">Description</span><span class="sxs-lookup"><span data-stu-id="7a8dc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7a8dc-107">BeginConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="7a8dc-107">BeginConnection Method</span></span>](iclrdebugmanager-beginconnection-method.md)|<span data-ttu-id="7a8dc-108">Établit une nouvelle connexion entre l’hôte et le débogueur pour associer des tâches à un identificateur et un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="7a8dc-108">Establishes a new connection between the host and the debugger to associate tasks with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="7a8dc-109">EndConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="7a8dc-109">EndConnection Method</span></span>](iclrdebugmanager-endconnection-method.md)|<span data-ttu-id="7a8dc-110">Supprime l’association entre une liste de tâches et un identificateur et un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="7a8dc-110">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="7a8dc-111">GetDacl, méthode</span><span class="sxs-lookup"><span data-stu-id="7a8dc-111">GetDacl Method</span></span>](iclrdebugmanager-getdacl-method.md)|<span data-ttu-id="7a8dc-112">Cette méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="7a8dc-112">This method is not implemented.</span></span>|  
|[<span data-ttu-id="7a8dc-113">IsDebuggerAttached, méthode</span><span class="sxs-lookup"><span data-stu-id="7a8dc-113">IsDebuggerAttached Method</span></span>](iclrdebugmanager-isdebuggerattached-method.md)|<span data-ttu-id="7a8dc-114">Obtient une valeur qui indique si un débogueur est attaché au processus.</span><span class="sxs-lookup"><span data-stu-id="7a8dc-114">Gets a value that indicates whether a debugger is attached to the process.</span></span>|  
|[<span data-ttu-id="7a8dc-115">SetConnectionTasks, méthode</span><span class="sxs-lookup"><span data-stu-id="7a8dc-115">SetConnectionTasks Method</span></span>](iclrdebugmanager-setconnectiontasks-method.md)|<span data-ttu-id="7a8dc-116">Associe une liste d’instances d' [ICLRTask](iclrtask-interface.md) à un identificateur et un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="7a8dc-116">Associates a list of [ICLRTask](iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="7a8dc-117">SetDacl, méthode</span><span class="sxs-lookup"><span data-stu-id="7a8dc-117">SetDacl Method</span></span>](iclrdebugmanager-setdacl-method.md)|<span data-ttu-id="7a8dc-118">Cette méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="7a8dc-118">This method is not implemented.</span></span>|  
|[<span data-ttu-id="7a8dc-119">SetSymbolReadingPolicy, méthode</span><span class="sxs-lookup"><span data-stu-id="7a8dc-119">SetSymbolReadingPolicy Method</span></span>](iclrdebugmanager-setsymbolreadingpolicy-method.md)|<span data-ttu-id="7a8dc-120">Définit la stratégie de lecture des fichiers de base de données du programme (PDB).</span><span class="sxs-lookup"><span data-stu-id="7a8dc-120">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="7a8dc-121">La stratégie détermine si les informations sur les numéros de ligne et les fichiers sont incluses dans les piles des appels.</span><span class="sxs-lookup"><span data-stu-id="7a8dc-121">The policy determines whether information about line numbers and files is included in call stacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a8dc-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="7a8dc-122">Remarks</span></span>  

 <span data-ttu-id="7a8dc-123">Dans les scénarios de débogage, un hôte peut souhaiter regrouper des tâches en fonction de sa propre logique de programmation.</span><span class="sxs-lookup"><span data-stu-id="7a8dc-123">In debugging scenarios, a host might want to group tasks according to its own programming logic.</span></span> <span data-ttu-id="7a8dc-124">Par exemple, un regroupement permettrait à un développeur de voir uniquement les tâches requises par les API du développeur, au lieu de voir toutes les tâches en cours d’exécution dans le processus.</span><span class="sxs-lookup"><span data-stu-id="7a8dc-124">For example, a grouping would allow a developer to see only the tasks required by the developer's APIs, instead of seeing every task running in the process.</span></span> <span data-ttu-id="7a8dc-125">`ICLRDebugManager` permet à l’hôte d’implémenter ce type de regroupement.</span><span class="sxs-lookup"><span data-stu-id="7a8dc-125">`ICLRDebugManager` allows the host to implement this kind of grouping.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7a8dc-126">Trois `ICLRDebugManager` méthodes, `BeginConnection` `SetConnectionTasks` et `EndConnection` sont dépendantes les unes des autres.</span><span class="sxs-lookup"><span data-stu-id="7a8dc-126">Three `ICLRDebugManager` methods, `BeginConnection`, `SetConnectionTasks` and `EndConnection`, are dependent upon each other.</span></span> <span data-ttu-id="7a8dc-127">Elles doivent être appelées dans l’ordre donné pour fonctionner comme prévu.</span><span class="sxs-lookup"><span data-stu-id="7a8dc-127">They must be called in the given order to work as expected.</span></span>  
  
 <span data-ttu-id="7a8dc-128">Le regroupement, les identificateurs et les noms conviviaux que l’hôte assigne au regroupement n’ont aucune signification pour le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="7a8dc-128">The grouping, and the identifiers and friendly names that the host assigns to the grouping, have no meaning for the common language runtime (CLR).</span></span> <span data-ttu-id="7a8dc-129">Le CLR transmet simplement les informations au débogueur.</span><span class="sxs-lookup"><span data-stu-id="7a8dc-129">The CLR merely passes the information along to the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a8dc-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7a8dc-130">Requirements</span></span>  

 <span data-ttu-id="7a8dc-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a8dc-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a8dc-132">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7a8dc-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7a8dc-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7a8dc-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7a8dc-134">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a8dc-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a8dc-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a8dc-135">See also</span></span>

- [<span data-ttu-id="7a8dc-136">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="7a8dc-136">Hosting Interfaces</span></span>](hosting-interfaces.md)
