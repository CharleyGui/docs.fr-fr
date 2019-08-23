---
title: ICorProfilerInfo4::GetCodeInfo3, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetCodeInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetCodeInfo3
helpviewer_keywords:
- GetCodeInfo3 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetCodeInfo3 method [.NET Framework profiling]
ms.assetid: bb8c105e-4d9a-4684-8c05-ed6909cc1b8c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 084007bd7ab20449c28d2c5e6125cbacfa280526
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912716"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a><span data-ttu-id="1df36-102">ICorProfilerInfo4::GetCodeInfo3, méthode</span><span class="sxs-lookup"><span data-stu-id="1df36-102">ICorProfilerInfo4::GetCodeInfo3 Method</span></span>
<span data-ttu-id="1df36-103">Obtient les étendues de code natif associées à la version recompilée juste-à-temps de la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1df36-103">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1df36-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1df36-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1df36-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1df36-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="1df36-106">[in] ID de la fonction à laquelle le code natif est associé.</span><span class="sxs-lookup"><span data-stu-id="1df36-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `reJitId`  
 <span data-ttu-id="1df36-107">[in] Identité de la fonction recompilée juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="1df36-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="1df36-108">[in] Taille du tableau `codeInfos`.</span><span class="sxs-lookup"><span data-stu-id="1df36-108">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="1df36-109">à Pointeur vers le nombre total de structures [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) disponibles.</span><span class="sxs-lookup"><span data-stu-id="1df36-109">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="1df36-110">[out] Mémoire tampon fournie par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="1df36-110">[out] A caller-provided buffer.</span></span> <span data-ttu-id="1df36-111">Suite au retour de la méthode, celle-ci contient un tableau de structures `COR_PRF_CODE_INFO` qui décrivent chacune un bloc de code natif.</span><span class="sxs-lookup"><span data-stu-id="1df36-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1df36-112">Notes</span><span class="sxs-lookup"><span data-stu-id="1df36-112">Remarks</span></span>  
 <span data-ttu-id="1df36-113">La `GetCodeInfo3` méthode est similaire à [GetCodeInfo2,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), à ceci près qu’elle obtient l’ID recompilé juste-à-temps de la fonction qui contient l’adresse IP spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1df36-113">The `GetCodeInfo3` method is similar to [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), except that it will get the JIT-recompiled ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1df36-114">`GetCodeInfo3`peut déclencher un garbage collection, contrairement à [GetCodeInfo2,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1df36-114">`GetCodeInfo3` can trigger a garbage collection, whereas [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) will not.</span></span> <span data-ttu-id="1df36-115">Pour plus d’informations, consultez [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span><span class="sxs-lookup"><span data-stu-id="1df36-115">For more information, see the [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span></span>  
  
 <span data-ttu-id="1df36-116">Les étendues sont triées par ordre croissant des offsets du langage CIL (Common Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="1df36-116">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="1df36-117">Après `GetCodeInfo3` le retour de, vous devez vérifier `codeInfos` que la mémoire tampon est suffisamment grande pour contenir toutes les structures [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="1df36-117">After `GetCodeInfo3` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="1df36-118">Pour ce faire, comparez la valeur de `cCodeInfos` à celle du paramètre `cchName`.</span><span class="sxs-lookup"><span data-stu-id="1df36-118">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="1df36-119">Si `cCodeInfos` le fractionnement par la taille d’une structure [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) est `pcCodeInfos`inférieur à, allouez une mémoire `cCodeInfos` tampon plus grande `codeInfos` , mettez à jour avec la `GetCodeInfo3` nouvelle taille plus grande, puis rappelez.</span><span class="sxs-lookup"><span data-stu-id="1df36-119">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo3` again.</span></span>  
  
 <span data-ttu-id="1df36-120">Vous pouvez également commencer par appeler `GetCodeInfo3` avec un tampon `codeInfos` de longueur nulle pour obtenir la taille correcte du tampon.</span><span class="sxs-lookup"><span data-stu-id="1df36-120">Alternatively, you can first call `GetCodeInfo3` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="1df36-121">Vous pouvez ensuite affecter à la `codeInfos` taille de la mémoire tampon la valeur retournée dans `pcCodeInfos`, multipliée par la taille d’une structure [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md), puis rappeler `GetCodeInfo3`.</span><span class="sxs-lookup"><span data-stu-id="1df36-121">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure, and call `GetCodeInfo3` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1df36-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1df36-122">Requirements</span></span>  
 <span data-ttu-id="1df36-123">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1df36-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1df36-124">**En-tête :** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1df36-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1df36-125">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1df36-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1df36-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1df36-126">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1df36-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1df36-127">See also</span></span>

- [<span data-ttu-id="1df36-128">GetCodeInfo2, méthode</span><span class="sxs-lookup"><span data-stu-id="1df36-128">GetCodeInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)
- [<span data-ttu-id="1df36-129">ICorProfilerInfo4, interface</span><span class="sxs-lookup"><span data-stu-id="1df36-129">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="1df36-130">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="1df36-130">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="1df36-131">Profilage</span><span class="sxs-lookup"><span data-stu-id="1df36-131">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
