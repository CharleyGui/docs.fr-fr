---
title: ICorDebugManagedCallback2::FunctionRemapComplete, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapComplete
helpviewer_keywords:
- FunctionRemapComplete method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapComplete method [.NET Framework debugging]
ms.assetid: 5396c4c3-4ec3-4e3a-a38d-d65b21f0a2fc
topic_type:
- apiref
ms.openlocfilehash: c6c1fa12248b9ff871e4a62a1a3584f688f2a921
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781491"
---
# <a name="icordebugmanagedcallback2functionremapcomplete-method"></a><span data-ttu-id="42db0-102">ICorDebugManagedCallback2::FunctionRemapComplete, méthode</span><span class="sxs-lookup"><span data-stu-id="42db0-102">ICorDebugManagedCallback2::FunctionRemapComplete Method</span></span>
<span data-ttu-id="42db0-103">Notifie le débogueur que l’exécution du code a basculé vers une nouvelle version d’une fonction modifiée.</span><span class="sxs-lookup"><span data-stu-id="42db0-103">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42db0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42db0-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionRemapComplete (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42db0-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="42db0-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="42db0-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant la fonction modifiée.</span><span class="sxs-lookup"><span data-stu-id="42db0-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="42db0-107">dans Pointeur vers un objet ICorDebugThread qui représente le thread sur lequel le point d’arrêt de remappage a été rencontré.</span><span class="sxs-lookup"><span data-stu-id="42db0-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pFunction`  
 <span data-ttu-id="42db0-108">dans Pointeur vers un objet ICorDebugFunction qui représente la version de la fonction en cours d’exécution sur le thread.</span><span class="sxs-lookup"><span data-stu-id="42db0-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function currently running on the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42db0-109">Notes</span><span class="sxs-lookup"><span data-stu-id="42db0-109">Remarks</span></span>  
 <span data-ttu-id="42db0-110">Ce rappel donne au débogueur la possibilité de recréer toutes les exécutions pas à pas qui existaient précédemment.</span><span class="sxs-lookup"><span data-stu-id="42db0-110">This callback gives the debugger an opportunity to recreate any steppers that previously existed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42db0-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="42db0-111">Requirements</span></span>  
 <span data-ttu-id="42db0-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42db0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42db0-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42db0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42db0-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42db0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42db0-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42db0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42db0-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42db0-116">See also</span></span>

- [<span data-ttu-id="42db0-117">ICorDebugManagedCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="42db0-117">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="42db0-118">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="42db0-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
