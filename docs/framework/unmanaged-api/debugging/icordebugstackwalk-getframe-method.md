---
title: ICorDebugStackWalk::GetFrame, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetFrame
helpviewer_keywords:
- GetFrame method [.NET Framework debugging]
- ICorDebugStackWalk::GetFrame method [.NET Framework debugging]
ms.assetid: 4083b505-5b59-44fb-8c5d-129db6a96c10
topic_type:
- apiref
ms.openlocfilehash: 77210edfdc954f38ff06bc43a8b41a6abe8dc3d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131835"
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="f7ec5-102">ICorDebugStackWalk::GetFrame, méthode</span><span class="sxs-lookup"><span data-stu-id="f7ec5-102">ICorDebugStackWalk::GetFrame Method</span></span>
<span data-ttu-id="f7ec5-103">Obtient le frame actuel dans l’objet [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f7ec5-103">Gets the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7ec5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7ec5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7ec5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f7ec5-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="f7ec5-106">dans Pointeur vers l’adresse de l’objet Frame créé qui représente le frame actuel dans la pile.</span><span class="sxs-lookup"><span data-stu-id="f7ec5-106">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7ec5-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f7ec5-107">Return Value</span></span>  
 <span data-ttu-id="f7ec5-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="f7ec5-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f7ec5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f7ec5-109">HRESULT</span></span>|<span data-ttu-id="f7ec5-110">Description</span><span class="sxs-lookup"><span data-stu-id="f7ec5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f7ec5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f7ec5-111">S_OK</span></span>|<span data-ttu-id="f7ec5-112">Le runtime a correctement retourné le frame actuel.</span><span class="sxs-lookup"><span data-stu-id="f7ec5-112">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="f7ec5-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f7ec5-113">E_FAIL</span></span>|<span data-ttu-id="f7ec5-114">Le frame actuel n’a pas été retourné.</span><span class="sxs-lookup"><span data-stu-id="f7ec5-114">The current frame was not returned.</span></span>|  
|<span data-ttu-id="f7ec5-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f7ec5-115">S_FALSE</span></span>|<span data-ttu-id="f7ec5-116">Le frame actuel est un frame de pile natif.</span><span class="sxs-lookup"><span data-stu-id="f7ec5-116">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="f7ec5-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f7ec5-117">E_INVALIDARG</span></span>|<span data-ttu-id="f7ec5-118">`pFrame` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="f7ec5-118">`pFrame` is null.</span></span>|  
|<span data-ttu-id="f7ec5-119">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="f7ec5-119">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="f7ec5-120">Le pointeur de frame est déjà à la fin de la pile ; par conséquent, il n’est pas possible d’accéder à des frames supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="f7ec5-120">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="f7ec5-121">Exceptions</span><span class="sxs-lookup"><span data-stu-id="f7ec5-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7ec5-122">Notes</span><span class="sxs-lookup"><span data-stu-id="f7ec5-122">Remarks</span></span>  
 <span data-ttu-id="f7ec5-123">`ICorDebugStackWalk` retourne uniquement les frames de pile réels.</span><span class="sxs-lookup"><span data-stu-id="f7ec5-123">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="f7ec5-124">Utilisez la méthode [ICorDebugThread3 :: GetActiveInternalFrames,](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) pour retourner des frames internes.</span><span class="sxs-lookup"><span data-stu-id="f7ec5-124">Use the [ICorDebugThread3::GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="f7ec5-125">(Les frames internes sont des structures de données faisant l’objet d’un push dans la pile par le runtime pour stocker des données temporaires.)</span><span class="sxs-lookup"><span data-stu-id="f7ec5-125">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7ec5-126">spécifications</span><span class="sxs-lookup"><span data-stu-id="f7ec5-126">Requirements</span></span>  
 <span data-ttu-id="f7ec5-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7ec5-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7ec5-128">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7ec5-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7ec5-129">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7ec5-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7ec5-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7ec5-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7ec5-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7ec5-131">See also</span></span>

- [<span data-ttu-id="f7ec5-132">ICorDebugStackWalk, interface</span><span class="sxs-lookup"><span data-stu-id="f7ec5-132">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [<span data-ttu-id="f7ec5-133">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f7ec5-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f7ec5-134">Débogage</span><span class="sxs-lookup"><span data-stu-id="f7ec5-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
