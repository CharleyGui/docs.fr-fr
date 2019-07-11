---
title: ICorDebugManagedCallback::LoadAssembly, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadAssembly
helpviewer_keywords:
- LoadAssembly method [.NET Framework debugging]
- ICorDebugManagedCallback::LoadAssembly method [.NET Framework debugging]
ms.assetid: 55cb673a-e240-43a6-a406-6912e7c0fe66
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3aa76b88d89e83c400b3f372d846c1a31add255
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761479"
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="1f04d-102">ICorDebugManagedCallback::LoadAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="1f04d-102">ICorDebugManagedCallback::LoadAssembly Method</span></span>
<span data-ttu-id="1f04d-103">Notifie le débogueur qu’un assembly du common language runtime (CLR) a été chargé.</span><span class="sxs-lookup"><span data-stu-id="1f04d-103">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f04d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f04d-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f04d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1f04d-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="1f04d-106">[in] Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application dans lequel l’assembly a été chargé.</span><span class="sxs-lookup"><span data-stu-id="1f04d-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="1f04d-107">[in] Pointeur vers un objet ICorDebugAssembly qui représente l’assembly.</span><span class="sxs-lookup"><span data-stu-id="1f04d-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f04d-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1f04d-108">Requirements</span></span>  
 <span data-ttu-id="1f04d-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f04d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f04d-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f04d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f04d-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f04d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f04d-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f04d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f04d-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f04d-113">See also</span></span>

- [<span data-ttu-id="1f04d-114">UnloadAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="1f04d-114">UnloadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)
- [<span data-ttu-id="1f04d-115">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="1f04d-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
