---
title: ICorProfilerInfo3::EnumModules, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumModules Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumModules
helpviewer_keywords:
- ICorProfilerInfo3::EnumModules method [.NET Framework profiling]
- EnumModules method [.NET Framework profiling]
ms.assetid: 1bf00b42-69da-4019-91b3-bf88026e83fb
topic_type:
- apiref
ms.openlocfilehash: 626ecddae8ba91d1830d98210208f9fbee36f073
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868584"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="6b364-102">ICorProfilerInfo3::EnumModules, méthode</span><span class="sxs-lookup"><span data-stu-id="6b364-102">ICorProfilerInfo3::EnumModules Method</span></span>
<span data-ttu-id="6b364-103">Retourne un énumérateur qui fournit des méthodes pour itérer séquentiellement au sein d’une collection de modules managés chargés dans l’application.</span><span class="sxs-lookup"><span data-stu-id="6b364-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b364-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b364-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b364-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="6b364-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="6b364-106">à Pointeur vers une interface [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="6b364-106">[out] A pointer to an [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b364-107">Notes</span><span class="sxs-lookup"><span data-stu-id="6b364-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b364-108">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="6b364-108">Requirements</span></span>  
 <span data-ttu-id="6b364-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b364-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b364-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6b364-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6b364-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b364-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b364-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b364-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b364-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b364-113">See also</span></span>

- [<span data-ttu-id="6b364-114">ICorProfilerFunctionEnum, interface</span><span class="sxs-lookup"><span data-stu-id="6b364-114">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="6b364-115">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="6b364-115">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="6b364-116">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="6b364-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="6b364-117">Profilage</span><span class="sxs-lookup"><span data-stu-id="6b364-117">Profiling</span></span>](index.md)
