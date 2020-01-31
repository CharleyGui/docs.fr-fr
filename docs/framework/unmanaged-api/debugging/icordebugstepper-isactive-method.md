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
ms.openlocfilehash: 703f454f7ed1d2a959b761726f433db22cb73b01
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791776"
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="83063-102">ICorDebugStepper::IsActive, méthode</span><span class="sxs-lookup"><span data-stu-id="83063-102">ICorDebugStepper::IsActive Method</span></span>
<span data-ttu-id="83063-103">Obtient une valeur qui indique si ces ICorDebugStepper exécutent actuellement une étape.</span><span class="sxs-lookup"><span data-stu-id="83063-103">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83063-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83063-104">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83063-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="83063-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="83063-106">à Retourne `true` si le pas à pas exécute actuellement une étape ; Sinon, retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="83063-106">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83063-107">Notes</span><span class="sxs-lookup"><span data-stu-id="83063-107">Remarks</span></span>  
 <span data-ttu-id="83063-108">Toute action d’étape reste active jusqu’à ce que le débogueur reçoive un appel [ICorDebugManagedCallback :: StepComplete](icordebugmanagedcallback-stepcomplete-method.md) , qui désactive automatiquement le pas à pas.</span><span class="sxs-lookup"><span data-stu-id="83063-108">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="83063-109">Une exécution pas à pas peut également être désactivée prématurément en appelant [ICorDebugStepper ::D eactivate](icordebugstepper-deactivate-method.md) avant que la condition de rappel soit atteinte.</span><span class="sxs-lookup"><span data-stu-id="83063-109">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83063-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="83063-110">Requirements</span></span>  
 <span data-ttu-id="83063-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83063-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83063-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83063-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83063-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83063-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83063-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83063-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
