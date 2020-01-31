---
title: ICorDebugStepper::StepRange, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type:
- apiref
ms.openlocfilehash: 21b8bf618e197372e301d5f56e7592c20710014d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791707"
---
# <a name="icordebugsteppersteprange-method"></a><span data-ttu-id="f02e2-102">ICorDebugStepper::StepRange, méthode</span><span class="sxs-lookup"><span data-stu-id="f02e2-102">ICorDebugStepper::StepRange Method</span></span>
<span data-ttu-id="f02e2-103">Fait en sorte que ces ICorDebugStepper effectuent un pas à pas détaillé dans son thread conteneur et le retournent lorsqu’il atteint le code au-delà de la dernière des plages spécifiées.</span><span class="sxs-lookup"><span data-stu-id="f02e2-103">Causes this ICorDebugStepper to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f02e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f02e2-104">Syntax</span></span>  
  
```cpp  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f02e2-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="f02e2-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="f02e2-106">dans Affectez la valeur `true` pour effectuer un pas à pas détaillé dans une fonction appelée dans le thread.</span><span class="sxs-lookup"><span data-stu-id="f02e2-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="f02e2-107">Affectez la valeur `false` pour effectuer un pas à pas principal dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="f02e2-107">Set to `false` to step over the function.</span></span>  
  
 `ranges`  
 <span data-ttu-id="f02e2-108">dans Tableau de structures COR_DEBUG_STEP_RANGE, chacune spécifiant une plage.</span><span class="sxs-lookup"><span data-stu-id="f02e2-108">[in] An array of COR_DEBUG_STEP_RANGE structures, each of which specifies a range.</span></span>  
  
 `cRangeCount`  
 <span data-ttu-id="f02e2-109">[in] Taille du tableau `ranges`.</span><span class="sxs-lookup"><span data-stu-id="f02e2-109">[in] The size of the `ranges` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f02e2-110">Notes</span><span class="sxs-lookup"><span data-stu-id="f02e2-110">Remarks</span></span>  
 <span data-ttu-id="f02e2-111">La méthode `StepRange` fonctionne comme la méthode [ICorDebugStepper :: Step](icordebugstepper-step-method.md) , sauf qu’elle ne se termine pas tant que le code en dehors de la plage donnée n’est pas atteint.</span><span class="sxs-lookup"><span data-stu-id="f02e2-111">The `StepRange` method works like the [ICorDebugStepper::Step](icordebugstepper-step-method.md) method, except that it does not complete until code outside the given range is reached.</span></span>  
  
 <span data-ttu-id="f02e2-112">Cela peut être plus efficace que l’exécution pas-à-pas d’une instruction à la fois.</span><span class="sxs-lookup"><span data-stu-id="f02e2-112">This can be more efficient than stepping one instruction at a time.</span></span> <span data-ttu-id="f02e2-113">Les plages sont spécifiées sous la forme d’une liste de paires d’offsets à partir du début de la trame de l’exécution pas à pas.</span><span class="sxs-lookup"><span data-stu-id="f02e2-113">Ranges are specified as a list of offset pairs from the start of the stepper's frame.</span></span>  
  
 <span data-ttu-id="f02e2-114">Les plages sont relatives au code MSIL (Microsoft Intermediate Language) d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="f02e2-114">Ranges are relative to the Microsoft intermediate language (MSIL) code of a method.</span></span> <span data-ttu-id="f02e2-115">Appelez [ICorDebugStepper :: SetRangeIL,](icordebugstepper-setrangeil-method.md) avec `false` pour rendre les plages relatives au code natif d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="f02e2-115">Call [ICorDebugStepper::SetRangeIL](icordebugstepper-setrangeil-method.md) with `false` to make the ranges relative to the native code of a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f02e2-116">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="f02e2-116">Requirements</span></span>  
 <span data-ttu-id="f02e2-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f02e2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f02e2-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f02e2-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f02e2-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f02e2-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f02e2-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f02e2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
