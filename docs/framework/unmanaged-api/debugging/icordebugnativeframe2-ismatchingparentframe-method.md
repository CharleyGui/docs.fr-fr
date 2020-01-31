---
title: ICorDebugNativeFrame2::IsMatchingParentFrame, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsMatchingParentFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsMatchingParentFrame
helpviewer_keywords:
- IsMatchingParentFrame method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsMatchingParentFrame method [.NET Framework debugging]
ms.assetid: d2ca20db-df22-4528-a0dd-a09ea62c8998
topic_type:
- apiref
ms.openlocfilehash: aeaa706ef35413a728f8b254cd325f0bcc83acd1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792713"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="cfbec-102">ICorDebugNativeFrame2::IsMatchingParentFrame, méthode</span><span class="sxs-lookup"><span data-stu-id="cfbec-102">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>
<span data-ttu-id="cfbec-103">Détermine si le frame spécifié est le parent du frame actuel.</span><span class="sxs-lookup"><span data-stu-id="cfbec-103">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfbec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cfbec-104">Syntax</span></span>  
  
```cpp  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfbec-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="cfbec-105">Parameters</span></span>  
 `pPotentialParentFrame`  
 <span data-ttu-id="cfbec-106">dans Pointeur vers l’objet Frame que vous souhaitez évaluer pour l’état parent.</span><span class="sxs-lookup"><span data-stu-id="cfbec-106">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="cfbec-107">[out] `true` si `pPotentialParentFrame` est le parent du frame actuel ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="cfbec-107">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cfbec-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="cfbec-108">Return Value</span></span>  
 <span data-ttu-id="cfbec-109">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="cfbec-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="cfbec-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cfbec-110">HRESULT</span></span>|<span data-ttu-id="cfbec-111">Description</span><span class="sxs-lookup"><span data-stu-id="cfbec-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cfbec-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="cfbec-112">S_OK</span></span>|<span data-ttu-id="cfbec-113">L’état parent a été retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="cfbec-113">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="cfbec-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cfbec-114">E_FAIL</span></span>|<span data-ttu-id="cfbec-115">L’état parent n’a pas pu être retourné.</span><span class="sxs-lookup"><span data-stu-id="cfbec-115">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="cfbec-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="cfbec-116">E_INVALIDARG</span></span>|<span data-ttu-id="cfbec-117">`pPotentialParentFrame` ou `pIsParent` est null.</span><span class="sxs-lookup"><span data-stu-id="cfbec-117">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="cfbec-118">Exceptions</span><span class="sxs-lookup"><span data-stu-id="cfbec-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfbec-119">Notes</span><span class="sxs-lookup"><span data-stu-id="cfbec-119">Remarks</span></span>  
 <span data-ttu-id="cfbec-120">`IsMatchingParentFrame` retourne `true` si l’objet Frame que vous transmettez à la méthode est le parent de l’objet Frame sur lequel la méthode a été appelée.</span><span class="sxs-lookup"><span data-stu-id="cfbec-120">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="cfbec-121">Si vous appelez la méthode sur un frame qui n’est pas un enfant du frame spécifié, elle retourne une erreur.</span><span class="sxs-lookup"><span data-stu-id="cfbec-121">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfbec-122">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="cfbec-122">Requirements</span></span>  
 <span data-ttu-id="cfbec-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfbec-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfbec-124">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cfbec-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cfbec-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfbec-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfbec-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfbec-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfbec-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cfbec-127">See also</span></span>

- [<span data-ttu-id="cfbec-128">ICorDebugNativeFrame2, interface</span><span class="sxs-lookup"><span data-stu-id="cfbec-128">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="cfbec-129">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="cfbec-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="cfbec-130">Débogage</span><span class="sxs-lookup"><span data-stu-id="cfbec-130">Debugging</span></span>](index.md)
