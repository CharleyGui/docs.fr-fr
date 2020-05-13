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
ms.openlocfilehash: b95e9f3a0d584511a2bcf156ed2c50a98f96d071
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379060"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="2bc49-102">ICorDebugRemote::DebugActiveProcessEx, méthode</span><span class="sxs-lookup"><span data-stu-id="2bc49-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="2bc49-103">Lance un processus sur un ordinateur distant sous le débogueur.</span><span class="sxs-lookup"><span data-stu-id="2bc49-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bc49-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bc49-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bc49-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2bc49-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="2bc49-106">dans Pointeur vers une [interface ICorDebugRemoteTarget](icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="2bc49-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="2bc49-107">Ce paramètre est utilisé pour déterminer l’ordinateur sur lequel le processus est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="2bc49-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="2bc49-108">dans ID du processus auquel le débogueur doit être attaché.</span><span class="sxs-lookup"><span data-stu-id="2bc49-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="2bc49-109">[in] `true` Si le débogueur doit se comporter comme le débogueur Win32 pour le processus et distribuer les rappels non managés ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="2bc49-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="2bc49-110">à Pointeur vers l’adresse d’un objet « ICorDebugProcess » qui représente le processus auquel le débogueur a été attaché.</span><span class="sxs-lookup"><span data-stu-id="2bc49-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2bc49-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2bc49-111">Return Value</span></span>  
 <span data-ttu-id="2bc49-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="2bc49-112">S_OK</span></span>  
 <span data-ttu-id="2bc49-113">Attachement réussi au processus sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2bc49-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="2bc49-114">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="2bc49-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="2bc49-115">Impossible d’attacher au processus sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="2bc49-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2bc49-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="2bc49-116">Remarks</span></span>  
 <span data-ttu-id="2bc49-117">Le débogage en mode mixte n’est pas pris en charge dans Silverlight.</span><span class="sxs-lookup"><span data-stu-id="2bc49-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bc49-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2bc49-118">Requirements</span></span>  
 <span data-ttu-id="2bc49-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bc49-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bc49-120">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2bc49-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2bc49-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2bc49-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bc49-122">**Versions de .NET Framework :** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="2bc49-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bc49-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2bc49-123">See also</span></span>

- [<span data-ttu-id="2bc49-124">ICorDebugRemote, interface</span><span class="sxs-lookup"><span data-stu-id="2bc49-124">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="2bc49-125">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="2bc49-125">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="2bc49-126">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="2bc49-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
