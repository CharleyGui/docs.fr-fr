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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a59476728280e42f45c416b614e6a721efaf26c8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765246"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a><span data-ttu-id="526c1-102">ICorDebugThread2::InterceptCurrentException, méthode</span><span class="sxs-lookup"><span data-stu-id="526c1-102">ICorDebugThread2::InterceptCurrentException Method</span></span>
<span data-ttu-id="526c1-103">Permet à un débogueur d’intercepter l’exception en cours sur ce thread.</span><span class="sxs-lookup"><span data-stu-id="526c1-103">Allows a debugger to intercept the current exception on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="526c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="526c1-104">Syntax</span></span>  
  
```cpp  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="526c1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="526c1-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="526c1-106">[in] Pointeur vers un ICorDebugFrame qui représente le frame de pile actif.</span><span class="sxs-lookup"><span data-stu-id="526c1-106">[in] A pointer to an ICorDebugFrame that represents the active stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="526c1-107">Notes</span><span class="sxs-lookup"><span data-stu-id="526c1-107">Remarks</span></span>  
 <span data-ttu-id="526c1-108">Le `InterceptCurrentException` méthode peut être appelée entre un rappel d’exception ([ICorDebugManagedCallback::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md) ou [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)) et l’appel associé à [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).</span><span class="sxs-lookup"><span data-stu-id="526c1-108">The `InterceptCurrentException` method can be called between an exception callback ([ICorDebugManagedCallback::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md) or [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)) and the associated call to [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="526c1-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="526c1-109">Requirements</span></span>  
 <span data-ttu-id="526c1-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="526c1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="526c1-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="526c1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="526c1-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="526c1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="526c1-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="526c1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
