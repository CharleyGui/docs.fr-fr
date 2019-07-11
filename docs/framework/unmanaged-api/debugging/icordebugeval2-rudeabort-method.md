---
title: ICorDebugEval2::RudeAbort, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.RudeAbort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::RudeAbort
helpviewer_keywords:
- ICorDebugEval2::RudeAbort method [.NET Framework debugging]
- RudeAbort method, ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: 02468edf-d32b-4cb3-aaa8-3dd2abfc8b25
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a1adb79e5081fc909d0cd180d8161eccea7e58e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754355"
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="6151f-102">ICorDebugEval2::RudeAbort, méthode</span><span class="sxs-lookup"><span data-stu-id="6151f-102">ICorDebugEval2::RudeAbort Method</span></span>
<span data-ttu-id="6151f-103">Abandonne le calcul que ce `ICorDebugEval2` en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="6151f-103">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6151f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6151f-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6151f-105">Notes</span><span class="sxs-lookup"><span data-stu-id="6151f-105">Remarks</span></span>  
 <span data-ttu-id="6151f-106">`RudeAbort` ne libère pas les verrous maintenus par l’évaluateur, donc elle ne laisse la session de débogage dans un état potentiellement dangereux.</span><span class="sxs-lookup"><span data-stu-id="6151f-106">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="6151f-107">Appelez cette méthode avec une extrême prudence.</span><span class="sxs-lookup"><span data-stu-id="6151f-107">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6151f-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6151f-108">Requirements</span></span>  
 <span data-ttu-id="6151f-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6151f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6151f-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6151f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6151f-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6151f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6151f-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6151f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
