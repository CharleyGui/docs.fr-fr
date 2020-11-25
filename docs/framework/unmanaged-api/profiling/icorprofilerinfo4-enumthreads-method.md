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
ms.openlocfilehash: df0e66c8563404d7de4f1e11f41483f2f61f519c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721554"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="7601e-102">ICorProfilerInfo4::EnumThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="7601e-102">ICorProfilerInfo4::EnumThreads Method</span></span>

<span data-ttu-id="7601e-103">Retourne un énumérateur qui fournit des méthodes pour itérer séquentiellement au sein de la collection de tous les threads managés dans le processus profilé.</span><span class="sxs-lookup"><span data-stu-id="7601e-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7601e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7601e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7601e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7601e-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="7601e-106">à Pointeur vers une interface [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="7601e-106">[out] A pointer to an [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7601e-107">Notes</span><span class="sxs-lookup"><span data-stu-id="7601e-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7601e-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7601e-108">Requirements</span></span>  

 <span data-ttu-id="7601e-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7601e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7601e-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7601e-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7601e-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7601e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7601e-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7601e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7601e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7601e-113">See also</span></span>

- [<span data-ttu-id="7601e-114">ICorProfilerThreadEnum, interface</span><span class="sxs-lookup"><span data-stu-id="7601e-114">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="7601e-115">ICorProfilerInfo4, interface</span><span class="sxs-lookup"><span data-stu-id="7601e-115">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="7601e-116">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="7601e-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="7601e-117">Profilage</span><span class="sxs-lookup"><span data-stu-id="7601e-117">Profiling</span></span>](index.md)
