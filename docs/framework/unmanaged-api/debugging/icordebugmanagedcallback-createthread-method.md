---
title: ICorDebugManagedCallback::CreateThread, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateThread method
helpviewer_keywords:
- ICorDebugManagedCallback::CreateThread method [.NET Framework debugging]
- CreateThread method [.NET Framework debugging]
ms.assetid: 6b961728-21c4-4e8d-ae81-197458be62f4
topic_type:
- apiref
ms.openlocfilehash: 0dcd6b2efea0e96a341962315bb5c631acef8a10
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781961"
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="b609f-102">ICorDebugManagedCallback::CreateThread, méthode</span><span class="sxs-lookup"><span data-stu-id="b609f-102">ICorDebugManagedCallback::CreateThread Method</span></span>
<span data-ttu-id="b609f-103">Notifie le débogueur qu’un thread a commencé à exécuter du code managé.</span><span class="sxs-lookup"><span data-stu-id="b609f-103">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b609f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b609f-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b609f-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="b609f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="b609f-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application qui contient le thread.</span><span class="sxs-lookup"><span data-stu-id="b609f-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="b609f-107">dans Pointeur vers un objet ICorDebugThread qui représente le thread.</span><span class="sxs-lookup"><span data-stu-id="b609f-107">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b609f-108">Notes</span><span class="sxs-lookup"><span data-stu-id="b609f-108">Remarks</span></span>  
 <span data-ttu-id="b609f-109">Le thread sera positionné au niveau de la première instruction de code managé à exécuter.</span><span class="sxs-lookup"><span data-stu-id="b609f-109">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b609f-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="b609f-110">Requirements</span></span>  
 <span data-ttu-id="b609f-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b609f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b609f-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b609f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b609f-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b609f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b609f-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b609f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b609f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b609f-115">See also</span></span>

- [<span data-ttu-id="b609f-116">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="b609f-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
