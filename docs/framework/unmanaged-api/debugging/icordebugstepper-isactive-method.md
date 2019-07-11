---
title: ICorDebugStepper::IsActive, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9dde27f74ac59d033b6e25fba1dbb8e52c4b91af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760678"
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="663b4-102">ICorDebugStepper::IsActive, méthode</span><span class="sxs-lookup"><span data-stu-id="663b4-102">ICorDebugStepper::IsActive Method</span></span>
<span data-ttu-id="663b4-103">Obtient une valeur qui indique si cet ICorDebugStepper exécute actuellement une étape.</span><span class="sxs-lookup"><span data-stu-id="663b4-103">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="663b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="663b4-104">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="663b4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="663b4-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="663b4-106">[out] Retourne `true` si l’exécution pas à pas exécute actuellement une étape ; sinon, retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="663b4-106">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="663b4-107">Notes</span><span class="sxs-lookup"><span data-stu-id="663b4-107">Remarks</span></span>  
 <span data-ttu-id="663b4-108">Toute étape reste active jusqu'à ce que le débogueur reçoive un [ICorDebugManagedCallback::StepComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) appeler, ce qui désactive automatiquement l’exécution pas à pas.</span><span class="sxs-lookup"><span data-stu-id="663b4-108">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="663b4-109">Une exécution pas à pas peut également être désactivée prématurément en appelant [ICorDebugStepper::Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) avant le rappel condition est atteinte.</span><span class="sxs-lookup"><span data-stu-id="663b4-109">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="663b4-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="663b4-110">Requirements</span></span>  
 <span data-ttu-id="663b4-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="663b4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="663b4-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="663b4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="663b4-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="663b4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="663b4-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="663b4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
