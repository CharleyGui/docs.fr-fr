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
ms.openlocfilehash: ae9cb089ad6c0b0422063d3db413b97eb6ff1405
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445802"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="ac324-102">ICorProfilerCallback::RemotingClientSendingMessage, méthode</span><span class="sxs-lookup"><span data-stu-id="ac324-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>
<span data-ttu-id="ac324-103">Notifies the profiler that the client is sending a request to the server.</span><span class="sxs-lookup"><span data-stu-id="ac324-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac324-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac324-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac324-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ac324-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="ac324-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span><span class="sxs-lookup"><span data-stu-id="ac324-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="ac324-107">Remoting GUID cookies are active.</span><span class="sxs-lookup"><span data-stu-id="ac324-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="ac324-108">The channel succeeds in transmitting the message.</span><span class="sxs-lookup"><span data-stu-id="ac324-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="ac324-109">GUID cookies are active on the server-side process.</span><span class="sxs-lookup"><span data-stu-id="ac324-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="ac324-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span><span class="sxs-lookup"><span data-stu-id="ac324-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="ac324-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span><span class="sxs-lookup"><span data-stu-id="ac324-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac324-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="ac324-112">Requirements</span></span>  
 <span data-ttu-id="ac324-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac324-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac324-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ac324-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ac324-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac324-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac324-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac324-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac324-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac324-117">See also</span></span>

- [<span data-ttu-id="ac324-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="ac324-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
