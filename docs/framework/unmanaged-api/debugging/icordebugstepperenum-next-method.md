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
ms.openlocfilehash: b8156b858bde550bb66a8f4ac254f850058ea1a2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697192"
---
# <a name="icordebugstepperenumnext-method"></a><span data-ttu-id="8b709-102">ICorDebugStepperEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="8b709-102">ICorDebugStepperEnum::Next Method</span></span>

<span data-ttu-id="8b709-103">Obtient le nombre spécifié d’instances de ICorDebugStepper à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="8b709-103">Gets the specified number of ICorDebugStepper instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b709-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b709-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b709-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8b709-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="8b709-106">dans Nombre d' `ICorDebugStepper` instances à récupérer.</span><span class="sxs-lookup"><span data-stu-id="8b709-106">[in] The number of `ICorDebugStepper` instances to be retrieved.</span></span>  
  
 `steppers`  
 <span data-ttu-id="8b709-107">à Tableau de pointeurs, chacun pointant vers un `ICorDebugStepper` objet.</span><span class="sxs-lookup"><span data-stu-id="8b709-107">[out] An array of pointers, each of which points to an `ICorDebugStepper` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="8b709-108">à Pointeur vers le nombre d' `ICorDebugStepper` instances réellement retournées.</span><span class="sxs-lookup"><span data-stu-id="8b709-108">[out] Pointer to the number of `ICorDebugStepper` instances actually returned.</span></span> <span data-ttu-id="8b709-109">Cette valeur peut être null si `celt` est un.</span><span class="sxs-lookup"><span data-stu-id="8b709-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b709-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8b709-110">Requirements</span></span>  

 <span data-ttu-id="8b709-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b709-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b709-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b709-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b709-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b709-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b709-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b709-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
