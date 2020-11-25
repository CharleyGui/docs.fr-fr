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
ms.openlocfilehash: d725cbe89e0631630affb6b0540a7d5f57ab6b89
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720111"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a><span data-ttu-id="ab525-102">ICorDebugManagedCallback2::DestroyConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="ab525-102">ICorDebugManagedCallback2::DestroyConnection Method</span></span>

<span data-ttu-id="ab525-103">Notifie le débogueur que la connexion spécifiée a été arrêtée.</span><span class="sxs-lookup"><span data-stu-id="ab525-103">Notifies the debugger that the specified connection has been terminated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab525-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab525-104">Syntax</span></span>  
  
```cpp  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab525-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ab525-105">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="ab525-106">dans Pointeur vers un objet ICorDebugProcess qui représente le processus contenant la connexion qui a été détruite.</span><span class="sxs-lookup"><span data-stu-id="ab525-106">[in] A pointer to an ICorDebugProcess object that represents the process containing the connection that was destroyed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="ab525-107">dans ID de la connexion qui a été détruite.</span><span class="sxs-lookup"><span data-stu-id="ab525-107">[in] The ID of the connection that was destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab525-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="ab525-108">Remarks</span></span>  

 <span data-ttu-id="ab525-109">Un `DestroyConnection` rappel est déclenché quand un hôte appelle [ICLRDebugManager :: EndConnection](../hosting/iclrdebugmanager-endconnection-method.md) dans l' [API d’hébergement](../hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="ab525-109">A `DestroyConnection` callback will be fired when a host calls [ICLRDebugManager::EndConnection](../hosting/iclrdebugmanager-endconnection-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab525-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ab525-110">Requirements</span></span>  

 <span data-ttu-id="ab525-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab525-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab525-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab525-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab525-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab525-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab525-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab525-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab525-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab525-115">See also</span></span>

- [<span data-ttu-id="ab525-116">ICorDebugManagedCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="ab525-116">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="ab525-117">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="ab525-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
