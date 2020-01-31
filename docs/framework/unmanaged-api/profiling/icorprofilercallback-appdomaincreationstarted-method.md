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
ms.openlocfilehash: 49c3ab4901537805a1ae1be79097c55cc331d29d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866713"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="bb4ba-102">ICorProfilerCallback::AppDomainCreationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="bb4ba-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>
<span data-ttu-id="bb4ba-103">Notifie le profileur qu’un domaine d’application est en cours de création.</span><span class="sxs-lookup"><span data-stu-id="bb4ba-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb4ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb4ba-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb4ba-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="bb4ba-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="bb4ba-106">\[in] identifie le domaine en cours de création.</span><span class="sxs-lookup"><span data-stu-id="bb4ba-106">\[in] Identifies the domain which is being created.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="bb4ba-107">Notes</span><span class="sxs-lookup"><span data-stu-id="bb4ba-107">Remarks</span></span>  
 <span data-ttu-id="bb4ba-108">L’ID n’est pas valide pour toute demande d’informations tant que la méthode [ICorProfilerCallback :: AppDomainCreationFinished](icorprofilercallback-appdomaincreationfinished-method.md) n’est pas appelée.</span><span class="sxs-lookup"><span data-stu-id="bb4ba-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb4ba-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="bb4ba-109">Requirements</span></span>  
 <span data-ttu-id="bb4ba-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb4ba-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb4ba-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bb4ba-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bb4ba-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb4ba-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb4ba-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb4ba-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb4ba-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb4ba-114">See also</span></span>

- [<span data-ttu-id="bb4ba-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="bb4ba-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
