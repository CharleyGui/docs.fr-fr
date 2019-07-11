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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff18d52091ca75152c20667d1ec1b024f44d6129
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782916"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="1dd15-102">ICorProfilerCallback::RemotingClientReceivingReply, méthode</span><span class="sxs-lookup"><span data-stu-id="1dd15-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="1dd15-103">Informe le profileur que la partie côté serveur d’un appel de communication à distance est terminée et le client reçoit maintenant et sur le point de traiter la réponse.</span><span class="sxs-lookup"><span data-stu-id="1dd15-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dd15-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1dd15-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);   
```  
  
## <a name="parameters"></a><span data-ttu-id="1dd15-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1dd15-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="1dd15-106">[in] Valeur qui correspond à la valeur fournie dans [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) dans ces conditions :</span><span class="sxs-lookup"><span data-stu-id="1dd15-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="1dd15-107">Les cookies GUID de communication à distance sont actifs.</span><span class="sxs-lookup"><span data-stu-id="1dd15-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="1dd15-108">Le canal réussit à transmettre le message.</span><span class="sxs-lookup"><span data-stu-id="1dd15-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="1dd15-109">Les cookies GUID sont actifs sur le processus côté serveur.</span><span class="sxs-lookup"><span data-stu-id="1dd15-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="1dd15-110">Cela permet un appariement simple d’appels de communication à distance.</span><span class="sxs-lookup"><span data-stu-id="1dd15-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="1dd15-111">[in] Une valeur qui est `true` si l’appel est asynchrone ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="1dd15-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dd15-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1dd15-112">Requirements</span></span>  
 <span data-ttu-id="1dd15-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dd15-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dd15-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1dd15-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1dd15-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1dd15-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1dd15-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dd15-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd15-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1dd15-117">See also</span></span>

- [<span data-ttu-id="1dd15-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="1dd15-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
