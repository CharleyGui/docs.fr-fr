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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d63dd911a5f674a3ce0b02ec78de443c7aebf84
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747171"
---
# <a name="icorprofilercallbackshutdown-method"></a><span data-ttu-id="82f7a-102">ICorProfilerCallback::Shutdown, méthode</span><span class="sxs-lookup"><span data-stu-id="82f7a-102">ICorProfilerCallback::Shutdown Method</span></span>
<span data-ttu-id="82f7a-103">Notifie le profileur que l’application est en cours d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="82f7a-103">Notifies the profiler that the application is shutting down.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82f7a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82f7a-104">Syntax</span></span>  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a><span data-ttu-id="82f7a-105">Notes</span><span class="sxs-lookup"><span data-stu-id="82f7a-105">Remarks</span></span>  
 <span data-ttu-id="82f7a-106">Le code du profileur ne peut pas appeler en toute sécurité les méthodes de la [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface après le `Shutdown` méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="82f7a-106">The profiler code cannot safely call methods of the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface after the `Shutdown` method is called.</span></span> <span data-ttu-id="82f7a-107">Tous les appels à `ICorProfilerInfo` méthodes entraînent un comportement indéfini après le `Shutdown` méthode retourne.</span><span class="sxs-lookup"><span data-stu-id="82f7a-107">Any calls to `ICorProfilerInfo` methods result in undefined behavior after the `Shutdown` method returns.</span></span> <span data-ttu-id="82f7a-108">Certains événements immuables peuvent encore se produire après l’arrêt ; le profileur doit veiller à retourner immédiatement lorsque cela se produit.</span><span class="sxs-lookup"><span data-stu-id="82f7a-108">Certain immutable events may still occur after shutdown; the profiler should take care to return immediately when this occurs.</span></span>  
  
 <span data-ttu-id="82f7a-109">Le `Shutdown` méthode sera appelée uniquement si l’application managée est en cours de profilage démarré en tant que code géré (autrement dit, le frame initial sur la pile de processus est géré).</span><span class="sxs-lookup"><span data-stu-id="82f7a-109">The `Shutdown` method will be called only if the managed application that is being profiled started as managed code (that is, the initial frame on the process stack is managed).</span></span> <span data-ttu-id="82f7a-110">Si l’application a démarré en tant que code non managé, mais a sauté ultérieurement dans le code managé, créant ainsi une instance du common language runtime (CLR), puis `Shutdown` ne sera pas appelé.</span><span class="sxs-lookup"><span data-stu-id="82f7a-110">If the application started as unmanaged code but later jumped into managed code, thereby creating an instance of the common language runtime (CLR), then `Shutdown` will not be called.</span></span> <span data-ttu-id="82f7a-111">Dans ce cas, le profileur doit inclure dans sa bibliothèque un `DllMain` valeur de routine qui utilise le DLL_PROCESS_DETACH pour libérer les ressources et exécuter le nettoyage de ses données, par exemple, vider des traces sur le disque et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="82f7a-111">For these cases, the profiler should include in its library a `DllMain` routine that uses the DLL_PROCESS_DETACH value to free any resources and perform clean-up processing of its data, such as flushing traces to disk and so on.</span></span>  
  
 <span data-ttu-id="82f7a-112">En règle générale, le profileur doit faire face à des arrêts inattendus.</span><span class="sxs-lookup"><span data-stu-id="82f7a-112">In general, the profiler must cope with unexpected shutdowns.</span></span> <span data-ttu-id="82f7a-113">Par exemple, un processus peut être arrêté par de Win32 `TerminateProcess` (méthode) (déclaré dans Winbase.h).</span><span class="sxs-lookup"><span data-stu-id="82f7a-113">For example, a process might be halted by Win32's `TerminateProcess` method (declared in Winbase.h).</span></span> <span data-ttu-id="82f7a-114">Dans d’autres cas, le CLR arrêtera certains threads managés (threads d’arrière-plan) sans la remise des messages de destruction de façon ordonnée pour eux.</span><span class="sxs-lookup"><span data-stu-id="82f7a-114">In other cases, the CLR will halt certain managed threads (background threads) without delivering orderly destruction messages for them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82f7a-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="82f7a-115">Requirements</span></span>  
 <span data-ttu-id="82f7a-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82f7a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82f7a-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="82f7a-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="82f7a-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82f7a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82f7a-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82f7a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82f7a-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82f7a-120">See also</span></span>

- [<span data-ttu-id="82f7a-121">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="82f7a-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="82f7a-122">Initialize, méthode</span><span class="sxs-lookup"><span data-stu-id="82f7a-122">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
