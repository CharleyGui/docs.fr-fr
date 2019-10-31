---
title: ICLRTaskManager::GetCurrentTaskType, méthode
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTaskType
helpviewer_keywords:
- GetCurrentTaskType method [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTaskType method [.NET Framework hosting]
ms.assetid: 6b0d9259-dbe2-45bb-b34d-990f60c73424
topic_type:
- apiref
ms.openlocfilehash: 848255d44ce8637182f18288d30151a3f0df0912
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092162"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a><span data-ttu-id="993b7-102">ICLRTaskManager::GetCurrentTaskType, méthode</span><span class="sxs-lookup"><span data-stu-id="993b7-102">ICLRTaskManager::GetCurrentTaskType Method</span></span>
<span data-ttu-id="993b7-103">Obtient le type de la tâche en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="993b7-103">Gets the type of the task that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="993b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="993b7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="993b7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="993b7-105">Parameters</span></span>  
 `pTaskType`  
 <span data-ttu-id="993b7-106">à Pointeur vers une valeur de l’énumération [ETaskType,](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md) qui indique le type de tâche en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="993b7-106">[out] A pointer to a value of the [ETaskType](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md) enumeration that indicates the type of task that is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="993b7-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="993b7-107">Requirements</span></span>  
 <span data-ttu-id="993b7-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="993b7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="993b7-109">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="993b7-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="993b7-110">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="993b7-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="993b7-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="993b7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="993b7-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="993b7-112">See also</span></span>

- [<span data-ttu-id="993b7-113">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="993b7-113">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
