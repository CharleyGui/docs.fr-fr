---
title: ICorConfiguration::SetGCThreadControl, méthode
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type:
- apiref
ms.openlocfilehash: f43ee6d9a3832fca1766ec27c9f02d1aab2f5b8d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127772"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="4d38a-102">ICorConfiguration::SetGCThreadControl, méthode</span><span class="sxs-lookup"><span data-stu-id="4d38a-102">ICorConfiguration::SetGCThreadControl Method</span></span>
<span data-ttu-id="4d38a-103">Définit l’interface de rappel pour les threads de planification pour les tâches non-Runtime qui seraient sinon bloquées pour un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4d38a-103">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d38a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d38a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d38a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4d38a-105">Parameters</span></span>  
 `pGCThreadControl`  
 <span data-ttu-id="4d38a-106">dans Pointeur vers un objet [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) qui avertit l’hôte de la suspension des threads pour les tâches qui ne sont pas au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="4d38a-106">[in] A pointer to an [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d38a-107">Notes</span><span class="sxs-lookup"><span data-stu-id="4d38a-107">Remarks</span></span>  
 <span data-ttu-id="4d38a-108">L’hôte peut choisir dans le rappel [IGCThreadControl :: ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) s’il faut replanifier un thread.</span><span class="sxs-lookup"><span data-stu-id="4d38a-108">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d38a-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="4d38a-109">Requirements</span></span>  
 <span data-ttu-id="4d38a-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d38a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d38a-111">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4d38a-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4d38a-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4d38a-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4d38a-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d38a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d38a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d38a-114">See also</span></span>

- [<span data-ttu-id="4d38a-115">ICorConfiguration, interface</span><span class="sxs-lookup"><span data-stu-id="4d38a-115">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
