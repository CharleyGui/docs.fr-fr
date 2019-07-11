---
title: ICorDebugManagedCallback2::CreateConnection, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.CreateConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10d0fc0c65d6c479ee4bf7bf527ee33615d53084
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761170"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="f8efc-102">ICorDebugManagedCallback2::CreateConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="f8efc-102">ICorDebugManagedCallback2::CreateConnection Method</span></span>
<span data-ttu-id="f8efc-103">Notifie le débogueur qu’une nouvelle connexion a été créée.</span><span class="sxs-lookup"><span data-stu-id="f8efc-103">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8efc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8efc-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8efc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f8efc-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="f8efc-106">[in] Un pointeur vers un objet « ICorDebugProcess » qui représente le processus dans lequel la connexion a été créée</span><span class="sxs-lookup"><span data-stu-id="f8efc-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="f8efc-107">[in] ID de la nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="f8efc-107">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="f8efc-108">[in] Un pointeur vers le nom de la nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="f8efc-108">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8efc-109">Notes</span><span class="sxs-lookup"><span data-stu-id="f8efc-109">Remarks</span></span>  
 <span data-ttu-id="f8efc-110">Un `CreateConnection` rappel est déclenché dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="f8efc-110">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="f8efc-111">Quand un débogueur est attaché à un processus qui contient les connexions.</span><span class="sxs-lookup"><span data-stu-id="f8efc-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="f8efc-112">Dans ce cas, le runtime générer et distribuer un `CreateConnection` événement et un [ICorDebugManagedCallback2::ChangeConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) événement pour chaque connexion dans le processus.</span><span class="sxs-lookup"><span data-stu-id="f8efc-112">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
- <span data-ttu-id="f8efc-113">Lorsqu’un hôte appelle [ICLRDebugManager::BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) dans le [API d’hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="f8efc-113">When a host calls [ICLRDebugManager::BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8efc-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f8efc-114">Requirements</span></span>  
 <span data-ttu-id="f8efc-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8efc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8efc-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8efc-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8efc-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8efc-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8efc-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8efc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8efc-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8efc-119">See also</span></span>

- [<span data-ttu-id="f8efc-120">ICorDebugManagedCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="f8efc-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="f8efc-121">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="f8efc-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
