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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 208552dd94f587b9326280ad455ca2478ae4ac4d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780251"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="2f2ac-102">ICorProfilerInfo::ForceGC, méthode</span><span class="sxs-lookup"><span data-stu-id="2f2ac-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="2f2ac-103">Force le garbage collection se produisent dans le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="2f2ac-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f2ac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f2ac-104">Syntax</span></span>  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="2f2ac-105">Notes</span><span class="sxs-lookup"><span data-stu-id="2f2ac-105">Remarks</span></span>  
 <span data-ttu-id="2f2ac-106">Le `ForceGC` méthode doit être appelée uniquement à partir d’un thread qui n’a jamais exécuté du code managé et n’a pas de rappels de profileur sur sa pile.</span><span class="sxs-lookup"><span data-stu-id="2f2ac-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="2f2ac-107">L’implémentation la plus commode consiste à créer un thread séparé dans le profileur appelle `ForceGC` quand il est signalé.</span><span class="sxs-lookup"><span data-stu-id="2f2ac-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f2ac-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2f2ac-108">Requirements</span></span>  
 <span data-ttu-id="2f2ac-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f2ac-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f2ac-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2f2ac-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2f2ac-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f2ac-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f2ac-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f2ac-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f2ac-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f2ac-113">See also</span></span>

- [<span data-ttu-id="2f2ac-114">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="2f2ac-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
