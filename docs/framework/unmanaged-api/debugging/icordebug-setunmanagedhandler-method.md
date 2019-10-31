---
title: ICorDebug::SetUnmanagedHandler, méthode
ms.date: 03/30/2017
api_name:
- ICorDebug.SetUnmanagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type:
- apiref
ms.openlocfilehash: 36d314211d95dff6648753f5d550a2cfd402a918
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134044"
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="2971f-102">ICorDebug::SetUnmanagedHandler, méthode</span><span class="sxs-lookup"><span data-stu-id="2971f-102">ICorDebug::SetUnmanagedHandler Method</span></span>
<span data-ttu-id="2971f-103">Spécifie l’objet de gestionnaire d’événements pour les événements non managés.</span><span class="sxs-lookup"><span data-stu-id="2971f-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2971f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2971f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2971f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2971f-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="2971f-106">dans Pointeur vers un objet [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) qui représente le gestionnaire d’événements pour les événements non managés.</span><span class="sxs-lookup"><span data-stu-id="2971f-106">[in] A pointer to an [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2971f-107">Notes</span><span class="sxs-lookup"><span data-stu-id="2971f-107">Remarks</span></span>  
 <span data-ttu-id="2971f-108">L’objet de gestionnaire d’événements pour les événements non managés doit être défini après un appel à [ICorDebug :: Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) et avant tout appel à [ICorDebug :: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) ou [ICorDebug ::D ebugactiveprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span><span class="sxs-lookup"><span data-stu-id="2971f-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="2971f-109">Toutefois, pour des raisons d’héritage, vous n’êtes pas obligé de définir l’objet de gestionnaire d’événements pour les événements non managés tant que le premier événement de débogage natif n’est pas déclenché.</span><span class="sxs-lookup"><span data-stu-id="2971f-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="2971f-110">Plus précisément, si `ICorDebug::CreateProcess` a défini l’indicateur CREATE_SUSPENDED, les événements de débogage natifs ne peuvent pas être distribués tant que le thread principal n’a pas repris.</span><span class="sxs-lookup"><span data-stu-id="2971f-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2971f-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="2971f-111">Requirements</span></span>  
 <span data-ttu-id="2971f-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2971f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2971f-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2971f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2971f-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2971f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2971f-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2971f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2971f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2971f-116">See also</span></span>

- [<span data-ttu-id="2971f-117">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="2971f-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
