---
title: ICorDebugInternalFrame2::IsCloserToLeaf, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.IsCloserToLeaf Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf
helpviewer_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf method [.NET Framework debugging]
- IsCloserToLeaf method [.NET Framework debugging]
ms.assetid: c1d3d1eb-8370-4f25-8297-3bd262b4740a
topic_type:
- apiref
ms.openlocfilehash: 83d3eda0f3c4619ec7a5df91d13ab9f3a58e5f01
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721346"
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a><span data-ttu-id="9c00f-102">ICorDebugInternalFrame2::IsCloserToLeaf, méthode</span><span class="sxs-lookup"><span data-stu-id="9c00f-102">ICorDebugInternalFrame2::IsCloserToLeaf Method</span></span>

<span data-ttu-id="9c00f-103">Vérifie si le `this` Frame interne est plus proche de la feuille que l’objet ICorDebugFrame spécifié.</span><span class="sxs-lookup"><span data-stu-id="9c00f-103">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c00f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c00f-104">Syntax</span></span>  
  
```cpp  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c00f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9c00f-105">Parameters</span></span>  

 `pFrameToCompare`  
 <span data-ttu-id="9c00f-106">dans Pointeur vers l’objet de comparaison `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="9c00f-106">[in] A pointer to the comparison `ICorDebugFrame` object.</span></span>  
  
 `pIsCloser`  
 <span data-ttu-id="9c00f-107">[out] `true` Si le `this` Frame interne est plus proche de la feuille que le frame spécifié par `pFrameToCompare` ; sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="9c00f-107">[out] `true` if the `this` internal frame is closer to the leaf than the frame specified by `pFrameToCompare`; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c00f-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="9c00f-108">Return Value</span></span>  

 <span data-ttu-id="9c00f-109">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="9c00f-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9c00f-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9c00f-110">HRESULT</span></span>|<span data-ttu-id="9c00f-111">Description</span><span class="sxs-lookup"><span data-stu-id="9c00f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9c00f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="9c00f-112">S_OK</span></span>|<span data-ttu-id="9c00f-113">La comparaison a été effectuée avec succès.</span><span class="sxs-lookup"><span data-stu-id="9c00f-113">The comparison was successfully performed.</span></span>|  
|<span data-ttu-id="9c00f-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9c00f-114">E_FAIL</span></span>|<span data-ttu-id="9c00f-115">La comparaison n’a pas pu être effectuée.</span><span class="sxs-lookup"><span data-stu-id="9c00f-115">The comparison could not be performed.</span></span>|  
|<span data-ttu-id="9c00f-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9c00f-116">E_INVALIDARG</span></span>|<span data-ttu-id="9c00f-117">`pFrameToCompare` ou `pIsCloser` est null.</span><span class="sxs-lookup"><span data-stu-id="9c00f-117">`pFrameToCompare` or `pIsCloser` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c00f-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="9c00f-118">Remarks</span></span>  

 <span data-ttu-id="9c00f-119">`IsCloserToLeaf` peut être utilisé pour implémenter une stratégie pour entrelacer des frames internes avec d’autres frames sur la pile.</span><span class="sxs-lookup"><span data-stu-id="9c00f-119">`IsCloserToLeaf` can be used to implement a policy for interleaving internal frames with other frames on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c00f-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9c00f-120">Requirements</span></span>  

 <span data-ttu-id="9c00f-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c00f-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c00f-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c00f-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c00f-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c00f-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c00f-124">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c00f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c00f-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c00f-125">See also</span></span>

- [<span data-ttu-id="9c00f-126">ICorDebugInternalFrame2, interface</span><span class="sxs-lookup"><span data-stu-id="9c00f-126">ICorDebugInternalFrame2 Interface</span></span>](icordebuginternalframe2-interface.md)
- [<span data-ttu-id="9c00f-127">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="9c00f-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9c00f-128">Débogage</span><span class="sxs-lookup"><span data-stu-id="9c00f-128">Debugging</span></span>](index.md)
