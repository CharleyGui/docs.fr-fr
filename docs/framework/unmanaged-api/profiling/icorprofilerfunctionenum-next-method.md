---
title: ICorProfilerFunctionEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Next
helpviewer_keywords:
- ICorProfilerFunctionEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 5ed4aa83-ce56-4b9f-9237-5da7587787fe
topic_type:
- apiref
ms.openlocfilehash: 9c7fa25712858d1119b45fc742a5d23454b55273
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864465"
---
# <a name="icorprofilerfunctionenumnext-method"></a><span data-ttu-id="e86bc-102">ICorProfilerFunctionEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="e86bc-102">ICorProfilerFunctionEnum::Next Method</span></span>
<span data-ttu-id="e86bc-103">Obtient le nombre spécifié de fonctions contiguës dans une collection séquentielle de fonctions, à commencer par la position actuelle de l'énumérateur dans la séquence.</span><span class="sxs-lookup"><span data-stu-id="e86bc-103">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e86bc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e86bc-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    COR_PRF_FUNCTION ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e86bc-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="e86bc-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e86bc-106">[in] Nombre de fonctions à récupérer.</span><span class="sxs-lookup"><span data-stu-id="e86bc-106">[in] The number of functions to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="e86bc-107">[out] Tableau de valeurs `COR_PRF_FUNCTION` qui représentent chacune une fonction récupérée.</span><span class="sxs-lookup"><span data-stu-id="e86bc-107">[out] An array of `COR_PRF_FUNCTION` values, each of which represents a retrieved function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="e86bc-108">[out] Pointeur vers le nombre de fonctions réellement retournées dans le tableau `ids`.</span><span class="sxs-lookup"><span data-stu-id="e86bc-108">[out] A pointer to the number of functions actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e86bc-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e86bc-109">Return Value</span></span>  
 <span data-ttu-id="e86bc-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="e86bc-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e86bc-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e86bc-111">HRESULT</span></span>|<span data-ttu-id="e86bc-112">Description</span><span class="sxs-lookup"><span data-stu-id="e86bc-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e86bc-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="e86bc-113">S_OK</span></span>|<span data-ttu-id="e86bc-114">`celt` éléments ont été retournés.</span><span class="sxs-lookup"><span data-stu-id="e86bc-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="e86bc-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e86bc-115">S_FALSE</span></span>|<span data-ttu-id="e86bc-116">Moins de `celt` éléments ont été retournés, ce qui indique que l'énumération est terminée.</span><span class="sxs-lookup"><span data-stu-id="e86bc-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e86bc-117">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="e86bc-117">Requirements</span></span>  
 <span data-ttu-id="e86bc-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e86bc-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e86bc-119">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e86bc-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e86bc-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e86bc-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e86bc-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e86bc-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e86bc-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e86bc-122">See also</span></span>

- [<span data-ttu-id="e86bc-123">ICorProfilerFunctionEnum, interface</span><span class="sxs-lookup"><span data-stu-id="e86bc-123">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="e86bc-124">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="e86bc-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
