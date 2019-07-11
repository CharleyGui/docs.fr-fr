---
title: ICorProfilerCallback::RemotingClientInvocationFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientInvocationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientInvocationFinished
helpviewer_keywords:
- RemotingClientInvocationFinished method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationFinished method [.NET Framework profiling]
ms.assetid: ea4b283b-1210-4f41-a7a2-c398b1adde4e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a8c29393f3127ec02d343221f28152fffbadb2b7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782943"
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a><span data-ttu-id="3757a-102">ICorProfilerCallback::RemotingClientInvocationFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="3757a-102">ICorProfilerCallback::RemotingClientInvocationFinished Method</span></span>
<span data-ttu-id="3757a-103">Informe le profileur qu’un appel de communication à distance a jusqu'à la fin sur le client.</span><span class="sxs-lookup"><span data-stu-id="3757a-103">Notifies the profiler that a remoting call has run to completion on the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3757a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3757a-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="3757a-105">Notes</span><span class="sxs-lookup"><span data-stu-id="3757a-105">Remarks</span></span>  
 <span data-ttu-id="3757a-106">Si l’appel de communication à distance était synchrone, il a également exécuté jusqu'à la fin sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="3757a-106">If the remoting call was synchronous, it has also run to completion on the server.</span></span> <span data-ttu-id="3757a-107">Si l’appel de communication à distance était asynchrone, une réponse peut encore être attendue lorsque l’appel est géré.</span><span class="sxs-lookup"><span data-stu-id="3757a-107">If the remoting call was asynchronous, a reply might still be expected when the call is handled.</span></span> <span data-ttu-id="3757a-108">Si une réponse est attendue, cela se produit comme un appel à [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) et un appel supplémentaire à `RemotingClientInvocationFinished` pour indiquer le traitement secondaire requis d’un appel asynchrone.</span><span class="sxs-lookup"><span data-stu-id="3757a-108">If a reply is expected, it will occur as a call to [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and an additional call to `RemotingClientInvocationFinished` to indicate the required secondary processing of an asynchronous call.</span></span>  
  
 <span data-ttu-id="3757a-109">Chacune des paires de rappels suivantes se produit sur le même thread :</span><span class="sxs-lookup"><span data-stu-id="3757a-109">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="3757a-110">`RemotingClientInvocationStarted` et [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="3757a-110">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="3757a-111">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) et [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="3757a-111">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="3757a-112">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) et [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="3757a-112">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="3757a-113">Vous devez être conscient des problèmes suivants avec les rappels de communication à distance :</span><span class="sxs-lookup"><span data-stu-id="3757a-113">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="3757a-114">Exécution d’une fonction de communication à distance n’est pas reflétée par le profileur API, afin de notifications pour les fonctions qui sont appelées à partir du client et exécutées sur le serveur ne sont pas correctement reçues.</span><span class="sxs-lookup"><span data-stu-id="3757a-114">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="3757a-115">L’appel réel se produit via un objet proxy ; le profileur, il semble que certaines fonctions sont compilé par JIT mais jamais utilisé.</span><span class="sxs-lookup"><span data-stu-id="3757a-115">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="3757a-116">Le profileur ne reçoit pas de notifications exactes pour les événements de communication à distance asynchrone.</span><span class="sxs-lookup"><span data-stu-id="3757a-116">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3757a-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3757a-117">Requirements</span></span>  
 <span data-ttu-id="3757a-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3757a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3757a-119">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3757a-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3757a-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3757a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3757a-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3757a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3757a-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3757a-122">See also</span></span>

- [<span data-ttu-id="3757a-123">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="3757a-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
