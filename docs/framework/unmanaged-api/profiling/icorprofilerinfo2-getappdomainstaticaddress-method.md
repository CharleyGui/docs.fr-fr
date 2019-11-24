---
title: ICorProfilerInfo2::GetAppDomainStaticAddress, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetAppDomainStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type:
- apiref
ms.openlocfilehash: 12c9b30dc72d1ccf7bfa79ca0745ba3f2c2290c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435877"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="11b19-102">ICorProfilerInfo2::GetAppDomainStaticAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="11b19-102">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>
<span data-ttu-id="11b19-103">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span><span class="sxs-lookup"><span data-stu-id="11b19-103">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11b19-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11b19-104">Syntax</span></span>  
  
```cpp  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11b19-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="11b19-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="11b19-106">[in] The class ID of the class that contains the requested application domain-static field.</span><span class="sxs-lookup"><span data-stu-id="11b19-106">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="11b19-107">[in] The metadata token for the requested application domain-static field.</span><span class="sxs-lookup"><span data-stu-id="11b19-107">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="11b19-108">[in] The ID of the application domain that is the scope for the requested static field.</span><span class="sxs-lookup"><span data-stu-id="11b19-108">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="11b19-109">[out] A pointer to the address of the static field that is within the specified application domain.</span><span class="sxs-lookup"><span data-stu-id="11b19-109">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11b19-110">Notes</span><span class="sxs-lookup"><span data-stu-id="11b19-110">Remarks</span></span>  
 <span data-ttu-id="11b19-111">The `GetAppDomainStaticAddress` method may return one of the following:</span><span class="sxs-lookup"><span data-stu-id="11b19-111">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="11b19-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span><span class="sxs-lookup"><span data-stu-id="11b19-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="11b19-113">The addresses of objects that may be in the garbage collection heap.</span><span class="sxs-lookup"><span data-stu-id="11b19-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="11b19-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span><span class="sxs-lookup"><span data-stu-id="11b19-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="11b19-115">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span><span class="sxs-lookup"><span data-stu-id="11b19-115">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11b19-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="11b19-116">Requirements</span></span>  
 <span data-ttu-id="11b19-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11b19-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11b19-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="11b19-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="11b19-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11b19-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11b19-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11b19-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11b19-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11b19-121">See also</span></span>

- [<span data-ttu-id="11b19-122">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="11b19-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="11b19-123">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="11b19-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
