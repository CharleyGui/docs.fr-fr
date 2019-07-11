---
title: ICorDebugManagedCallback::Exception, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e944a6debf790907b75760c8856ae3a365a84650
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759619"
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="52acf-102">ICorDebugManagedCallback::Exception, méthode</span><span class="sxs-lookup"><span data-stu-id="52acf-102">ICorDebugManagedCallback::Exception Method</span></span>
<span data-ttu-id="52acf-103">Notifie le débogueur qu’une exception a été levée à partir du code managé.</span><span class="sxs-lookup"><span data-stu-id="52acf-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52acf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52acf-104">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52acf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="52acf-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="52acf-106">[in] Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application dans lequel l’exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="52acf-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="52acf-107">[in] Pointeur vers un objet ICorDebugThread qui représente le thread dans lequel l’exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="52acf-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="52acf-108">[in] Si cette valeur est `false`, l’exception n’a pas encore été traitée par l’application ; sinon, l’exception n’est pas gérée et le processus prendra fin.</span><span class="sxs-lookup"><span data-stu-id="52acf-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52acf-109">Notes</span><span class="sxs-lookup"><span data-stu-id="52acf-109">Remarks</span></span>  
 <span data-ttu-id="52acf-110">L’exception spécifique peut être récupérée à partir de l’objet thread.</span><span class="sxs-lookup"><span data-stu-id="52acf-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52acf-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="52acf-111">Requirements</span></span>  
 <span data-ttu-id="52acf-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52acf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52acf-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52acf-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52acf-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52acf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52acf-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52acf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52acf-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52acf-116">See also</span></span>

- [<span data-ttu-id="52acf-117">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="52acf-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
