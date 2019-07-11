---
title: ICorDebugStepper::SetRangeIL, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetRangeIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 610225708bf990850fce73d6d7ff66c556e24e5d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760595"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="ddb71-102">ICorDebugStepper::SetRangeIL, méthode</span><span class="sxs-lookup"><span data-stu-id="ddb71-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="ddb71-103">Définit une valeur qui spécifie si les appels à [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) passer un argument de valeurs qui sont par rapport à du code natif ou par rapport à Microsoft intermédiaire code language (MSIL) de la méthode qui est en cours en escalier par le biais.</span><span class="sxs-lookup"><span data-stu-id="ddb71-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddb71-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ddb71-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ddb71-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ddb71-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="ddb71-106">[in] La valeur `true` pour spécifier que les plages sont relatives au code MSIL.</span><span class="sxs-lookup"><span data-stu-id="ddb71-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="ddb71-107">La valeur `false` pour spécifier que les plages sont relatives au code natif.</span><span class="sxs-lookup"><span data-stu-id="ddb71-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="ddb71-108">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="ddb71-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddb71-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ddb71-109">Requirements</span></span>  
 <span data-ttu-id="ddb71-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddb71-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddb71-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ddb71-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ddb71-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ddb71-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ddb71-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddb71-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
