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
ms.openlocfilehash: 0bce14a6853c872d27057b9fffc32b54c59abf13
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723387"
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="7ff2e-102">ICorDebug::SetUnmanagedHandler, méthode</span><span class="sxs-lookup"><span data-stu-id="7ff2e-102">ICorDebug::SetUnmanagedHandler Method</span></span>

<span data-ttu-id="7ff2e-103">Spécifie l’objet de gestionnaire d’événements pour les événements non managés.</span><span class="sxs-lookup"><span data-stu-id="7ff2e-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ff2e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ff2e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ff2e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7ff2e-105">Parameters</span></span>  

 `pCallback`  
 <span data-ttu-id="7ff2e-106">dans Pointeur vers un objet [ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md) qui représente le gestionnaire d’événements pour les événements non managés.</span><span class="sxs-lookup"><span data-stu-id="7ff2e-106">[in] A pointer to an [ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ff2e-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="7ff2e-107">Remarks</span></span>  

 <span data-ttu-id="7ff2e-108">L’objet de gestionnaire d’événements pour les événements non managés doit être défini après un appel à [ICorDebug :: Initialize](icordebug-initialize-method.md) et avant tout appel à [ICorDebug :: CreateProcess](icordebug-createprocess-method.md) ou [ICorDebug ::D ebugactiveprocess](icordebug-debugactiveprocess-method.md).</span><span class="sxs-lookup"><span data-stu-id="7ff2e-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="7ff2e-109">Toutefois, pour des raisons d’héritage, vous n’êtes pas obligé de définir l’objet de gestionnaire d’événements pour les événements non managés tant que le premier événement de débogage natif n’est pas déclenché.</span><span class="sxs-lookup"><span data-stu-id="7ff2e-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="7ff2e-110">En particulier, si `ICorDebug::CreateProcess` a défini l’indicateur CREATE_SUSPENDED, les événements de débogage natifs ne peuvent pas être distribués tant que le thread principal n’a pas repris.</span><span class="sxs-lookup"><span data-stu-id="7ff2e-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ff2e-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7ff2e-111">Requirements</span></span>  

 <span data-ttu-id="7ff2e-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ff2e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ff2e-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7ff2e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ff2e-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ff2e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ff2e-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ff2e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ff2e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ff2e-116">See also</span></span>

- [<span data-ttu-id="7ff2e-117">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="7ff2e-117">ICorDebug Interface</span></span>](icordebug-interface.md)
