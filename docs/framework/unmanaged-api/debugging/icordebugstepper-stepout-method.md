---
title: ICorDebugStepper::StepOut, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepOut
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type:
- apiref
ms.openlocfilehash: 9f6962f987079da1ccb04ea368307d7c119910a6
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379507"
---
# <a name="icordebugstepperstepout-method"></a><span data-ttu-id="e8f7e-102">ICorDebugStepper::StepOut, méthode</span><span class="sxs-lookup"><span data-stu-id="e8f7e-102">ICorDebugStepper::StepOut Method</span></span>
<span data-ttu-id="e8f7e-103">Fait en sorte que ces ICorDebugStepper effectuent un pas à pas détaillé dans son thread conteneur et se termine lorsque le frame actuel retourne le contrôle au frame appelant.</span><span class="sxs-lookup"><span data-stu-id="e8f7e-103">Causes this ICorDebugStepper to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8f7e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8f7e-104">Syntax</span></span>  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="e8f7e-105">Notes </span><span class="sxs-lookup"><span data-stu-id="e8f7e-105">Remarks</span></span>  
 <span data-ttu-id="e8f7e-106">Une `StepOut` opération se termine après avoir été retournée normalement du frame actuel au frame appelant.</span><span class="sxs-lookup"><span data-stu-id="e8f7e-106">A `StepOut` operation will complete after returning normally from the current frame to the calling frame.</span></span>  
  
 <span data-ttu-id="e8f7e-107">Si `StepOut` est appelé lorsque, dans du code non managé, l’étape se termine lorsque le frame actuel retourne au code managé qui l’a appelé.</span><span class="sxs-lookup"><span data-stu-id="e8f7e-107">If `StepOut` is called when in unmanaged code, the step will complete when the current frame returns to the managed code that called it.</span></span>  
  
 <span data-ttu-id="e8f7e-108">Dans la version 2,0 de .NET Framework, n’utilisez pas `StepOut` avec l’indicateur STOP_UNMANAGED défini, car il échouera.</span><span class="sxs-lookup"><span data-stu-id="e8f7e-108">In the .NET Framework version 2.0, do not use `StepOut` with the STOP_UNMANAGED flag set because it will fail.</span></span> <span data-ttu-id="e8f7e-109">(Utilisez [ICorDebugStepper :: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) pour définir des indicateurs pour l’exécution pas à pas.) Les débogueurs d’interopérabilité doivent effectuer eux-mêmes un pas à pas sortant du code natif.</span><span class="sxs-lookup"><span data-stu-id="e8f7e-109">(Use [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) to set flags for stepping.) Interop debuggers must step out to native code themselves.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8f7e-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e8f7e-110">Requirements</span></span>  
 <span data-ttu-id="e8f7e-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8f7e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8f7e-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8f7e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8f7e-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8f7e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8f7e-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8f7e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
