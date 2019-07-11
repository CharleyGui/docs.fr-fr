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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 93b52e0faef0fa3cc22283d6b46c5fe5153c3eb2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779863"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="40f15-102">ICorConfiguration::SetGCThreadControl, méthode</span><span class="sxs-lookup"><span data-stu-id="40f15-102">ICorConfiguration::SetGCThreadControl Method</span></span>
<span data-ttu-id="40f15-103">Définit l’interface de rappel pour la planification des threads pour les tâches non-runtime qui seraient sinon bloqués pour un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="40f15-103">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40f15-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40f15-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40f15-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="40f15-105">Parameters</span></span>  
 `pGCThreadControl`  
 <span data-ttu-id="40f15-106">[in] Un pointeur vers un [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) objet qui avertit l’hôte sur la suspension des threads pour les tâches non-runtime.</span><span class="sxs-lookup"><span data-stu-id="40f15-106">[in] A pointer to an [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40f15-107">Notes</span><span class="sxs-lookup"><span data-stu-id="40f15-107">Remarks</span></span>  
 <span data-ttu-id="40f15-108">L’hôte peut choisir dans le [IGCThreadControl::ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) rappel s’il faut replanifier un thread.</span><span class="sxs-lookup"><span data-stu-id="40f15-108">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40f15-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="40f15-109">Requirements</span></span>  
 <span data-ttu-id="40f15-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40f15-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40f15-111">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="40f15-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40f15-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="40f15-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40f15-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40f15-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40f15-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40f15-114">See also</span></span>

- [<span data-ttu-id="40f15-115">ICorConfiguration, interface</span><span class="sxs-lookup"><span data-stu-id="40f15-115">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
