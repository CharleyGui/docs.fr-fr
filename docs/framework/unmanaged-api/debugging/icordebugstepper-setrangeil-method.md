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
ms.openlocfilehash: 88270cb73515cc1a671bfb3fb5c479697ad7b359
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137545"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="02f08-102">ICorDebugStepper::SetRangeIL, méthode</span><span class="sxs-lookup"><span data-stu-id="02f08-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="02f08-103">Définit une valeur qui spécifie si les appels à [ICorDebugStepper :: StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) passent des valeurs d’argument qui sont relatives au code natif ou relatives au code MSIL (Microsoft Intermediate Language) de la méthode en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="02f08-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02f08-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02f08-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02f08-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="02f08-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="02f08-106">dans Affectez la valeur `true` pour spécifier que les plages sont relatives au code MSIL.</span><span class="sxs-lookup"><span data-stu-id="02f08-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="02f08-107">Affectez la valeur `false` pour spécifier que les plages sont relatives au code natif.</span><span class="sxs-lookup"><span data-stu-id="02f08-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="02f08-108">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="02f08-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02f08-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="02f08-109">Requirements</span></span>  
 <span data-ttu-id="02f08-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02f08-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02f08-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02f08-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02f08-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02f08-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02f08-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02f08-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
