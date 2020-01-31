---
title: ICorProfilerCallback::Shutdown, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
ms.openlocfilehash: 490f9dd5446a51bd07881cdb9825d737e380a63e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865855"
---
# <a name="icorprofilercallbackshutdown-method"></a><span data-ttu-id="1fc37-102">ICorProfilerCallback::Shutdown, méthode</span><span class="sxs-lookup"><span data-stu-id="1fc37-102">ICorProfilerCallback::Shutdown Method</span></span>
<span data-ttu-id="1fc37-103">Notifie le profileur que l’application est en cours d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="1fc37-103">Notifies the profiler that the application is shutting down.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fc37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fc37-104">Syntax</span></span>  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a><span data-ttu-id="1fc37-105">Notes</span><span class="sxs-lookup"><span data-stu-id="1fc37-105">Remarks</span></span>  
 <span data-ttu-id="1fc37-106">Le code du profileur ne peut pas appeler sans risque les méthodes de l’interface [ICorProfilerInfo](icorprofilerinfo-interface.md) après l’appel de la méthode `Shutdown`.</span><span class="sxs-lookup"><span data-stu-id="1fc37-106">The profiler code cannot safely call methods of the [ICorProfilerInfo](icorprofilerinfo-interface.md) interface after the `Shutdown` method is called.</span></span> <span data-ttu-id="1fc37-107">Tous les appels aux méthodes `ICorProfilerInfo` entraînent un comportement indéfini après le retour de la méthode `Shutdown`.</span><span class="sxs-lookup"><span data-stu-id="1fc37-107">Any calls to `ICorProfilerInfo` methods result in undefined behavior after the `Shutdown` method returns.</span></span> <span data-ttu-id="1fc37-108">Certains événements immuables peuvent encore se produire après l’arrêt ; le profileur doit effectuer un retour immédiatement lorsque cela se produit.</span><span class="sxs-lookup"><span data-stu-id="1fc37-108">Certain immutable events may still occur after shutdown; the profiler should take care to return immediately when this occurs.</span></span>  
  
 <span data-ttu-id="1fc37-109">La méthode `Shutdown` est appelée uniquement si l’application managée en cours de profilage a démarré en tant que code managé (autrement dit, le frame initial sur la pile de processus est managé).</span><span class="sxs-lookup"><span data-stu-id="1fc37-109">The `Shutdown` method will be called only if the managed application that is being profiled started as managed code (that is, the initial frame on the process stack is managed).</span></span> <span data-ttu-id="1fc37-110">Si l’application a démarré en tant que code non managé mais est ensuite basculée dans le code managé, créant ainsi une instance du common language runtime (CLR), `Shutdown` ne sera pas appelé.</span><span class="sxs-lookup"><span data-stu-id="1fc37-110">If the application started as unmanaged code but later jumped into managed code, thereby creating an instance of the common language runtime (CLR), then `Shutdown` will not be called.</span></span> <span data-ttu-id="1fc37-111">Dans ce cas, le profileur doit inclure dans sa bibliothèque une routine de `DllMain` qui utilise la valeur DLL_PROCESS_DETACH pour libérer des ressources et effectuer le traitement du nettoyage de ses données, telles que le vidage des traces sur le disque, etc.</span><span class="sxs-lookup"><span data-stu-id="1fc37-111">For these cases, the profiler should include in its library a `DllMain` routine that uses the DLL_PROCESS_DETACH value to free any resources and perform clean-up processing of its data, such as flushing traces to disk and so on.</span></span>  
  
 <span data-ttu-id="1fc37-112">En général, le profileur doit faire face à des arrêts inattendus.</span><span class="sxs-lookup"><span data-stu-id="1fc37-112">In general, the profiler must cope with unexpected shutdowns.</span></span> <span data-ttu-id="1fc37-113">Par exemple, un processus peut être arrêté par Win32 `TerminateProcess` méthode (déclaré dans Winbase. h).</span><span class="sxs-lookup"><span data-stu-id="1fc37-113">For example, a process might be halted by Win32's `TerminateProcess` method (declared in Winbase.h).</span></span> <span data-ttu-id="1fc37-114">Dans d’autres cas, le CLR arrêtera certains threads managés (threads d’arrière-plan) sans fournir de messages de destruction ordonnés pour eux.</span><span class="sxs-lookup"><span data-stu-id="1fc37-114">In other cases, the CLR will halt certain managed threads (background threads) without delivering orderly destruction messages for them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fc37-115">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="1fc37-115">Requirements</span></span>  
 <span data-ttu-id="1fc37-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fc37-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fc37-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1fc37-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1fc37-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1fc37-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1fc37-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fc37-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fc37-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1fc37-120">See also</span></span>

- [<span data-ttu-id="1fc37-121">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="1fc37-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="1fc37-122">Initialize, méthode</span><span class="sxs-lookup"><span data-stu-id="1fc37-122">Initialize Method</span></span>](icorprofilercallback-initialize-method.md)
