---
title: ICorProfilerModuleEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Next
helpviewer_keywords:
- ICorProfilerModuleEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: a3cea59d-7622-4323-897a-0a464c40f77f
topic_type:
- apiref
ms.openlocfilehash: 695a4386d9399a079df41f11f52a3185083784ed
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861383"
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="e7119-102">ICorProfilerModuleEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="e7119-102">ICorProfilerModuleEnum::Next Method</span></span>
<span data-ttu-id="e7119-103">Obtient le nombre spécifié de modules contigus dans une collection séquentielle de modules, à commencer par la position actuelle de l'énumérateur dans la séquence.</span><span class="sxs-lookup"><span data-stu-id="e7119-103">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7119-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7119-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7119-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="e7119-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e7119-106">[in] Nombre de modules à récupérer.</span><span class="sxs-lookup"><span data-stu-id="e7119-106">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="e7119-107">[out] Tableau de valeurs `ModuleID` qui représentent chacune un module récupéré.</span><span class="sxs-lookup"><span data-stu-id="e7119-107">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="e7119-108">[out] Pointeur vers le nombre d'éléments réellement retournés dans le tableau `ids`.</span><span class="sxs-lookup"><span data-stu-id="e7119-108">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7119-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e7119-109">Return Value</span></span>  
 <span data-ttu-id="e7119-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="e7119-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e7119-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e7119-111">HRESULT</span></span>|<span data-ttu-id="e7119-112">Description</span><span class="sxs-lookup"><span data-stu-id="e7119-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e7119-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="e7119-113">S_OK</span></span>|<span data-ttu-id="e7119-114">`celt` éléments ont été retournés.</span><span class="sxs-lookup"><span data-stu-id="e7119-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="e7119-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e7119-115">S_FALSE</span></span>|<span data-ttu-id="e7119-116">Moins de `celt` éléments ont été retournés, ce qui indique que l'énumération est terminée.</span><span class="sxs-lookup"><span data-stu-id="e7119-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e7119-117">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="e7119-117">Requirements</span></span>  
 <span data-ttu-id="e7119-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7119-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7119-119">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e7119-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e7119-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7119-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7119-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7119-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7119-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7119-122">See also</span></span>

- [<span data-ttu-id="e7119-123">ICorProfilerModuleEnum, interface</span><span class="sxs-lookup"><span data-stu-id="e7119-123">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="e7119-124">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="e7119-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
