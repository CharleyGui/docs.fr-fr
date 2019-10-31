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
ms.openlocfilehash: 6ea2b24d37f56a5cb9e6b3dea0d666c8acc719dc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091029"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="6b55a-102">ICorDebugFrame::CreateStepper, méthode</span><span class="sxs-lookup"><span data-stu-id="6b55a-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="6b55a-103">Obtient une exécution pas à pas qui permet au débogueur d’effectuer des opérations pas à pas relatives à ce ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="6b55a-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b55a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b55a-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b55a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6b55a-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="6b55a-106">à Pointeur vers l’adresse d’un objet ICorDebugStepper qui permet au débogueur d’effectuer des opérations pas à pas relatives au frame actuel.</span><span class="sxs-lookup"><span data-stu-id="6b55a-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b55a-107">Notes</span><span class="sxs-lookup"><span data-stu-id="6b55a-107">Remarks</span></span>  
 <span data-ttu-id="6b55a-108">Si le frame n’est pas actif, l’objet de pas à pas devra généralement revenir au frame avant la fin de l’étape.</span><span class="sxs-lookup"><span data-stu-id="6b55a-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b55a-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="6b55a-109">Requirements</span></span>  
 <span data-ttu-id="6b55a-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b55a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b55a-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b55a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b55a-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b55a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b55a-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b55a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
