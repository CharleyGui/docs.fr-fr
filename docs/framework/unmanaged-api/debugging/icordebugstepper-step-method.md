---
title: ICorDebugStepper::Step, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Step
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type:
- apiref
ms.openlocfilehash: 43f86e704e4a52a702b8f563e3c613806eb061b5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137532"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="3d0b6-102">ICorDebugStepper::Step, méthode</span><span class="sxs-lookup"><span data-stu-id="3d0b6-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="3d0b6-103">Fait en sorte que ces ICorDebugStepper effectuent un pas à pas détaillé dans son thread conteneur et, éventuellement, continue à exécuter des fonctions pas à pas dans les fonctions appelées dans le thread.</span><span class="sxs-lookup"><span data-stu-id="3d0b6-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d0b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d0b6-104">Syntax</span></span>  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d0b6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3d0b6-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="3d0b6-106">dans Affectez la valeur `true` pour effectuer un pas à pas détaillé dans une fonction appelée dans le thread.</span><span class="sxs-lookup"><span data-stu-id="3d0b6-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="3d0b6-107">Affectez la valeur `false` pour effectuer un pas à pas principal dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="3d0b6-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d0b6-108">Notes</span><span class="sxs-lookup"><span data-stu-id="3d0b6-108">Remarks</span></span>  
 <span data-ttu-id="3d0b6-109">L’étape se termine lorsque l’common language runtime exécute l’instruction managée suivante dans le frame de ce pas à pas.</span><span class="sxs-lookup"><span data-stu-id="3d0b6-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="3d0b6-110">Si `Step` est appelé sur une exécution pas à pas, qui n’est pas en code managé, l’étape se termine lorsque l’instruction de code managé suivante est exécutée par le thread.</span><span class="sxs-lookup"><span data-stu-id="3d0b6-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d0b6-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="3d0b6-111">Requirements</span></span>  
 <span data-ttu-id="3d0b6-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d0b6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d0b6-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d0b6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d0b6-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d0b6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d0b6-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d0b6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
