---
title: ICorProfilerInfo3::GetRuntimeInformation, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
ms.openlocfilehash: 20556d85655a0a1bbe069a94b99c19c774a13ce6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449678"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="b15e4-102">ICorProfilerInfo3::GetRuntimeInformation, méthode</span><span class="sxs-lookup"><span data-stu-id="b15e4-102">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>
<span data-ttu-id="b15e4-103">Provides version information about the common language runtime (CLR) that is being profiled.</span><span class="sxs-lookup"><span data-stu-id="b15e4-103">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b15e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b15e4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b15e4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b15e4-105">Parameters</span></span>  
 `pClrInstanceId`  
 <span data-ttu-id="b15e4-106">[out] The representative ID of a running CLR instance in a process.</span><span class="sxs-lookup"><span data-stu-id="b15e4-106">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="b15e4-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span><span class="sxs-lookup"><span data-stu-id="b15e4-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="b15e4-108">[out] The runtime type.</span><span class="sxs-lookup"><span data-stu-id="b15e4-108">[out] The runtime type.</span></span> <span data-ttu-id="b15e4-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span><span class="sxs-lookup"><span data-stu-id="b15e4-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="b15e4-110">[out] The major version number of the CLR.</span><span class="sxs-lookup"><span data-stu-id="b15e4-110">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="b15e4-111">[out] The minor version number of the CLR.</span><span class="sxs-lookup"><span data-stu-id="b15e4-111">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="b15e4-112">[out] The build version number of the CLR.</span><span class="sxs-lookup"><span data-stu-id="b15e4-112">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="b15e4-113">[out] The version number of the CLR that is associated with a software update.</span><span class="sxs-lookup"><span data-stu-id="b15e4-113">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="b15e4-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span><span class="sxs-lookup"><span data-stu-id="b15e4-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="b15e4-115">[out] The length, in characters, of `szVersionString`.</span><span class="sxs-lookup"><span data-stu-id="b15e4-115">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="b15e4-116">[out] The CLR version string.</span><span class="sxs-lookup"><span data-stu-id="b15e4-116">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b15e4-117">Notes</span><span class="sxs-lookup"><span data-stu-id="b15e4-117">Remarks</span></span>  
 <span data-ttu-id="b15e4-118">You may pass null for any parameter.</span><span class="sxs-lookup"><span data-stu-id="b15e4-118">You may pass null for any parameter.</span></span> <span data-ttu-id="b15e4-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span><span class="sxs-lookup"><span data-stu-id="b15e4-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b15e4-120">spécifications</span><span class="sxs-lookup"><span data-stu-id="b15e4-120">Requirements</span></span>  
 <span data-ttu-id="b15e4-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b15e4-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b15e4-122">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b15e4-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b15e4-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b15e4-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b15e4-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b15e4-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b15e4-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b15e4-125">See also</span></span>

- [<span data-ttu-id="b15e4-126">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="b15e4-126">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="b15e4-127">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="b15e4-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="b15e4-128">Profilage</span><span class="sxs-lookup"><span data-stu-id="b15e4-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
