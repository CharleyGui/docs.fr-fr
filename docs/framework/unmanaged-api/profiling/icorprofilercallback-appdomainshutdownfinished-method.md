---
title: ICorProfilerCallback::AppDomainShutdownFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type:
- apiref
ms.openlocfilehash: 8ff7d5a593388bd3a584e031aea411dfdb6c9845
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445197"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="6daa1-102">ICorProfilerCallback::AppDomainShutdownFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="6daa1-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>
<span data-ttu-id="6daa1-103">Notifies the profiler that an application domain has been unloaded from a process.</span><span class="sxs-lookup"><span data-stu-id="6daa1-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6daa1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6daa1-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6daa1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6daa1-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="6daa1-106">[in] Identifies the domain in which the application's assemblies are stored.</span><span class="sxs-lookup"><span data-stu-id="6daa1-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="6daa1-107">[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span><span class="sxs-lookup"><span data-stu-id="6daa1-107">[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6daa1-108">Notes</span><span class="sxs-lookup"><span data-stu-id="6daa1-108">Remarks</span></span>  
 <span data-ttu-id="6daa1-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span><span class="sxs-lookup"><span data-stu-id="6daa1-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="6daa1-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span><span class="sxs-lookup"><span data-stu-id="6daa1-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="6daa1-111">A failure HRESULT in `hrStatus` indicates a failure.</span><span class="sxs-lookup"><span data-stu-id="6daa1-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="6daa1-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span><span class="sxs-lookup"><span data-stu-id="6daa1-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6daa1-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="6daa1-113">Requirements</span></span>  
 <span data-ttu-id="6daa1-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6daa1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6daa1-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6daa1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6daa1-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6daa1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6daa1-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6daa1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6daa1-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6daa1-118">See also</span></span>

- [<span data-ttu-id="6daa1-119">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="6daa1-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
