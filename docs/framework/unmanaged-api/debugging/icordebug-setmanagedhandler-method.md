---
title: ICorDebug::SetManagedHandler, méthode
ms.date: 03/30/2017
api_name:
- ICorDebug.SetManagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 90eb63b277f5c40053ecc3939890c87adc145251
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738118"
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="d2aea-102">ICorDebug::SetManagedHandler, méthode</span><span class="sxs-lookup"><span data-stu-id="d2aea-102">ICorDebug::SetManagedHandler Method</span></span>
<span data-ttu-id="d2aea-103">Spécifie l’objet de gestionnaire d’événements pour les événements managés.</span><span class="sxs-lookup"><span data-stu-id="d2aea-103">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2aea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2aea-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2aea-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d2aea-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="d2aea-106">[in] Un pointeur vers un [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) objet, qui est l’objet de gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="d2aea-106">[in] A pointer to an [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2aea-107">Notes</span><span class="sxs-lookup"><span data-stu-id="d2aea-107">Remarks</span></span>  
 <span data-ttu-id="d2aea-108">`SetManagedHandler` doit être appelée au moment de la création.</span><span class="sxs-lookup"><span data-stu-id="d2aea-108">`SetManagedHandler` must be called at creation time.</span></span>  
  
 <span data-ttu-id="d2aea-109">Si le `ICorDebugManagedCallback` implémentation ne contient pas suffisamment d’interfaces pour gérer les événements de débogage de l’application est en cours de débogage `SetManagedHandler` retourne un HRESULT d’E_NOINTERFACE.</span><span class="sxs-lookup"><span data-stu-id="d2aea-109">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2aea-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d2aea-110">Requirements</span></span>  
 <span data-ttu-id="d2aea-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2aea-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2aea-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2aea-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2aea-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2aea-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2aea-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2aea-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2aea-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2aea-115">See also</span></span>

- [<span data-ttu-id="d2aea-116">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="d2aea-116">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
