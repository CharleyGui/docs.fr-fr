---
title: ICorDebugManagedCallback::UnloadClass, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadClass
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadClass method [.NET Framework debugging]
- UnloadClass method [.NET Framework debugging]
ms.assetid: 66a59b18-ce9a-41f4-b23b-4dd6753d6d36
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 629a4850d47940633c8c69a7e464cfae315b3c56
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761248"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="561fc-102">ICorDebugManagedCallback::UnloadClass, méthode</span><span class="sxs-lookup"><span data-stu-id="561fc-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="561fc-103">Notifie le débogueur qu’une classe est déchargée.</span><span class="sxs-lookup"><span data-stu-id="561fc-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="561fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="561fc-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="561fc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="561fc-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="561fc-106">[in] Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant la classe.</span><span class="sxs-lookup"><span data-stu-id="561fc-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="561fc-107">[in] Pointeur vers un objet ICorDebugClass qui représente la classe.</span><span class="sxs-lookup"><span data-stu-id="561fc-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="561fc-108">Notes</span><span class="sxs-lookup"><span data-stu-id="561fc-108">Remarks</span></span>  
 <span data-ttu-id="561fc-109">La classe ne doit pas être référencée après cet appel.</span><span class="sxs-lookup"><span data-stu-id="561fc-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="561fc-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="561fc-110">Requirements</span></span>  
 <span data-ttu-id="561fc-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="561fc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="561fc-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="561fc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="561fc-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="561fc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="561fc-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="561fc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="561fc-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="561fc-115">See also</span></span>

- [<span data-ttu-id="561fc-116">LoadClass, méthode</span><span class="sxs-lookup"><span data-stu-id="561fc-116">LoadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="561fc-117">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="561fc-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
