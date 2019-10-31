---
title: ICorDebugManagedCallback2::ExceptionUnwind, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ExceptionUnwind
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type:
- apiref
ms.openlocfilehash: fa317e1217ac0a9ca46bfeb312446534b1fca63a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131562"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="d8121-102">ICorDebugManagedCallback2::ExceptionUnwind, méthode</span><span class="sxs-lookup"><span data-stu-id="d8121-102">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>
<span data-ttu-id="d8121-103">Fournit une notification d’État pendant le processus de déroulement de l’exception.</span><span class="sxs-lookup"><span data-stu-id="d8121-103">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8121-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8121-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8121-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d8121-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d8121-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le thread sur lequel l’exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="d8121-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="d8121-107">dans Pointeur vers un objet ICorDebugThread qui représente le thread sur lequel l’exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="d8121-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="d8121-108">dans Valeur de l’énumération CorDebugExceptionUnwindCallbackType, qui spécifie l’événement signalé par le rappel au cours de la phase de déroulement.</span><span class="sxs-lookup"><span data-stu-id="d8121-108">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d8121-109">dans Valeur de l’énumération [CorDebugExceptionFlags,](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) qui spécifie des informations supplémentaires sur l’exception.</span><span class="sxs-lookup"><span data-stu-id="d8121-109">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8121-110">Notes</span><span class="sxs-lookup"><span data-stu-id="d8121-110">Remarks</span></span>  
 <span data-ttu-id="d8121-111">`ExceptionUnwind` est appelé à différents points pendant la phase de déroulement du processus de gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="d8121-111">`ExceptionUnwind` is called at various points during the unwind phase of the exception-handling process.</span></span> <span data-ttu-id="d8121-112">`ExceptionUnwind` peut être appelé plusieurs fois tout en déroulant une seule exception.</span><span class="sxs-lookup"><span data-stu-id="d8121-112">`ExceptionUnwind` can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="d8121-113">Si `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, le pointeur d’instruction se trouve dans le frame de feuille du thread, au point de séquence avant (il peut y avoir plusieurs instructions avant) l’instruction qui a mené à l’exception.</span><span class="sxs-lookup"><span data-stu-id="d8121-113">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8121-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="d8121-114">Requirements</span></span>  
 <span data-ttu-id="d8121-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8121-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8121-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8121-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8121-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8121-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8121-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8121-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8121-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8121-119">See also</span></span>

- [<span data-ttu-id="d8121-120">ICorDebugManagedCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="d8121-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="d8121-121">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="d8121-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
