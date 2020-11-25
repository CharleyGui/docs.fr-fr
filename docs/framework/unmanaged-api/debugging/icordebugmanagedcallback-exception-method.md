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
ms.openlocfilehash: 05fed13a556cbcc3b8362e41d73c2b659b1e5eeb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731785"
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="ce767-102">ICorDebugManagedCallback::Exception, méthode</span><span class="sxs-lookup"><span data-stu-id="ce767-102">ICorDebugManagedCallback::Exception Method</span></span>

<span data-ttu-id="ce767-103">Notifie le débogueur qu’une exception a été levée à partir du code managé.</span><span class="sxs-lookup"><span data-stu-id="ce767-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce767-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce767-104">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce767-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ce767-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="ce767-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application dans lequel l’exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="ce767-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="ce767-107">dans Pointeur vers un objet ICorDebugThread qui représente le thread dans lequel l’exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="ce767-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="ce767-108">dans Si cette valeur est `false` , l’exception n’a pas encore été traitée par l’application ; sinon, l’exception n’est pas gérée et met fin au processus.</span><span class="sxs-lookup"><span data-stu-id="ce767-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce767-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="ce767-109">Remarks</span></span>  

 <span data-ttu-id="ce767-110">L’exception spécifique peut être récupérée à partir de l’objet thread.</span><span class="sxs-lookup"><span data-stu-id="ce767-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce767-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ce767-111">Requirements</span></span>  

 <span data-ttu-id="ce767-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce767-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce767-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce767-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce767-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce767-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce767-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce767-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce767-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce767-116">See also</span></span>

- [<span data-ttu-id="ce767-117">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="ce767-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
