---
title: ICorProfilerInfo2::GetThreadAppDomain, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadAppDomain
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadAppDomain
helpviewer_keywords:
- ICorProfilerInfo2::GetThreadAppDomain method [.NET Framework profiling]
- GetThreadAppDomain method [.NET Framework profiling]
ms.assetid: 4a11b264-8540-4732-aa35-bc2d95b95b8e
topic_type:
- apiref
ms.openlocfilehash: 8637be3c0a59676dc52aea985d7418bfd8f247bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443105"
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a><span data-ttu-id="28925-102">ICorProfilerInfo2::GetThreadAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="28925-102">ICorProfilerInfo2::GetThreadAppDomain Method</span></span>
<span data-ttu-id="28925-103">Gets the ID of the application domain in which the specified thread is currently executing code.</span><span class="sxs-lookup"><span data-stu-id="28925-103">Gets the ID of the application domain in which the specified thread is currently executing code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28925-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28925-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28925-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="28925-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="28925-106">[in] The ID specifying the thread.</span><span class="sxs-lookup"><span data-stu-id="28925-106">[in] The ID specifying the thread.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="28925-107">[out] A pointer to the ID of the application domain.</span><span class="sxs-lookup"><span data-stu-id="28925-107">[out] A pointer to the ID of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28925-108">spécifications</span><span class="sxs-lookup"><span data-stu-id="28925-108">Requirements</span></span>  
 <span data-ttu-id="28925-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28925-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28925-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="28925-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="28925-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28925-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28925-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28925-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28925-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28925-113">See also</span></span>

- [<span data-ttu-id="28925-114">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="28925-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="28925-115">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="28925-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
