---
title: ICLRTask::RudeAbort, méthode
ms.date: 03/30/2017
api_name:
- ICLRTask.RudeAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::RudeAbort
helpviewer_keywords:
- RudeAbort method, ICLRTask interface [.NET Framework hosting]
- ICLRTask::RudeAbort method [.NET Framework hosting]
ms.assetid: b5785468-fcd7-4cc3-8a5d-8796337b53fc
topic_type:
- apiref
ms.openlocfilehash: 5d6e19fe307373c2920fd60b04bff482b238c5c4
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762953"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="05371-102">ICLRTask::RudeAbort, méthode</span><span class="sxs-lookup"><span data-stu-id="05371-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="05371-103">Indique au common language runtime (CLR) d’abandonner immédiatement et sans condition la tâche représentée par l’instance d' [interface ICLRTask](iclrtask-interface.md) actuelle.</span><span class="sxs-lookup"><span data-stu-id="05371-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05371-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05371-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();
```  
  
## <a name="return-value"></a><span data-ttu-id="05371-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="05371-105">Return Value</span></span>  
  
|<span data-ttu-id="05371-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="05371-106">HRESULT</span></span>|<span data-ttu-id="05371-107">Description</span><span class="sxs-lookup"><span data-stu-id="05371-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="05371-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="05371-108">S_OK</span></span>|<span data-ttu-id="05371-109">`RudeAbort`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="05371-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="05371-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="05371-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="05371-111">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="05371-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="05371-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="05371-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="05371-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="05371-113">The call timed out.</span></span>|  
|<span data-ttu-id="05371-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="05371-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="05371-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="05371-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="05371-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="05371-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="05371-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="05371-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="05371-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="05371-118">E_FAIL</span></span>|<span data-ttu-id="05371-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="05371-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="05371-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="05371-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="05371-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="05371-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05371-122">Notes</span><span class="sxs-lookup"><span data-stu-id="05371-122">Remarks</span></span>  
 <span data-ttu-id="05371-123">Un hôte appelle `RudeAbort` pour abandonner immédiatement une tâche.</span><span class="sxs-lookup"><span data-stu-id="05371-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="05371-124">Il n’est pas garanti que les finaliseurs et les routines de gestion des exceptions soient exécutées.</span><span class="sxs-lookup"><span data-stu-id="05371-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05371-125">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="05371-125">Requirements</span></span>  
 <span data-ttu-id="05371-126">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05371-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05371-127">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="05371-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05371-128">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="05371-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05371-129">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05371-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05371-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05371-130">See also</span></span>

- [<span data-ttu-id="05371-131">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="05371-131">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="05371-132">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="05371-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="05371-133">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="05371-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="05371-134">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="05371-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
