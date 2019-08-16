---
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: e0493ed3f8796019d5715ef468c88675b9970a39
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973839"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a><span data-ttu-id="a1d8e-102">ICorProfilerInfo9:: GetCodeInfo4, méthode</span><span class="sxs-lookup"><span data-stu-id="a1d8e-102">ICorProfilerInfo9::GetCodeInfo4 Method</span></span>
  
 <span data-ttu-id="a1d8e-103">À partir de l’adresse de début du code natif, retourne les blocs de mémoire virtuelle qui stockent ce code.</span><span class="sxs-lookup"><span data-stu-id="a1d8e-103">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="a1d8e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1d8e-104">Syntax</span></span>  
  
```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1d8e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a1d8e-105">Parameters</span></span>  
 `pNativeCodeStartAddress`  
 <span data-ttu-id="a1d8e-106">dans Pointeur vers le début d’une fonction native.</span><span class="sxs-lookup"><span data-stu-id="a1d8e-106">[in] A pointer to the start of a native function.</span></span>  

 `cCodeInfos`  
 <span data-ttu-id="a1d8e-107">[in] Taille du tableau `codeInfos`.</span><span class="sxs-lookup"><span data-stu-id="a1d8e-107">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="a1d8e-108">à Pointeur vers le nombre total de structures [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) disponibles.</span><span class="sxs-lookup"><span data-stu-id="a1d8e-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="a1d8e-109">[out] Mémoire tampon fournie par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="a1d8e-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="a1d8e-110">Suite au retour de la méthode, celle-ci contient un tableau de structures `COR_PRF_CODE_INFO` qui décrivent chacune un bloc de code natif.</span><span class="sxs-lookup"><span data-stu-id="a1d8e-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1d8e-111">Notes</span><span class="sxs-lookup"><span data-stu-id="a1d8e-111">Remarks</span></span>  
 <span data-ttu-id="a1d8e-112">La `GetCodeInfo4` méthode est semblable à [getcodeinfo3,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md), à ceci près qu’elle peut rechercher des informations de code pour différentes versions natives d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="a1d8e-112">The `GetCodeInfo4` method is similar to [GetCodeInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md), except that it can look up code information for different native versions of a method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1d8e-113">`GetCodeInfo4`peut déclencher un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="a1d8e-113">`GetCodeInfo4` can trigger a garbage collection.</span></span>
  
 <span data-ttu-id="a1d8e-114">Les étendues sont triées par ordre croissant des offsets du langage CIL (Common Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="a1d8e-114">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="a1d8e-115">Après `GetCodeInfo4` le retour de, vous devez vérifier `codeInfos` que la mémoire tampon est suffisamment grande pour contenir toutes les structures [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="a1d8e-115">After `GetCodeInfo4` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="a1d8e-116">Pour ce faire, comparez la valeur de `cCodeInfos` à celle du paramètre `cchName`.</span><span class="sxs-lookup"><span data-stu-id="a1d8e-116">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="a1d8e-117">Si `cCodeInfos` le fractionnement par la taille d’une structure [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) est `pcCodeInfos`inférieur à, allouez une mémoire `cCodeInfos` tampon plus grande `codeInfos` , mettez à jour avec la `GetCodeInfo4` nouvelle taille plus grande, puis rappelez.</span><span class="sxs-lookup"><span data-stu-id="a1d8e-117">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo4` again.</span></span>  
  
 <span data-ttu-id="a1d8e-118">Vous pouvez également commencer par appeler `GetCodeInfo4` avec un tampon `codeInfos` de longueur nulle pour obtenir la taille correcte du tampon.</span><span class="sxs-lookup"><span data-stu-id="a1d8e-118">Alternatively, you can first call `GetCodeInfo4` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="a1d8e-119">Vous pouvez ensuite affecter à la `codeInfos` taille de la mémoire tampon la valeur retournée dans `pcCodeInfos`, multipliée par la taille d’une structure [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md), puis rappeler `GetCodeInfo4`.</span><span class="sxs-lookup"><span data-stu-id="a1d8e-119">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure, and call `GetCodeInfo4` again.</span></span>   
  

## <a name="requirements"></a><span data-ttu-id="a1d8e-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a1d8e-120">Requirements</span></span>  
 <span data-ttu-id="a1d8e-121">**Plateformes** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="a1d8e-121">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="a1d8e-122">**En-tête :** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a1d8e-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a1d8e-123">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1d8e-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1d8e-124">**Versions de .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1d8e-124">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="a1d8e-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1d8e-125">See also</span></span>
- [<span data-ttu-id="a1d8e-126">Interface ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="a1d8e-126">ICorProfilerInfo9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/ICorProfilerInfo9-interface.md)

