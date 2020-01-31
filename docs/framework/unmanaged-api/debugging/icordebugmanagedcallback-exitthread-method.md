---
title: ICorDebugManagedCallback::ExitThread, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitThread
helpviewer_keywords:
- ExitThread method [.NET Framework debugging]
- ICorDebugManagedCallback::ExitThread method [.NET Framework debugging]
ms.assetid: 62db708b-6cf0-45c5-b897-4b5c75bd2505
topic_type:
- apiref
ms.openlocfilehash: fa649fd1983a76c71d400ad3e6965ac0794da6ed
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781610"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="0888d-102">ICorDebugManagedCallback::ExitThread, méthode</span><span class="sxs-lookup"><span data-stu-id="0888d-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="0888d-103">Notifie le débogueur qu’un thread qui exécutait du code managé s’est arrêté.</span><span class="sxs-lookup"><span data-stu-id="0888d-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0888d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0888d-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0888d-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="0888d-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="0888d-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le thread managé.</span><span class="sxs-lookup"><span data-stu-id="0888d-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="0888d-107">dans Pointeur vers un objet ICorDebugThread qui représente le thread managé.</span><span class="sxs-lookup"><span data-stu-id="0888d-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0888d-108">Notes</span><span class="sxs-lookup"><span data-stu-id="0888d-108">Remarks</span></span>  
 <span data-ttu-id="0888d-109">Une fois le rappel de `ExitThread` déclenché, le thread n’apparaît plus dans les énumérations de thread.</span><span class="sxs-lookup"><span data-stu-id="0888d-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0888d-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="0888d-110">Requirements</span></span>  
 <span data-ttu-id="0888d-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0888d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0888d-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0888d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0888d-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0888d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0888d-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0888d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0888d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0888d-115">See also</span></span>

- [<span data-ttu-id="0888d-116">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="0888d-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
