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
ms.openlocfilehash: 51d34e68851bc6a60d25f643f63d112396abdc4e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209069"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="f52d0-102">ICorDebugManagedCallback2::CreateConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="f52d0-102">ICorDebugManagedCallback2::CreateConnection Method</span></span>
<span data-ttu-id="f52d0-103">Notifie le débogueur qu’une nouvelle connexion a été créée.</span><span class="sxs-lookup"><span data-stu-id="f52d0-103">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f52d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f52d0-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f52d0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f52d0-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="f52d0-106">dans Pointeur vers un objet « ICorDebugProcess » qui représente le processus dans lequel la connexion a été créée.</span><span class="sxs-lookup"><span data-stu-id="f52d0-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="f52d0-107">dans ID de la nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="f52d0-107">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="f52d0-108">dans Pointeur vers le nom de la nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="f52d0-108">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f52d0-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="f52d0-109">Remarks</span></span>  
 <span data-ttu-id="f52d0-110">Un `CreateConnection` rappel est déclenché dans l’un des cas suivants :</span><span class="sxs-lookup"><span data-stu-id="f52d0-110">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="f52d0-111">Quand un débogueur est attaché à un processus qui contient des connexions.</span><span class="sxs-lookup"><span data-stu-id="f52d0-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="f52d0-112">Dans ce cas, le runtime génère et distribue un `CreateConnection` événement et un événement [ICorDebugManagedCallback2 :: ChangeConnection,](icordebugmanagedcallback2-changeconnection-method.md) pour chaque connexion dans le processus.</span><span class="sxs-lookup"><span data-stu-id="f52d0-112">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
- <span data-ttu-id="f52d0-113">Lorsqu’un hôte appelle [ICLRDebugManager :: BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) dans l' [API d’hébergement](../hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="f52d0-113">When a host calls [ICLRDebugManager::BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f52d0-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f52d0-114">Requirements</span></span>  
 <span data-ttu-id="f52d0-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f52d0-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f52d0-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f52d0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f52d0-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f52d0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f52d0-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f52d0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f52d0-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f52d0-119">See also</span></span>

- [<span data-ttu-id="f52d0-120">ICorDebugManagedCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="f52d0-120">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="f52d0-121">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="f52d0-121">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
