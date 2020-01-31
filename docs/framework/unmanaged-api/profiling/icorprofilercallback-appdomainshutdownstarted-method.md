---
title: ICorProfilerCallback::AppDomainShutdownStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownStarted
helpviewer_keywords:
- AppDomainShutdownStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownStarted method [.NET Framework profiling]
ms.assetid: d23a3408-b525-4aec-a186-2ac7ca65d7a4
topic_type:
- apiref
ms.openlocfilehash: d280b008b34befce04159d02dfbb3de37b262c3c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866661"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="5c5bf-102">ICorProfilerCallback::AppDomainShutdownStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="5c5bf-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="5c5bf-103">Notifie le profileur qu’un domaine d’application est en cours de déchargement d’un processus.</span><span class="sxs-lookup"><span data-stu-id="5c5bf-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c5bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c5bf-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c5bf-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="5c5bf-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="5c5bf-106">\[in] identifie le domaine dans lequel les assemblys de l’application sont stockés.</span><span class="sxs-lookup"><span data-stu-id="5c5bf-106">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

## <a name="remarks"></a><span data-ttu-id="5c5bf-107">Notes</span><span class="sxs-lookup"><span data-stu-id="5c5bf-107">Remarks</span></span>  
 <span data-ttu-id="5c5bf-108">La valeur de `appDomainId` n’est pas valide pour toute demande d’informations après le retour de la méthode `AppDomainShutdownStarted`, il s’agit de la dernière chance du profileur d’obtenir des informations sur ce domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="5c5bf-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c5bf-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="5c5bf-109">Requirements</span></span>  
 <span data-ttu-id="5c5bf-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c5bf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c5bf-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5c5bf-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5c5bf-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c5bf-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c5bf-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c5bf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c5bf-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c5bf-114">See also</span></span>

- [<span data-ttu-id="5c5bf-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="5c5bf-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
