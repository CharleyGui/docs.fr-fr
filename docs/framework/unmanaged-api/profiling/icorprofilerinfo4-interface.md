---
title: ICorProfilerInfo4, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4
helpviewer_keywords:
- ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type:
- apiref
ms.openlocfilehash: cbd7c0d8fff55766a98e727ce22c77dd5214611b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448007"
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="ac246-102">ICorProfilerInfo4, interface</span><span class="sxs-lookup"><span data-stu-id="ac246-102">ICorProfilerInfo4 Interface</span></span>
<span data-ttu-id="ac246-103">Fournit des méthodes utilisées par les profileurs de code pour communiquer avec le common language runtime (CLR) afin de contrôler la surveillance des événements et les informations de demande.</span><span class="sxs-lookup"><span data-stu-id="ac246-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="ac246-104">.</span><span class="sxs-lookup"><span data-stu-id="ac246-104">.</span></span> <span data-ttu-id="ac246-105">L’interface `ICorProfilerInfo4` est une extension des autres interfaces `ICorProfilerInfo`.</span><span class="sxs-lookup"><span data-stu-id="ac246-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="ac246-106">Il fournit de nouvelles méthodes pour prendre en charge la recompilation juste-à-temps (JIT), ajoutée dans le .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="ac246-106">It provides new methods to support just-in-time (JIT) recompilation, added in the .NET Framework 4.5.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ac246-107">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ac246-107">Methods</span></span>  
  
|<span data-ttu-id="ac246-108">Méthode</span><span class="sxs-lookup"><span data-stu-id="ac246-108">Method</span></span>|<span data-ttu-id="ac246-109">Description</span><span class="sxs-lookup"><span data-stu-id="ac246-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ac246-110">EnumJITedFunctions2, méthode</span><span class="sxs-lookup"><span data-stu-id="ac246-110">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="ac246-111">Retourne un énumérateur pour toutes les fonctions qui ont été précédemment compilées juste-à-temps et qui ont été recompilées juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="ac246-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="ac246-112">EnumThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="ac246-112">EnumThreads Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="ac246-113">Obtient un énumérateur qui fournit des méthodes pour itérer séquentiellement au sein de la collection de tous les threads managés dans le processus profilé.</span><span class="sxs-lookup"><span data-stu-id="ac246-113">Gets an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="ac246-114">GetCodeInfo3, méthode</span><span class="sxs-lookup"><span data-stu-id="ac246-114">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="ac246-115">Obtient les étendues de code natif associées à la version recompilée juste-à-temps de la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ac246-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="ac246-116">GetFunctionFromIP2, méthode</span><span class="sxs-lookup"><span data-stu-id="ac246-116">GetFunctionFromIP2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="ac246-117">Mappe un pointeur d’instruction de code managé à la version recompilée juste-à-temps d’une fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ac246-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="ac246-118">GetILToNativeMapping2, méthode</span><span class="sxs-lookup"><span data-stu-id="ac246-118">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="ac246-119">Obtient un mappage des offsets MSIL (Microsoft Intermediate Language) aux offsets natifs pour le code contenu dans la version recompilée juste-à-temps de la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ac246-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="ac246-120">GetObjectSize2, méthode</span><span class="sxs-lookup"><span data-stu-id="ac246-120">GetObjectSize2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="ac246-121">Retourne la taille d’un objet spécifié.</span><span class="sxs-lookup"><span data-stu-id="ac246-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="ac246-122">GetReJITIDs, méthode</span><span class="sxs-lookup"><span data-stu-id="ac246-122">GetReJITIDs Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="ac246-123">Retourne un tableau d’ID identifiant toutes les versions recompilées juste-à-temps de la fonction spécifiée qui sont toujours allouées.</span><span class="sxs-lookup"><span data-stu-id="ac246-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="ac246-124">InitializeCurrentThread, méthode</span><span class="sxs-lookup"><span data-stu-id="ac246-124">InitializeCurrentThread Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="ac246-125">Initialise le thread actuel avant les appels d’API du profileur suivants sur le même thread, afin que l’interblocage puisse être évité.</span><span class="sxs-lookup"><span data-stu-id="ac246-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="ac246-126">RequestReJIT, méthode</span><span class="sxs-lookup"><span data-stu-id="ac246-126">RequestReJIT Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="ac246-127">Demande une recompilation juste-à-temps de toutes les instances des fonctions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="ac246-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="ac246-128">RequestRevert, méthode</span><span class="sxs-lookup"><span data-stu-id="ac246-128">RequestRevert Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="ac246-129">Rétablit les versions d'origine de toutes les instances des fonctions spécifiées.</span><span class="sxs-lookup"><span data-stu-id="ac246-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac246-130">Notes</span><span class="sxs-lookup"><span data-stu-id="ac246-130">Remarks</span></span>  
 <span data-ttu-id="ac246-131">Le CLR implémente les méthodes de l'interface `ICorProfilerInfo4` à l'aide du modèle libre de threads.</span><span class="sxs-lookup"><span data-stu-id="ac246-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="ac246-132">Chaque méthode retourne un HRESULT pour indiquer la réussite ou l'échec.</span><span class="sxs-lookup"><span data-stu-id="ac246-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="ac246-133">Pour obtenir la liste des codes de retour possibles, consultez le fichier CorError.h.</span><span class="sxs-lookup"><span data-stu-id="ac246-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac246-134">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ac246-134">Requirements</span></span>  
 <span data-ttu-id="ac246-135">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac246-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac246-136">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ac246-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ac246-137">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac246-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac246-138">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac246-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac246-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac246-139">See also</span></span>

- [<span data-ttu-id="ac246-140">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="ac246-140">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="ac246-141">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="ac246-141">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
