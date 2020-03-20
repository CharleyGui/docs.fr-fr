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
ms.openlocfilehash: 680af5afa3ebef5bcaf9e34580e421dcc8093aaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178462"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="527ce-102">ICorDebugThread3::GetActiveInternalFrames, méthode</span><span class="sxs-lookup"><span data-stu-id="527ce-102">ICorDebugThread3::GetActiveInternalFrames Method</span></span>
<span data-ttu-id="527ce-103">Retourne une gamme d’images internes (objets[ICorDebugInternalFrame2)](icordebuginternalframe2-interface.md) sur la pile.</span><span class="sxs-lookup"><span data-stu-id="527ce-103">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="527ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="527ce-104">Syntax</span></span>  
  
```cpp
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a><span data-ttu-id="527ce-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="527ce-105">Parameters</span></span>  
 `cInternalFrames`  
 <span data-ttu-id="527ce-106">[dans] Le nombre de cadres `ppInternalFrames`internes attendus dans .</span><span class="sxs-lookup"><span data-stu-id="527ce-106">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="527ce-107">[out] Un pointeur `ULONG32` à un qui contient le nombre de cadres internes sur la pile.</span><span class="sxs-lookup"><span data-stu-id="527ce-107">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="527ce-108">[dans, dehors] Un pointeur à l’adresse d’un tableau de cadres internes sur la pile.</span><span class="sxs-lookup"><span data-stu-id="527ce-108">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="527ce-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="527ce-109">Return Value</span></span>  
 <span data-ttu-id="527ce-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="527ce-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="527ce-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="527ce-111">HRESULT</span></span>|<span data-ttu-id="527ce-112">Description</span><span class="sxs-lookup"><span data-stu-id="527ce-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="527ce-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="527ce-113">S_OK</span></span>|<span data-ttu-id="527ce-114">[L’objet ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) a été créé avec succès.</span><span class="sxs-lookup"><span data-stu-id="527ce-114">The [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="527ce-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="527ce-115">E_INVALIDARG</span></span>|<span data-ttu-id="527ce-116">`cInternalFrames`n’est `ppInternalFrames` pas `null`nul `pcInternalFrames` `null`et est , ou est .</span><span class="sxs-lookup"><span data-stu-id="527ce-116">`cInternalFrames` is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="527ce-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="527ce-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="527ce-118">`ppInternalFrames`est plus petit que le nombre de cadres internes.</span><span class="sxs-lookup"><span data-stu-id="527ce-118">`ppInternalFrames` is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="527ce-119">Exceptions</span><span class="sxs-lookup"><span data-stu-id="527ce-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="527ce-120">Notes </span><span class="sxs-lookup"><span data-stu-id="527ce-120">Remarks</span></span>  
 <span data-ttu-id="527ce-121">Les cadres internes sont des structures de données poussées sur la pile par le temps d’exécution pour stocker des données temporaires.</span><span class="sxs-lookup"><span data-stu-id="527ce-121">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="527ce-122">Lorsque vous `GetActiveInternalFrames`appelez pour la `cInternalFrames` première fois, vous devez `ppInternalFrames` définir le paramètre à 0 (zéro), et le paramètre à annuler.</span><span class="sxs-lookup"><span data-stu-id="527ce-122">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="527ce-123">Lors `GetActiveInternalFrames` de `pcInternalFrames` la première revient, contient le compte des cadres internes sur la pile.</span><span class="sxs-lookup"><span data-stu-id="527ce-123">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 <span data-ttu-id="527ce-124">`GetActiveInternalFrames`devrait alors être appelé une deuxième fois.</span><span class="sxs-lookup"><span data-stu-id="527ce-124">`GetActiveInternalFrames` should then be called a second time.</span></span> <span data-ttu-id="527ce-125">Vous devez passer le`pcInternalFrames`bon nombre `cInternalFrames` ( ) dans le paramètre, `ppInternalFrames`et spécifier un pointeur à un tableau de taille appropriée dans .</span><span class="sxs-lookup"><span data-stu-id="527ce-125">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="527ce-126">Utilisez la méthode [ICorDebugStackWalk::GetFrame](icordebugthread3-getactiveinternalframes-method.md) pour retourner les cadres de pile réels.</span><span class="sxs-lookup"><span data-stu-id="527ce-126">Use the [ICorDebugStackWalk::GetFrame](icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="527ce-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="527ce-127">Requirements</span></span>  
 <span data-ttu-id="527ce-128">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="527ce-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="527ce-129">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="527ce-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="527ce-130">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="527ce-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="527ce-131">**.NET Versions-cadre:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="527ce-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="527ce-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="527ce-132">See also</span></span>

- [<span data-ttu-id="527ce-133">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="527ce-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="527ce-134">Débogage</span><span class="sxs-lookup"><span data-stu-id="527ce-134">Debugging</span></span>](index.md)
