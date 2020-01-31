---
title: Interfaces de profilage
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
ms.openlocfilehash: 8b6b9acff2945e2d8fd684bfa31e4af086ea5ab9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868146"
---
# <a name="profiling-interfaces"></a><span data-ttu-id="66861-102">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="66861-102">Profiling Interfaces</span></span>
<span data-ttu-id="66861-103">Cette section décrit les interfaces non managées qui vous permettent de profiler un programme exécuté par le CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="66861-103">This section describes the unmanaged interfaces that enable you to profile a program that is being executed by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="66861-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="66861-104">In This Section</span></span>  
 [<span data-ttu-id="66861-105">ICLRProfiling, interface</span><span class="sxs-lookup"><span data-stu-id="66861-105">ICLRProfiling Interface</span></span>](iclrprofiling-interface.md)  
 <span data-ttu-id="66861-106">Fournit la méthode [AttachProfiler](iclrprofiling-attachprofiler-method.md) , qui permet à un profileur de s’attacher à un processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="66861-106">Provides the [AttachProfiler](iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
 [<span data-ttu-id="66861-107">ICorProfilerAssemblyReferenceProvider, interface</span><span class="sxs-lookup"><span data-stu-id="66861-107">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)  
 <span data-ttu-id="66861-108">Permet au profileur d’informer le CLR des références d’assembly que le profileur ajoutera dans le rappel de [ICorProfilerCallback :: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="66861-108">Enables the profiler to inform the CLR of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
 [<span data-ttu-id="66861-109">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="66861-109">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)  
 <span data-ttu-id="66861-110">Fournit des méthodes qui sont utilisées par le CLR pour envoyer des notifications à un profileur de code quand les événements auxquels le profileur s'est abonné se produisent.</span><span class="sxs-lookup"><span data-stu-id="66861-110">Provides methods that are used by the CLR to notify a code profiler when the events to which the profiler has subscribed occur.</span></span>  
  
 [<span data-ttu-id="66861-111">ICorProfilerCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="66861-111">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)  
 <span data-ttu-id="66861-112">Étend l'interface `ICorProfilerCallback` avec des rappels pris en charge dans .NET Framework 2.0 et ultérieur.</span><span class="sxs-lookup"><span data-stu-id="66861-112">Extends the `ICorProfilerCallback` interface with callbacks supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="66861-113">ICorProfilerCallback3, interface</span><span class="sxs-lookup"><span data-stu-id="66861-113">ICorProfilerCallback3 Interface</span></span>](icorprofilercallback3-interface.md)  
 <span data-ttu-id="66861-114">Fournit des méthodes de rappel que le CLR utilise pour communiquer au profileur des informations d'état d'attachement et de détachement.</span><span class="sxs-lookup"><span data-stu-id="66861-114">Provides callback methods that the CLR uses to communicate attach and detach state information to the profiler.</span></span>  
  
 [<span data-ttu-id="66861-115">ICorProfilerCallback4, interface</span><span class="sxs-lookup"><span data-stu-id="66861-115">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)  
 <span data-ttu-id="66861-116">Fournit des méthodes de rappel que le CLR utilise pour communiquer des informations au profileur.</span><span class="sxs-lookup"><span data-stu-id="66861-116">Provides callback methods that the CLR uses to communicate information to the profiler.</span></span>  
  
 [<span data-ttu-id="66861-117">ICorProfilerCallback5, interface</span><span class="sxs-lookup"><span data-stu-id="66861-117">ICorProfilerCallback5 Interface</span></span>](icorprofilercallback5-interface.md)  
 <span data-ttu-id="66861-118">Fournit une méthode qui identifie la fermeture transitive d’objets référencés par des racines de récupération de mémoire.</span><span class="sxs-lookup"><span data-stu-id="66861-118">Provides a method that identifies the transitive closure of objects referenced by garbage collection roots.</span></span>  
  
 [<span data-ttu-id="66861-119">ICorProfilerCallback6, interface</span><span class="sxs-lookup"><span data-stu-id="66861-119">ICorProfilerCallback6 Interface</span></span>](icorprofilercallback6-interface.md)  
 <span data-ttu-id="66861-120">Fournit une méthode de rappel utilisée par le CLR pour envoyer une notification à un profileur quand un assembly est en cours de chargement.</span><span class="sxs-lookup"><span data-stu-id="66861-120">Provides a callback method that the CLR uses to notify a profiler that an assembly is loading.</span></span>  
  
 [<span data-ttu-id="66861-121">ICorProfilerCallback7, interface</span><span class="sxs-lookup"><span data-stu-id="66861-121">ICorProfilerCallback7 Interface</span></span>](icorprofilercallback7-interface.md)  
 <span data-ttu-id="66861-122">Fournit une méthode de rappel que le common language runtime utilise pour informer le profileur que le flux de symboles associé à un module en mémoire est mis à jour.</span><span class="sxs-lookup"><span data-stu-id="66861-122">Provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  

[<span data-ttu-id="66861-123">ICorProfilerCallback8, interface</span><span class="sxs-lookup"><span data-stu-id="66861-123">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)  
<span data-ttu-id="66861-124">Fournit des méthodes de rappel que le common language runtime utilise pour informer le profileur que la compilation JIT d’une méthode dynamique a démarré et se termine.</span><span class="sxs-lookup"><span data-stu-id="66861-124">Provides callback methods that the common language runtime uses to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>

[<span data-ttu-id="66861-125">ICorProfilerCallback9, interface</span><span class="sxs-lookup"><span data-stu-id="66861-125">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)  
<span data-ttu-id="66861-126">Fournit une méthode de rappel que le common language runtime utilise pour informer le profileur qu’une méthode dynamique est récupérée par le garbage collector et déchargée par la suite.</span><span class="sxs-lookup"><span data-stu-id="66861-126">Provides a callback method that the common language runtime uses to notify the profiler that a dynamic method is garbage collected and subsequently unloaded.</span></span>

 [<span data-ttu-id="66861-127">ICorProfilerFunctionControl, interface</span><span class="sxs-lookup"><span data-stu-id="66861-127">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)  
 <span data-ttu-id="66861-128">Fournit des méthodes qui permettent à un profileur de code de communiquer avec le CLR (Common Language Runtime) pour contrôler comment le compilateur juste-à-temps doit générer du code lors de la recompilation d'une méthode spécifique.</span><span class="sxs-lookup"><span data-stu-id="66861-128">Provides methods that allow a code profiler to communicate with the CLR to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
 [<span data-ttu-id="66861-129">ICorProfilerFunctionEnum, interface</span><span class="sxs-lookup"><span data-stu-id="66861-129">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)  
 <span data-ttu-id="66861-130">Fournit des méthodes pour boucler séquentiellement dans une collection de fonctions dans le CLR.</span><span class="sxs-lookup"><span data-stu-id="66861-130">Provides methods to sequentially iterate through a collection of functions in the CLR.</span></span>  
  
 [<span data-ttu-id="66861-131">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="66861-131">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)  
 <span data-ttu-id="66861-132">Fournit des méthodes utilisées par les profileurs de code pour communiquer avec le CLR pour contrôler la surveillance des événements et demander des informations.</span><span class="sxs-lookup"><span data-stu-id="66861-132">Provides methods for use by code profilers to communicate with the CLR to control event monitoring and request information.</span></span>  
  
 [<span data-ttu-id="66861-133">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="66861-133">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)  
 <span data-ttu-id="66861-134">Étend l'interface `ICorProfilerInfo` avec des méthodes prises en charge dans .NET Framework 2.0 et ultérieur.</span><span class="sxs-lookup"><span data-stu-id="66861-134">Extends the `ICorProfilerInfo` interface with methods supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="66861-135">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="66861-135">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)  
 <span data-ttu-id="66861-136">Étend l’interface `ICorProfilerInfo2` avec les méthodes prises en charge dans le .NET Framework 4 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="66861-136">Extends the `ICorProfilerInfo2` interface with methods supported in the .NET Framework 4 and later versions.</span></span>  
  
 [<span data-ttu-id="66861-137">ICorProfilerInfo4, interface</span><span class="sxs-lookup"><span data-stu-id="66861-137">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)  
 <span data-ttu-id="66861-138">Fournit des méthodes utilisées par les profileurs de code pour communiquer avec le CLR pour contrôler la surveillance des événements et demander des informations.</span><span class="sxs-lookup"><span data-stu-id="66861-138">Provides methods that code profilers use to communicate with the CLR to control event monitoring and to request information.</span></span>  
  
 [<span data-ttu-id="66861-139">ICorProfilerInfo5, interface</span><span class="sxs-lookup"><span data-stu-id="66861-139">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)  
 <span data-ttu-id="66861-140">Fournit des méthodes utilisées par les profileurs de code pour communiquer avec le CLR pour contrôler la surveillance des événements.</span><span class="sxs-lookup"><span data-stu-id="66861-140">Provides methods for use by code profilers to communicate with the CLR to control event monitoring.</span></span>  
  
 [<span data-ttu-id="66861-141">ICorProfilerInfo6, interface</span><span class="sxs-lookup"><span data-stu-id="66861-141">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)  
 <span data-ttu-id="66861-142">Fournit un énumérateur à toutes les méthodes qui appartiennent à un module NGen donné et qui sont inline dans le corps d’une méthode donnée.</span><span class="sxs-lookup"><span data-stu-id="66861-142">Provides an enumerator to all the methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>  
  
 [<span data-ttu-id="66861-143">ICorProfilerInfo7, interface</span><span class="sxs-lookup"><span data-stu-id="66861-143">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)  
 <span data-ttu-id="66861-144">Fournit une méthode pour appliquer des métadonnées nouvellement définies à un module et qui fournit l’accès à un flux de symboles en mémoire.</span><span class="sxs-lookup"><span data-stu-id="66861-144">Provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
 [<span data-ttu-id="66861-145">ICorProfilerModuleEnum, interface</span><span class="sxs-lookup"><span data-stu-id="66861-145">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)  
 <span data-ttu-id="66861-146">Fournit des méthodes pour boucler séquentiellement dans une collection de modules chargés par l’application ou par le profileur.</span><span class="sxs-lookup"><span data-stu-id="66861-146">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
 [<span data-ttu-id="66861-147">ICorProfilerObjectEnum, interface</span><span class="sxs-lookup"><span data-stu-id="66861-147">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)  
 <span data-ttu-id="66861-148">Fournit des méthodes pour itérer séquentiellement au sein d’une collection d’objets figés qui sont générés par [Ngen. exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="66861-148">Provides methods to sequentially iterate through a collection of frozen objects that are generated by [Ngen.exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>  
  
 [<span data-ttu-id="66861-149">ICorProfilerThreadEnum, interface</span><span class="sxs-lookup"><span data-stu-id="66861-149">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)  
 <span data-ttu-id="66861-150">Fournit des méthodes pour boucler séquentiellement dans une collection de threads dans le CLR.</span><span class="sxs-lookup"><span data-stu-id="66861-150">Provides methods to sequentially iterate through a collection of threads in the CLR.</span></span>  
  
 [<span data-ttu-id="66861-151">IMethodMalloc, interface</span><span class="sxs-lookup"><span data-stu-id="66861-151">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)  
 <span data-ttu-id="66861-152">Fournit la méthode [Alloc](imethodmalloc-alloc-method.md) pour allouer de la mémoire pour un nouveau corps de fonction MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="66861-152">Provides the [Alloc](imethodmalloc-alloc-method.md) method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="66861-153">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="66861-153">Related Sections</span></span>  
 [<span data-ttu-id="66861-154">Vue d’ensemble du profilage</span><span class="sxs-lookup"><span data-stu-id="66861-154">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="66861-155">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="66861-155">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="66861-156">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="66861-156">Profiling Enumerations</span></span>](profiling-enumerations.md)  
  
 [<span data-ttu-id="66861-157">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="66861-157">Profiling Structures</span></span>](profiling-structures.md)
