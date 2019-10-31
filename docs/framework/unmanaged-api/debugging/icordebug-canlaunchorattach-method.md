---
title: ICorDebug::CanLaunchOrAttach, méthode
ms.date: 03/30/2017
api_name:
- ICorDebug.CanLaunchOrAttach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type:
- apiref
ms.openlocfilehash: 805f9a5d1f2590a06bfa929c152bdfd13900531a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134283"
---
# <a name="icordebugcanlaunchorattach-method"></a><span data-ttu-id="edf21-102">ICorDebug::CanLaunchOrAttach, méthode</span><span class="sxs-lookup"><span data-stu-id="edf21-102">ICorDebug::CanLaunchOrAttach Method</span></span>
<span data-ttu-id="edf21-103">Retourne un HRESULT qui indique si le lancement d’un nouveau processus ou l’attachement au processus existant spécifié est possible dans le contexte de la configuration d’ordinateur et d’exécution actuelle.</span><span class="sxs-lookup"><span data-stu-id="edf21-103">Returns an HRESULT that indicates whether launching a new process or attaching to the specified existing process is possible within the context of the current machine and runtime configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edf21-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="edf21-104">Syntax</span></span>  
  
```cpp  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="edf21-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="edf21-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="edf21-106">dans ID d’un processus existant.</span><span class="sxs-lookup"><span data-stu-id="edf21-106">[in] The ID of an existing process.</span></span>  
  
 `win32DebuggingEnabled`  
 <span data-ttu-id="edf21-107">dans Transmettez `true` si vous envisagez de lancer avec le débogage Win32 activé ou pour attacher le débogage Win32 activé ; Sinon, transmettez `false`.</span><span class="sxs-lookup"><span data-stu-id="edf21-107">[in] Pass in `true` if you plan to launch with Win32 debugging enabled, or to attach with Win32 debugging enabled; otherwise, pass `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="edf21-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="edf21-108">Return Value</span></span>  
 <span data-ttu-id="edf21-109">S_OK si les services de débogage déterminent que le lancement d’un nouveau processus ou l’attachement au processus donné est possible, en fonction des informations relatives à la configuration actuelle de l’ordinateur et de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="edf21-109">S_OK if the debugging services determine that launching a new process or attaching to the given process is possible, given the information about the current machine and runtime configuration.</span></span> <span data-ttu-id="edf21-110">Les valeurs HRESULT possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="edf21-110">Possible HRESULT values are:</span></span>  
  
- <span data-ttu-id="edf21-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="edf21-111">S_OK</span></span>  
  
- <span data-ttu-id="edf21-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span><span class="sxs-lookup"><span data-stu-id="edf21-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span></span>  
  
- <span data-ttu-id="edf21-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span><span class="sxs-lookup"><span data-stu-id="edf21-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span></span>  
  
- <span data-ttu-id="edf21-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span><span class="sxs-lookup"><span data-stu-id="edf21-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edf21-115">Notes</span><span class="sxs-lookup"><span data-stu-id="edf21-115">Remarks</span></span>  
 <span data-ttu-id="edf21-116">Cette méthode est purement informatif.</span><span class="sxs-lookup"><span data-stu-id="edf21-116">This method is purely informational.</span></span> <span data-ttu-id="edf21-117">L’interface ne vous empêche pas de lancer ou de s’attacher à un processus, quelle que soit la valeur retournée par `CanLaunchOrAttach`.</span><span class="sxs-lookup"><span data-stu-id="edf21-117">The interface will not stop you from launching or attaching to a process, regardless of the value returned by `CanLaunchOrAttach`.</span></span>  
  
 <span data-ttu-id="edf21-118">Si vous envisagez de lancer avec le débogage Win32 activé ou si l’attachement avec le débogage Win32 est activé, transmettez `true` pour `win32DebuggingEnabled`.</span><span class="sxs-lookup"><span data-stu-id="edf21-118">If you plan to launch with Win32 debugging enabled or attach with Win32 debugging enabled, pass `true` for `win32DebuggingEnabled`.</span></span> <span data-ttu-id="edf21-119">Le HRESULT retourné par `CanLaunchOrAttach` peut différer si vous utilisez cette option.</span><span class="sxs-lookup"><span data-stu-id="edf21-119">The HRESULT returned by `CanLaunchOrAttach` might differ if you use this option.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edf21-120">spécifications</span><span class="sxs-lookup"><span data-stu-id="edf21-120">Requirements</span></span>  
 <span data-ttu-id="edf21-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edf21-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edf21-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="edf21-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="edf21-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="edf21-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="edf21-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edf21-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edf21-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="edf21-125">See also</span></span>

- [<span data-ttu-id="edf21-126">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="edf21-126">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
