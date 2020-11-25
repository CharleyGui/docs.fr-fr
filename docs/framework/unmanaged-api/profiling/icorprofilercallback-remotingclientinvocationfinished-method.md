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
ms.openlocfilehash: d41ccd30707eba269bbac7231e06792363615544
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719318"
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a><span data-ttu-id="45be4-102">ICorProfilerCallback::RemotingClientInvocationFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="45be4-102">ICorProfilerCallback::RemotingClientInvocationFinished Method</span></span>

<span data-ttu-id="45be4-103">Notifie le profileur qu’un appel de communication à distance a été exécuté sur le client.</span><span class="sxs-lookup"><span data-stu-id="45be4-103">Notifies the profiler that a remoting call has run to completion on the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45be4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45be4-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="45be4-105">Notes</span><span class="sxs-lookup"><span data-stu-id="45be4-105">Remarks</span></span>  

 <span data-ttu-id="45be4-106">Si l’appel de communication à distance était synchrone, il s’est également exécuté sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="45be4-106">If the remoting call was synchronous, it has also run to completion on the server.</span></span> <span data-ttu-id="45be4-107">Si l’appel de communication à distance était asynchrone, il est possible qu’une réponse soit toujours attendue lorsque l’appel est géré.</span><span class="sxs-lookup"><span data-stu-id="45be4-107">If the remoting call was asynchronous, a reply might still be expected when the call is handled.</span></span> <span data-ttu-id="45be4-108">Si une réponse est attendue, elle se produit comme un appel à [ICorProfilerCallback :: RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) et un appel supplémentaire à `RemotingClientInvocationFinished` pour indiquer le traitement secondaire requis d’un appel asynchrone.</span><span class="sxs-lookup"><span data-stu-id="45be4-108">If a reply is expected, it will occur as a call to [ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and an additional call to `RemotingClientInvocationFinished` to indicate the required secondary processing of an asynchronous call.</span></span>  
  
 <span data-ttu-id="45be4-109">Chaque paire de rappels suivante aura lieu sur le même thread :</span><span class="sxs-lookup"><span data-stu-id="45be4-109">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="45be4-110">`RemotingClientInvocationStarted` et [ICorProfilerCallback :: RemotingClientSendingMessage,](icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="45be4-110">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="45be4-111">[ICorProfilerCallback :: RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) et [ICorProfilerCallback :: RemotingClientInvocationFinished,](icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="45be4-111">[ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="45be4-112">[ICorProfilerCallback :: RemotingServerInvocationReturned,](icorprofilercallback-remotingserverinvocationreturned-method.md) et [ICorProfilerCallback :: RemotingServerSendingReply,](icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="45be4-112">[ICorProfilerCallback::RemotingServerInvocationReturned](icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="45be4-113">Vous devez être conscient des problèmes suivants avec les rappels de communication à distance :</span><span class="sxs-lookup"><span data-stu-id="45be4-113">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="45be4-114">L’exécution d’une fonction de communication à distance n’est pas reflétée par l’API du profileur, de sorte que les notifications pour les fonctions qui sont appelées à partir du client et exécutées sur le serveur ne sont pas correctement reçues.</span><span class="sxs-lookup"><span data-stu-id="45be4-114">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="45be4-115">L’appel réel se produit via un objet proxy ; pour le profileur, certaines fonctions sont compilées juste-à-temps (JIT), mais jamais utilisées.</span><span class="sxs-lookup"><span data-stu-id="45be4-115">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="45be4-116">Le profileur ne reçoit pas de notifications exactes pour les événements de communication à distance asynchrones.</span><span class="sxs-lookup"><span data-stu-id="45be4-116">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45be4-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="45be4-117">Requirements</span></span>  

 <span data-ttu-id="45be4-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45be4-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45be4-119">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="45be4-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="45be4-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45be4-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45be4-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45be4-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45be4-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45be4-122">See also</span></span>

- [<span data-ttu-id="45be4-123">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="45be4-123">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
