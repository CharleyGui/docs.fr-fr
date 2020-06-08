---
title: ICorProfilerInfo4::EnumThreads, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumThreads
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumThreads
helpviewer_keywords:
- ICorProfilerInfo4::EnumThreads method [.NET Framework profiling]
- EnumThreads method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: bca7a5b4-c207-4894-918c-0733926296dd
topic_type:
- apiref
ms.openlocfilehash: d42c86a458661d3559f99235a6d5b208c82d1963
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502806"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="38dc1-102">ICorProfilerInfo4::EnumThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="38dc1-102">ICorProfilerInfo4::EnumThreads Method</span></span>
<span data-ttu-id="38dc1-103">Retourne un énumérateur qui fournit des méthodes pour itérer séquentiellement au sein de la collection de tous les threads managés dans le processus profilé.</span><span class="sxs-lookup"><span data-stu-id="38dc1-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38dc1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38dc1-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38dc1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="38dc1-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="38dc1-106">à Pointeur vers une interface [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="38dc1-106">[out] A pointer to an [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38dc1-107">Notes</span><span class="sxs-lookup"><span data-stu-id="38dc1-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38dc1-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="38dc1-108">Requirements</span></span>  
 <span data-ttu-id="38dc1-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38dc1-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38dc1-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="38dc1-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="38dc1-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38dc1-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38dc1-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38dc1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38dc1-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38dc1-113">See also</span></span>

- [<span data-ttu-id="38dc1-114">ICorProfilerThreadEnum, interface</span><span class="sxs-lookup"><span data-stu-id="38dc1-114">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="38dc1-115">ICorProfilerInfo4, interface</span><span class="sxs-lookup"><span data-stu-id="38dc1-115">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="38dc1-116">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="38dc1-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="38dc1-117">Profilage</span><span class="sxs-lookup"><span data-stu-id="38dc1-117">Profiling</span></span>](index.md)
