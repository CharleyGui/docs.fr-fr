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
ms.openlocfilehash: 478772925dfb7ca7389b5267433f9b06ace3d5a3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729614"
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="eff6d-102">ICorDebugEval2::RudeAbort, méthode</span><span class="sxs-lookup"><span data-stu-id="eff6d-102">ICorDebugEval2::RudeAbort Method</span></span>

<span data-ttu-id="eff6d-103">Abandonne le calcul en cours d' `ICorDebugEval2` exécution.</span><span class="sxs-lookup"><span data-stu-id="eff6d-103">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eff6d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eff6d-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="eff6d-105">Notes</span><span class="sxs-lookup"><span data-stu-id="eff6d-105">Remarks</span></span>  

 <span data-ttu-id="eff6d-106">`RudeAbort` ne libère pas les verrous détenus par l’évaluateur, il laisse donc la session de débogage dans un État non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="eff6d-106">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="eff6d-107">Appelez cette méthode avec une extrême prudence.</span><span class="sxs-lookup"><span data-stu-id="eff6d-107">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eff6d-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="eff6d-108">Requirements</span></span>  

 <span data-ttu-id="eff6d-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eff6d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eff6d-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eff6d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eff6d-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eff6d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eff6d-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eff6d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
