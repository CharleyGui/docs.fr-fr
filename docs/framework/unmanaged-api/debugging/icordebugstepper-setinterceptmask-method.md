---
title: ICorDebugStepper::SetInterceptMask, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetInterceptMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type:
- apiref
ms.openlocfilehash: aaba751a58e5b23b98b1d0629ea3cc9e1e7a83a9
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379005"
---
# <a name="icordebugsteppersetinterceptmask-method"></a><span data-ttu-id="d7e14-102">ICorDebugStepper::SetInterceptMask, méthode</span><span class="sxs-lookup"><span data-stu-id="d7e14-102">ICorDebugStepper::SetInterceptMask Method</span></span>
<span data-ttu-id="d7e14-103">Définit une valeur qui spécifie les types de code qui sont en escalier.</span><span class="sxs-lookup"><span data-stu-id="d7e14-103">Sets a value that specifies the types of code that are stepped into.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7e14-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7e14-104">Syntax</span></span>  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7e14-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d7e14-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="d7e14-106">dans Combinaison de valeurs de l’énumération CorDebugIntercept, qui spécifie les types de code.</span><span class="sxs-lookup"><span data-stu-id="d7e14-106">[in] A combination of values of the CorDebugIntercept enumeration that specifies the types of code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7e14-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="d7e14-107">Remarks</span></span>  
 <span data-ttu-id="d7e14-108">Si le bit d’un intercepteur est défini, le pas à pas se termine lorsque le type donné de code d’interception est rencontré.</span><span class="sxs-lookup"><span data-stu-id="d7e14-108">If the bit for an interceptor is set, the stepper will complete when the given type of intercepting code is encountered.</span></span> <span data-ttu-id="d7e14-109">Si le bit est effacé, le code d’interception est ignoré.</span><span class="sxs-lookup"><span data-stu-id="d7e14-109">If the bit is cleared, the intercepting code will be skipped.</span></span>  
  
 <span data-ttu-id="d7e14-110">La `SetInterceptMask` méthode peut avoir des interactions imprévues avec [ICorDebugStepper :: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) (du point de vue de l’utilisateur).</span><span class="sxs-lookup"><span data-stu-id="d7e14-110">The `SetInterceptMask` method may have unforeseen interactions with [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) (from the user's point of view).</span></span> <span data-ttu-id="d7e14-111">Par exemple, si la seule partie visible (autrement dit, non interne) du code d’initialisation de classe n’a pas d’informations de mappage et que STOP_NO_MAPPING_INFO n’est pas défini (consultez la méthode [ICorDebugStepper :: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) et l’énumération CorDebugUnmappedStop,), l’exécution pas à pas de la classe s’effectue pas à pas.</span><span class="sxs-lookup"><span data-stu-id="d7e14-111">For example, if the only visible (that is, non-internal) portion of class initialization code lacks mapping information and STOP_NO_MAPPING_INFO isn't set (see the [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) method and the CorDebugUnmappedStop enumeration), the stepper will step over the class initialization.</span></span> <span data-ttu-id="d7e14-112">Par défaut, seule la valeur INTERCEPT_NONE de l' `CorDebugIntercept` énumération sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="d7e14-112">By default, only the INTERCEPT_NONE value of the `CorDebugIntercept` enumeration will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7e14-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d7e14-113">Requirements</span></span>  
 <span data-ttu-id="d7e14-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7e14-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7e14-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7e14-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7e14-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7e14-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7e14-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7e14-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
