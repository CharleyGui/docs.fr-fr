---
title: ICorProfilerInfo::SetILInstrumentedCodeMap, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
ms.openlocfilehash: 32e63a6d2b6f739025d4c5558c16fe2d74fde73c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449867"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a><span data-ttu-id="e3672-102">ICorProfilerInfo::SetILInstrumentedCodeMap, méthode</span><span class="sxs-lookup"><span data-stu-id="e3672-102">ICorProfilerInfo::SetILInstrumentedCodeMap Method</span></span>

<span data-ttu-id="e3672-103">Sets a code map for the specified function using the specified Microsoft intermediate language (MSIL) map entries.</span><span class="sxs-lookup"><span data-stu-id="e3672-103">Sets a code map for the specified function using the specified Microsoft intermediate language (MSIL) map entries.</span></span>

> [!NOTE]
> <span data-ttu-id="e3672-104">In the .NET Framework version 2.0, calling `SetILInstrumentedCodeMap` on a `FunctionID` that represents a generic function in a particular application domain will affect all instances of that function in the application domain.</span><span class="sxs-lookup"><span data-stu-id="e3672-104">In the .NET Framework version 2.0, calling `SetILInstrumentedCodeMap` on a `FunctionID` that represents a generic function in a particular application domain will affect all instances of that function in the application domain.</span></span>

## <a name="syntax"></a><span data-ttu-id="e3672-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3672-105">Syntax</span></span>

```cpp
HRESULT SetILInstrumentedCodeMap(
    [in]  FunctionID functionId,
    [in]  BOOL       fStartJit,
    [in]  ULONG      cILMapEntries,
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);
```

## <a name="parameters"></a><span data-ttu-id="e3672-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e3672-106">Parameters</span></span>

`functionId`\
<span data-ttu-id="e3672-107">[in] The ID of the function for which to set the code map.</span><span class="sxs-lookup"><span data-stu-id="e3672-107">[in] The ID of the function for which to set the code map.</span></span>

