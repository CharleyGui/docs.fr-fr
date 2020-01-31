---
title: ICorDebugThread2::InterceptCurrentException, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.InterceptCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type:
- apiref
ms.openlocfilehash: c25a03ef5bbba18da31787c911f83a1348badd4b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791456"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a><span data-ttu-id="6d0ce-102">ICorDebugThread2::InterceptCurrentException, méthode</span><span class="sxs-lookup"><span data-stu-id="6d0ce-102">ICorDebugThread2::InterceptCurrentException Method</span></span>
<span data-ttu-id="6d0ce-103">Permet à un débogueur d’intercepter l’exception actuelle sur ce thread.</span><span class="sxs-lookup"><span data-stu-id="6d0ce-103">Allows a debugger to intercept the current exception on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d0ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d0ce-104">Syntax</span></span>  
  
```cpp  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d0ce-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="6d0ce-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="6d0ce-106">dans Pointeur vers un ICorDebugFrame qui représente le frame de pile actif.</span><span class="sxs-lookup"><span data-stu-id="6d0ce-106">[in] A pointer to an ICorDebugFrame that represents the active stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d0ce-107">Notes</span><span class="sxs-lookup"><span data-stu-id="6d0ce-107">Remarks</span></span>  
 <span data-ttu-id="6d0ce-108">La méthode `InterceptCurrentException` peut être appelée entre un rappel d’exception ([ICorDebugManagedCallback :: exception](icordebugmanagedcallback-exception-method.md) ou [ICorDebugManagedCallback2 :: exception](icordebugmanagedcallback2-exception-method.md)) et l’appel associé à [ICorDebugController :: continue](icordebugcontroller-continue-method.md).</span><span class="sxs-lookup"><span data-stu-id="6d0ce-108">The `InterceptCurrentException` method can be called between an exception callback ([ICorDebugManagedCallback::Exception](icordebugmanagedcallback-exception-method.md) or [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md)) and the associated call to [ICorDebugController::Continue](icordebugcontroller-continue-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d0ce-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="6d0ce-109">Requirements</span></span>  
 <span data-ttu-id="6d0ce-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d0ce-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d0ce-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d0ce-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d0ce-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d0ce-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d0ce-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d0ce-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
