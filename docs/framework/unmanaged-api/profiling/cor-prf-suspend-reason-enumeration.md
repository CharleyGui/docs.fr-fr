---
title: COR_PRF_SUSPEND_REASON, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_SUSPEND_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SUSPEND_REASON
helpviewer_keywords:
- COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type:
- apiref
ms.openlocfilehash: d2d9ca77e764fe439753f1174a42af5ef80faa59
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447709"
---
# <a name="cor_prf_suspend_reason-enumeration"></a><span data-ttu-id="17e34-102">COR_PRF_SUSPEND_REASON, énumération</span><span class="sxs-lookup"><span data-stu-id="17e34-102">COR_PRF_SUSPEND_REASON Enumeration</span></span>
<span data-ttu-id="17e34-103">Indique la raison pour laquelle le runtime est suspendu.</span><span class="sxs-lookup"><span data-stu-id="17e34-103">Indicates the reason that the runtime is suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17e34-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17e34-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_SUSPEND_OTHER                   = 0x00,  
    COR_PRF_SUSPEND_FOR_GC                  = 0x01,  
    COR_PRF_SUSPEND_FOR_APPDOMAIN_SHUTDOWN  = 0x02,  
    COR_PRF_SUSPEND_FOR_CODE_PITCHING       = 0x03,  
    COR_PRF_SUSPEND_FOR_SHUTDOWN            = 0x04,  
    COR_PRF_SUSPEND_FOR_INPROC_DEBUGGER     = 0x06,  
    COR_PRF_SUSPEND_FOR_GC_PREP             = 0x07,    COR_PRF_SUSPEND_FOR_REJIT               = 8  
} COR_PRF_SUSPEND_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="17e34-105">Membres</span><span class="sxs-lookup"><span data-stu-id="17e34-105">Members</span></span>  
  
|<span data-ttu-id="17e34-106">Membre</span><span class="sxs-lookup"><span data-stu-id="17e34-106">Member</span></span>|<span data-ttu-id="17e34-107">Description</span><span class="sxs-lookup"><span data-stu-id="17e34-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|<span data-ttu-id="17e34-108">Le runtime est suspendu pour une raison non spécifiée.</span><span class="sxs-lookup"><span data-stu-id="17e34-108">The runtime is suspended for an unspecified reason.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|<span data-ttu-id="17e34-109">Le runtime est suspendu pour traiter une demande de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="17e34-109">The runtime is suspended to service a garbage collection request.</span></span><br /><br /> <span data-ttu-id="17e34-110">Les rappels liés à garbage collection se produisent entre les rappels [ICorProfilerCallback :: RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) et [ICorProfilerCallback :: RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="17e34-110">The garbage collection-related callbacks occur between the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|<span data-ttu-id="17e34-111">Le runtime est interrompu afin qu’un `AppDomain` puisse être arrêté.</span><span class="sxs-lookup"><span data-stu-id="17e34-111">The runtime is suspended so that an `AppDomain` can be shut down.</span></span><br /><br /> <span data-ttu-id="17e34-112">Pendant que le runtime est suspendu, le runtime détermine les threads qui se trouvent dans le `AppDomain` en cours d’arrêt et les affecte à la valeur Abort lorsqu’ils reprennent.</span><span class="sxs-lookup"><span data-stu-id="17e34-112">While the runtime is suspended, the runtime will determine which threads are in the `AppDomain` that is being shut down and set them to abort when they resume.</span></span> <span data-ttu-id="17e34-113">Il n’y a pas de rappels spécifiques à `AppDomain`pendant cette interruption.</span><span class="sxs-lookup"><span data-stu-id="17e34-113">There are no `AppDomain`-specific callbacks during this suspension.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|<span data-ttu-id="17e34-114">Le runtime est interrompu afin que la présentation du code puisse se produire.</span><span class="sxs-lookup"><span data-stu-id="17e34-114">The runtime is suspended so that code pitching can occur.</span></span><br /><br /> <span data-ttu-id="17e34-115">La mise à l’échelle du code se présente uniquement lorsque le compilateur juste-à-temps (JIT) est actif avec la mise à l’échelle du code activée.</span><span class="sxs-lookup"><span data-stu-id="17e34-115">Code pitching ensues only when the just-in-time (JIT) compiler is active with code pitching enabled.</span></span> <span data-ttu-id="17e34-116">Les rappels de présentation de code se produisent entre le `ICorProfilerCallback::RuntimeSuspendFinished` et les rappels de `ICorProfilerCallback::RuntimeResumeStarted`.</span><span class="sxs-lookup"><span data-stu-id="17e34-116">Code pitching callbacks occur between the `ICorProfilerCallback::RuntimeSuspendFinished` and `ICorProfilerCallback::RuntimeResumeStarted` callbacks.</span></span> <span data-ttu-id="17e34-117">**Remarque :**  Le JIT CLR ne met pas en valeur les fonctions dans la version 2,0 de .NET Framework, donc cette valeur n’est pas utilisée dans 2,0.</span><span class="sxs-lookup"><span data-stu-id="17e34-117">**Note:**  The CLR JIT does not pitch functions in the .NET Framework version 2.0, so this value is not used in 2.0.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|<span data-ttu-id="17e34-118">Le runtime est suspendu pour pouvoir être arrêté.</span><span class="sxs-lookup"><span data-stu-id="17e34-118">The runtime is suspended so that it can shut down.</span></span> <span data-ttu-id="17e34-119">Il doit suspendre tous les threads pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="17e34-119">It must suspend all threads to complete the operation.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|<span data-ttu-id="17e34-120">Le runtime est suspendu pour le débogage en cours de processus.</span><span class="sxs-lookup"><span data-stu-id="17e34-120">The runtime is suspended for in-process debugging.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|<span data-ttu-id="17e34-121">Le runtime est suspendu pour préparer un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="17e34-121">The runtime is suspended to prepare for a garbage collection.</span></span>|  
|`COR_PRF_SUSPEND_FOR_REJIT`|<span data-ttu-id="17e34-122">Le runtime est suspendu pour la recompilation JIT.</span><span class="sxs-lookup"><span data-stu-id="17e34-122">The runtime is suspended for JIT recompilation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17e34-123">Notes</span><span class="sxs-lookup"><span data-stu-id="17e34-123">Remarks</span></span>  
 <span data-ttu-id="17e34-124">Tous les threads d’exécution qui se trouvent dans du code non managé sont autorisés à continuer à s’exécuter jusqu’à ce qu’ils essaient d’entrer à nouveau le Runtime. à partir de là, ils sont également suspendus jusqu’à la reprise du Runtime.</span><span class="sxs-lookup"><span data-stu-id="17e34-124">All runtime threads that are in unmanaged code are permitted to continue running until they try to re-enter the runtime, at which point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="17e34-125">Cela s’applique également aux nouveaux threads qui entrent dans le Runtime.</span><span class="sxs-lookup"><span data-stu-id="17e34-125">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="17e34-126">Tous les threads au sein du runtime sont suspendus immédiatement s’ils sont dans le code interruptible, ou ils sont invités à s’interrompre lorsqu’ils atteignent du code interruptible.</span><span class="sxs-lookup"><span data-stu-id="17e34-126">All threads within the runtime are either suspended immediately if they are in interruptible code, or asked to suspend when they do reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17e34-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="17e34-127">Requirements</span></span>  
 <span data-ttu-id="17e34-128">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17e34-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17e34-129">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="17e34-129">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="17e34-130">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17e34-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17e34-131">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17e34-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17e34-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17e34-132">See also</span></span>

- [<span data-ttu-id="17e34-133">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="17e34-133">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
