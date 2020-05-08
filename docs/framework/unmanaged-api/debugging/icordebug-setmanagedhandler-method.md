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
ms.openlocfilehash: a197d260c55d24f906da7d7f2768bb7ba1ad751f
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895345"
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="161be-102">ICorDebug::SetManagedHandler, méthode</span><span class="sxs-lookup"><span data-stu-id="161be-102">ICorDebug::SetManagedHandler Method</span></span>
<span data-ttu-id="161be-103">Spécifie l’objet de gestionnaire d’événements pour les événements managés.</span><span class="sxs-lookup"><span data-stu-id="161be-103">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="161be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="161be-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="161be-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="161be-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="161be-106">dans Pointeur vers un objet [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) , qui est l’objet de gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="161be-106">[in] A pointer to an [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="161be-107">Notes </span><span class="sxs-lookup"><span data-stu-id="161be-107">Remarks</span></span>  
 <span data-ttu-id="161be-108">`SetManagedHandler`doit être appelé au moment de la création.</span><span class="sxs-lookup"><span data-stu-id="161be-108">`SetManagedHandler` must be called at creation time.</span></span>  
  
 <span data-ttu-id="161be-109">Si l' `ICorDebugManagedCallback` implémentation ne contient pas suffisamment d’interfaces pour gérer les événements de débogage de l’application en cours de débogage `SetManagedHandler` , retourne un HRESULT de E_NOINTERFACE.</span><span class="sxs-lookup"><span data-stu-id="161be-109">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="161be-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="161be-110">Requirements</span></span>  
 <span data-ttu-id="161be-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="161be-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="161be-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="161be-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="161be-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="161be-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="161be-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="161be-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="161be-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="161be-115">See also</span></span>

- [<span data-ttu-id="161be-116">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="161be-116">ICorDebug Interface</span></span>](icordebug-interface.md)
