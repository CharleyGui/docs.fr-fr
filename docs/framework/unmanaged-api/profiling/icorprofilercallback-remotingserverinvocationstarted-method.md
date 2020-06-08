---
title: ICorProfilerCallback::RemotingServerInvocationStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerInvocationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerInvocationStarted
helpviewer_keywords:
- RemotingServerInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerInvocationStarted method [.NET Framework profiling]
ms.assetid: 86051a11-ad8e-4ace-9a11-ff0f982a5e11
topic_type:
- apiref
ms.openlocfilehash: 3725b73ab55f6e4dc789a1fde8d1224695a174d7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499933"
---
# <a name="icorprofilercallbackremotingserverinvocationstarted-method"></a><span data-ttu-id="efcd1-102">ICorProfilerCallback::RemotingServerInvocationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="efcd1-102">ICorProfilerCallback::RemotingServerInvocationStarted Method</span></span>
<span data-ttu-id="efcd1-103">Notifie le profileur que le processus appelle une méthode en réponse à une demande d’appel de méthode distante.</span><span class="sxs-lookup"><span data-stu-id="efcd1-103">Notifies the profiler that the process is invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efcd1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efcd1-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerInvocationStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="efcd1-105">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="efcd1-105">Requirements</span></span>  
 <span data-ttu-id="efcd1-106">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efcd1-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efcd1-107">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="efcd1-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="efcd1-108">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="efcd1-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efcd1-109">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efcd1-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efcd1-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efcd1-110">See also</span></span>

- [<span data-ttu-id="efcd1-111">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="efcd1-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
