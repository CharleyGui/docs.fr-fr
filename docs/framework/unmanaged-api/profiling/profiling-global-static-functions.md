---
title: Fonctions statiques globales du profilage
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
ms.openlocfilehash: 20ee2a9e045d839aa8ac043e035c438986b987ef
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860864"
---
# <a name="profiling-global-static-functions"></a><span data-ttu-id="c0c5a-102">Fonctions statiques globales du profilage</span><span class="sxs-lookup"><span data-stu-id="c0c5a-102">Profiling Global Static Functions</span></span>
<span data-ttu-id="c0c5a-103">Cette section décrit les fonctions d’API non managées utilisées par l’API de profilage.</span><span class="sxs-lookup"><span data-stu-id="c0c5a-103">This section describes the unmanaged API functions that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c0c5a-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c0c5a-104">In This Section</span></span>  
  
## <a name="net-framework-version-1-profiling-functions"></a><span data-ttu-id="c0c5a-105">.NET Framework les fonctions de profilage de la version 1</span><span class="sxs-lookup"><span data-stu-id="c0c5a-105">.NET Framework version 1 Profiling Functions</span></span>  
 [<span data-ttu-id="c0c5a-106">FunctionEnter, fonction</span><span class="sxs-lookup"><span data-stu-id="c0c5a-106">FunctionEnter Function</span></span>](functionenter-function.md)  
 <span data-ttu-id="c0c5a-107">Indique au profileur que le contrôle est passé à une fonction.</span><span class="sxs-lookup"><span data-stu-id="c0c5a-107">Notifies the profiler that control is being passed to a function.</span></span> <span data-ttu-id="c0c5a-108">Déconseillé dans le .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="c0c5a-108">Deprecated in the .NET Framework 2.0.</span></span>  
  
 [<span data-ttu-id="c0c5a-109">FunctionLeave, fonction</span><span class="sxs-lookup"><span data-stu-id="c0c5a-109">FunctionLeave Function</span></span>](functionleave-function.md)  
 <span data-ttu-id="c0c5a-110">Notifie le profileur qu’une fonction va retourner à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="c0c5a-110">Notifies the profiler that a function is about to return to the caller.</span></span> <span data-ttu-id="c0c5a-111">Déconseillé dans le .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="c0c5a-111">Deprecated in the .NET Framework 2.0.</span></span>  
  
 [<span data-ttu-id="c0c5a-112">FunctionTailcall, fonction</span><span class="sxs-lookup"><span data-stu-id="c0c5a-112">FunctionTailcall Function</span></span>](functiontailcall-function.md)  
 <span data-ttu-id="c0c5a-113">Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction.</span><span class="sxs-lookup"><span data-stu-id="c0c5a-113">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span> <span data-ttu-id="c0c5a-114">Déconseillé dans le .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="c0c5a-114">Deprecated in the .NET Framework 2.0.</span></span>  
  
