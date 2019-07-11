---
title: ICorDebugFrame::CreateStepper, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd105a5cbdb857aaa902e60968ff1d94473259b6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754243"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="340d5-102">ICorDebugFrame::CreateStepper, méthode</span><span class="sxs-lookup"><span data-stu-id="340d5-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="340d5-103">Obtient une exécution pas à pas qui permet au débogueur d’effectuer des opérations ICorDebugFrame pas à pas.</span><span class="sxs-lookup"><span data-stu-id="340d5-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="340d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="340d5-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="340d5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="340d5-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="340d5-106">[out] Pointeur vers l’adresse d’un objet ICorDebugStepper qui permet au débogueur d’effectuer des opérations pas à pas relatif à l’image actuelle.</span><span class="sxs-lookup"><span data-stu-id="340d5-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="340d5-107">Notes</span><span class="sxs-lookup"><span data-stu-id="340d5-107">Remarks</span></span>  
 <span data-ttu-id="340d5-108">Si le frame n’est pas actif, l’objet d’exécution pas à pas aura généralement revenir à l’image avant la fin de l’étape.</span><span class="sxs-lookup"><span data-stu-id="340d5-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="340d5-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="340d5-109">Requirements</span></span>  
 <span data-ttu-id="340d5-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="340d5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="340d5-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="340d5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="340d5-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="340d5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="340d5-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="340d5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
