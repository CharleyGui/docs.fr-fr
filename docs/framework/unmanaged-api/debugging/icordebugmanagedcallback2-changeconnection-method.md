---
title: ICorDebugManagedCallback2::ChangeConnection, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ChangeConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type:
- apiref
ms.openlocfilehash: d60644d54373dfb3d1d191900df71d3e5f6547a6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788293"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a><span data-ttu-id="d8efe-102">ICorDebugManagedCallback2::ChangeConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="d8efe-102">ICorDebugManagedCallback2::ChangeConnection Method</span></span>
<span data-ttu-id="d8efe-103">Notifie le débogueur que l’ensemble des tâches associées à la connexion spécifiée a changé.</span><span class="sxs-lookup"><span data-stu-id="d8efe-103">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8efe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8efe-104">Syntax</span></span>  
  
```cpp  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8efe-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="d8efe-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="d8efe-106">dans Pointeur vers un objet « ICorDebugProcess » qui représente le processus contenant la connexion qui a changé.</span><span class="sxs-lookup"><span data-stu-id="d8efe-106">[in] A pointer to an "ICorDebugProcess" object that represents the process containing the connection that changed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="d8efe-107">dans ID de la connexion qui a changé.</span><span class="sxs-lookup"><span data-stu-id="d8efe-107">[in] The ID of the connection that changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8efe-108">Notes</span><span class="sxs-lookup"><span data-stu-id="d8efe-108">Remarks</span></span>  
 <span data-ttu-id="d8efe-109">Un rappel de `ChangeConnection` est déclenché dans l’un des cas suivants :</span><span class="sxs-lookup"><span data-stu-id="d8efe-109">A `ChangeConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="d8efe-110">Quand un débogueur est attaché à un processus qui contient des connexions.</span><span class="sxs-lookup"><span data-stu-id="d8efe-110">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="d8efe-111">Dans ce cas, le runtime génère et distribue un événement [ICorDebugManagedCallback2 :: CreateConnection](icordebugmanagedcallback2-createconnection-method.md) et un événement `ChangeConnection` pour chaque connexion dans le processus.</span><span class="sxs-lookup"><span data-stu-id="d8efe-111">In this case, the runtime will generate and dispatch a [ICorDebugManagedCallback2::CreateConnection](icordebugmanagedcallback2-createconnection-method.md) event and a `ChangeConnection` event for each connection in the process.</span></span> <span data-ttu-id="d8efe-112">Un événement `ChangeConnection` est généré pour chaque connexion existante, que l’ensemble de tâches de cette connexion ait été modifié ou non depuis sa création.</span><span class="sxs-lookup"><span data-stu-id="d8efe-112">A `ChangeConnection` event is generated for every existing connection, regardless of whether that connection’s set of tasks has been changed since its creation.</span></span>  
  
- <span data-ttu-id="d8efe-113">Lorsqu’un hôte appelle [ICLRDebugManager :: SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) dans l' [API d’hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="d8efe-113">When a host calls [ICLRDebugManager::SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
 <span data-ttu-id="d8efe-114">Le débogueur doit analyser tous les threads du processus pour récupérer les nouvelles modifications.</span><span class="sxs-lookup"><span data-stu-id="d8efe-114">The debugger should scan all threads in the process to pick up the new changes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8efe-115">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="d8efe-115">Requirements</span></span>  
 <span data-ttu-id="d8efe-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8efe-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8efe-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8efe-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8efe-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8efe-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8efe-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8efe-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8efe-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8efe-120">See also</span></span>

- [<span data-ttu-id="d8efe-121">ICorDebugManagedCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="d8efe-121">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="d8efe-122">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="d8efe-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
