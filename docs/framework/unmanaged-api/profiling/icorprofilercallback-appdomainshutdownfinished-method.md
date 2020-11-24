---
title: ICorProfilerCallback::AppDomainShutdownFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type:
- apiref
ms.openlocfilehash: ddb2d6eeb75a118a12f681b354f6feccd1231c64
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685377"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="24ac1-102">ICorProfilerCallback::AppDomainShutdownFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="24ac1-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>

<span data-ttu-id="24ac1-103">Notifie le profileur qu’un domaine d’application a été déchargé d’un processus.</span><span class="sxs-lookup"><span data-stu-id="24ac1-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24ac1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24ac1-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24ac1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="24ac1-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="24ac1-106">\[in] identifie le domaine dans lequel les assemblys de l’application sont stockés.</span><span class="sxs-lookup"><span data-stu-id="24ac1-106">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

- `hrStatus`

  <span data-ttu-id="24ac1-107">\[dans] HRESULT qui indique si le domaine d’application a été déchargé avec succès.</span><span class="sxs-lookup"><span data-stu-id="24ac1-107">\[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="24ac1-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="24ac1-108">Remarks</span></span>  

 <span data-ttu-id="24ac1-109">La valeur de `appDomainId` n’est pas valide pour une demande d’informations après le retour de la méthode [ICorProfilerCallback :: AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="24ac1-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="24ac1-110">Certaines parties du déchargement du domaine d’application peuvent continuer après le `AppDomainCreationFinished` rappel.</span><span class="sxs-lookup"><span data-stu-id="24ac1-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="24ac1-111">Un HRESULT d’échec dans `hrStatus` indique un échec.</span><span class="sxs-lookup"><span data-stu-id="24ac1-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="24ac1-112">Toutefois, un HRESULT de réussite dans `hrStatus` indique uniquement que la première partie du déchargement du domaine d’application a réussi.</span><span class="sxs-lookup"><span data-stu-id="24ac1-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24ac1-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="24ac1-113">Requirements</span></span>  

 <span data-ttu-id="24ac1-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24ac1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24ac1-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="24ac1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="24ac1-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24ac1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24ac1-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24ac1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24ac1-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24ac1-118">See also</span></span>

- [<span data-ttu-id="24ac1-119">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="24ac1-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
