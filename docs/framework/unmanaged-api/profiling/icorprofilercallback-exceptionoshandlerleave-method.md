---
title: ICorProfilerCallback::ExceptionOSHandlerLeave, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerLeave
helpviewer_keywords:
- ExceptionOSHandlerLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerLeave method [.NET Framework profiling]
ms.assetid: 4d164676-0ee9-4f67-a8ea-cb474db09053
topic_type:
- apiref
ms.openlocfilehash: 37e3c9139a202e3cb31bd824d182389ae10b7389
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699922"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="e634a-102">ICorProfilerCallback::ExceptionOSHandlerLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="e634a-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>

<span data-ttu-id="e634a-103">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="e634a-103">Not implemented.</span></span> <span data-ttu-id="e634a-104">Un profileur qui a besoin d’informations sur les exceptions non managées doit obtenir ces informations par d’autres moyens.</span><span class="sxs-lookup"><span data-stu-id="e634a-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e634a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e634a-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="e634a-106">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e634a-106">Requirements</span></span>  

 <span data-ttu-id="e634a-107">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e634a-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e634a-108">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e634a-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e634a-109">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e634a-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e634a-110">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e634a-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e634a-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e634a-111">See also</span></span>

- [<span data-ttu-id="e634a-112">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="e634a-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
