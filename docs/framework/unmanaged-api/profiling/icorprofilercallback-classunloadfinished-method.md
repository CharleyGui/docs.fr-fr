---
title: ICorProfilerCallback::ClassUnloadFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type:
- apiref
ms.openlocfilehash: 14eb90c707618796d6d62ed2ec5710ceba31ba6c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500375"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="8fd3f-102">ICorProfilerCallback::ClassUnloadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="8fd3f-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="8fd3f-103">Notifie le profileur qu’une classe a terminé le déchargement.</span><span class="sxs-lookup"><span data-stu-id="8fd3f-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fd3f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fd3f-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fd3f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8fd3f-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="8fd3f-106">\[in] identifie la classe qui a été déchargée.</span><span class="sxs-lookup"><span data-stu-id="8fd3f-106">\[in] Identifies the class that was unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="8fd3f-107">\[dans] HRESULT qui indique si la classe a été déchargée avec succès.</span><span class="sxs-lookup"><span data-stu-id="8fd3f-107">\[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="8fd3f-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="8fd3f-108">Remarks</span></span>  
 <span data-ttu-id="8fd3f-109">Certaines parties du déchargement de la classe peuvent continuer après le `ClassUnloadFinished` rappel.</span><span class="sxs-lookup"><span data-stu-id="8fd3f-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="8fd3f-110">Un HRESULT d’échec dans `hrStatus` indique un échec.</span><span class="sxs-lookup"><span data-stu-id="8fd3f-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="8fd3f-111">Toutefois, un HRESULT de réussite dans `hrStatus` indique uniquement que la première partie du déchargement de la classe a réussi.</span><span class="sxs-lookup"><span data-stu-id="8fd3f-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fd3f-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8fd3f-112">Requirements</span></span>  
 <span data-ttu-id="8fd3f-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fd3f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fd3f-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8fd3f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8fd3f-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8fd3f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fd3f-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fd3f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fd3f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8fd3f-117">See also</span></span>

- [<span data-ttu-id="8fd3f-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="8fd3f-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="8fd3f-119">ClassUnloadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="8fd3f-119">ClassUnloadStarted Method</span></span>](icorprofilercallback-classunloadstarted-method.md)
