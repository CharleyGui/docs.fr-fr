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
ms.openlocfilehash: 953b7c1cb5e471072776fe03e53a46d3ff19c0ac
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379864"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="faf99-102">ICorDebugThread3::GetActiveInternalFrames, méthode</span><span class="sxs-lookup"><span data-stu-id="faf99-102">ICorDebugThread3::GetActiveInternalFrames Method</span></span>
<span data-ttu-id="faf99-103">Retourne un tableau de frames internes (objets[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) ) sur la pile.</span><span class="sxs-lookup"><span data-stu-id="faf99-103">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faf99-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="faf99-104">Syntax</span></span>  
  
```cpp
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a><span data-ttu-id="faf99-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="faf99-105">Parameters</span></span>  
 `cInternalFrames`  
 <span data-ttu-id="faf99-106">dans Nombre de frames internes attendus dans `ppInternalFrames` .</span><span class="sxs-lookup"><span data-stu-id="faf99-106">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="faf99-107">à Pointeur vers un `ULONG32` qui contient le nombre de frames internes sur la pile.</span><span class="sxs-lookup"><span data-stu-id="faf99-107">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="faf99-108">[in, out] Pointeur vers l’adresse d’un tableau de frames internes sur la pile.</span><span class="sxs-lookup"><span data-stu-id="faf99-108">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="faf99-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="faf99-109">Return Value</span></span>  
 <span data-ttu-id="faf99-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="faf99-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="faf99-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="faf99-111">HRESULT</span></span>|<span data-ttu-id="faf99-112">Description</span><span class="sxs-lookup"><span data-stu-id="faf99-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="faf99-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="faf99-113">S_OK</span></span>|<span data-ttu-id="faf99-114">L’objet [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) a été créé avec succès.</span><span class="sxs-lookup"><span data-stu-id="faf99-114">The [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="faf99-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="faf99-115">E_INVALIDARG</span></span>|<span data-ttu-id="faf99-116">`cInternalFrames`n’est pas égal à zéro et `ppInternalFrames` est `null` , ou a la valeur `pcInternalFrames` `null` .</span><span class="sxs-lookup"><span data-stu-id="faf99-116">`cInternalFrames` is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="faf99-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="faf99-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="faf99-118">`ppInternalFrames`est plus petit que le nombre de frames internes.</span><span class="sxs-lookup"><span data-stu-id="faf99-118">`ppInternalFrames` is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="faf99-119">Exceptions</span><span class="sxs-lookup"><span data-stu-id="faf99-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="faf99-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="faf99-120">Remarks</span></span>  
 <span data-ttu-id="faf99-121">Les frames internes sont des structures de données envoyées dans la pile par le runtime pour stocker des données temporaires.</span><span class="sxs-lookup"><span data-stu-id="faf99-121">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="faf99-122">Lorsque vous appelez `GetActiveInternalFrames` pour la première fois, vous devez affecter la valeur `cInternalFrames` 0 (zéro) au paramètre et la `ppInternalFrames` valeur null au paramètre.</span><span class="sxs-lookup"><span data-stu-id="faf99-122">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="faf99-123">Lors `GetActiveInternalFrames` du premier retour, `pcInternalFrames` contient le nombre de frames internes sur la pile.</span><span class="sxs-lookup"><span data-stu-id="faf99-123">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 <span data-ttu-id="faf99-124">`GetActiveInternalFrames`doit ensuite être appelée une deuxième fois.</span><span class="sxs-lookup"><span data-stu-id="faf99-124">`GetActiveInternalFrames` should then be called a second time.</span></span> <span data-ttu-id="faf99-125">Vous devez passer le nombre correct ( `pcInternalFrames` ) dans le `cInternalFrames` paramètre et spécifier un pointeur vers un tableau de taille appropriée dans `ppInternalFrames` .</span><span class="sxs-lookup"><span data-stu-id="faf99-125">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="faf99-126">Utilisez la méthode [ICorDebugStackWalk :: GetFrame](icordebugthread3-getactiveinternalframes-method.md) pour retourner des frames de pile réels.</span><span class="sxs-lookup"><span data-stu-id="faf99-126">Use the [ICorDebugStackWalk::GetFrame](icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faf99-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="faf99-127">Requirements</span></span>  
 <span data-ttu-id="faf99-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faf99-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faf99-129">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="faf99-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="faf99-130">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="faf99-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="faf99-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faf99-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faf99-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="faf99-132">See also</span></span>

- [<span data-ttu-id="faf99-133">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="faf99-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="faf99-134">Débogage</span><span class="sxs-lookup"><span data-stu-id="faf99-134">Debugging</span></span>](index.md)
