---
title: ICorDebugRemote::DebugActiveProcessEx, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.DebugActiveProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type:
- apiref
ms.openlocfilehash: b78bff2994cefc6c35a4bd59133338392c3a1b24
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791974"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="a6b9b-102">ICorDebugRemote::DebugActiveProcessEx, méthode</span><span class="sxs-lookup"><span data-stu-id="a6b9b-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="a6b9b-103">Lance un processus sur un ordinateur distant sous le débogueur.</span><span class="sxs-lookup"><span data-stu-id="a6b9b-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6b9b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6b9b-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6b9b-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="a6b9b-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="a6b9b-106">dans Pointeur vers une [interface ICorDebugRemoteTarget](icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a6b9b-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="a6b9b-107">Ce paramètre est utilisé pour déterminer l’ordinateur sur lequel le processus est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a6b9b-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="a6b9b-108">dans ID du processus auquel le débogueur doit être attaché.</span><span class="sxs-lookup"><span data-stu-id="a6b9b-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="a6b9b-109">[in] `true` si le débogueur doit se comporter comme le débogueur Win32 pour le processus et pour distribuer les rappels non managés ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="a6b9b-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="a6b9b-110">à Pointeur vers l’adresse d’un objet « ICorDebugProcess » qui représente le processus auquel le débogueur a été attaché.</span><span class="sxs-lookup"><span data-stu-id="a6b9b-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6b9b-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a6b9b-111">Return Value</span></span>  
 <span data-ttu-id="a6b9b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a6b9b-112">S_OK</span></span>  
 <span data-ttu-id="a6b9b-113">Attachement réussi au processus sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="a6b9b-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="a6b9b-114">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="a6b9b-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="a6b9b-115">Impossible d’attacher au processus sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="a6b9b-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6b9b-116">Notes</span><span class="sxs-lookup"><span data-stu-id="a6b9b-116">Remarks</span></span>  
 <span data-ttu-id="a6b9b-117">Le débogage en mode mixte n’est pas pris en charge dans Silverlight.</span><span class="sxs-lookup"><span data-stu-id="a6b9b-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6b9b-118">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="a6b9b-118">Requirements</span></span>  
 <span data-ttu-id="a6b9b-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6b9b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6b9b-120">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6b9b-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6b9b-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6b9b-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6b9b-122">**Versions de .NET Framework :** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="a6b9b-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6b9b-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6b9b-123">See also</span></span>

- [<span data-ttu-id="a6b9b-124">ICorDebugRemote, interface</span><span class="sxs-lookup"><span data-stu-id="a6b9b-124">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="a6b9b-125">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="a6b9b-125">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="a6b9b-126">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="a6b9b-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
