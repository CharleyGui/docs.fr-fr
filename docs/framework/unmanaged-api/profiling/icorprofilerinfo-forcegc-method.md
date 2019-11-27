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
ms.openlocfilehash: 9f97da4e68d4b76178198e91c3fb8f08b56dda7b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448188"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="fbde8-102">ICorProfilerInfo::ForceGC, méthode</span><span class="sxs-lookup"><span data-stu-id="fbde8-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="fbde8-103">Force garbage collection se produire dans le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="fbde8-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbde8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbde8-104">Syntax</span></span>  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="fbde8-105">Notes</span><span class="sxs-lookup"><span data-stu-id="fbde8-105">Remarks</span></span>  
 <span data-ttu-id="fbde8-106">La méthode `ForceGC` doit être appelée uniquement à partir d’un thread qui n’a jamais exécuté de code managé et qui n’a pas de rappels de profileur sur sa pile.</span><span class="sxs-lookup"><span data-stu-id="fbde8-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="fbde8-107">L’implémentation la plus pratique consiste à créer un thread distinct dans le profileur qui appelle `ForceGC` lorsqu’il est signalé.</span><span class="sxs-lookup"><span data-stu-id="fbde8-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbde8-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fbde8-108">Requirements</span></span>  
 <span data-ttu-id="fbde8-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbde8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbde8-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fbde8-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fbde8-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbde8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbde8-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbde8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbde8-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbde8-113">See also</span></span>

- [<span data-ttu-id="fbde8-114">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="fbde8-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
