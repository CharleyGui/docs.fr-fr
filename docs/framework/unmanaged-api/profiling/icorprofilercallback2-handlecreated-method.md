---
title: ICorProfilerCallback2::HandleCreated, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.HandleCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::HandleCreated
helpviewer_keywords:
- HandleCreated method [.NET Framework profiling]
- ICorProfilerCallback2::HandleCreated method [.NET Framework profiling]
ms.assetid: 6bbb7786-7c38-490f-9834-91aa2795c355
topic_type:
- apiref
ms.openlocfilehash: 6cd931f6c680a07327915ab4680702af298ca1ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717308"
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="1cdd0-102">ICorProfilerCallback2::HandleCreated, méthode</span><span class="sxs-lookup"><span data-stu-id="1cdd0-102">ICorProfilerCallback2::HandleCreated Method</span></span>

<span data-ttu-id="1cdd0-103">Notifie le profileur de code qu’un handle de garbage collection a été créé.</span><span class="sxs-lookup"><span data-stu-id="1cdd0-103">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cdd0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1cdd0-104">Syntax</span></span>  
  
```cpp  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cdd0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1cdd0-105">Parameters</span></span>  

 `handleId`  
 <span data-ttu-id="1cdd0-106">dans ID du descripteur pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="1cdd0-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="1cdd0-107">dans ID de l’objet pour lequel le handle de garbage collection a été créé.</span><span class="sxs-lookup"><span data-stu-id="1cdd0-107">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cdd0-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1cdd0-108">Requirements</span></span>  

 <span data-ttu-id="1cdd0-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cdd0-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cdd0-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1cdd0-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1cdd0-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1cdd0-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1cdd0-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cdd0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cdd0-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1cdd0-113">See also</span></span>

- [<span data-ttu-id="1cdd0-114">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="1cdd0-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="1cdd0-115">ICorProfilerCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="1cdd0-115">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
