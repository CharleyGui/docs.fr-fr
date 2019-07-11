---
title: IHostTask::Start, méthode
ms.date: 03/30/2017
api_name:
- IHostTask.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Start
helpviewer_keywords:
- IHostTask::Start method [.NET Framework hosting]
- Start method, IHostTask interface [.NET Framework hosting]
ms.assetid: b18742b0-d8c4-401c-ae89-e6eccdaa81d0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bc996973a98f3b8596b449e1524d5c93b4456e3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749807"
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="afa08-102">IHostTask::Start, méthode</span><span class="sxs-lookup"><span data-stu-id="afa08-102">IHostTask::Start Method</span></span>
<span data-ttu-id="afa08-103">Demande que l’hôte déplace la tâche représentée par l’actuel [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance à partir d’un suspendu à un état actif, dans lequel le code peut être exécuté.</span><span class="sxs-lookup"><span data-stu-id="afa08-103">Requests that the host move the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afa08-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afa08-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="afa08-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="afa08-105">Return Value</span></span>  
  
|<span data-ttu-id="afa08-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="afa08-106">HRESULT</span></span>|<span data-ttu-id="afa08-107">Description</span><span class="sxs-lookup"><span data-stu-id="afa08-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="afa08-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="afa08-108">S_OK</span></span>|<span data-ttu-id="afa08-109">Start est retournée avec succès.</span><span class="sxs-lookup"><span data-stu-id="afa08-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="afa08-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="afa08-110">E_FAIL</span></span>|<span data-ttu-id="afa08-111">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="afa08-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="afa08-112">Lorsqu’une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="afa08-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="afa08-113">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="afa08-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afa08-114">Notes</span><span class="sxs-lookup"><span data-stu-id="afa08-114">Remarks</span></span>  
 <span data-ttu-id="afa08-115">`Start` Retourne toujours une valeur HRESULT de S_OK, sauf dans les cas où une défaillance irrémédiable s’est produite.</span><span class="sxs-lookup"><span data-stu-id="afa08-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afa08-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="afa08-116">Requirements</span></span>  
 <span data-ttu-id="afa08-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afa08-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afa08-118">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="afa08-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="afa08-119">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="afa08-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="afa08-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afa08-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afa08-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afa08-121">See also</span></span>

- [<span data-ttu-id="afa08-122">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="afa08-122">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="afa08-123">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="afa08-123">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="afa08-124">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="afa08-124">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="afa08-125">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="afa08-125">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
