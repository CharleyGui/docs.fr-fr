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
ms.openlocfilehash: 328c10c1895f65b43dc365b1be6b4ec5ef01e720
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777359"
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="1ee2c-102">ICorDebugManagedCallback::Exception, méthode</span><span class="sxs-lookup"><span data-stu-id="1ee2c-102">ICorDebugManagedCallback::Exception Method</span></span>
<span data-ttu-id="1ee2c-103">Notifie le débogueur qu’une exception a été levée à partir du code managé.</span><span class="sxs-lookup"><span data-stu-id="1ee2c-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ee2c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ee2c-104">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ee2c-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="1ee2c-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="1ee2c-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application dans lequel l’exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="1ee2c-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="1ee2c-107">dans Pointeur vers un objet ICorDebugThread qui représente le thread dans lequel l’exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="1ee2c-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="1ee2c-108">dans Si cette valeur est `false`, l’exception n’a pas encore été traitée par l’application ; dans le cas contraire, l’exception n’est pas gérée et met fin au processus.</span><span class="sxs-lookup"><span data-stu-id="1ee2c-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ee2c-109">Notes</span><span class="sxs-lookup"><span data-stu-id="1ee2c-109">Remarks</span></span>  
 <span data-ttu-id="1ee2c-110">L’exception spécifique peut être récupérée à partir de l’objet thread.</span><span class="sxs-lookup"><span data-stu-id="1ee2c-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ee2c-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="1ee2c-111">Requirements</span></span>  
 <span data-ttu-id="1ee2c-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ee2c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ee2c-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ee2c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ee2c-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ee2c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ee2c-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ee2c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ee2c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ee2c-116">See also</span></span>

- [<span data-ttu-id="1ee2c-117">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="1ee2c-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