`fStartJit`\
<span data-ttu-id="e3672-108">[in] A Boolean value that indicates whether the call to the `SetILInstrumentedCodeMap` method is the first for a particular `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="e3672-108">[in] A Boolean value that indicates whether the call to the `SetILInstrumentedCodeMap` method is the first for a particular `FunctionID`.</span></span> <span data-ttu-id="e3672-109">Set `fStartJit` to `true` in the first call to `SetILInstrumentedCodeMap` for a given `FunctionID`, and to `false` thereafter.</span><span class="sxs-lookup"><span data-stu-id="e3672-109">Set `fStartJit` to `true` in the first call to `SetILInstrumentedCodeMap` for a given `FunctionID`, and to `false` thereafter.</span></span>

`cILMapEntries`\
<span data-ttu-id="e3672-110">[in] The number of elements in the `cILMapEntries` array.</span><span class="sxs-lookup"><span data-stu-id="e3672-110">[in] The number of elements in the `cILMapEntries` array.</span></span>

`rgILMapEntries`\
<span data-ttu-id="e3672-111">[in] An array of COR_IL_MAP structures, each of which specifies an MSIL offset.</span><span class="sxs-lookup"><span data-stu-id="e3672-111">[in] An array of COR_IL_MAP structures, each of which specifies an MSIL offset.</span></span>

## <a name="remarks"></a><span data-ttu-id="e3672-112">Notes</span><span class="sxs-lookup"><span data-stu-id="e3672-112">Remarks</span></span>

<span data-ttu-id="e3672-113">A profiler often inserts statements within the source code of a method in order to instrument that method (for example, to notify when a given source line is reached).</span><span class="sxs-lookup"><span data-stu-id="e3672-113">A profiler often inserts statements within the source code of a method in order to instrument that method (for example, to notify when a given source line is reached).</span></span> <span data-ttu-id="e3672-114">`SetILInstrumentedCodeMap` enables a profiler to map the original MSIL instructions to their new locations.</span><span class="sxs-lookup"><span data-stu-id="e3672-114">`SetILInstrumentedCodeMap` enables a profiler to map the original MSIL instructions to their new locations.</span></span> <span data-ttu-id="e3672-115">A profiler can use the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method to get the original MSIL offset for a given native offset.</span><span class="sxs-lookup"><span data-stu-id="e3672-115">A profiler can use the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method to get the original MSIL offset for a given native offset.</span></span>

<span data-ttu-id="e3672-116">The debugger will assume that each old offset refers to an MSIL offset within the original, unmodified MSIL code, and that each new offset refers to the MSIL offset within the new, instrumented code.</span><span class="sxs-lookup"><span data-stu-id="e3672-116">The debugger will assume that each old offset refers to an MSIL offset within the original, unmodified MSIL code, and that each new offset refers to the MSIL offset within the new, instrumented code.</span></span> <span data-ttu-id="e3672-117">The map should be sorted in increasing order.</span><span class="sxs-lookup"><span data-stu-id="e3672-117">The map should be sorted in increasing order.</span></span> <span data-ttu-id="e3672-118">For stepping to work properly, follow these guidelines:</span><span class="sxs-lookup"><span data-stu-id="e3672-118">For stepping to work properly, follow these guidelines:</span></span>

- <span data-ttu-id="e3672-119">Do not reorder instrumented MSIL code.</span><span class="sxs-lookup"><span data-stu-id="e3672-119">Do not reorder instrumented MSIL code.</span></span>

- <span data-ttu-id="e3672-120">Do not remove the original MSIL code.</span><span class="sxs-lookup"><span data-stu-id="e3672-120">Do not remove the original MSIL code.</span></span>

- <span data-ttu-id="e3672-121">Include entries for all the sequence points from the program database (PDB) file in the map.</span><span class="sxs-lookup"><span data-stu-id="e3672-121">Include entries for all the sequence points from the program database (PDB) file in the map.</span></span> <span data-ttu-id="e3672-122">The map does not interpolate missing entries.</span><span class="sxs-lookup"><span data-stu-id="e3672-122">The map does not interpolate missing entries.</span></span> <span data-ttu-id="e3672-123">So, given the following map:</span><span class="sxs-lookup"><span data-stu-id="e3672-123">So, given the following map:</span></span>

  <span data-ttu-id="e3672-124">(0 old, 0 new)</span><span class="sxs-lookup"><span data-stu-id="e3672-124">(0 old, 0 new)</span></span>

  <span data-ttu-id="e3672-125">(5 old, 10 new)</span><span class="sxs-lookup"><span data-stu-id="e3672-125">(5 old, 10 new)</span></span>

  <span data-ttu-id="e3672-126">(9 old, 20 new)</span><span class="sxs-lookup"><span data-stu-id="e3672-126">(9 old, 20 new)</span></span>

  - <span data-ttu-id="e3672-127">An old offset of 0, 1, 2, 3, or 4 will be mapped to new offset 0.</span><span class="sxs-lookup"><span data-stu-id="e3672-127">An old offset of 0, 1, 2, 3, or 4 will be mapped to new offset 0.</span></span>

  - <span data-ttu-id="e3672-128">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span><span class="sxs-lookup"><span data-stu-id="e3672-128">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>

  - <span data-ttu-id="e3672-129">An old offset of 9 or higher will be mapped to new offset 20.</span><span class="sxs-lookup"><span data-stu-id="e3672-129">An old offset of 9 or higher will be mapped to new offset 20.</span></span>

  - <span data-ttu-id="e3672-130">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span><span class="sxs-lookup"><span data-stu-id="e3672-130">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>

  - <span data-ttu-id="e3672-131">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span><span class="sxs-lookup"><span data-stu-id="e3672-131">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>

  - <span data-ttu-id="e3672-132">A new offset of 20 or higher will be mapped to old offset 9.</span><span class="sxs-lookup"><span data-stu-id="e3672-132">A new offset of 20 or higher will be mapped to old offset 9.</span></span>

<span data-ttu-id="e3672-133">In the .NET Framework 3.5 and previous versions, you allocate the `rgILMapEntries` array by calling the [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) method.</span><span class="sxs-lookup"><span data-stu-id="e3672-133">In the .NET Framework 3.5 and previous versions, you allocate the `rgILMapEntries` array by calling the [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) method.</span></span> <span data-ttu-id="e3672-134">Because the runtime takes ownership of this memory, the profiler should not attempt to free it.</span><span class="sxs-lookup"><span data-stu-id="e3672-134">Because the runtime takes ownership of this memory, the profiler should not attempt to free it.</span></span>

## <a name="requirements"></a><span data-ttu-id="e3672-135">spécifications</span><span class="sxs-lookup"><span data-stu-id="e3672-135">Requirements</span></span>

<span data-ttu-id="e3672-136">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3672-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="e3672-137">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e3672-137">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="e3672-138">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3672-138">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="e3672-139">**Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3672-139">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e3672-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3672-140">See also</span></span>

- [<span data-ttu-id="e3672-141">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="e3672-141">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
