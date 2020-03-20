---
title: ICorProfilerCallback::AppDomainCreationFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type:
- apiref
ms.openlocfilehash: 8b3f7712436c001e5cd44f214f6edb06390abd41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177070"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="b9c21-102">ICorProfilerCallback::AppDomainCreationFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="b9c21-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="b9c21-103">Informe le profileur qu’un domaine d’application a été créé.</span><span class="sxs-lookup"><span data-stu-id="b9c21-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9c21-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9c21-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);
```  
  
## <a name="parameters"></a><span data-ttu-id="b9c21-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b9c21-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="b9c21-106">\[dans) Identifie le domaine qui a été créé.</span><span class="sxs-lookup"><span data-stu-id="b9c21-106">\[in] Identifies the domain which has been created.</span></span>

- `hrStatus`

  <span data-ttu-id="b9c21-107">\[dans] Un HRESULT qui indique si la création du domaine d’application a été complétée avec succès.</span><span class="sxs-lookup"><span data-stu-id="b9c21-107">\[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9c21-108">Notes </span><span class="sxs-lookup"><span data-stu-id="b9c21-108">Remarks</span></span>  
 <span data-ttu-id="b9c21-109">L’ID de demande n’est `AppDomainCreationFinished` pas valide pour toute demande d’information jusqu’à ce que la méthode soit appelée.</span><span class="sxs-lookup"><span data-stu-id="b9c21-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="b9c21-110">Certaines parties du chargement du `AppDomainCreationFinished` domaine d’application peuvent continuer après le rappel.</span><span class="sxs-lookup"><span data-stu-id="b9c21-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="b9c21-111">Un échec HRESULT dans `hrStatus` indique une défaillance.</span><span class="sxs-lookup"><span data-stu-id="b9c21-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="b9c21-112">Cependant, un succès HRESULT indique `hrStatus` seulement que la première partie de la création du domaine de l’application a réussi.</span><span class="sxs-lookup"><span data-stu-id="b9c21-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9c21-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b9c21-113">Requirements</span></span>  
 <span data-ttu-id="b9c21-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9c21-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9c21-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b9c21-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b9c21-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9c21-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9c21-117">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9c21-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9c21-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9c21-118">See also</span></span>

- [<span data-ttu-id="b9c21-119">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="b9c21-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
