---
title: ICorProfilerCallback::ModuleLoadFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type:
- apiref
ms.openlocfilehash: 661229e5fbd5d106662f0e823a1753bd76c33311
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866167"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="b93e0-102">ICorProfilerCallback::ModuleLoadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="b93e0-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="b93e0-103">Notifie le profileur qu’un module a fini de se charger.</span><span class="sxs-lookup"><span data-stu-id="b93e0-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b93e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b93e0-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b93e0-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="b93e0-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="b93e0-106">dans ID du module dont le chargement est terminé.</span><span class="sxs-lookup"><span data-stu-id="b93e0-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="b93e0-107">dans HRESULT qui indique si le module a été chargé avec succès.</span><span class="sxs-lookup"><span data-stu-id="b93e0-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b93e0-108">Notes</span><span class="sxs-lookup"><span data-stu-id="b93e0-108">Remarks</span></span>  
 <span data-ttu-id="b93e0-109">La valeur de `moduleId` n’est pas valide pour une demande d’informations jusqu’à ce que la méthode `ModuleLoadFinished` soit appelée.</span><span class="sxs-lookup"><span data-stu-id="b93e0-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="b93e0-110">Certaines parties du chargement du module peuvent continuer après le rappel `ModuleLoadFinished`.</span><span class="sxs-lookup"><span data-stu-id="b93e0-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="b93e0-111">Un HRESULT d’échec dans `hrStatus` indique un échec.</span><span class="sxs-lookup"><span data-stu-id="b93e0-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="b93e0-112">Toutefois, un HRESULT de réussite dans `hrStatus` indique uniquement que la première partie du chargement du module a réussi.</span><span class="sxs-lookup"><span data-stu-id="b93e0-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b93e0-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="b93e0-113">Requirements</span></span>  
 <span data-ttu-id="b93e0-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b93e0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b93e0-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b93e0-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b93e0-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b93e0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b93e0-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b93e0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b93e0-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b93e0-118">See also</span></span>

- [<span data-ttu-id="b93e0-119">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="b93e0-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b93e0-120">ModuleLoadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="b93e0-120">ModuleLoadStarted Method</span></span>](icorprofilercallback-moduleloadstarted-method.md)
