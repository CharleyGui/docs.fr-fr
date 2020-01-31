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
ms.openlocfilehash: 8ae58344a7a17637bf08b9b5179abdba7e7060d6
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866024"
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="67678-102">ICorProfilerCallback::RemotingClientSendingMessage, méthode</span><span class="sxs-lookup"><span data-stu-id="67678-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>
<span data-ttu-id="67678-103">Indique au profileur que le client envoie une demande au serveur.</span><span class="sxs-lookup"><span data-stu-id="67678-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67678-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67678-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67678-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="67678-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="67678-106">dans Valeur qui correspond à la valeur fournie dans [ICorProfilerCallback :: RemotingServerReceivingMessage,](icorprofilercallback-remotingserverreceivingmessage-method.md) dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="67678-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="67678-107">Les cookies du GUID de communication à distance sont actifs.</span><span class="sxs-lookup"><span data-stu-id="67678-107">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="67678-108">Le canal parvient à transmettre le message.</span><span class="sxs-lookup"><span data-stu-id="67678-108">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="67678-109">Les cookies GUID sont actifs sur le processus côté serveur.</span><span class="sxs-lookup"><span data-stu-id="67678-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="67678-110">Cela permet d’associer facilement les appels de communication à distance et la création d’une pile des appels logiques.</span><span class="sxs-lookup"><span data-stu-id="67678-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="67678-111">dans Valeur `true` si l’appel est asynchrone ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="67678-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67678-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="67678-112">Requirements</span></span>  
 <span data-ttu-id="67678-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67678-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67678-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="67678-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="67678-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67678-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67678-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67678-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67678-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67678-117">See also</span></span>

- [<span data-ttu-id="67678-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="67678-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
