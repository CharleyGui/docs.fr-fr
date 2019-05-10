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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8bec96ef50416d946b1f12fd503e04f976ca58f1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662932"
---
# <a name="icorprofilercallbackremotingclientinvocationstarted-method"></a><span data-ttu-id="c0e87-102">ICorProfilerCallback::RemotingClientInvocationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="c0e87-102">ICorProfilerCallback::RemotingClientInvocationStarted Method</span></span>
<span data-ttu-id="c0e87-103">Notifie le profileur qu’un appel de communication à distance a démarré.</span><span class="sxs-lookup"><span data-stu-id="c0e87-103">Notifies the profiler that a remoting call has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0e87-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0e87-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientInvocationStarted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c0e87-105">Notes</span><span class="sxs-lookup"><span data-stu-id="c0e87-105">Remarks</span></span>  
 <span data-ttu-id="c0e87-106">Cet événement est le même pour les appels synchrones et asynchrones.</span><span class="sxs-lookup"><span data-stu-id="c0e87-106">This event is the same for synchronous and asynchronous calls.</span></span>  
  
 <span data-ttu-id="c0e87-107">Chacune des paires de rappels suivantes se produit sur le même thread :</span><span class="sxs-lookup"><span data-stu-id="c0e87-107">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="c0e87-108">`RemotingClientInvocationStarted` et [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="c0e87-108">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="c0e87-109">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) et [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="c0e87-109">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="c0e87-110">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) et [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="c0e87-110">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="c0e87-111">Vous devez être conscient des problèmes suivants avec les rappels de communication à distance :</span><span class="sxs-lookup"><span data-stu-id="c0e87-111">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="c0e87-112">Exécution d’une fonction de communication à distance n’est pas reflétée par le profileur API, afin de notifications pour les fonctions qui sont appelées à partir du client et exécutées sur le serveur ne sont pas correctement reçues.</span><span class="sxs-lookup"><span data-stu-id="c0e87-112">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="c0e87-113">L’appel réel se produit via un objet proxy ; le profileur, il semble que certaines fonctions sont compilé par JIT mais jamais utilisé.</span><span class="sxs-lookup"><span data-stu-id="c0e87-113">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="c0e87-114">Le profileur ne reçoit pas de notifications exactes pour les événements de communication à distance asynchrone.</span><span class="sxs-lookup"><span data-stu-id="c0e87-114">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0e87-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c0e87-115">Requirements</span></span>  
 <span data-ttu-id="c0e87-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0e87-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0e87-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c0e87-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c0e87-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0e87-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0e87-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0e87-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0e87-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0e87-120">See also</span></span>

- [<span data-ttu-id="c0e87-121">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="c0e87-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
