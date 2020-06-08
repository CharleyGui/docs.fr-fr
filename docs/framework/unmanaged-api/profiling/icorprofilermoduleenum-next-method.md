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
ms.openlocfilehash: 7a3ad94a4149d6ebb70e077926771e28d7f82779
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494837"
---
# <a name="icorprofilermoduleenumnext-method"></a><span data-ttu-id="544b1-102">ICorProfilerModuleEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="544b1-102">ICorProfilerModuleEnum::Next Method</span></span>
<span data-ttu-id="544b1-103">Obtient le nombre spécifié de modules contigus dans une collection séquentielle de modules, à commencer par la position actuelle de l'énumérateur dans la séquence.</span><span class="sxs-lookup"><span data-stu-id="544b1-103">Gets the specified number of contiguous modules from a sequential collection of modules, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="544b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="544b1-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="544b1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="544b1-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="544b1-106">[in] Nombre de modules à récupérer.</span><span class="sxs-lookup"><span data-stu-id="544b1-106">[in] The number of modules to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="544b1-107">[out] Tableau de valeurs `ModuleID` qui représentent chacune un module récupéré.</span><span class="sxs-lookup"><span data-stu-id="544b1-107">[out] An array of `ModuleID` values, each of which represents a retrieved module.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="544b1-108">[out] Pointeur vers le nombre d'éléments réellement retournés dans le tableau `ids`.</span><span class="sxs-lookup"><span data-stu-id="544b1-108">[out] A pointer to the number of elements actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="544b1-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="544b1-109">Return Value</span></span>  
 <span data-ttu-id="544b1-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="544b1-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="544b1-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="544b1-111">HRESULT</span></span>|<span data-ttu-id="544b1-112">Description</span><span class="sxs-lookup"><span data-stu-id="544b1-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="544b1-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="544b1-113">S_OK</span></span>|<span data-ttu-id="544b1-114">`celt` éléments ont été retournés.</span><span class="sxs-lookup"><span data-stu-id="544b1-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="544b1-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="544b1-115">S_FALSE</span></span>|<span data-ttu-id="544b1-116">Moins de `celt` éléments ont été retournés, ce qui indique que l'énumération est terminée.</span><span class="sxs-lookup"><span data-stu-id="544b1-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="544b1-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="544b1-117">Requirements</span></span>  
 <span data-ttu-id="544b1-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="544b1-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="544b1-119">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="544b1-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="544b1-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="544b1-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="544b1-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="544b1-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="544b1-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="544b1-122">See also</span></span>

- [<span data-ttu-id="544b1-123">ICorProfilerModuleEnum, interface</span><span class="sxs-lookup"><span data-stu-id="544b1-123">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="544b1-124">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="544b1-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
