---
title: ICorProfilerInfo::ForceGC, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.ForceGC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::ForceGC
helpviewer_keywords:
- ICorProfilerInfo::ForceGC method [.NET Framework profiling]
- ForceGC method [.NET Framework profiling]
ms.assetid: 0da1ef80-d242-4636-87d0-43e0470b342a
topic_type:
- apiref
ms.openlocfilehash: 75f2db5e5489f02dcae3db0c3e6af19c922e0745
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669196"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="05bc1-102">ICorProfilerInfo::ForceGC, méthode</span><span class="sxs-lookup"><span data-stu-id="05bc1-102">ICorProfilerInfo::ForceGC Method</span></span>

<span data-ttu-id="05bc1-103">Force garbage collection se produire dans le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="05bc1-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05bc1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05bc1-104">Syntax</span></span>  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="05bc1-105">Notes</span><span class="sxs-lookup"><span data-stu-id="05bc1-105">Remarks</span></span>  

 <span data-ttu-id="05bc1-106">La `ForceGC` méthode doit être appelée uniquement à partir d’un thread qui n’a jamais exécuté de code managé et qui n’a pas de rappels de profileur sur sa pile.</span><span class="sxs-lookup"><span data-stu-id="05bc1-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="05bc1-107">L’implémentation la plus pratique consiste à créer un thread distinct dans le profileur qui appelle lorsqu’il est `ForceGC` signalé.</span><span class="sxs-lookup"><span data-stu-id="05bc1-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05bc1-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="05bc1-108">Requirements</span></span>  

 <span data-ttu-id="05bc1-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05bc1-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05bc1-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="05bc1-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="05bc1-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05bc1-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05bc1-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05bc1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05bc1-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05bc1-113">See also</span></span>

- [<span data-ttu-id="05bc1-114">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="05bc1-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
