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
ms.openlocfilehash: 62973a36e899b1a8c618888e5245bfc00d8ad777
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866060"
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="25194-102">ICorProfilerCallback::RemotingClientReceivingReply, méthode</span><span class="sxs-lookup"><span data-stu-id="25194-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="25194-103">Indique au profileur que la partie côté serveur d’un appel de communication à distance est terminée et que le client reçoit et est à présent en train de traiter la réponse.</span><span class="sxs-lookup"><span data-stu-id="25194-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25194-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25194-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);   
```  
  
## <a name="parameters"></a><span data-ttu-id="25194-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="25194-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="25194-106">dans Valeur qui correspond à la valeur fournie dans [ICorProfilerCallback :: RemotingServerSendingReply,](icorprofilercallback-remotingserversendingreply-method.md) dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="25194-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="25194-107">Les cookies du GUID de communication à distance sont actifs.</span><span class="sxs-lookup"><span data-stu-id="25194-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="25194-108">Le canal parvient à transmettre le message.</span><span class="sxs-lookup"><span data-stu-id="25194-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="25194-109">Les cookies GUID sont actifs sur le processus côté serveur.</span><span class="sxs-lookup"><span data-stu-id="25194-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="25194-110">Cela permet d’associer facilement les appels de communication à distance.</span><span class="sxs-lookup"><span data-stu-id="25194-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="25194-111">dans Valeur `true` si l’appel est asynchrone ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="25194-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25194-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="25194-112">Requirements</span></span>  
 <span data-ttu-id="25194-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25194-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25194-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="25194-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="25194-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25194-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25194-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25194-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25194-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25194-117">See also</span></span>

- [<span data-ttu-id="25194-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="25194-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
