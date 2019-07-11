---
title: ICorProfilerCallback3::ProfilerDetachSucceeded, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerDetachSucceeded Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerDetachSucceeded
helpviewer_keywords:
- ProfilerDetachSucceeded method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerDetachSucceeded method [.NET Framework profiling]
ms.assetid: 05164966-16ce-4cc9-a530-43a640c00711
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8cff277179be761bb0dc78b02702e7d35ad4b6a9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779252"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a><span data-ttu-id="09299-102">ICorProfilerCallback3::ProfilerDetachSucceeded, méthode</span><span class="sxs-lookup"><span data-stu-id="09299-102">ICorProfilerCallback3::ProfilerDetachSucceeded Method</span></span>
<span data-ttu-id="09299-103">Indique au profileur que le Common Language Runtime (CLR) est sur le point de décharger sa DLL.</span><span class="sxs-lookup"><span data-stu-id="09299-103">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09299-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09299-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a><span data-ttu-id="09299-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="09299-105">Return Value</span></span>  
 <span data-ttu-id="09299-106">La valeur de retour de ce rappel est ignorée.</span><span class="sxs-lookup"><span data-stu-id="09299-106">The return value from this callback is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09299-107">Notes</span><span class="sxs-lookup"><span data-stu-id="09299-107">Remarks</span></span>  
 <span data-ttu-id="09299-108">Le rappel `ProfilerDetachSucceeded` est émis une fois que tous les threads ont quitté le code du profileur.</span><span class="sxs-lookup"><span data-stu-id="09299-108">The `ProfilerDetachSucceeded` callback is issued after all threads have exited the profiler's code.</span></span> <span data-ttu-id="09299-109">Quand cette méthode est appelée, le profileur doit effectuer les tâches de dernière minute qui ne sont pas appropriées pour son destructeur, telles que la notification de son interface utilisateur ou l’enregistrement du composant.</span><span class="sxs-lookup"><span data-stu-id="09299-109">When this method is called, the profiler should perform any last-minute tasks that are not appropriate for its destructor, such as notifying its UI or logging component.</span></span> <span data-ttu-id="09299-110">Toutefois, le profileur ne doit pas appeler de fonctions sur les interfaces qui sont fournies par le CLR pendant ce rappel (telles que la [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) ou `IMetaData*` interfaces).</span><span class="sxs-lookup"><span data-stu-id="09299-110">However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) or `IMetaData*` interfaces).</span></span>  
  
 <span data-ttu-id="09299-111">Le CLR crée une entrée dans le journal des événements d'application Windows pour indiquer que l'opération de détachement a abouti.</span><span class="sxs-lookup"><span data-stu-id="09299-111">The CLR creates an entry in the Windows Application event log to indicate that the detach operation is successful.</span></span>  
  
 <span data-ttu-id="09299-112">Quand le profileur retourne de ce rappel, le CLR libère l'objet de profileur et décharge la DLL du profileur.</span><span class="sxs-lookup"><span data-stu-id="09299-112">After the profiler returns from this callback, the CLR releases the profiler object and unloads the profiler DLL.</span></span> <span data-ttu-id="09299-113">Par conséquent, le profileur ne doit pas exécuter d'actions susceptibles de provoquer l'exécution à l'intérieur de la DLL du profileur après le retour de ce rappel.</span><span class="sxs-lookup"><span data-stu-id="09299-113">Therefore, the profiler must not perform any actions that would cause execution to occur inside the profiler DLL after it returns from this callback.</span></span> <span data-ttu-id="09299-114">Par exemple, il ne doit pas créer de threads ou enregistrer de rappels de la minuterie.</span><span class="sxs-lookup"><span data-stu-id="09299-114">For example, it must not create threads or register timer callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09299-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="09299-115">Requirements</span></span>  
 <span data-ttu-id="09299-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09299-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09299-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="09299-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="09299-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09299-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09299-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09299-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09299-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09299-120">See also</span></span>

- [<span data-ttu-id="09299-121">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="09299-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="09299-122">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="09299-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="09299-123">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="09299-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="09299-124">Profilage</span><span class="sxs-lookup"><span data-stu-id="09299-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
