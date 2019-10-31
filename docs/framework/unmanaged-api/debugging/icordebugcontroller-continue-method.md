---
title: ICorDebugController::Continue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
ms.openlocfilehash: 14356a12c944ef93dba5e7b818d3ee5cf5adc607
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125424"
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="84e08-102">ICorDebugController::Continue, méthode</span><span class="sxs-lookup"><span data-stu-id="84e08-102">ICorDebugController::Continue Method</span></span>

<span data-ttu-id="84e08-103">Reprend l’exécution des threads managés après un appel à la [méthode Stop](icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="84e08-103">Resumes execution of managed threads after a call to [Stop Method](icordebugcontroller-stop-method.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="84e08-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84e08-104">Syntax</span></span>

```cpp
HRESULT Continue (
    [in] BOOL fIsOutOfBand
);
```

## <a name="parameters"></a><span data-ttu-id="84e08-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="84e08-105">Parameters</span></span>

`fIsOutOfBand`  
<span data-ttu-id="84e08-106">dans Défini sur `true` en cas de continuation à partir d’un événement hors bande ; Sinon, affectez la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="84e08-106">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="84e08-107">Notes</span><span class="sxs-lookup"><span data-stu-id="84e08-107">Remarks</span></span>

<span data-ttu-id="84e08-108">`Continue` poursuit le processus après un appel à la méthode `ICorDebugController::Stop`.</span><span class="sxs-lookup"><span data-stu-id="84e08-108">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>

<span data-ttu-id="84e08-109">Lors du débogage en mode mixte, n’appelez pas `Continue` sur le thread d’événements Win32, à moins que vous ne continuiez à partir d’un événement hors bande.</span><span class="sxs-lookup"><span data-stu-id="84e08-109">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>

<span data-ttu-id="84e08-110">Un *événement intrabande* est un événement managé ou un événement non managé normal, pendant lequel le débogueur prend en charge l’interaction avec l’état managé du processus.</span><span class="sxs-lookup"><span data-stu-id="84e08-110">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="84e08-111">Dans ce cas, le débogueur reçoit le rappel [ICorDebugUnmanagedCallback ::D ebugevent](icordebugunmanagedcallback-debugevent-method.md) avec son paramètre `fOutOfBand` défini sur `false`.</span><span class="sxs-lookup"><span data-stu-id="84e08-111">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>

<span data-ttu-id="84e08-112">Un *événement hors bande* est un événement non managé pendant lequel l’interaction avec l’état managé du processus est impossible tant que le processus est arrêté en raison de l’événement.</span><span class="sxs-lookup"><span data-stu-id="84e08-112">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="84e08-113">Dans ce cas, le débogueur reçoit le rappel `ICorDebugUnmanagedCallback::DebugEvent` avec son paramètre `fOutOfBand` défini sur `true`.</span><span class="sxs-lookup"><span data-stu-id="84e08-113">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>

## <a name="requirements"></a><span data-ttu-id="84e08-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="84e08-114">Requirements</span></span>

<span data-ttu-id="84e08-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84e08-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="84e08-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84e08-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="84e08-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84e08-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="84e08-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84e08-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