## <a name="net-framework-version-2-profiling-functions"></a><span data-ttu-id="c0c5a-115">.NET Framework les fonctions de profilage de la version 2</span><span class="sxs-lookup"><span data-stu-id="c0c5a-115">.NET Framework version 2 Profiling Functions</span></span>  
 [<span data-ttu-id="c0c5a-116">FunctionIDMapper, fonction</span><span class="sxs-lookup"><span data-stu-id="c0c5a-116">FunctionIDMapper Function</span></span>](functionidmapper-function.md)  
 <span data-ttu-id="c0c5a-117">Notifie le profileur que l’identificateur donné d’une fonction peut être remappé à un autre ID à utiliser dans les rappels [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)et [FunctionTailcall2](functiontailcall2-function.md) pour cette fonction.</span><span class="sxs-lookup"><span data-stu-id="c0c5a-117">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="c0c5a-118">Permet également au profileur d’indiquer s’il souhaite recevoir des rappels pour cette fonction</span><span class="sxs-lookup"><span data-stu-id="c0c5a-118">Also enables the profiler to indicate whether it wants to receive callbacks for that function</span></span>  
  
 [<span data-ttu-id="c0c5a-119">FunctionEnter2, fonction</span><span class="sxs-lookup"><span data-stu-id="c0c5a-119">FunctionEnter2 Function</span></span>](functionenter2-function.md)  
 <span data-ttu-id="c0c5a-120">Notifie le profileur que le contrôle est passé à une fonction et fournit des informations sur le frame de pile et les arguments de fonction.</span><span class="sxs-lookup"><span data-stu-id="c0c5a-120">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="c0c5a-121">Déconseillé dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c0c5a-121">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="c0c5a-122">FunctionLeave2, fonction</span><span class="sxs-lookup"><span data-stu-id="c0c5a-122">FunctionLeave2 Function</span></span>](functionleave2-function.md)  
 <span data-ttu-id="c0c5a-123">Notifie le profileur qu’une fonction va retourner à l’appelant et fournit des informations sur le frame de pile et la valeur de retour de fonction.</span><span class="sxs-lookup"><span data-stu-id="c0c5a-123">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span> <span data-ttu-id="c0c5a-124">Déconseillé dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c0c5a-124">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="c0c5a-125">FunctionTailcall2, fonction</span><span class="sxs-lookup"><span data-stu-id="c0c5a-125">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)  
 <span data-ttu-id="c0c5a-126">Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction et fournit des informations sur le frame de pile.</span><span class="sxs-lookup"><span data-stu-id="c0c5a-126">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span> <span data-ttu-id="c0c5a-127">Déconseillé dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c0c5a-127">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="c0c5a-128">StackSnapshotCallback, fonction</span><span class="sxs-lookup"><span data-stu-id="c0c5a-128">StackSnapshotCallback Function</span></span>](stacksnapshotcallback-function.md)  
 <span data-ttu-id="c0c5a-129">Fournit au profileur des informations sur chaque frame managé et chaque série de frames non managés sur la pile pendant un parcours de pile, qui est initié par la méthode [ICorProfilerInfo2 ::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c0c5a-129">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="net-framework-version-4-profiling-functions"></a><span data-ttu-id="c0c5a-130">.NET Framework les fonctions de profilage de la version 4</span><span class="sxs-lookup"><span data-stu-id="c0c5a-130">.NET Framework version 4 Profiling Functions</span></span>  
 [<span data-ttu-id="c0c5a-131">FunctionIDMapper2, fonction</span><span class="sxs-lookup"><span data-stu-id="c0c5a-131">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)  
 <span data-ttu-id="c0c5a-132">Notifie le profileur que l’identificateur donné d’une fonction peut être remappé à un autre ID à utiliser dans les rappels [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)et [FunctionTailcall3](functiontailcall3-function.md), ou[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)et [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) pour cette fonction.</span><span class="sxs-lookup"><span data-stu-id="c0c5a-132">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md), or[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="c0c5a-133">Permet également au profileur d’indiquer s’il souhaite recevoir des rappels pour cette fonction.</span><span class="sxs-lookup"><span data-stu-id="c0c5a-133">Also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
 <span data-ttu-id="c0c5a-134">`FunctionIDMapper2` étend la fonction [FunctionIDMapper](functionidmapper-function.md) avec un paramètre `clientData`, que les profileurs peuvent utiliser pour lever l’ambiguïté entre les runtimes.</span><span class="sxs-lookup"><span data-stu-id="c0c5a-134">`FunctionIDMapper2` extends the [FunctionIDMapper](functionidmapper-function.md) function with a `clientData` parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
 [<span data-ttu-id="c0c5a-135">FunctionEnter3, fonction</span><span class="sxs-lookup"><span data-stu-id="c0c5a-135">FunctionEnter3 Function</span></span>](functionenter3-function.md)  
 <span data-ttu-id="c0c5a-136">Indique au profileur que le contrôle est passé à une fonction.</span><span class="sxs-lookup"><span data-stu-id="c0c5a-136">Notifies the profiler that control is being passed to a function.</span></span>  
  
 [<span data-ttu-id="c0c5a-137">FunctionEnter3WithInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="c0c5a-137">FunctionEnter3WithInfo Function</span></span>](functionenter3withinfo-function.md)  
 <span data-ttu-id="c0c5a-138">Notifie le profileur que le contrôle est passé à une fonction et fournit un handle qui peut être passé à [ICorProfilerInfo3 :: GetFunctionEnter3Info,](icorprofilerinfo3-getfunctionenter3info-method.md) pour récupérer le frame de pile et les arguments de fonction.</span><span class="sxs-lookup"><span data-stu-id="c0c5a-138">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
 [<span data-ttu-id="c0c5a-139">FunctionLeave3, fonction</span><span class="sxs-lookup"><span data-stu-id="c0c5a-139">FunctionLeave3 Function</span></span>](functionleave3-function.md)  
 <span data-ttu-id="c0c5a-140">Indique au profileur que le contrôle est retourné à partir d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="c0c5a-140">Notifies the profiler that control is being returned from a function.</span></span>  
  
 [<span data-ttu-id="c0c5a-141">FunctionLeave3WithInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="c0c5a-141">FunctionLeave3WithInfo Function</span></span>](functionleave3withinfo-function.md)  
 <span data-ttu-id="c0c5a-142">Indique au profileur que le contrôle est retourné à partir d’une fonction et fournit un handle qui peut être passé à [ICorProfilerInfo3 :: GetFunctionLeave3Info,](icorprofilerinfo3-getfunctionleave3info-method.md) pour récupérer le frame de pile et la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="c0c5a-142">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
 [<span data-ttu-id="c0c5a-143">FunctionTailcall3, fonction</span><span class="sxs-lookup"><span data-stu-id="c0c5a-143">FunctionTailcall3 Function</span></span>](functiontailcall3-function.md)  
 <span data-ttu-id="c0c5a-144">Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction.</span><span class="sxs-lookup"><span data-stu-id="c0c5a-144">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
 [<span data-ttu-id="c0c5a-145">FunctionTailcall3WithInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="c0c5a-145">FunctionTailcall3WithInfo Function</span></span>](functiontailcall3withinfo-function.md)  
 <span data-ttu-id="c0c5a-146">Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction et fournit un handle qui peut être passé à [ICorProfilerInfo3 :: GetFunctionTailcall3Info,](icorprofilerinfo3-getfunctiontailcall3info-method.md) pour récupérer le frame de pile.</span><span class="sxs-lookup"><span data-stu-id="c0c5a-146">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionTailcall3Info](icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c0c5a-147">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="c0c5a-147">Related Sections</span></span>  
 [<span data-ttu-id="c0c5a-148">Vue d’ensemble du profilage</span><span class="sxs-lookup"><span data-stu-id="c0c5a-148">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="c0c5a-149">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="c0c5a-149">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="c0c5a-150">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="c0c5a-150">Profiling Enumerations</span></span>](profiling-enumerations.md)  
  
 [<span data-ttu-id="c0c5a-151">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="c0c5a-151">Profiling Structures</span></span>](profiling-structures.md)
