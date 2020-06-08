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
ms.openlocfilehash: 8e31f0a649fd1ca80d6557a0a7176549c67bf203
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501922"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a><span data-ttu-id="e0e36-102">ICorDebugManagedCallback2::CreateConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="e0e36-102">ICorDebugManagedCallback2::CreateConnection Method</span></span>
<span data-ttu-id="e0e36-103">Notifie le débogueur qu’une nouvelle connexion a été créée.</span><span class="sxs-lookup"><span data-stu-id="e0e36-103">Notifies the debugger that a new connection has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0e36-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0e36-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0e36-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e0e36-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="e0e36-106">dans Pointeur vers un objet « ICorDebugProcess » qui représente le processus dans lequel la connexion a été créée.</span><span class="sxs-lookup"><span data-stu-id="e0e36-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the connection was created</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="e0e36-107">dans ID de la nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="e0e36-107">[in] The ID of the new connection.</span></span>  
  
 `pConnName`  
 <span data-ttu-id="e0e36-108">dans Pointeur vers le nom de la nouvelle connexion.</span><span class="sxs-lookup"><span data-stu-id="e0e36-108">[in] A pointer to the name of the new connection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0e36-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="e0e36-109">Remarks</span></span>  
 <span data-ttu-id="e0e36-110">Un `CreateConnection` rappel est déclenché dans l’un des cas suivants :</span><span class="sxs-lookup"><span data-stu-id="e0e36-110">A `CreateConnection` callback will be fired in either of the following cases:</span></span>  
  
- <span data-ttu-id="e0e36-111">Quand un débogueur est attaché à un processus qui contient des connexions.</span><span class="sxs-lookup"><span data-stu-id="e0e36-111">When a debugger attaches to a process that contains connections.</span></span> <span data-ttu-id="e0e36-112">Dans ce cas, le runtime génère et distribue un `CreateConnection` événement et un événement [ICorDebugManagedCallback2 :: ChangeConnection,](icordebugmanagedcallback2-changeconnection-method.md) pour chaque connexion dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e0e36-112">In this case, the runtime will generate and dispatch a `CreateConnection` event and a [ICorDebugManagedCallback2::ChangeConnection](icordebugmanagedcallback2-changeconnection-method.md) event for each connection in the process.</span></span>  
  
- <span data-ttu-id="e0e36-113">Lorsqu’un hôte appelle [ICLRDebugManager :: BeginConnection](../hosting/iclrdebugmanager-beginconnection-method.md) dans l' [API d’hébergement](../hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="e0e36-113">When a host calls [ICLRDebugManager::BeginConnection](../hosting/iclrdebugmanager-beginconnection-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0e36-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e0e36-114">Requirements</span></span>  
 <span data-ttu-id="e0e36-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0e36-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0e36-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0e36-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0e36-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0e36-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0e36-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0e36-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0e36-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0e36-119">See also</span></span>

- [<span data-ttu-id="e0e36-120">ICorDebugManagedCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="e0e36-120">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="e0e36-121">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="e0e36-121">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
