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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36a33b74a692761d772a888ce918aa28a2d92678
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760557"
---
# <a name="icordebugstepperstepout-method"></a><span data-ttu-id="9da82-102">ICorDebugStepper::StepOut, méthode</span><span class="sxs-lookup"><span data-stu-id="9da82-102">ICorDebugStepper::StepOut Method</span></span>
<span data-ttu-id="9da82-103">Provoque ICorDebugStepper pas à pas son thread conteneur et se termine lorsque le frame actuel retourne le contrôle au frame appelant.</span><span class="sxs-lookup"><span data-stu-id="9da82-103">Causes this ICorDebugStepper to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9da82-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9da82-104">Syntax</span></span>  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="9da82-105">Notes</span><span class="sxs-lookup"><span data-stu-id="9da82-105">Remarks</span></span>  
 <span data-ttu-id="9da82-106">Un `StepOut` opération se termine après le retour normal du frame actuel au frame appelant.</span><span class="sxs-lookup"><span data-stu-id="9da82-106">A `StepOut` operation will complete after returning normally from the current frame to the calling frame.</span></span>  
  
 <span data-ttu-id="9da82-107">Si `StepOut` est appelée lorsque en code non managé, l’étape se termine lorsque le frame actuel retourne du code managé qui l’a appelée.</span><span class="sxs-lookup"><span data-stu-id="9da82-107">If `StepOut` is called when in unmanaged code, the step will complete when the current frame returns to the managed code that called it.</span></span>  
  
 <span data-ttu-id="9da82-108">Dans le .NET Framework version 2.0, n’utilisez pas `StepOut` avec l’indicateur STOP_UNMANAGED ensemble, car elle échouera.</span><span class="sxs-lookup"><span data-stu-id="9da82-108">In the .NET Framework version 2.0, do not use `StepOut` with the STOP_UNMANAGED flag set because it will fail.</span></span> <span data-ttu-id="9da82-109">(Utilisez [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) pour définir les indicateurs d’exécution pas à pas.) Les débogueurs d’interopérabilité doivent pas à pas sortant en code natif eux-mêmes.</span><span class="sxs-lookup"><span data-stu-id="9da82-109">(Use [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) to set flags for stepping.) Interop debuggers must step out to native code themselves.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9da82-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9da82-110">Requirements</span></span>  
 <span data-ttu-id="9da82-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9da82-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9da82-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9da82-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9da82-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9da82-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9da82-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9da82-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
