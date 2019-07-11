---
title: ICorDebugThread3::GetActiveInternalFrames, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.GetActiveInternalFrames Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58aaf0445fe42d083c12541056cb362f9a994944
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765213"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="05f14-102">ICorDebugThread3::GetActiveInternalFrames, méthode</span><span class="sxs-lookup"><span data-stu-id="05f14-102">ICorDebugThread3::GetActiveInternalFrames Method</span></span>
<span data-ttu-id="05f14-103">Retourne un tableau de frames internes ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objets) sur la pile.</span><span class="sxs-lookup"><span data-stu-id="05f14-103">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05f14-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05f14-104">Syntax</span></span>  
  
```cpp 
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a><span data-ttu-id="05f14-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="05f14-105">Parameters</span></span>  
 `cInternalFrames`  
 <span data-ttu-id="05f14-106">[in] Le nombre de frames internes prévus dans `ppInternalFrames`.</span><span class="sxs-lookup"><span data-stu-id="05f14-106">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="05f14-107">[out] Un pointeur vers un `ULONG32` qui contient le nombre de frames internes sur la pile.</span><span class="sxs-lookup"><span data-stu-id="05f14-107">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="05f14-108">[in, out] Pointeur vers l’adresse d’un tableau de frames internes sur la pile.</span><span class="sxs-lookup"><span data-stu-id="05f14-108">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05f14-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="05f14-109">Return Value</span></span>  
 <span data-ttu-id="05f14-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="05f14-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="05f14-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="05f14-111">HRESULT</span></span>|<span data-ttu-id="05f14-112">Description</span><span class="sxs-lookup"><span data-stu-id="05f14-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="05f14-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="05f14-113">S_OK</span></span>|<span data-ttu-id="05f14-114">Le [ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objet a été créé avec succès.</span><span class="sxs-lookup"><span data-stu-id="05f14-114">The [ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="05f14-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="05f14-115">E_INVALIDARG</span></span>|<span data-ttu-id="05f14-116">`cInternalFrames` n’est pas égal à zéro et `ppInternalFrames` est `null`, ou `pcInternalFrames` est `null`.</span><span class="sxs-lookup"><span data-stu-id="05f14-116">`cInternalFrames` is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="05f14-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="05f14-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="05f14-118">`ppInternalFrames` est inférieur au nombre de frames internes.</span><span class="sxs-lookup"><span data-stu-id="05f14-118">`ppInternalFrames` is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="05f14-119">Exceptions</span><span class="sxs-lookup"><span data-stu-id="05f14-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05f14-120">Notes</span><span class="sxs-lookup"><span data-stu-id="05f14-120">Remarks</span></span>  
 <span data-ttu-id="05f14-121">Frames internes sont des structures de données envoyées à la pile par le runtime pour stocker des données temporaires.</span><span class="sxs-lookup"><span data-stu-id="05f14-121">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="05f14-122">Lorsque vous appelez `GetActiveInternalFrames`, vous devez définir le `cInternalFrames` paramètre 0 (zéro) et le `ppInternalFrames` paramètre null.</span><span class="sxs-lookup"><span data-stu-id="05f14-122">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="05f14-123">Lorsque `GetActiveInternalFrames` retourne en premier, `pcInternalFrames` contient le nombre de frames internes sur la pile.</span><span class="sxs-lookup"><span data-stu-id="05f14-123">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 <span data-ttu-id="05f14-124">`GetActiveInternalFrames` doit ensuite être appelé une deuxième fois.</span><span class="sxs-lookup"><span data-stu-id="05f14-124">`GetActiveInternalFrames` should then be called a second time.</span></span> <span data-ttu-id="05f14-125">Vous devez passer le nombre correct (`pcInternalFrames`) dans le `cInternalFrames` paramètre, et spécifiez un pointeur vers un tableau de taille appropriée dans `ppInternalFrames`.</span><span class="sxs-lookup"><span data-stu-id="05f14-125">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="05f14-126">Utilisez le [ICorDebugStackWalk::GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) méthode pour retourner réelle des frames de pile.</span><span class="sxs-lookup"><span data-stu-id="05f14-126">Use the [ICorDebugStackWalk::GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05f14-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="05f14-127">Requirements</span></span>  
 <span data-ttu-id="05f14-128">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05f14-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05f14-129">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05f14-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05f14-130">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05f14-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05f14-131">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05f14-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05f14-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05f14-132">See also</span></span>

- [<span data-ttu-id="05f14-133">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="05f14-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="05f14-134">Débogage</span><span class="sxs-lookup"><span data-stu-id="05f14-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
