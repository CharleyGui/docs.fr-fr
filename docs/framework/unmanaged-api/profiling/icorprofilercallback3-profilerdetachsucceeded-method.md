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
ms.openlocfilehash: b044c493649b73566a2e70db2e19977a6a7b877d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439449"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a><span data-ttu-id="cdb89-102">ICorProfilerCallback3::ProfilerDetachSucceeded, méthode</span><span class="sxs-lookup"><span data-stu-id="cdb89-102">ICorProfilerCallback3::ProfilerDetachSucceeded Method</span></span>
<span data-ttu-id="cdb89-103">Indique au profileur que le Common Language Runtime (CLR) est sur le point de décharger sa DLL.</span><span class="sxs-lookup"><span data-stu-id="cdb89-103">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdb89-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cdb89-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a><span data-ttu-id="cdb89-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="cdb89-105">Return Value</span></span>  
 <span data-ttu-id="cdb89-106">La valeur de retour de ce rappel est ignorée.</span><span class="sxs-lookup"><span data-stu-id="cdb89-106">The return value from this callback is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cdb89-107">Notes</span><span class="sxs-lookup"><span data-stu-id="cdb89-107">Remarks</span></span>  
 <span data-ttu-id="cdb89-108">Le rappel `ProfilerDetachSucceeded` est émis une fois que tous les threads ont quitté le code du profileur.</span><span class="sxs-lookup"><span data-stu-id="cdb89-108">The `ProfilerDetachSucceeded` callback is issued after all threads have exited the profiler's code.</span></span> <span data-ttu-id="cdb89-109">Quand cette méthode est appelée, le profileur doit effectuer les tâches de dernière minute qui ne sont pas appropriées pour son destructeur, telles que la notification de son interface utilisateur ou l’enregistrement du composant.</span><span class="sxs-lookup"><span data-stu-id="cdb89-109">When this method is called, the profiler should perform any last-minute tasks that are not appropriate for its destructor, such as notifying its UI or logging component.</span></span> <span data-ttu-id="cdb89-110">However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) or `IMetaData*` interfaces).</span><span class="sxs-lookup"><span data-stu-id="cdb89-110">However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) or `IMetaData*` interfaces).</span></span>  
  
 <span data-ttu-id="cdb89-111">Le CLR crée une entrée dans le journal des événements d'application Windows pour indiquer que l'opération de détachement a abouti.</span><span class="sxs-lookup"><span data-stu-id="cdb89-111">The CLR creates an entry in the Windows Application event log to indicate that the detach operation is successful.</span></span>  
  
 <span data-ttu-id="cdb89-112">Quand le profileur retourne de ce rappel, le CLR libère l'objet de profileur et décharge la DLL du profileur.</span><span class="sxs-lookup"><span data-stu-id="cdb89-112">After the profiler returns from this callback, the CLR releases the profiler object and unloads the profiler DLL.</span></span> <span data-ttu-id="cdb89-113">Par conséquent, le profileur ne doit pas exécuter d'actions susceptibles de provoquer l'exécution à l'intérieur de la DLL du profileur après le retour de ce rappel.</span><span class="sxs-lookup"><span data-stu-id="cdb89-113">Therefore, the profiler must not perform any actions that would cause execution to occur inside the profiler DLL after it returns from this callback.</span></span> <span data-ttu-id="cdb89-114">Par exemple, il ne doit pas créer de threads ou enregistrer de rappels de la minuterie.</span><span class="sxs-lookup"><span data-stu-id="cdb89-114">For example, it must not create threads or register timer callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdb89-115">spécifications</span><span class="sxs-lookup"><span data-stu-id="cdb89-115">Requirements</span></span>  
 <span data-ttu-id="cdb89-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdb89-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdb89-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cdb89-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cdb89-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cdb89-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cdb89-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdb89-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdb89-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cdb89-120">See also</span></span>

- [<span data-ttu-id="cdb89-121">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="cdb89-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="cdb89-122">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="cdb89-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="cdb89-123">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="cdb89-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="cdb89-124">Profilage</span><span class="sxs-lookup"><span data-stu-id="cdb89-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
