---
title: ICorProfilerInfo2::GetStringLayout, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStringLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type:
- apiref
ms.openlocfilehash: 71e2bc1d60e050d817429db5bc6926b3b16c637c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431407"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="6d1a2-102">ICorProfilerInfo2::GetStringLayout, méthode</span><span class="sxs-lookup"><span data-stu-id="6d1a2-102">ICorProfilerInfo2::GetStringLayout Method</span></span>
<span data-ttu-id="6d1a2-103">Obtient des informations sur la disposition d'un objet string.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="6d1a2-104">This method is deprecated in the .NET Framework 4, and is superseded by the [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-104">This method is deprecated in the .NET Framework 4, and is superseded by the [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d1a2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d1a2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d1a2-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6d1a2-106">Parameters</span></span>  
 `pBufferLengthOffset`  
 <span data-ttu-id="6d1a2-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="6d1a2-108">The length is stored as a `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6d1a2-109">This parameter returns the length of the string itself, not the length of the buffer.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="6d1a2-110">The length of the buffer is no longer available.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="6d1a2-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="6d1a2-112">The length is stored as a `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="6d1a2-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d1a2-114">Notes</span><span class="sxs-lookup"><span data-stu-id="6d1a2-114">Remarks</span></span>  
 <span data-ttu-id="6d1a2-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span><span class="sxs-lookup"><span data-stu-id="6d1a2-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
- <span data-ttu-id="6d1a2-116">The length of the string's buffer.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-116">The length of the string's buffer.</span></span>  
  
- <span data-ttu-id="6d1a2-117">The length of the string itself.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-117">The length of the string itself.</span></span>  
  
- <span data-ttu-id="6d1a2-118">The buffer that contains the actual string of wide characters.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="6d1a2-119">Strings may be null-terminated.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d1a2-120">spécifications</span><span class="sxs-lookup"><span data-stu-id="6d1a2-120">Requirements</span></span>  
 <span data-ttu-id="6d1a2-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d1a2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d1a2-122">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6d1a2-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6d1a2-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d1a2-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d1a2-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d1a2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d1a2-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d1a2-125">See also</span></span>

- [<span data-ttu-id="6d1a2-126">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="6d1a2-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="6d1a2-127">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="6d1a2-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
