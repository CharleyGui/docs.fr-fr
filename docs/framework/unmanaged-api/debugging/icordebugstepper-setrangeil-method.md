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
ms.openlocfilehash: 5a27f155021661022b27022bbb252e00dfa67255
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698778"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="53ddd-102">ICorDebugStepper::SetRangeIL, méthode</span><span class="sxs-lookup"><span data-stu-id="53ddd-102">ICorDebugStepper::SetRangeIL Method</span></span>

<span data-ttu-id="53ddd-103">Définit une valeur qui spécifie si les appels à [ICorDebugStepper :: StepRange](icordebugstepper-steprange-method.md) passent des valeurs d’argument qui sont relatives au code natif ou relatives au code MSIL (Microsoft Intermediate Language) de la méthode en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="53ddd-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53ddd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53ddd-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53ddd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="53ddd-105">Parameters</span></span>  

 `bIL`  
 <span data-ttu-id="53ddd-106">dans Affectez `true` la valeur pour spécifier que les plages sont relatives au code MSIL.</span><span class="sxs-lookup"><span data-stu-id="53ddd-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="53ddd-107">Affectez `false` la valeur pour spécifier que les plages sont relatives au code natif.</span><span class="sxs-lookup"><span data-stu-id="53ddd-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="53ddd-108">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="53ddd-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53ddd-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="53ddd-109">Requirements</span></span>  

 <span data-ttu-id="53ddd-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53ddd-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53ddd-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53ddd-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53ddd-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53ddd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53ddd-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53ddd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
