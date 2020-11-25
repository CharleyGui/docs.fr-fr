---
title: Fonctions statiques globales du profilage
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
ms.openlocfilehash: 1b0ad42e6b34e99212e112f6a594b0a36b6715e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723075"
---
# <a name="profiling-global-static-functions"></a><span data-ttu-id="f5fba-102">Fonctions statiques globales du profilage</span><span class="sxs-lookup"><span data-stu-id="f5fba-102">Profiling Global Static Functions</span></span>

<span data-ttu-id="f5fba-103">Cette section décrit les fonctions d’API non managées utilisées par l’API de profilage.</span><span class="sxs-lookup"><span data-stu-id="f5fba-103">This section describes the unmanaged API functions that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f5fba-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f5fba-104">In This Section</span></span>  
  
## <a name="net-framework-version-1-profiling-functions"></a><span data-ttu-id="f5fba-105">.NET Framework les fonctions de profilage de la version 1</span><span class="sxs-lookup"><span data-stu-id="f5fba-105">.NET Framework version 1 Profiling Functions</span></span>  

 [<span data-ttu-id="f5fba-106">FunctionEnter (fonction)</span><span class="sxs-lookup"><span data-stu-id="f5fba-106">FunctionEnter Function</span></span>](functionenter-function.md)  
 <span data-ttu-id="f5fba-107">Indique au profileur que le contrôle est passé à une fonction.</span><span class="sxs-lookup"><span data-stu-id="f5fba-107">Notifies the profiler that control is being passed to a function.</span></span> <span data-ttu-id="f5fba-108">Déconseillé dans le .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="f5fba-108">Deprecated in the .NET Framework 2.0.</span></span>  
  
 [<span data-ttu-id="f5fba-109">FunctionLeave (fonction)</span><span class="sxs-lookup"><span data-stu-id="f5fba-109">FunctionLeave Function</span></span>](functionleave-function.md)  
 <span data-ttu-id="f5fba-110">Notifie le profileur qu’une fonction va retourner à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="f5fba-110">Notifies the profiler that a function is about to return to the caller.</span></span> <span data-ttu-id="f5fba-111">Déconseillé dans le .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="f5fba-111">Deprecated in the .NET Framework 2.0.</span></span>  
  
 [<span data-ttu-id="f5fba-112">FunctionTailcall (fonction)</span><span class="sxs-lookup"><span data-stu-id="f5fba-112">FunctionTailcall Function</span></span>](functiontailcall-function.md)  
 <span data-ttu-id="f5fba-113">Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction.</span><span class="sxs-lookup"><span data-stu-id="f5fba-113">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span> <span data-ttu-id="f5fba-114">Déconseillé dans le .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="f5fba-114">Deprecated in the .NET Framework 2.0.</span></span>  
  
