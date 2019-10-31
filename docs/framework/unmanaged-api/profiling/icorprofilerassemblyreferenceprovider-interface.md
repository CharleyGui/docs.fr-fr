---
title: ICorProfilerAssemblyReferenceProvider, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerAssemblyReferenceProvider
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 17205116-66e1-4acc-8f01-532fb3867028
topic_type:
- apiref
ms.openlocfilehash: f5ba72dca25889fb57c0ae1bb2429e54a8cf2228
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128714"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="2a028-102">ICorProfilerAssemblyReferenceProvider, interface</span><span class="sxs-lookup"><span data-stu-id="2a028-102">ICorProfilerAssemblyReferenceProvider Interface</span></span>
<span data-ttu-id="2a028-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="2a028-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="2a028-104">Permet au profileur d’informer le common language runtime (CLR) des références d’assembly que le profileur ajoutera dans le rappel de [ICorProfilerCallback :: ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2a028-104">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2a028-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="2a028-105">Methods</span></span>  
  
|<span data-ttu-id="2a028-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="2a028-106">Method</span></span>|<span data-ttu-id="2a028-107">Description</span><span class="sxs-lookup"><span data-stu-id="2a028-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2a028-108">AddAssemblyReference, méthode</span><span class="sxs-lookup"><span data-stu-id="2a028-108">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="2a028-109">Informe le CLR d’une référence d’assembly que le profileur prévoit d’ajouter dans le rappel [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2a028-109">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a028-110">Notes</span><span class="sxs-lookup"><span data-stu-id="2a028-110">Remarks</span></span>  
 <span data-ttu-id="2a028-111">Le CLR transmet au profileur un objet d’interface `ICorProfilerAssemblyReferenceProvider` dans le rappel [ICorProfilerCallback6 :: GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2a028-111">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="2a028-112">Cela permet au profileur d’informer le CLR des références d’assembly que le profileur prévoit d’ajouter ultérieurement dans [ICorProfilerCallback :: ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="2a028-112">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="2a028-113">rappel.</span><span class="sxs-lookup"><span data-stu-id="2a028-113">callback.</span></span> <span data-ttu-id="2a028-114">Ceci améliore la précision de l'analyseur de fermeture de référence d'assembly du CLR et de ses algorithmes pour déterminer si les assemblys peuvent être partagés.</span><span class="sxs-lookup"><span data-stu-id="2a028-114">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="2a028-115">Cette interface peut être utilisée uniquement dans le rappel [ICorProfilerCallback6 :: GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) qui passe cet objet d’interface au profileur.</span><span class="sxs-lookup"><span data-stu-id="2a028-115">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a028-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="2a028-116">Requirements</span></span>  
 <span data-ttu-id="2a028-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a028-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a028-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2a028-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2a028-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a028-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a028-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a028-120">See also</span></span>

- [<span data-ttu-id="2a028-121">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="2a028-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
