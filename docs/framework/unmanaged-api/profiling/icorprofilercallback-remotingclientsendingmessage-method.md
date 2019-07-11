---
title: ICorProfilerCallback::RemotingClientSendingMessage, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientSendingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientSendingMessage
helpviewer_keywords:
- RemotingClientSendingMessage method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientSendingMessage method [.NET Framework profiling]
ms.assetid: 54d9a5a5-3877-49c1-a503-ce7c7943bc2a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4729a8d3ac2c6f7ec51a032a07ebfd1c2838cb9a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782909"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="f7d36-102">ICorProfilerCallback::RemotingClientSendingMessage, méthode</span><span class="sxs-lookup"><span data-stu-id="f7d36-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>
<span data-ttu-id="f7d36-103">Notifie le profileur que le client envoie une demande au serveur.</span><span class="sxs-lookup"><span data-stu-id="f7d36-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7d36-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7d36-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7d36-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f7d36-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="f7d36-106">[in] Une valeur qui correspond à la valeur fournie dans [ICorProfilerCallback::RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) dans ces conditions :</span><span class="sxs-lookup"><span data-stu-id="f7d36-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="f7d36-107">Les cookies GUID de communication à distance sont actifs.</span><span class="sxs-lookup"><span data-stu-id="f7d36-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="f7d36-108">Le canal réussit à transmettre le message.</span><span class="sxs-lookup"><span data-stu-id="f7d36-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="f7d36-109">Les cookies GUID sont actifs sur le processus côté serveur.</span><span class="sxs-lookup"><span data-stu-id="f7d36-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="f7d36-110">Cela permet un appariement simple d’appels de communication à distance et de la création d’une pile d’appel logique.</span><span class="sxs-lookup"><span data-stu-id="f7d36-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="f7d36-111">[in] Une valeur qui est `true` si l’appel est asynchrone ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="f7d36-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7d36-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f7d36-112">Requirements</span></span>  
 <span data-ttu-id="f7d36-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7d36-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7d36-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f7d36-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f7d36-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7d36-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7d36-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7d36-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7d36-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7d36-117">See also</span></span>

- [<span data-ttu-id="f7d36-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="f7d36-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
