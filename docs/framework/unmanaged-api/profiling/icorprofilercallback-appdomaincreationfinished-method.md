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
ms.openlocfilehash: 688b9975cc68463de066e5225c6ab1e04cbb5337
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685369"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="30a4b-102">ICorProfilerCallback::AppDomainCreationFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="30a4b-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>

<span data-ttu-id="30a4b-103">Notifie le profileur qu’un domaine d’application a été créé.</span><span class="sxs-lookup"><span data-stu-id="30a4b-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30a4b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30a4b-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);
```  
  
## <a name="parameters"></a><span data-ttu-id="30a4b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="30a4b-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="30a4b-106">\[in] identifie le domaine qui a été créé.</span><span class="sxs-lookup"><span data-stu-id="30a4b-106">\[in] Identifies the domain which has been created.</span></span>

- `hrStatus`

  <span data-ttu-id="30a4b-107">\[dans] HRESULT qui indique si la création du domaine d’application s’est terminée avec succès.</span><span class="sxs-lookup"><span data-stu-id="30a4b-107">\[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="30a4b-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="30a4b-108">Remarks</span></span>  

 <span data-ttu-id="30a4b-109">L’ID d’application n’est valide pour aucune demande d’informations tant que la `AppDomainCreationFinished` méthode n’est pas appelée.</span><span class="sxs-lookup"><span data-stu-id="30a4b-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="30a4b-110">Certaines parties du chargement du domaine d’application peuvent continuer après le `AppDomainCreationFinished` rappel.</span><span class="sxs-lookup"><span data-stu-id="30a4b-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="30a4b-111">Un HRESULT d’échec dans `hrStatus` indique un échec.</span><span class="sxs-lookup"><span data-stu-id="30a4b-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="30a4b-112">Toutefois, un HRESULT de réussite dans `hrStatus` indique uniquement que la première partie de la création du domaine d’application a réussi.</span><span class="sxs-lookup"><span data-stu-id="30a4b-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30a4b-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="30a4b-113">Requirements</span></span>  

 <span data-ttu-id="30a4b-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30a4b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30a4b-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="30a4b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="30a4b-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30a4b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30a4b-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30a4b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30a4b-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30a4b-118">See also</span></span>

- [<span data-ttu-id="30a4b-119">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="30a4b-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