## <a name="net-framework-version-2-profiling-functions"></a><span data-ttu-id="f5fba-115">.NET Framework les fonctions de profilage de la version 2</span><span class="sxs-lookup"><span data-stu-id="f5fba-115">.NET Framework version 2 Profiling Functions</span></span>  

 [<span data-ttu-id="f5fba-116">FunctionIDMapper (fonction)</span><span class="sxs-lookup"><span data-stu-id="f5fba-116">FunctionIDMapper Function</span></span>](functionidmapper-function.md)  
 <span data-ttu-id="f5fba-117">Notifie le profileur que l’identificateur donné d’une fonction peut être remappé à un autre ID à utiliser dans les rappels [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)et [FunctionTailcall2](functiontailcall2-function.md) pour cette fonction.</span><span class="sxs-lookup"><span data-stu-id="f5fba-117">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="f5fba-118">Permet également au profileur d’indiquer s’il souhaite recevoir des rappels pour cette fonction</span><span class="sxs-lookup"><span data-stu-id="f5fba-118">Also enables the profiler to indicate whether it wants to receive callbacks for that function</span></span>  
  
 [<span data-ttu-id="f5fba-119">FunctionEnter2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="f5fba-119">FunctionEnter2 Function</span></span>](functionenter2-function.md)  
 <span data-ttu-id="f5fba-120">Notifie le profileur que le contrôle est passé à une fonction et fournit des informations sur le frame de pile et les arguments de fonction.</span><span class="sxs-lookup"><span data-stu-id="f5fba-120">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="f5fba-121">Déconseillé dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f5fba-121">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="f5fba-122">FunctionLeave2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="f5fba-122">FunctionLeave2 Function</span></span>](functionleave2-function.md)  
 <span data-ttu-id="f5fba-123">Notifie le profileur qu’une fonction va retourner à l’appelant et fournit des informations sur le frame de pile et la valeur de retour de fonction.</span><span class="sxs-lookup"><span data-stu-id="f5fba-123">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span> <span data-ttu-id="f5fba-124">Déconseillé dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f5fba-124">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="f5fba-125">FunctionTailcall2 (fonction)</span><span class="sxs-lookup"><span data-stu-id="f5fba-125">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)  
 <span data-ttu-id="f5fba-126">Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction et fournit des informations sur le frame de pile.</span><span class="sxs-lookup"><span data-stu-id="f5fba-126">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span> <span data-ttu-id="f5fba-127">Déconseillé dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f5fba-127">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="f5fba-128">StackSnapshotCallback (fonction)</span><span class="sxs-lookup"><span data-stu-id="f5fba-128">StackSnapshotCallback Function</span></span>](stacksnapshotcallback-function.md)  
 <span data-ttu-id="f5fba-129">Fournit au profileur des informations sur chaque frame managé et chaque série de frames non managés sur la pile pendant un parcours de pile, qui est initié par la méthode [ICorProfilerInfo2 ::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f5fba-129">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="net-framework-version-4-profiling-functions"></a><span data-ttu-id="f5fba-130">.NET Framework les fonctions de profilage de la version 4</span><span class="sxs-lookup"><span data-stu-id="f5fba-130">.NET Framework version 4 Profiling Functions</span></span>  

 [<span data-ttu-id="f5fba-131">FunctionIDMapper2, fonction</span><span class="sxs-lookup"><span data-stu-id="f5fba-131">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)  
 <span data-ttu-id="f5fba-132">Notifie le profileur que l’identificateur donné d’une fonction peut être remappé à un autre ID à utiliser dans les rappels [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)et [FunctionTailcall3](functiontailcall3-function.md), ou[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)et [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) pour cette fonction.</span><span class="sxs-lookup"><span data-stu-id="f5fba-132">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md), or[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="f5fba-133">Permet également au profileur d’indiquer s’il souhaite recevoir des rappels pour cette fonction.</span><span class="sxs-lookup"><span data-stu-id="f5fba-133">Also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
 <span data-ttu-id="f5fba-134">`FunctionIDMapper2` étend la fonction [FunctionIDMapper](functionidmapper-function.md) avec un `clientData` paramètre, que les profileurs peuvent utiliser pour lever l’ambiguïté entre les runtimes.</span><span class="sxs-lookup"><span data-stu-id="f5fba-134">`FunctionIDMapper2` extends the [FunctionIDMapper](functionidmapper-function.md) function with a `clientData` parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
 [<span data-ttu-id="f5fba-135">FunctionEnter3, fonction</span><span class="sxs-lookup"><span data-stu-id="f5fba-135">FunctionEnter3 Function</span></span>](functionenter3-function.md)  
 <span data-ttu-id="f5fba-136">Indique au profileur que le contrôle est passé à une fonction.</span><span class="sxs-lookup"><span data-stu-id="f5fba-136">Notifies the profiler that control is being passed to a function.</span></span>  
  
 [<span data-ttu-id="f5fba-137">FunctionEnter3WithInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="f5fba-137">FunctionEnter3WithInfo Function</span></span>](functionenter3withinfo-function.md)  
 <span data-ttu-id="f5fba-138">Notifie le profileur que le contrôle est passé à une fonction et fournit un handle qui peut être passé à [ICorProfilerInfo3 :: GetFunctionEnter3Info,](icorprofilerinfo3-getfunctionenter3info-method.md) pour récupérer le frame de pile et les arguments de fonction.</span><span class="sxs-lookup"><span data-stu-id="f5fba-138">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
 [<span data-ttu-id="f5fba-139">FunctionLeave3, fonction</span><span class="sxs-lookup"><span data-stu-id="f5fba-139">FunctionLeave3 Function</span></span>](functionleave3-function.md)  
 <span data-ttu-id="f5fba-140">Indique au profileur que le contrôle est retourné à partir d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="f5fba-140">Notifies the profiler that control is being returned from a function.</span></span>  
  
 [<span data-ttu-id="f5fba-141">FunctionLeave3WithInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="f5fba-141">FunctionLeave3WithInfo Function</span></span>](functionleave3withinfo-function.md)  
 <span data-ttu-id="f5fba-142">Indique au profileur que le contrôle est retourné à partir d’une fonction et fournit un handle qui peut être passé à [ICorProfilerInfo3 :: GetFunctionLeave3Info,](icorprofilerinfo3-getfunctionleave3info-method.md) pour récupérer le frame de pile et la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="f5fba-142">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
 [<span data-ttu-id="f5fba-143">FunctionTailcall3, fonction</span><span class="sxs-lookup"><span data-stu-id="f5fba-143">FunctionTailcall3 Function</span></span>](functiontailcall3-function.md)  
 <span data-ttu-id="f5fba-144">Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction.</span><span class="sxs-lookup"><span data-stu-id="f5fba-144">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
 [<span data-ttu-id="f5fba-145">FunctionTailcall3WithInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="f5fba-145">FunctionTailcall3WithInfo Function</span></span>](functiontailcall3withinfo-function.md)  
 <span data-ttu-id="f5fba-146">Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction et fournit un handle qui peut être passé à [ICorProfilerInfo3 :: GetFunctionTailcall3Info,](icorprofilerinfo3-getfunctiontailcall3info-method.md) pour récupérer le frame de pile.</span><span class="sxs-lookup"><span data-stu-id="f5fba-146">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionTailcall3Info](icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f5fba-147">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="f5fba-147">Related Sections</span></span>  

 [<span data-ttu-id="f5fba-148">Vue d’ensemble du profilage</span><span class="sxs-lookup"><span data-stu-id="f5fba-148">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="f5fba-149">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="f5fba-149">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="f5fba-150">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="f5fba-150">Profiling Enumerations</span></span>](profiling-enumerations.md)  
  
 [<span data-ttu-id="f5fba-151">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="f5fba-151">Profiling Structures</span></span>](profiling-structures.md)
