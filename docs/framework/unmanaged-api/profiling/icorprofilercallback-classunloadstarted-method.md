---
title: ICorProfilerCallback::ClassUnloadStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3a305835651867a533e17f1c5c3b85b16975c3b1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745383"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="0a26d-102">ICorProfilerCallback::ClassUnloadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="0a26d-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="0a26d-103">Notifie le profileur qu’une classe est déchargée.</span><span class="sxs-lookup"><span data-stu-id="0a26d-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a26d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a26d-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a26d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0a26d-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="0a26d-106">[in] Identifie la classe qui est en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="0a26d-106">[in] Identifies the class that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a26d-107">Notes</span><span class="sxs-lookup"><span data-stu-id="0a26d-107">Remarks</span></span>  
 <span data-ttu-id="0a26d-108">La valeur de `classId` n’est pas valide pour une demande d’informations après la `ClassUnloadStarted` retourne de la méthode, il s’agit dernière chance du profileur d’obtenir des informations sur cette classe.</span><span class="sxs-lookup"><span data-stu-id="0a26d-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a26d-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0a26d-109">Requirements</span></span>  
 <span data-ttu-id="0a26d-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a26d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a26d-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0a26d-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0a26d-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a26d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a26d-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a26d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a26d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a26d-114">See also</span></span>

- [<span data-ttu-id="0a26d-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="0a26d-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="0a26d-116">ClassUnloadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="0a26d-116">ClassUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)
