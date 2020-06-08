---
title: ICorProfilerCallback::ClassLoadFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type:
- apiref
ms.openlocfilehash: 4be2a50664b001e865b5ecdd9aabe8ba727b8c26
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500388"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="fc8dd-102">ICorProfilerCallback::ClassLoadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="fc8dd-102">ICorProfilerCallback::ClassLoadFinished Method</span></span>
<span data-ttu-id="fc8dd-103">Notifie le profileur qu’une classe a fini de se charger.</span><span class="sxs-lookup"><span data-stu-id="fc8dd-103">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc8dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc8dd-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc8dd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fc8dd-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="fc8dd-106">\[in] identifie la classe qui a été chargée.</span><span class="sxs-lookup"><span data-stu-id="fc8dd-106">\[in] Identifies the class that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="fc8dd-107">\[dans] HRESULT qui indique si la classe a été chargée avec succès.</span><span class="sxs-lookup"><span data-stu-id="fc8dd-107">\[in] An HRESULT that indicates whether the class loaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="fc8dd-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="fc8dd-108">Remarks</span></span>  
 <span data-ttu-id="fc8dd-109">La valeur de `classId` n’est pas valide pour une demande d’informations tant que la `ClassLoadFinished` méthode n’est pas appelée.</span><span class="sxs-lookup"><span data-stu-id="fc8dd-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="fc8dd-110">Certaines parties du chargement de la classe peuvent continuer après le `ClassLoadFinished` rappel.</span><span class="sxs-lookup"><span data-stu-id="fc8dd-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="fc8dd-111">Un HRESULT d’échec dans `hrStatus` indique un échec.</span><span class="sxs-lookup"><span data-stu-id="fc8dd-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="fc8dd-112">Toutefois, un HRESULT de réussite dans `hrStatus` indique uniquement que la première partie du chargement de la classe a réussi.</span><span class="sxs-lookup"><span data-stu-id="fc8dd-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc8dd-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fc8dd-113">Requirements</span></span>  
 <span data-ttu-id="fc8dd-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc8dd-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc8dd-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fc8dd-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fc8dd-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc8dd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc8dd-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc8dd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc8dd-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc8dd-118">See also</span></span>

- [<span data-ttu-id="fc8dd-119">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="fc8dd-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="fc8dd-120">ClassLoadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="fc8dd-120">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
