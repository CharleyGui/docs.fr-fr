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
ms.openlocfilehash: 213bee96531fa0bbc9bf0ae76b2505019833abfc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724700"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="00b63-102">ICorDebugNativeFrame2::IsMatchingParentFrame, méthode</span><span class="sxs-lookup"><span data-stu-id="00b63-102">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>

<span data-ttu-id="00b63-103">Détermine si le frame spécifié est le parent du frame actuel.</span><span class="sxs-lookup"><span data-stu-id="00b63-103">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00b63-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00b63-104">Syntax</span></span>  
  
```cpp  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00b63-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="00b63-105">Parameters</span></span>  

 `pPotentialParentFrame`  
 <span data-ttu-id="00b63-106">dans Pointeur vers l’objet Frame que vous souhaitez évaluer pour l’état parent.</span><span class="sxs-lookup"><span data-stu-id="00b63-106">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="00b63-107">[out] `true` Si `pPotentialParentFrame` est le parent du frame actuel ; sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="00b63-107">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00b63-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="00b63-108">Return Value</span></span>  

 <span data-ttu-id="00b63-109">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="00b63-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="00b63-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="00b63-110">HRESULT</span></span>|<span data-ttu-id="00b63-111">Description</span><span class="sxs-lookup"><span data-stu-id="00b63-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="00b63-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="00b63-112">S_OK</span></span>|<span data-ttu-id="00b63-113">L’état parent a été retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="00b63-113">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="00b63-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="00b63-114">E_FAIL</span></span>|<span data-ttu-id="00b63-115">L’état parent n’a pas pu être retourné.</span><span class="sxs-lookup"><span data-stu-id="00b63-115">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="00b63-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="00b63-116">E_INVALIDARG</span></span>|<span data-ttu-id="00b63-117">`pPotentialParentFrame` ou `pIsParent` est null.</span><span class="sxs-lookup"><span data-stu-id="00b63-117">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="00b63-118">Exceptions</span><span class="sxs-lookup"><span data-stu-id="00b63-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00b63-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="00b63-119">Remarks</span></span>  

 <span data-ttu-id="00b63-120">`IsMatchingParentFrame` retourne `true` si l’objet Frame que vous transmettez à la méthode est le parent de l’objet Frame sur lequel la méthode a été appelée.</span><span class="sxs-lookup"><span data-stu-id="00b63-120">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="00b63-121">Si vous appelez la méthode sur un frame qui n’est pas un enfant du frame spécifié, elle retourne une erreur.</span><span class="sxs-lookup"><span data-stu-id="00b63-121">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00b63-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="00b63-122">Requirements</span></span>  

 <span data-ttu-id="00b63-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00b63-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00b63-124">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="00b63-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00b63-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00b63-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00b63-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00b63-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00b63-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00b63-127">See also</span></span>

- [<span data-ttu-id="00b63-128">ICorDebugNativeFrame2, interface</span><span class="sxs-lookup"><span data-stu-id="00b63-128">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="00b63-129">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="00b63-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="00b63-130">Débogage</span><span class="sxs-lookup"><span data-stu-id="00b63-130">Debugging</span></span>](index.md)
