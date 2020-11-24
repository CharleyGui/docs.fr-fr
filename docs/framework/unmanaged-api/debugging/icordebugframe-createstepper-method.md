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
ms.openlocfilehash: 5dfb64d0c440cbd2c8a8a65b2c18d78f02a7615e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679713"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="5a781-102">ICorDebugFrame::CreateStepper, méthode</span><span class="sxs-lookup"><span data-stu-id="5a781-102">ICorDebugFrame::CreateStepper Method</span></span>

<span data-ttu-id="5a781-103">Obtient une exécution pas à pas qui permet au débogueur d’effectuer des opérations pas à pas relatives à ce ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="5a781-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a781-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a781-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a781-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5a781-105">Parameters</span></span>  

 `ppStepper`  
 <span data-ttu-id="5a781-106">à Pointeur vers l’adresse d’un objet ICorDebugStepper qui permet au débogueur d’effectuer des opérations pas à pas relatives au frame actuel.</span><span class="sxs-lookup"><span data-stu-id="5a781-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a781-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="5a781-107">Remarks</span></span>  

 <span data-ttu-id="5a781-108">Si le frame n’est pas actif, l’objet de pas à pas devra généralement revenir au frame avant la fin de l’étape.</span><span class="sxs-lookup"><span data-stu-id="5a781-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a781-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5a781-109">Requirements</span></span>  

 <span data-ttu-id="5a781-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a781-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a781-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a781-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a781-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a781-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a781-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a781-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
