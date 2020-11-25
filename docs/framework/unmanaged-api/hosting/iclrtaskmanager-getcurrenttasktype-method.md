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
ms.openlocfilehash: 684b94471c53701c5ebe1dc7e7593eae16ad50fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728782"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a><span data-ttu-id="f4c30-102">ICLRTaskManager::GetCurrentTaskType, méthode</span><span class="sxs-lookup"><span data-stu-id="f4c30-102">ICLRTaskManager::GetCurrentTaskType Method</span></span>

<span data-ttu-id="f4c30-103">Obtient le type de la tâche en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f4c30-103">Gets the type of the task that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4c30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4c30-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4c30-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f4c30-105">Parameters</span></span>  

 `pTaskType`  
 <span data-ttu-id="f4c30-106">à Pointeur vers une valeur de l’énumération [ETaskType,](etasktype-enumeration.md) qui indique le type de tâche en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f4c30-106">[out] A pointer to a value of the [ETaskType](etasktype-enumeration.md) enumeration that indicates the type of task that is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4c30-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f4c30-107">Requirements</span></span>  

 <span data-ttu-id="f4c30-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4c30-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4c30-109">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f4c30-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f4c30-110">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f4c30-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4c30-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4c30-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4c30-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4c30-112">See also</span></span>

- [<span data-ttu-id="f4c30-113">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="f4c30-113">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
