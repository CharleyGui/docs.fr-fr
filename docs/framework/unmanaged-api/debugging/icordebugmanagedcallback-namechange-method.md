---
title: ICorDebugManagedCallback::NameChange, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.NameChange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type:
- apiref
ms.openlocfilehash: 456a79ec290964df8e9f74fc6ca19ef9aabe1230
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130677"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="650ca-102">ICorDebugManagedCallback::NameChange, méthode</span><span class="sxs-lookup"><span data-stu-id="650ca-102">ICorDebugManagedCallback::NameChange Method</span></span>
<span data-ttu-id="650ca-103">Notifie le débogueur que le nom d’un domaine d’application ou d’un thread a changé.</span><span class="sxs-lookup"><span data-stu-id="650ca-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="650ca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="650ca-104">Syntax</span></span>  
  
```cpp  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="650ca-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="650ca-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="650ca-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application dont le nom a été modifié ou qui contient le thread qui a subi un changement de nom.</span><span class="sxs-lookup"><span data-stu-id="650ca-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="650ca-107">dans Pointeur vers un objet ICorDebugThread qui représente le thread dont le nom a été modifié.</span><span class="sxs-lookup"><span data-stu-id="650ca-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="650ca-108">spécifications</span><span class="sxs-lookup"><span data-stu-id="650ca-108">Requirements</span></span>  
 <span data-ttu-id="650ca-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="650ca-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="650ca-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="650ca-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="650ca-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="650ca-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="650ca-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="650ca-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="650ca-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="650ca-113">See also</span></span>

- [<span data-ttu-id="650ca-114">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="650ca-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
