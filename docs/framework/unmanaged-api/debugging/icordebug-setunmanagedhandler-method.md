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
ms.openlocfilehash: cafa1c99a8988c199d866796911d1983aabb7208
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785062"
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="4721a-102">ICorDebug::SetUnmanagedHandler, méthode</span><span class="sxs-lookup"><span data-stu-id="4721a-102">ICorDebug::SetUnmanagedHandler Method</span></span>
<span data-ttu-id="4721a-103">Spécifie l’objet de gestionnaire d’événements pour les événements non managés.</span><span class="sxs-lookup"><span data-stu-id="4721a-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4721a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4721a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4721a-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="4721a-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="4721a-106">dans Pointeur vers un objet [ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md) qui représente le gestionnaire d’événements pour les événements non managés.</span><span class="sxs-lookup"><span data-stu-id="4721a-106">[in] A pointer to an [ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4721a-107">Notes</span><span class="sxs-lookup"><span data-stu-id="4721a-107">Remarks</span></span>  
 <span data-ttu-id="4721a-108">L’objet de gestionnaire d’événements pour les événements non managés doit être défini après un appel à [ICorDebug :: Initialize](icordebug-initialize-method.md) et avant tout appel à [ICorDebug :: CreateProcess](icordebug-createprocess-method.md) ou [ICorDebug ::D ebugactiveprocess](icordebug-debugactiveprocess-method.md).</span><span class="sxs-lookup"><span data-stu-id="4721a-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="4721a-109">Toutefois, pour des raisons d’héritage, vous n’êtes pas obligé de définir l’objet de gestionnaire d’événements pour les événements non managés tant que le premier événement de débogage natif n’est pas déclenché.</span><span class="sxs-lookup"><span data-stu-id="4721a-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="4721a-110">Plus précisément, si `ICorDebug::CreateProcess` a défini l’indicateur CREATE_SUSPENDED, les événements de débogage natifs ne peuvent pas être distribués tant que le thread principal n’a pas repris.</span><span class="sxs-lookup"><span data-stu-id="4721a-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4721a-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="4721a-111">Requirements</span></span>  
 <span data-ttu-id="4721a-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4721a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4721a-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4721a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4721a-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4721a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4721a-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4721a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4721a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4721a-116">See also</span></span>

- [<span data-ttu-id="4721a-117">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="4721a-117">ICorDebug Interface</span></span>](icordebug-interface.md)
