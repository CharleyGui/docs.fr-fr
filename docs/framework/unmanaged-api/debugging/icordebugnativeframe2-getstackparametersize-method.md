---
title: ICorDebugNativeFrame2::GetStackParameterSize, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.GetStackParameterSize Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize
helpviewer_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize method [.NET Framework debugging]
- GetStackParameterSize method [.NET Framework debugging]
ms.assetid: f6a449c8-a941-43ba-9a90-c98b29ae3c36
topic_type:
- apiref
ms.openlocfilehash: 21af3980de9b5a768b6af9a8aca74b693c7ac528
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695489"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="3756a-102">ICorDebugNativeFrame2::GetStackParameterSize, méthode</span><span class="sxs-lookup"><span data-stu-id="3756a-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>

<span data-ttu-id="3756a-103">Retourne la taille cumulée des paramètres sur la pile sur les systèmes d’exploitation x86.</span><span class="sxs-lookup"><span data-stu-id="3756a-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3756a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3756a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a><span data-ttu-id="3756a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3756a-105">Parameters</span></span>  

 `pSize`  
 <span data-ttu-id="3756a-106">à Pointeur vers la taille cumulée des paramètres sur la pile.</span><span class="sxs-lookup"><span data-stu-id="3756a-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3756a-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="3756a-107">Return Value</span></span>  

 <span data-ttu-id="3756a-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="3756a-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3756a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3756a-109">HRESULT</span></span>|<span data-ttu-id="3756a-110">Description</span><span class="sxs-lookup"><span data-stu-id="3756a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3756a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3756a-111">S_OK</span></span>|<span data-ttu-id="3756a-112">La taille de la pile a été correctement retournée.</span><span class="sxs-lookup"><span data-stu-id="3756a-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="3756a-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="3756a-113">S_FALSE</span></span>|<span data-ttu-id="3756a-114">`GetStackParameterSize` a été appelé sur une plateforme non-x86.</span><span class="sxs-lookup"><span data-stu-id="3756a-114">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="3756a-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3756a-115">E_FAIL</span></span>|<span data-ttu-id="3756a-116">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="3756a-116">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="3756a-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3756a-117">E_INVALIDARG</span></span>|<span data-ttu-id="3756a-118">`pSize` Est de `null` .</span><span class="sxs-lookup"><span data-stu-id="3756a-118">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="3756a-119">Exceptions</span><span class="sxs-lookup"><span data-stu-id="3756a-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3756a-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="3756a-120">Remarks</span></span>  

 <span data-ttu-id="3756a-121">Les méthodes [ICorDebugStackWalk](icordebugstackwalk-interface.md) n’ajustent pas le pointeur de pile pour les paramètres qui font l’objet d’un push sur la pile.</span><span class="sxs-lookup"><span data-stu-id="3756a-121">The [ICorDebugStackWalk](icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="3756a-122">Au lieu de cela, vous pouvez utiliser la valeur retournée par `GetStackParameterSize` pour ajuster le pointeur de pile pour amorcer un dérouleur natif, qui ajuste les paramètres.</span><span class="sxs-lookup"><span data-stu-id="3756a-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3756a-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3756a-123">Requirements</span></span>  

 <span data-ttu-id="3756a-124">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3756a-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3756a-125">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3756a-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3756a-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3756a-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3756a-127">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3756a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3756a-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3756a-128">See also</span></span>

- [<span data-ttu-id="3756a-129">ICorDebugNativeFrame2, interface</span><span class="sxs-lookup"><span data-stu-id="3756a-129">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="3756a-130">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="3756a-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="3756a-131">Débogage</span><span class="sxs-lookup"><span data-stu-id="3756a-131">Debugging</span></span>](index.md)
