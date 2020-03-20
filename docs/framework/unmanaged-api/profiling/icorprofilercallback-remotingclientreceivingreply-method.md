---
title: ICorProfilerCallback::RemotingClientReceivingReply, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientReceivingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply
helpviewer_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply method [.NET Framework profiling]
- RemotingClientReceivingReply method [.NET Framework profiling]
ms.assetid: 15cfc300-8231-4ecb-9a04-19851c3eb484
topic_type:
- apiref
ms.openlocfilehash: f7a943627e2087e6b8c78ced9fc32824843d44fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175133"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="86c0c-102">ICorProfilerCallback::RemotingClientReceivingReply, méthode</span><span class="sxs-lookup"><span data-stu-id="86c0c-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="86c0c-103">Informe le profileur que la partie serveur d’un appel de remotage est terminée et que le client reçoit maintenant et est sur le point de traiter la réponse.</span><span class="sxs-lookup"><span data-stu-id="86c0c-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86c0c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86c0c-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);
```  
  
## <a name="parameters"></a><span data-ttu-id="86c0c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="86c0c-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="86c0c-106">[dans] Une valeur qui correspondra à la valeur fournie dans [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) dans ces conditions:</span><span class="sxs-lookup"><span data-stu-id="86c0c-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="86c0c-107">La remotage des cookies GUID est active.</span><span class="sxs-lookup"><span data-stu-id="86c0c-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="86c0c-108">Le canal réussit à transmettre le message.</span><span class="sxs-lookup"><span data-stu-id="86c0c-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="86c0c-109">Les cookies GUID sont actifs sur le processus côté serveur.</span><span class="sxs-lookup"><span data-stu-id="86c0c-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="86c0c-110">Cela permet un jumelage facile d’appels de remotage.</span><span class="sxs-lookup"><span data-stu-id="86c0c-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="86c0c-111">[dans] Une valeur `true` qui est si l’appel est asynchrone; autrement, `false`.</span><span class="sxs-lookup"><span data-stu-id="86c0c-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86c0c-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="86c0c-112">Requirements</span></span>  
 <span data-ttu-id="86c0c-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86c0c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86c0c-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="86c0c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="86c0c-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86c0c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86c0c-116">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86c0c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86c0c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86c0c-117">See also</span></span>

- [<span data-ttu-id="86c0c-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="86c0c-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
