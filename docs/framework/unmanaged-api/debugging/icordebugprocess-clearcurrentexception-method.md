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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ad7dd3ae0e547933fdf7d579116dccc62ae579c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766145"
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="c0d3c-102">ICorDebugProcess::ClearCurrentException, méthode</span><span class="sxs-lookup"><span data-stu-id="c0d3c-102">ICorDebugProcess::ClearCurrentException Method</span></span>
<span data-ttu-id="c0d3c-103">Efface l’exception non managée actuelle sur le thread donné.</span><span class="sxs-lookup"><span data-stu-id="c0d3c-103">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0d3c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0d3c-104">Syntax</span></span>  
  
```cpp  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0d3c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c0d3c-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="c0d3c-106">[in] L’ID du thread sur lequel l’exception non managée actuelle est effacée.</span><span class="sxs-lookup"><span data-stu-id="c0d3c-106">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0d3c-107">Notes</span><span class="sxs-lookup"><span data-stu-id="c0d3c-107">Remarks</span></span>  
 <span data-ttu-id="c0d3c-108">Appelez cette méthode avant d’appeler [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) quand un thread a signalé une exception non managée qui doit être ignorée par l’élément débogué.</span><span class="sxs-lookup"><span data-stu-id="c0d3c-108">Call this method before calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="c0d3c-109">Cela efface à la fois les en suspens en intrabande (IB) et hors-bande (OOB) événements sur le thread donné.</span><span class="sxs-lookup"><span data-stu-id="c0d3c-109">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="c0d3c-110">Tous les points d’arrêt OOB et les exceptions de la seule étape sont automatiquement effacées.</span><span class="sxs-lookup"><span data-stu-id="c0d3c-110">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="c0d3c-111">Utilisez [ICorDebugThread2::InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) intercepter actuel exception sur un thread managé.</span><span class="sxs-lookup"><span data-stu-id="c0d3c-111">Use [ICorDebugThread2::InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0d3c-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c0d3c-112">Requirements</span></span>  
 <span data-ttu-id="c0d3c-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0d3c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0d3c-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0d3c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0d3c-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0d3c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0d3c-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0d3c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
