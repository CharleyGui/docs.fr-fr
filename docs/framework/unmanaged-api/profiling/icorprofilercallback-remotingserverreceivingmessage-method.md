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
ms.openlocfilehash: 157e6bc6cb9603fa9558ad6d39f0b086849fc7b0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499894"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="8a470-102">ICorProfilerCallback::RemotingServerReceivingMessage, méthode</span><span class="sxs-lookup"><span data-stu-id="8a470-102">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>
<span data-ttu-id="8a470-103">Indique au profileur que le processus a reçu une demande d’appel ou d’activation de méthode distante.</span><span class="sxs-lookup"><span data-stu-id="8a470-103">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a470-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a470-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a470-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8a470-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="8a470-106">dans Valeur qui correspond à la valeur fournie dans [ICorProfilerCallback :: RemotingClientSendingMessage,](icorprofilercallback-remotingclientsendingmessage-method.md) dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="8a470-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="8a470-107">Les cookies du GUID de communication à distance sont actifs.</span><span class="sxs-lookup"><span data-stu-id="8a470-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="8a470-108">Le canal parvient à transmettre le message.</span><span class="sxs-lookup"><span data-stu-id="8a470-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="8a470-109">Les cookies GUID sont actifs sur le processus côté client.</span><span class="sxs-lookup"><span data-stu-id="8a470-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="8a470-110">Cela permet d’associer facilement les appels de communication à distance et la création d’une pile des appels logiques.</span><span class="sxs-lookup"><span data-stu-id="8a470-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="8a470-111">dans Valeur qui est `true` si l’appel est asynchrone ; sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="8a470-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a470-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="8a470-112">Remarks</span></span>  
 <span data-ttu-id="8a470-113">Si la demande de message est asynchrone, la demande peut être desservie par n’importe quel thread arbitraire.</span><span class="sxs-lookup"><span data-stu-id="8a470-113">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a470-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8a470-114">Requirements</span></span>  
 <span data-ttu-id="8a470-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a470-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a470-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8a470-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8a470-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a470-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a470-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a470-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a470-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a470-119">See also</span></span>

- [<span data-ttu-id="8a470-120">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="8a470-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
