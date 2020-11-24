---
title: ICorProfilerCallback::RemotingServerReceivingMessage, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerReceivingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage method [.NET Framework profiling]
- RemotingServerReceivingMessage method [.NET Framework profiling]
ms.assetid: 5604d21f-e6b7-490e-b469-42122a7568e1
topic_type:
- apiref
ms.openlocfilehash: 0fc84a15d3250d5103c1dbc6486960f0ea780a2b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676814"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="601e8-102">ICorProfilerCallback::RemotingServerReceivingMessage, méthode</span><span class="sxs-lookup"><span data-stu-id="601e8-102">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>

<span data-ttu-id="601e8-103">Indique au profileur que le processus a reçu une demande d’appel ou d’activation de méthode distante.</span><span class="sxs-lookup"><span data-stu-id="601e8-103">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="601e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="601e8-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="601e8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="601e8-105">Parameters</span></span>  

 `pCookie`  
 <span data-ttu-id="601e8-106">dans Valeur qui correspond à la valeur fournie dans [ICorProfilerCallback :: RemotingClientSendingMessage,](icorprofilercallback-remotingclientsendingmessage-method.md) dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="601e8-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="601e8-107">Les cookies du GUID de communication à distance sont actifs.</span><span class="sxs-lookup"><span data-stu-id="601e8-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="601e8-108">Le canal parvient à transmettre le message.</span><span class="sxs-lookup"><span data-stu-id="601e8-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="601e8-109">Les cookies GUID sont actifs sur le processus côté client.</span><span class="sxs-lookup"><span data-stu-id="601e8-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="601e8-110">Cela permet d’associer facilement les appels de communication à distance et la création d’une pile des appels logiques.</span><span class="sxs-lookup"><span data-stu-id="601e8-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="601e8-111">dans Valeur qui est `true` si l’appel est asynchrone ; sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="601e8-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="601e8-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="601e8-112">Remarks</span></span>  

 <span data-ttu-id="601e8-113">Si la demande de message est asynchrone, la demande peut être desservie par n’importe quel thread arbitraire.</span><span class="sxs-lookup"><span data-stu-id="601e8-113">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="601e8-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="601e8-114">Requirements</span></span>  

 <span data-ttu-id="601e8-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="601e8-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="601e8-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="601e8-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="601e8-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="601e8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="601e8-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="601e8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="601e8-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="601e8-119">See also</span></span>

- [<span data-ttu-id="601e8-120">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="601e8-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
