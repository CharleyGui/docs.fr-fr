---
title: ICorDebugProcess::ClearCurrentException, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ClearCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type:
- apiref
ms.openlocfilehash: 4cfacb7f3303947ec8b11362fde82649687889d8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792661"
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="4eea1-102">ICorDebugProcess::ClearCurrentException, méthode</span><span class="sxs-lookup"><span data-stu-id="4eea1-102">ICorDebugProcess::ClearCurrentException Method</span></span>
<span data-ttu-id="4eea1-103">Efface l’exception non managée actuelle sur le thread donné.</span><span class="sxs-lookup"><span data-stu-id="4eea1-103">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4eea1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4eea1-104">Syntax</span></span>  
  
```cpp  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4eea1-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="4eea1-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="4eea1-106">dans ID du thread sur lequel l’exception non managée actuelle sera effacée.</span><span class="sxs-lookup"><span data-stu-id="4eea1-106">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4eea1-107">Notes</span><span class="sxs-lookup"><span data-stu-id="4eea1-107">Remarks</span></span>  
 <span data-ttu-id="4eea1-108">Appelez cette méthode avant d’appeler [ICorDebugController :: continue](icordebugcontroller-continue-method.md) lorsqu’un thread a signalé une exception non managée qui doit être ignorée par l’élément débogué.</span><span class="sxs-lookup"><span data-stu-id="4eea1-108">Call this method before calling [ICorDebugController::Continue](icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="4eea1-109">Cela effacera à la fois les événements in-Band (IB) et hors bande (OOB) en suspens sur le thread donné.</span><span class="sxs-lookup"><span data-stu-id="4eea1-109">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="4eea1-110">Tous les points d’arrêt OOB et les exceptions à une seule étape sont automatiquement effacés.</span><span class="sxs-lookup"><span data-stu-id="4eea1-110">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="4eea1-111">Utilisez [ICorDebugThread2 :: InterceptCurrentException,](icordebugthread2-interceptcurrentexception-method.md) pour intercepter l’exception managée actuelle sur un thread.</span><span class="sxs-lookup"><span data-stu-id="4eea1-111">Use [ICorDebugThread2::InterceptCurrentException](icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4eea1-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="4eea1-112">Requirements</span></span>  
 <span data-ttu-id="4eea1-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4eea1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4eea1-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4eea1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4eea1-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4eea1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4eea1-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4eea1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
