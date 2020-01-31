---
title: ICorProfilerCallback::RemotingClientInvocationStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientInvocationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientInvocationStarted
helpviewer_keywords:
- RemotingClientInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationStarted method [.NET Framework profiling]
ms.assetid: 796b63f3-c809-47f1-89cc-b23ad8eb5e79
topic_type:
- apiref
ms.openlocfilehash: 93bd1010374413f3f4ef7e1424ff8194dded8bb3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866043"
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a><span data-ttu-id="36f9c-102">ICorProfilerCallback::RemotingClientInvocationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="36f9c-102">ICorProfilerCallback::RemotingClientInvocationStarted Method</span></span>
<span data-ttu-id="36f9c-103">Notifie le profileur qu’un appel de communication à distance a démarré.</span><span class="sxs-lookup"><span data-stu-id="36f9c-103">Notifies the profiler that a remoting call has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36f9c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36f9c-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="36f9c-105">Notes</span><span class="sxs-lookup"><span data-stu-id="36f9c-105">Remarks</span></span>  
 <span data-ttu-id="36f9c-106">Cet événement est le même pour les appels synchrones et asynchrones.</span><span class="sxs-lookup"><span data-stu-id="36f9c-106">This event is the same for synchronous and asynchronous calls.</span></span>  
  
 <span data-ttu-id="36f9c-107">Chaque paire de rappels suivante aura lieu sur le même thread :</span><span class="sxs-lookup"><span data-stu-id="36f9c-107">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="36f9c-108">`RemotingClientInvocationStarted` et [ICorProfilerCallback :: RemotingClientSendingMessage,](icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="36f9c-108">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="36f9c-109">[ICorProfilerCallback :: RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) et [ICorProfilerCallback :: RemotingClientInvocationFinished,](icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="36f9c-109">[ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="36f9c-110">[ICorProfilerCallback :: RemotingServerInvocationReturned,](icorprofilercallback-remotingserverinvocationreturned-method.md) et [ICorProfilerCallback :: RemotingServerSendingReply,](icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="36f9c-110">[ICorProfilerCallback::RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="36f9c-111">Vous devez être conscient des problèmes suivants avec les rappels de communication à distance :</span><span class="sxs-lookup"><span data-stu-id="36f9c-111">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="36f9c-112">L’exécution d’une fonction de communication à distance n’est pas reflétée par l’API du profileur, de sorte que les notifications pour les fonctions qui sont appelées à partir du client et exécutées sur le serveur ne sont pas correctement reçues.</span><span class="sxs-lookup"><span data-stu-id="36f9c-112">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="36f9c-113">L’appel réel se produit via un objet proxy ; pour le profileur, certaines fonctions sont compilées juste-à-temps (JIT), mais jamais utilisées.</span><span class="sxs-lookup"><span data-stu-id="36f9c-113">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="36f9c-114">Le profileur ne reçoit pas de notifications exactes pour les événements de communication à distance asynchrones.</span><span class="sxs-lookup"><span data-stu-id="36f9c-114">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36f9c-115">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="36f9c-115">Requirements</span></span>  
 <span data-ttu-id="36f9c-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36f9c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36f9c-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="36f9c-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="36f9c-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36f9c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36f9c-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36f9c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36f9c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36f9c-120">See also</span></span>

- [<span data-ttu-id="36f9c-121">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="36f9c-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
