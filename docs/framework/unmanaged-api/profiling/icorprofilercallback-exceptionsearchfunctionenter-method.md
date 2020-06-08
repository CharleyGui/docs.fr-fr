---
title: ICorProfilerCallback::ExceptionSearchFunctionEnter, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFunctionEnter
helpviewer_keywords:
- ExceptionSearchFunctionEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionEnter method [.NET Framework profiling]
ms.assetid: bfd54573-b7e6-4bd1-a184-7f08a8b39fae
topic_type:
- apiref
ms.openlocfilehash: 244227aadb50720514f7511be563089d520b4bf5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500193"
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="1c213-102">ICorProfilerCallback::ExceptionSearchFunctionEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="1c213-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>
<span data-ttu-id="1c213-103">Notifie le profileur que la phase de recherche de la gestion des exceptions a commencé à rechercher une fonction pour trouver un gestionnaire pour l’exception actuelle.</span><span class="sxs-lookup"><span data-stu-id="1c213-103">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c213-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c213-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c213-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1c213-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="1c213-106">\[in] ID de la fonction qui a été entrée.</span><span class="sxs-lookup"><span data-stu-id="1c213-106">\[in] The ID of the function that has been entered.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="1c213-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1c213-107">Requirements</span></span>  
 <span data-ttu-id="1c213-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c213-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c213-109">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1c213-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1c213-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c213-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c213-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c213-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c213-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c213-112">See also</span></span>

- [<span data-ttu-id="1c213-113">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="1c213-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="1c213-114">ExceptionSearchFunctionLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="1c213-114">ExceptionSearchFunctionLeave Method</span></span>](icorprofilercallback-exceptionsearchfunctionleave-method.md)
