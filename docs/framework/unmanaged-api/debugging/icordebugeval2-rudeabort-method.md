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
ms.openlocfilehash: a486935d5d53a6fc7d862160ed1186c5774814c7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084796"
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="d4e80-102">ICorDebugEval2::RudeAbort, méthode</span><span class="sxs-lookup"><span data-stu-id="d4e80-102">ICorDebugEval2::RudeAbort Method</span></span>
<span data-ttu-id="d4e80-103">Abandonne le calcul que ce `ICorDebugEval2` est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="d4e80-103">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4e80-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4e80-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="d4e80-105">Notes</span><span class="sxs-lookup"><span data-stu-id="d4e80-105">Remarks</span></span>  
 <span data-ttu-id="d4e80-106">`RudeAbort` ne libère pas les verrous que l’évaluateur détient, il laisse la session de débogage dans un État non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="d4e80-106">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="d4e80-107">Appelez cette méthode avec une extrême prudence.</span><span class="sxs-lookup"><span data-stu-id="d4e80-107">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4e80-108">spécifications</span><span class="sxs-lookup"><span data-stu-id="d4e80-108">Requirements</span></span>  
 <span data-ttu-id="d4e80-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4e80-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4e80-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4e80-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4e80-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4e80-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4e80-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4e80-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
