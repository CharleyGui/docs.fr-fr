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
ms.openlocfilehash: c121e403d116581ce3fa823d5d8cadbb2a58e296
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445784"
---
# <a name="icorprofilercallbackremotingserverinvocationreturned-method"></a><span data-ttu-id="4fceb-102">ICorProfilerCallback::RemotingServerInvocationReturned, méthode</span><span class="sxs-lookup"><span data-stu-id="4fceb-102">ICorProfilerCallback::RemotingServerInvocationReturned Method</span></span>
<span data-ttu-id="4fceb-103">Notifies the profiler that the process has finished invoking a method in response to a remote method invocation request.</span><span class="sxs-lookup"><span data-stu-id="4fceb-103">Notifies the profiler that the process has finished invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fceb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fceb-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerInvocationReturned();  
```  
  
## <a name="requirements"></a><span data-ttu-id="4fceb-105">spécifications</span><span class="sxs-lookup"><span data-stu-id="4fceb-105">Requirements</span></span>  
 <span data-ttu-id="4fceb-106">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fceb-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fceb-107">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4fceb-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4fceb-108">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fceb-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fceb-109">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fceb-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fceb-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4fceb-110">See also</span></span>

- [<span data-ttu-id="4fceb-111">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="4fceb-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
