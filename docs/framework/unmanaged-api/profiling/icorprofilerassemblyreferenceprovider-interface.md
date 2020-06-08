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
ms.openlocfilehash: 17fb3de830d1aed2214631bbe8254a7f58030025
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500518"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="025aa-102">ICorProfilerAssemblyReferenceProvider, interface</span><span class="sxs-lookup"><span data-stu-id="025aa-102">ICorProfilerAssemblyReferenceProvider Interface</span></span>
<span data-ttu-id="025aa-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="025aa-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="025aa-104">Permet au profileur d’informer le common language runtime (CLR) des références d’assembly que le profileur ajoutera dans le rappel de [ICorProfilerCallback :: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="025aa-104">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="025aa-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="025aa-105">Methods</span></span>  
  
|<span data-ttu-id="025aa-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="025aa-106">Method</span></span>|<span data-ttu-id="025aa-107">Description</span><span class="sxs-lookup"><span data-stu-id="025aa-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="025aa-108">AddAssemblyReference, méthode</span><span class="sxs-lookup"><span data-stu-id="025aa-108">AddAssemblyReference Method</span></span>](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="025aa-109">Informe le CLR d’une référence d’assembly que le profileur prévoit d’ajouter dans le rappel [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="025aa-109">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="025aa-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="025aa-110">Remarks</span></span>  
 <span data-ttu-id="025aa-111">Le CLR passe le profileur `ICorProfilerAssemblyReferenceProvider` à un objet d’interface dans le rappel [ICorProfilerCallback6 :: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="025aa-111">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="025aa-112">Cela permet au profileur d’informer le CLR des références d’assembly que le profileur prévoit d’ajouter ultérieurement dans [ICorProfilerCallback :: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="025aa-112">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="025aa-113">rappel.</span><span class="sxs-lookup"><span data-stu-id="025aa-113">callback.</span></span> <span data-ttu-id="025aa-114">Ceci améliore la précision de l'analyseur de fermeture de référence d'assembly du CLR et de ses algorithmes pour déterminer si les assemblys peuvent être partagés.</span><span class="sxs-lookup"><span data-stu-id="025aa-114">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="025aa-115">Cette interface peut être utilisée uniquement dans le rappel [ICorProfilerCallback6 :: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) qui passe cet objet d’interface au profileur.</span><span class="sxs-lookup"><span data-stu-id="025aa-115">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="025aa-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="025aa-116">Requirements</span></span>  
 <span data-ttu-id="025aa-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="025aa-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="025aa-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="025aa-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="025aa-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="025aa-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="025aa-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="025aa-120">See also</span></span>

- [<span data-ttu-id="025aa-121">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="025aa-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
