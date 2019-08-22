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
ms.openlocfilehash: e6708971909c1035e41786f4d8dad1cf9afdffaf
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665614"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a><span data-ttu-id="ebf75-102">ICorProfilerInfo9:: GetCodeInfo4, méthode</span><span class="sxs-lookup"><span data-stu-id="ebf75-102">ICorProfilerInfo9::GetCodeInfo4 Method</span></span>

<span data-ttu-id="ebf75-103">À partir de l’adresse de début du code natif, retourne les blocs de mémoire virtuelle qui stockent ce code.</span><span class="sxs-lookup"><span data-stu-id="ebf75-103">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span>

## <a name="syntax"></a><span data-ttu-id="ebf75-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebf75-104">Syntax</span></span>

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

#### <a name="parameters"></a><span data-ttu-id="ebf75-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ebf75-105">Parameters</span></span>

`pNativeCodeStartAddress` \
<span data-ttu-id="ebf75-106">dans Pointeur vers le début d’une fonction native.</span><span class="sxs-lookup"><span data-stu-id="ebf75-106">[in] A pointer to the start of a native function.</span></span>

`cCodeInfos` \
<span data-ttu-id="ebf75-107">[in] Taille du tableau `codeInfos`.</span><span class="sxs-lookup"><span data-stu-id="ebf75-107">[in] The size of the `codeInfos` array.</span></span>

`pcCodeInfos` \
<span data-ttu-id="ebf75-108">à Pointeur vers le nombre total de structures [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) disponibles.</span><span class="sxs-lookup"><span data-stu-id="ebf75-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>

`codeInfos` \
<span data-ttu-id="ebf75-109">[out] Mémoire tampon fournie par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="ebf75-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="ebf75-110">Suite au retour de la méthode, celle-ci contient un tableau de structures `COR_PRF_CODE_INFO` qui décrivent chacune un bloc de code natif.</span><span class="sxs-lookup"><span data-stu-id="ebf75-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ebf75-111">Notes</span><span class="sxs-lookup"><span data-stu-id="ebf75-111">Remarks</span></span>

<span data-ttu-id="ebf75-112">La `GetCodeInfo4` méthode est semblable à [getcodeinfo3,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md), à ceci près qu’elle peut rechercher des informations de code pour différentes versions natives d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="ebf75-112">The `GetCodeInfo4` method is similar to [GetCodeInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md), except that it can look up code information for different native versions of a method.</span></span>

> [!NOTE]
> <span data-ttu-id="ebf75-113">`GetCodeInfo4`peut déclencher un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="ebf75-113">`GetCodeInfo4` can trigger a garbage collection.</span></span>

<span data-ttu-id="ebf75-114">Les étendues sont triées par ordre croissant des offsets du langage CIL (Common Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="ebf75-114">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>

<span data-ttu-id="ebf75-115">Après `GetCodeInfo4` le retour de, vous devez vérifier `codeInfos` que la mémoire tampon est suffisamment grande pour contenir toutes les structures [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="ebf75-115">After `GetCodeInfo4` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="ebf75-116">Pour ce faire, comparez la valeur de `cCodeInfos` à celle du paramètre `cchName`.</span><span class="sxs-lookup"><span data-stu-id="ebf75-116">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="ebf75-117">Si `cCodeInfos` le fractionnement par la taille d’une structure [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) est `pcCodeInfos`inférieur à, allouez une mémoire `cCodeInfos` tampon plus grande `codeInfos` , mettez à jour avec la `GetCodeInfo4` nouvelle taille plus grande, puis rappelez.</span><span class="sxs-lookup"><span data-stu-id="ebf75-117">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo4` again.</span></span>

<span data-ttu-id="ebf75-118">Vous pouvez également commencer par appeler `GetCodeInfo4` avec un tampon `codeInfos` de longueur nulle pour obtenir la taille correcte du tampon.</span><span class="sxs-lookup"><span data-stu-id="ebf75-118">Alternatively, you can first call `GetCodeInfo4` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="ebf75-119">Vous pouvez ensuite affecter à la `codeInfos` taille de la mémoire tampon la valeur retournée dans `pcCodeInfos`, multipliée par la taille d’une structure [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md), puis rappeler `GetCodeInfo4`.</span><span class="sxs-lookup"><span data-stu-id="ebf75-119">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure, and call `GetCodeInfo4` again.</span></span>

## <a name="requirements"></a><span data-ttu-id="ebf75-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ebf75-120">Requirements</span></span>

<span data-ttu-id="ebf75-121">**Plateformes** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="ebf75-121">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="ebf75-122">**En-tête :** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ebf75-122">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="ebf75-123">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebf75-123">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="ebf75-124">**Versions de .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebf75-124">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ebf75-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebf75-125">See also</span></span>

- [<span data-ttu-id="ebf75-126">Interface ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="ebf75-126">ICorProfilerInfo9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/ICorProfilerInfo9-interface.md)
