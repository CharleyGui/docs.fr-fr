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
ms.openlocfilehash: d87f07e6cadf8c9b5a4d8bb3063333c26e2c4ff1
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379032"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a><span data-ttu-id="3e2fc-102">ICorDebugThread2::InterceptCurrentException, méthode</span><span class="sxs-lookup"><span data-stu-id="3e2fc-102">ICorDebugThread2::InterceptCurrentException Method</span></span>
<span data-ttu-id="3e2fc-103">Permet à un débogueur d’intercepter l’exception actuelle sur ce thread.</span><span class="sxs-lookup"><span data-stu-id="3e2fc-103">Allows a debugger to intercept the current exception on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e2fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e2fc-104">Syntax</span></span>  
  
```cpp  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e2fc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3e2fc-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="3e2fc-106">dans Pointeur vers un ICorDebugFrame qui représente le frame de pile actif.</span><span class="sxs-lookup"><span data-stu-id="3e2fc-106">[in] A pointer to an ICorDebugFrame that represents the active stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e2fc-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="3e2fc-107">Remarks</span></span>  
 <span data-ttu-id="3e2fc-108">La `InterceptCurrentException` méthode peut être appelée entre un rappel d’exception ([ICorDebugManagedCallback :: exception](icordebugmanagedcallback-exception-method.md) ou [ICorDebugManagedCallback2 :: exception](icordebugmanagedcallback2-exception-method.md)) et l’appel associé à [ICorDebugController :: continue](icordebugcontroller-continue-method.md).</span><span class="sxs-lookup"><span data-stu-id="3e2fc-108">The `InterceptCurrentException` method can be called between an exception callback ([ICorDebugManagedCallback::Exception](icordebugmanagedcallback-exception-method.md) or [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md)) and the associated call to [ICorDebugController::Continue](icordebugcontroller-continue-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e2fc-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3e2fc-109">Requirements</span></span>  
 <span data-ttu-id="3e2fc-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e2fc-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e2fc-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e2fc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e2fc-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e2fc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e2fc-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e2fc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
