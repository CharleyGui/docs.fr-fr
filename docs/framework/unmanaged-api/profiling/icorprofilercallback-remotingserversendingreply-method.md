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
ms.openlocfilehash: 1d876644ae35d13a481b01d9e0e5ff0d0764ca18
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713949"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="06934-102">ICorProfilerCallback::RemotingServerSendingReply, méthode</span><span class="sxs-lookup"><span data-stu-id="06934-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>

<span data-ttu-id="06934-103">Indique au profileur que le processus a terminé le traitement d’une demande d’appel de méthode distante et qu’il est sur le paragraphe de transmettre la réponse via un canal.</span><span class="sxs-lookup"><span data-stu-id="06934-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06934-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06934-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06934-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="06934-105">Parameters</span></span>  

 `pCookie`  
 <span data-ttu-id="06934-106">dans Pointeur vers un GUID qui correspond à la valeur fournie dans [ICorProfilerCallback :: RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="06934-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="06934-107">Les cookies du GUID de communication à distance sont actifs.</span><span class="sxs-lookup"><span data-stu-id="06934-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="06934-108">Le canal parvient à transmettre le message.</span><span class="sxs-lookup"><span data-stu-id="06934-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="06934-109">Les cookies GUID sont actifs sur le processus côté client.</span><span class="sxs-lookup"><span data-stu-id="06934-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="06934-110">Cela permet d’associer facilement les appels de communication à distance et la création d’une pile des appels logiques.</span><span class="sxs-lookup"><span data-stu-id="06934-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="06934-111">dans Valeur qui est `true` si l’appel est asynchrone ; sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="06934-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06934-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="06934-112">Requirements</span></span>  

 <span data-ttu-id="06934-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06934-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06934-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="06934-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="06934-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06934-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06934-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06934-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06934-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06934-117">See also</span></span>

- [<span data-ttu-id="06934-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="06934-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
