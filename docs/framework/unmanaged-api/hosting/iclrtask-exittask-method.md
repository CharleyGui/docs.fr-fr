---
title: ICLRTask::ExitTask, méthode
ms.date: 03/30/2017
api_name:
- ICLRTask.ExitTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::ExitTask
helpviewer_keywords:
- ExitTask method [.NET Framework hosting]
- ICLRTask::ExitTask method [.NET Framework hosting]
ms.assetid: 746c85a6-4b33-4f72-a2e9-379fdf2e96af
topic_type:
- apiref
ms.openlocfilehash: bcd1cac47e4b59cc47c95145f0ccf60c92ea54fe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690835"
---
# <a name="iclrtaskexittask-method"></a><span data-ttu-id="b8c3e-102">ICLRTask::ExitTask, méthode</span><span class="sxs-lookup"><span data-stu-id="b8c3e-102">ICLRTask::ExitTask Method</span></span>

<span data-ttu-id="b8c3e-103">Avertit le common language runtime (CLR) que la tâche représentée par l’instance d' [ICLRTask](iclrtask-interface.md) actuelle se termine et tente d’arrêter la tâche correctement.</span><span class="sxs-lookup"><span data-stu-id="b8c3e-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](iclrtask-interface.md) instance is ending, and attempts to shut the task down gracefully.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8c3e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8c3e-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b8c3e-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b8c3e-105">Return Value</span></span>  
  
|<span data-ttu-id="b8c3e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b8c3e-106">HRESULT</span></span>|<span data-ttu-id="b8c3e-107">Description</span><span class="sxs-lookup"><span data-stu-id="b8c3e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b8c3e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="b8c3e-108">S_OK</span></span>|<span data-ttu-id="b8c3e-109">`ExitTask` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="b8c3e-109">`ExitTask` returned successfully.</span></span>|  
|<span data-ttu-id="b8c3e-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b8c3e-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b8c3e-111">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="b8c3e-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b8c3e-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b8c3e-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b8c3e-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="b8c3e-113">The call timed out.</span></span>|  
|<span data-ttu-id="b8c3e-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b8c3e-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b8c3e-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="b8c3e-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b8c3e-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b8c3e-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b8c3e-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="b8c3e-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b8c3e-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b8c3e-118">E_FAIL</span></span>|<span data-ttu-id="b8c3e-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b8c3e-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b8c3e-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="b8c3e-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b8c3e-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b8c3e-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8c3e-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="b8c3e-122">Remarks</span></span>  

 <span data-ttu-id="b8c3e-123">`ExitTask` tente un arrêt correct d’une tâche, d’une manière analogue au détachement d’un thread d’une bibliothèque de types non managée.</span><span class="sxs-lookup"><span data-stu-id="b8c3e-123">`ExitTask` attempts a clean shutdown of a task, in a manner analogous to detaching a thread from an unmanaged type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8c3e-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b8c3e-124">Requirements</span></span>  

 <span data-ttu-id="b8c3e-125">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8c3e-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8c3e-126">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b8c3e-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b8c3e-127">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b8c3e-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b8c3e-128">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8c3e-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8c3e-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8c3e-129">See also</span></span>

- [<span data-ttu-id="b8c3e-130">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="b8c3e-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="b8c3e-131">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="b8c3e-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="b8c3e-132">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="b8c3e-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="b8c3e-133">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="b8c3e-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
