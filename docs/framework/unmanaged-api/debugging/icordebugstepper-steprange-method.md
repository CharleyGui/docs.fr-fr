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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e1ace501bf5de741ea110fe4d3bb4bc44843bf8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760534"
---
# <a name="icordebugsteppersteprange-method"></a><span data-ttu-id="b5cd5-102">ICorDebugStepper::StepRange, méthode</span><span class="sxs-lookup"><span data-stu-id="b5cd5-102">ICorDebugStepper::StepRange Method</span></span>
<span data-ttu-id="b5cd5-103">Provoque ICorDebugStepper pas à pas son thread conteneur et à retourner lorsqu’il atteint le code au-delà de la dernière des plages spécifiées.</span><span class="sxs-lookup"><span data-stu-id="b5cd5-103">Causes this ICorDebugStepper to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5cd5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5cd5-104">Syntax</span></span>  
  
```cpp  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5cd5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b5cd5-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="b5cd5-106">[in] La valeur `true` à l’étape dans une fonction qui est appelée dans le thread.</span><span class="sxs-lookup"><span data-stu-id="b5cd5-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="b5cd5-107">La valeur `false` pour ignorer la fonction.</span><span class="sxs-lookup"><span data-stu-id="b5cd5-107">Set to `false` to step over the function.</span></span>  
  
 `ranges`  
 <span data-ttu-id="b5cd5-108">[in] Tableau de structures COR_DEBUG_STEP_RANGE, dont chacun spécifie une plage.</span><span class="sxs-lookup"><span data-stu-id="b5cd5-108">[in] An array of COR_DEBUG_STEP_RANGE structures, each of which specifies a range.</span></span>  
  
 `cRangeCount`  
 <span data-ttu-id="b5cd5-109">[in] Taille du tableau `ranges`.</span><span class="sxs-lookup"><span data-stu-id="b5cd5-109">[in] The size of the `ranges` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5cd5-110">Notes</span><span class="sxs-lookup"><span data-stu-id="b5cd5-110">Remarks</span></span>  
 <span data-ttu-id="b5cd5-111">Le `StepRange` méthode fonctionne comme le [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) (méthode), sauf qu’elle ne se termine pas tant que le code en dehors de la plage donnée est atteinte.</span><span class="sxs-lookup"><span data-stu-id="b5cd5-111">The `StepRange` method works like the [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) method, except that it does not complete until code outside the given range is reached.</span></span>  
  
 <span data-ttu-id="b5cd5-112">Cela peut être plus efficace que l’exécution pas à pas d’une instruction à la fois.</span><span class="sxs-lookup"><span data-stu-id="b5cd5-112">This can be more efficient than stepping one instruction at a time.</span></span> <span data-ttu-id="b5cd5-113">Les plages sont spécifiées comme une liste de paires d’offsets à partir du début du frame de d’exécution pas à pas.</span><span class="sxs-lookup"><span data-stu-id="b5cd5-113">Ranges are specified as a list of offset pairs from the start of the stepper's frame.</span></span>  
  
 <span data-ttu-id="b5cd5-114">Les plages sont relatives au code Microsoft intermediate language (MSIL) d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="b5cd5-114">Ranges are relative to the Microsoft intermediate language (MSIL) code of a method.</span></span> <span data-ttu-id="b5cd5-115">Appelez [ICorDebugStepper::SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) avec `false` pour que les plages par rapport au code natif d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="b5cd5-115">Call [ICorDebugStepper::SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) with `false` to make the ranges relative to the native code of a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5cd5-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b5cd5-116">Requirements</span></span>  
 <span data-ttu-id="b5cd5-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5cd5-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5cd5-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b5cd5-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5cd5-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5cd5-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5cd5-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5cd5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
