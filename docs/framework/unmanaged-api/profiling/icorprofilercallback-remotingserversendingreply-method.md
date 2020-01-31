---
title: ICorProfilerCallback::RemotingServerSendingReply, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerSendingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerSendingReply
helpviewer_keywords:
- RemotingServerSendingReply method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerSendingReply method [.NET Framework profiling]
ms.assetid: dfe84a19-2e03-4be2-8b25-f02bad38e4a9
topic_type:
- apiref
ms.openlocfilehash: f77901623ef4df7b43276c18a910cf62fcc4451d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865972"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="2e752-102">ICorProfilerCallback::RemotingServerSendingReply, méthode</span><span class="sxs-lookup"><span data-stu-id="2e752-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="2e752-103">Indique au profileur que le processus a terminé le traitement d’une demande d’appel de méthode distante et qu’il est sur le paragraphe de transmettre la réponse via un canal.</span><span class="sxs-lookup"><span data-stu-id="2e752-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e752-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e752-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e752-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="2e752-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="2e752-106">dans Pointeur vers un GUID qui correspond à la valeur fournie dans [ICorProfilerCallback :: RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="2e752-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="2e752-107">Les cookies du GUID de communication à distance sont actifs.</span><span class="sxs-lookup"><span data-stu-id="2e752-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="2e752-108">Le canal parvient à transmettre le message.</span><span class="sxs-lookup"><span data-stu-id="2e752-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="2e752-109">Les cookies GUID sont actifs sur le processus côté client.</span><span class="sxs-lookup"><span data-stu-id="2e752-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="2e752-110">Cela permet d’associer facilement les appels de communication à distance et la création d’une pile des appels logiques.</span><span class="sxs-lookup"><span data-stu-id="2e752-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="2e752-111">dans Valeur `true` si l’appel est asynchrone ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="2e752-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e752-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="2e752-112">Requirements</span></span>  
 <span data-ttu-id="2e752-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e752-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e752-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2e752-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2e752-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e752-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e752-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e752-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e752-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e752-117">See also</span></span>

- [<span data-ttu-id="2e752-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="2e752-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
