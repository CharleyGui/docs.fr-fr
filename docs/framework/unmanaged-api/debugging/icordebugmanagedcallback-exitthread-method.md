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
ms.openlocfilehash: 2ccb06b974cb17dff987ba42b647224cdc4c4ff2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688927"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="d59f3-102">ICorDebugManagedCallback::ExitThread, méthode</span><span class="sxs-lookup"><span data-stu-id="d59f3-102">ICorDebugManagedCallback::ExitThread Method</span></span>

<span data-ttu-id="d59f3-103">Notifie le débogueur qu’un thread qui exécutait du code managé s’est arrêté.</span><span class="sxs-lookup"><span data-stu-id="d59f3-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d59f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d59f3-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d59f3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d59f3-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="d59f3-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le thread managé.</span><span class="sxs-lookup"><span data-stu-id="d59f3-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="d59f3-107">dans Pointeur vers un objet ICorDebugThread qui représente le thread managé.</span><span class="sxs-lookup"><span data-stu-id="d59f3-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d59f3-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="d59f3-108">Remarks</span></span>  

 <span data-ttu-id="d59f3-109">Une fois le `ExitThread` rappel déclenché, le thread n’apparaît plus dans les énumérations de thread.</span><span class="sxs-lookup"><span data-stu-id="d59f3-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d59f3-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d59f3-110">Requirements</span></span>  

 <span data-ttu-id="d59f3-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d59f3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d59f3-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d59f3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d59f3-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d59f3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d59f3-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d59f3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d59f3-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d59f3-115">See also</span></span>

- [<span data-ttu-id="d59f3-116">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="d59f3-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
