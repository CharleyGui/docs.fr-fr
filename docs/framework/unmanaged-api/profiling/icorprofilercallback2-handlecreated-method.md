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
ms.openlocfilehash: 772f0c00bb850e35a6f5bf7fa4df2b3052999df5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499790"
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="66623-102">ICorProfilerCallback2::HandleCreated, méthode</span><span class="sxs-lookup"><span data-stu-id="66623-102">ICorProfilerCallback2::HandleCreated Method</span></span>
<span data-ttu-id="66623-103">Notifie le profileur de code qu’un handle de garbage collection a été créé.</span><span class="sxs-lookup"><span data-stu-id="66623-103">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66623-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66623-104">Syntax</span></span>  
  
```cpp  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66623-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="66623-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="66623-106">dans ID du descripteur pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="66623-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="66623-107">dans ID de l’objet pour lequel le handle de garbage collection a été créé.</span><span class="sxs-lookup"><span data-stu-id="66623-107">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66623-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="66623-108">Requirements</span></span>  
 <span data-ttu-id="66623-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66623-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66623-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="66623-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="66623-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66623-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66623-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66623-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66623-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66623-113">See also</span></span>

- [<span data-ttu-id="66623-114">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="66623-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="66623-115">ICorProfilerCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="66623-115">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
