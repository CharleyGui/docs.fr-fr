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
ms.openlocfilehash: 39d2fd0163b0e61295187461d5dbdf5742450306
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379515"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="f0d31-102">ICorDebugStepper::Step, méthode</span><span class="sxs-lookup"><span data-stu-id="f0d31-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="f0d31-103">Fait en sorte que ces ICorDebugStepper effectuent un pas à pas détaillé dans son thread conteneur et, éventuellement, continue à exécuter des fonctions pas à pas dans les fonctions appelées dans le thread.</span><span class="sxs-lookup"><span data-stu-id="f0d31-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0d31-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0d31-104">Syntax</span></span>  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0d31-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f0d31-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="f0d31-106">dans Affectez `true` la valeur pour effectuer un pas à pas détaillé dans une fonction appelée dans le thread.</span><span class="sxs-lookup"><span data-stu-id="f0d31-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="f0d31-107">Affectez `false` la valeur à pour effectuer un pas à pas principal dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="f0d31-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0d31-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="f0d31-108">Remarks</span></span>  
 <span data-ttu-id="f0d31-109">L’étape se termine lorsque l’common language runtime exécute l’instruction managée suivante dans le frame de ce pas à pas.</span><span class="sxs-lookup"><span data-stu-id="f0d31-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="f0d31-110">Si `Step` est appelé sur une exécution pas à pas, qui n’est pas en code managé, l’étape se termine lorsque l’instruction de code managé suivante est exécutée par le thread.</span><span class="sxs-lookup"><span data-stu-id="f0d31-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0d31-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f0d31-111">Requirements</span></span>  
 <span data-ttu-id="f0d31-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0d31-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0d31-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0d31-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0d31-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0d31-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0d31-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0d31-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
