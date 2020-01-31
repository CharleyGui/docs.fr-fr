---
title: ICorDebugManagedCallback2::DestroyConnection, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.DestroyConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::DestroyConnection
helpviewer_keywords:
- DestroyConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::DestroyConnection method [.NET Framework debugging]
ms.assetid: cf7940e9-4558-4319-925c-09f6c98c8fcd
topic_type:
- apiref
ms.openlocfilehash: 4f6940f863504a9aedd9539e121c7b3791f746b9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788307"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a><span data-ttu-id="f1a11-102">ICorDebugManagedCallback2::DestroyConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="f1a11-102">ICorDebugManagedCallback2::DestroyConnection Method</span></span>
<span data-ttu-id="f1a11-103">Notifie le débogueur que la connexion spécifiée a été arrêtée.</span><span class="sxs-lookup"><span data-stu-id="f1a11-103">Notifies the debugger that the specified connection has been terminated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1a11-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1a11-104">Syntax</span></span>  
  
```cpp  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1a11-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="f1a11-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="f1a11-106">dans Pointeur vers un objet ICorDebugProcess qui représente le processus contenant la connexion qui a été détruite.</span><span class="sxs-lookup"><span data-stu-id="f1a11-106">[in] A pointer to an ICorDebugProcess object that represents the process containing the connection that was destroyed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="f1a11-107">dans ID de la connexion qui a été détruite.</span><span class="sxs-lookup"><span data-stu-id="f1a11-107">[in] The ID of the connection that was destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1a11-108">Notes</span><span class="sxs-lookup"><span data-stu-id="f1a11-108">Remarks</span></span>  
 <span data-ttu-id="f1a11-109">Un rappel de `DestroyConnection` est déclenché quand un hôte appelle [ICLRDebugManager :: EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) dans l' [API d’hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="f1a11-109">A `DestroyConnection` callback will be fired when a host calls [ICLRDebugManager::EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1a11-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="f1a11-110">Requirements</span></span>  
 <span data-ttu-id="f1a11-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1a11-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1a11-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1a11-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1a11-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1a11-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1a11-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1a11-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1a11-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1a11-115">See also</span></span>

- [<span data-ttu-id="f1a11-116">ICorDebugManagedCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="f1a11-116">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="f1a11-117">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="f1a11-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
