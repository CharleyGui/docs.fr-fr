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
ms.openlocfilehash: 481fc2c40331e31f6a018d012fb2b2543d4fd9b5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503365"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="7b6a6-102">ICorProfilerCallback::ModuleLoadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="7b6a6-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="7b6a6-103">Notifie le profileur qu’un module a fini de se charger.</span><span class="sxs-lookup"><span data-stu-id="7b6a6-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b6a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b6a6-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b6a6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7b6a6-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="7b6a6-106">dans ID du module dont le chargement est terminé.</span><span class="sxs-lookup"><span data-stu-id="7b6a6-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="7b6a6-107">dans HRESULT qui indique si le module a été chargé avec succès.</span><span class="sxs-lookup"><span data-stu-id="7b6a6-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b6a6-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="7b6a6-108">Remarks</span></span>  
 <span data-ttu-id="7b6a6-109">La valeur de `moduleId` n’est pas valide pour une demande d’informations tant que la `ModuleLoadFinished` méthode n’est pas appelée.</span><span class="sxs-lookup"><span data-stu-id="7b6a6-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="7b6a6-110">Certaines parties du chargement du module peuvent continuer après le `ModuleLoadFinished` rappel.</span><span class="sxs-lookup"><span data-stu-id="7b6a6-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="7b6a6-111">Un HRESULT d’échec dans `hrStatus` indique un échec.</span><span class="sxs-lookup"><span data-stu-id="7b6a6-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="7b6a6-112">Toutefois, un HRESULT de réussite dans `hrStatus` indique uniquement que la première partie du chargement du module a réussi.</span><span class="sxs-lookup"><span data-stu-id="7b6a6-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b6a6-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7b6a6-113">Requirements</span></span>  
 <span data-ttu-id="7b6a6-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b6a6-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b6a6-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7b6a6-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7b6a6-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b6a6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b6a6-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b6a6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b6a6-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b6a6-118">See also</span></span>

- [<span data-ttu-id="7b6a6-119">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="7b6a6-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="7b6a6-120">ModuleLoadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="7b6a6-120">ModuleLoadStarted Method</span></span>](icorprofilercallback-moduleloadstarted-method.md)
