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
ms.openlocfilehash: faddf30248b58c68037635480d8977f22ad077d0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379025"
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="c3f0f-102">ICorDebugStepper::IsActive, méthode</span><span class="sxs-lookup"><span data-stu-id="c3f0f-102">ICorDebugStepper::IsActive Method</span></span>
<span data-ttu-id="c3f0f-103">Obtient une valeur qui indique si ces ICorDebugStepper exécutent actuellement une étape.</span><span class="sxs-lookup"><span data-stu-id="c3f0f-103">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3f0f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3f0f-104">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3f0f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c3f0f-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="c3f0f-106">à Retourne `true` si l’exécution pas à pas exécute actuellement une étape ; sinon, retourne `false` .</span><span class="sxs-lookup"><span data-stu-id="c3f0f-106">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3f0f-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="c3f0f-107">Remarks</span></span>  
 <span data-ttu-id="c3f0f-108">Toute action d’étape reste active jusqu’à ce que le débogueur reçoive un appel [ICorDebugManagedCallback :: StepComplete](icordebugmanagedcallback-stepcomplete-method.md) , qui désactive automatiquement le pas à pas.</span><span class="sxs-lookup"><span data-stu-id="c3f0f-108">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="c3f0f-109">Une exécution pas à pas peut également être désactivée prématurément en appelant [ICorDebugStepper ::D eactivate](icordebugstepper-deactivate-method.md) avant que la condition de rappel soit atteinte.</span><span class="sxs-lookup"><span data-stu-id="c3f0f-109">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3f0f-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c3f0f-110">Requirements</span></span>  
 <span data-ttu-id="c3f0f-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3f0f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3f0f-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3f0f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3f0f-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3f0f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3f0f-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3f0f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
