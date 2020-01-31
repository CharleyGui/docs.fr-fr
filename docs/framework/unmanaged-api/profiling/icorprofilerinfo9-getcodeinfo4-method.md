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
ms.openlocfilehash: 3e3e3afc221d153ff3573126ff10014d39af761a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868302"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a><span data-ttu-id="1fb18-102">ICorProfilerInfo9 :: GetCodeInfo4, méthode</span><span class="sxs-lookup"><span data-stu-id="1fb18-102">ICorProfilerInfo9::GetCodeInfo4 Method</span></span>

<span data-ttu-id="1fb18-103">À partir de l’adresse de début du code natif, retourne les blocs de mémoire virtuelle qui stockent ce code.</span><span class="sxs-lookup"><span data-stu-id="1fb18-103">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span>

## <a name="syntax"></a><span data-ttu-id="1fb18-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fb18-104">Syntax</span></span>

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

## <a name="parameters"></a><span data-ttu-id="1fb18-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="1fb18-105">Parameters</span></span>

- `pNativeCodeStartAddress`

  <span data-ttu-id="1fb18-106">\[dans] pointeur vers le début d’une fonction native.</span><span class="sxs-lookup"><span data-stu-id="1fb18-106">\[in] A pointer to the start of a native function.</span></span>

- `cCodeInfos`

  <span data-ttu-id="1fb18-107">\[dans] taille du tableau de `codeInfos`.</span><span class="sxs-lookup"><span data-stu-id="1fb18-107">\[in] The size of the `codeInfos` array.</span></span>

- `pcCodeInfos`

  <span data-ttu-id="1fb18-108">\[out] pointeur vers le nombre total de structures [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) disponibles.</span><span class="sxs-lookup"><span data-stu-id="1fb18-108">\[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>

- `codeInfos`

  <span data-ttu-id="1fb18-109">\[out] une mémoire tampon fournie par l’appelant.</span><span class="sxs-lookup"><span data-stu-id="1fb18-109">\[out] A caller-provided buffer.</span></span> <span data-ttu-id="1fb18-110">Suite au retour de la méthode, celle-ci contient un tableau de structures `COR_PRF_CODE_INFO` qui décrivent chacune un bloc de code natif.</span><span class="sxs-lookup"><span data-stu-id="1fb18-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1fb18-111">Notes</span><span class="sxs-lookup"><span data-stu-id="1fb18-111">Remarks</span></span>

<span data-ttu-id="1fb18-112">La méthode `GetCodeInfo4` est semblable à [getcodeinfo3,](icorprofilerinfo4-getcodeinfo3-method.md), à ceci près qu’elle peut rechercher des informations de code pour différentes versions natives d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="1fb18-112">The `GetCodeInfo4` method is similar to [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md), except that it can look up code information for different native versions of a method.</span></span>

> [!NOTE]
> <span data-ttu-id="1fb18-113">`GetCodeInfo4` pouvez déclencher une garbage collection.</span><span class="sxs-lookup"><span data-stu-id="1fb18-113">`GetCodeInfo4` can trigger a garbage collection.</span></span>

<span data-ttu-id="1fb18-114">Les étendues sont triées par ordre croissant des offsets du langage CIL (Common Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="1fb18-114">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>

<span data-ttu-id="1fb18-115">Une fois que `GetCodeInfo4` a retourné, vous devez vérifier que la mémoire tampon de `codeInfos` est suffisamment grande pour contenir toutes les structures de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="1fb18-115">After `GetCodeInfo4` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="1fb18-116">Pour ce faire, comparez la valeur de `cCodeInfos` à celle du paramètre `cchName`.</span><span class="sxs-lookup"><span data-stu-id="1fb18-116">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="1fb18-117">Si `cCodeInfos` divisée par la taille d’une structure [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) est plus petite que `pcCodeInfos`, allouez une plus grande mémoire tampon d' `codeInfos`, mettez à jour `cCodeInfos` avec la nouvelle taille plus grande, puis appelez à nouveau `GetCodeInfo4`.</span><span class="sxs-lookup"><span data-stu-id="1fb18-117">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo4` again.</span></span>

<span data-ttu-id="1fb18-118">Vous pouvez également commencer par appeler `GetCodeInfo4` avec un tampon `codeInfos` de longueur nulle pour obtenir la taille correcte du tampon.</span><span class="sxs-lookup"><span data-stu-id="1fb18-118">Alternatively, you can first call `GetCodeInfo4` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="1fb18-119">Vous pouvez ensuite affecter à la `codeInfos` taille de la mémoire tampon la valeur retournée dans `pcCodeInfos`, multipliée par la taille d’une structure [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md), puis rappeler `GetCodeInfo4`.</span><span class="sxs-lookup"><span data-stu-id="1fb18-119">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure, and call `GetCodeInfo4` again.</span></span>

## <a name="requirements"></a><span data-ttu-id="1fb18-120">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="1fb18-120">Requirements</span></span>

<span data-ttu-id="1fb18-121">**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="1fb18-121">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="1fb18-122">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1fb18-122">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="1fb18-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1fb18-123">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="1fb18-124">**Versions de .net :** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fb18-124">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1fb18-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1fb18-125">See also</span></span>

- [<span data-ttu-id="1fb18-126">Interface ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="1fb18-126">ICorProfilerInfo9 Interface</span></span>](ICorProfilerInfo9-interface.md)
