---
title: ICorDebugManagedCallback::ExitAppDomain, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitAppDomain
helpviewer_keywords:
- ICorDebugManagedCallback::ExitAppDomain method [.NET Framework debugging]
- ExitAppDomain method [.NET Framework debugging]
ms.assetid: d815486e-b3bd-4fe8-ba28-02abdb4d67ba
topic_type:
- apiref
ms.openlocfilehash: 7bfa71ccff4a65e72a6b548a09d27648b67c0ae5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781854"
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="978bf-102">ICorDebugManagedCallback::ExitAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="978bf-102">ICorDebugManagedCallback::ExitAppDomain Method</span></span>
<span data-ttu-id="978bf-103">Notifie le débogueur qu’un domaine d’application s’est arrêté.</span><span class="sxs-lookup"><span data-stu-id="978bf-103">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="978bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="978bf-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="978bf-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="978bf-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="978bf-106">dans Pointeur vers un objet ICorDebugProcess qui représente le processus qui contient le domaine d’application donné.</span><span class="sxs-lookup"><span data-stu-id="978bf-106">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="978bf-107">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application qui s’est arrêté.</span><span class="sxs-lookup"><span data-stu-id="978bf-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="978bf-108">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="978bf-108">Requirements</span></span>  
 <span data-ttu-id="978bf-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="978bf-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="978bf-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="978bf-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="978bf-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="978bf-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="978bf-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="978bf-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="978bf-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="978bf-113">See also</span></span>

- [<span data-ttu-id="978bf-114">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="978bf-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
