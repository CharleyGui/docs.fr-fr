---
title: IHostTaskManager::GetStackGuarantee, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.GetStackGuarantee
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetStackGuarantee
helpviewer_keywords:
- GetStackGuarantee method [.NET Framework hosting]
- IHostTaskManager::GetStackGuarantee method [.NET Framework hosting]
ms.assetid: 8176d732-c25c-4520-811d-e3310f339947
topic_type:
- apiref
ms.openlocfilehash: 22ec34c82d0f8e550dfc8941f2c048ebed6cf1d7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133037"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="7c86c-102">IHostTaskManager::GetStackGuarantee, méthode</span><span class="sxs-lookup"><span data-stu-id="7c86c-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="7c86c-103">Obtient la quantité d’espace de pile dont la disponibilité est garantie après la fin d’une opération de pile, mais avant la fermeture d’un processus.</span><span class="sxs-lookup"><span data-stu-id="7c86c-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c86c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c86c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c86c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7c86c-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="7c86c-106">à Pointeur vers le nombre d’octets disponibles.</span><span class="sxs-lookup"><span data-stu-id="7c86c-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c86c-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="7c86c-107">Requirements</span></span>  
 <span data-ttu-id="7c86c-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c86c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c86c-109">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7c86c-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c86c-110">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7c86c-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c86c-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c86c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c86c-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c86c-112">See also</span></span>

- [<span data-ttu-id="7c86c-113">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="7c86c-113">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
