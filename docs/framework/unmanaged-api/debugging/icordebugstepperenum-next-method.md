---
title: ICorDebugStepperEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStepperEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepperEnum::Next
helpviewer_keywords:
- Next method, ICorDebugStepperEnum interface [.NET Framework debugging]
- ICorDebugStepperEnum::Next method [.NET Framework debugging]
ms.assetid: d0ea0f30-e8d2-48b0-8477-e1a029ceb4dd
topic_type:
- apiref
ms.openlocfilehash: 11d9c7393827b613d49e23972b4896bfe657a544
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138988"
---
# <a name="icordebugstepperenumnext-method"></a><span data-ttu-id="9e0e4-102">ICorDebugStepperEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="9e0e4-102">ICorDebugStepperEnum::Next Method</span></span>
<span data-ttu-id="9e0e4-103">Obtient le nombre spécifié d’instances de ICorDebugStepper à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="9e0e4-103">Gets the specified number of ICorDebugStepper instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e0e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e0e4-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e0e4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9e0e4-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="9e0e4-106">dans Nombre d’instances de `ICorDebugStepper` à récupérer.</span><span class="sxs-lookup"><span data-stu-id="9e0e4-106">[in] The number of `ICorDebugStepper` instances to be retrieved.</span></span>  
  
 `steppers`  
 <span data-ttu-id="9e0e4-107">à Tableau de pointeurs, chacun pointant vers un objet `ICorDebugStepper`.</span><span class="sxs-lookup"><span data-stu-id="9e0e4-107">[out] An array of pointers, each of which points to an `ICorDebugStepper` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9e0e4-108">à Pointeur vers le nombre d’instances `ICorDebugStepper` réellement retournées.</span><span class="sxs-lookup"><span data-stu-id="9e0e4-108">[out] Pointer to the number of `ICorDebugStepper` instances actually returned.</span></span> <span data-ttu-id="9e0e4-109">Cette valeur peut être null si `celt` est un.</span><span class="sxs-lookup"><span data-stu-id="9e0e4-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e0e4-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="9e0e4-110">Requirements</span></span>  
 <span data-ttu-id="9e0e4-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e0e4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e0e4-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e0e4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e0e4-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e0e4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e0e4-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e0e4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
