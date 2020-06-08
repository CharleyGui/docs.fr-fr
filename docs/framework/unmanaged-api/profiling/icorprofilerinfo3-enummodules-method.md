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
ms.openlocfilehash: 85adf2dbdbb8c02192a9017bc4f664274a08ee24
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496579"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="63446-102">ICorProfilerInfo3::EnumModules, méthode</span><span class="sxs-lookup"><span data-stu-id="63446-102">ICorProfilerInfo3::EnumModules Method</span></span>
<span data-ttu-id="63446-103">Retourne un énumérateur qui fournit des méthodes pour itérer séquentiellement au sein d’une collection de modules managés chargés dans l’application.</span><span class="sxs-lookup"><span data-stu-id="63446-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63446-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63446-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63446-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="63446-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="63446-106">à Pointeur vers une interface [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="63446-106">[out] A pointer to an [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63446-107">Notes</span><span class="sxs-lookup"><span data-stu-id="63446-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63446-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="63446-108">Requirements</span></span>  
 <span data-ttu-id="63446-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63446-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63446-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="63446-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="63446-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63446-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63446-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63446-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63446-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63446-113">See also</span></span>

- [<span data-ttu-id="63446-114">ICorProfilerFunctionEnum, interface</span><span class="sxs-lookup"><span data-stu-id="63446-114">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="63446-115">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="63446-115">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="63446-116">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="63446-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="63446-117">Profilage</span><span class="sxs-lookup"><span data-stu-id="63446-117">Profiling</span></span>](index.md)
