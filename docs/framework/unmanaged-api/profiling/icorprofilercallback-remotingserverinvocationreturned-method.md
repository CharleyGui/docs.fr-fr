---
title: ICorProfilerCallback::RemotingServerInvocationReturned, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerInvocationReturned
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerInvocationReturned
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerInvocationReturned method [.NET Framework profiling]
- RemotingServerInvocationReturned method [.NET Framework profiling]
ms.assetid: a4de6805-e159-4280-99e5-3390c86166d0
topic_type:
- apiref
ms.openlocfilehash: ff1670472b34292cb216a1a8817243ced6a938af
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704836"
---
# <a name="icorprofilercallbackremotingserverinvocationreturned-method"></a><span data-ttu-id="d9e7e-102">ICorProfilerCallback::RemotingServerInvocationReturned, méthode</span><span class="sxs-lookup"><span data-stu-id="d9e7e-102">ICorProfilerCallback::RemotingServerInvocationReturned Method</span></span>

<span data-ttu-id="d9e7e-103">Notifie le profileur que le processus a fini d’appeler une méthode en réponse à une demande d’appel de méthode distante.</span><span class="sxs-lookup"><span data-stu-id="d9e7e-103">Notifies the profiler that the process has finished invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9e7e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="d9e7e-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerInvocationReturned();  
```  
  
## <a name="requirements"></a><span data-ttu-id="d9e7e-105">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d9e7e-105">Requirements</span></span>  

 <span data-ttu-id="d9e7e-106">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9e7e-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9e7e-107">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d9e7e-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d9e7e-108">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9e7e-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9e7e-109">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9e7e-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e7e-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9e7e-110">See also</span></span>

- [<span data-ttu-id="d9e7e-111">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="d9e7e-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
