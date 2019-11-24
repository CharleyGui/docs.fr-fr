---
title: ICorProfilerCallback::AppDomainCreationStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationStarted
helpviewer_keywords:
- AppDomainCreationStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationStarted method [.NET Framework profiling]
ms.assetid: b2a8240b-07fe-4859-bb2b-7d3adbfa0a9f
topic_type:
- apiref
ms.openlocfilehash: 6a0f6dc9d2559bafed416d409063088d2f51c27d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445213"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="079fd-102">ICorProfilerCallback::AppDomainCreationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="079fd-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>
<span data-ttu-id="079fd-103">Notifies the profiler that an application domain is being created.</span><span class="sxs-lookup"><span data-stu-id="079fd-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="079fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="079fd-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="079fd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="079fd-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="079fd-106">[in] Identifies the domain which is being created.</span><span class="sxs-lookup"><span data-stu-id="079fd-106">[in] Identifies the domain which is being created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="079fd-107">Notes</span><span class="sxs-lookup"><span data-stu-id="079fd-107">Remarks</span></span>  
 <span data-ttu-id="079fd-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span><span class="sxs-lookup"><span data-stu-id="079fd-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="079fd-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="079fd-109">Requirements</span></span>  
 <span data-ttu-id="079fd-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="079fd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="079fd-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="079fd-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="079fd-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="079fd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="079fd-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="079fd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="079fd-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="079fd-114">See also</span></span>

- [<span data-ttu-id="079fd-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="079fd-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
