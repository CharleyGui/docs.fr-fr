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
ms.openlocfilehash: 54ef1cab27a39de39b39996729be6b8160570745
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788967"
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="0d4f7-102">ICorDebug::SetManagedHandler, méthode</span><span class="sxs-lookup"><span data-stu-id="0d4f7-102">ICorDebug::SetManagedHandler Method</span></span>
<span data-ttu-id="0d4f7-103">Spécifie l’objet de gestionnaire d’événements pour les événements managés.</span><span class="sxs-lookup"><span data-stu-id="0d4f7-103">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d4f7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d4f7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d4f7-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="0d4f7-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="0d4f7-106">dans Pointeur vers un objet [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) , qui est l’objet de gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="0d4f7-106">[in] A pointer to an [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d4f7-107">Notes</span><span class="sxs-lookup"><span data-stu-id="0d4f7-107">Remarks</span></span>  
 <span data-ttu-id="0d4f7-108">`SetManagedHandler` doit être appelée au moment de la création.</span><span class="sxs-lookup"><span data-stu-id="0d4f7-108">`SetManagedHandler` must be called at creation time.</span></span>  
  
 <span data-ttu-id="0d4f7-109">Si l’implémentation de `ICorDebugManagedCallback` ne contient pas d’interfaces suffisantes pour gérer les événements de débogage de l’application en cours de débogage, `SetManagedHandler` retourne un HRESULT de E_NOINTERFACE.</span><span class="sxs-lookup"><span data-stu-id="0d4f7-109">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d4f7-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="0d4f7-110">Requirements</span></span>  
 <span data-ttu-id="0d4f7-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d4f7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d4f7-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d4f7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d4f7-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d4f7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d4f7-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d4f7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d4f7-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d4f7-115">See also</span></span>

- [<span data-ttu-id="0d4f7-116">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="0d4f7-116">ICorDebug Interface</span></span>](icordebug-interface.md)
