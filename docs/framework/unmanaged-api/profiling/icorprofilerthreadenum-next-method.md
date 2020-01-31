---
title: ICorProfilerThreadEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Next
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Next
helpviewer_keywords:
- ICorProfilerThreadEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: f3535279-3c63-41a2-ab0e-a129dc5a01e8
topic_type:
- apiref
ms.openlocfilehash: 4e08e74a2b7e5b853f089b95328c0a55de5a87cd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860904"
---
# <a name="icorprofilerthreadenumnext-method"></a><span data-ttu-id="61cd8-102">ICorProfilerThreadEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="61cd8-102">ICorProfilerThreadEnum::Next Method</span></span>
<span data-ttu-id="61cd8-103">Obtient le nombre spécifié de threads contigus dans une collection séquentielle de threads, à commencer par la position actuelle de l’énumérateur dans la séquence.</span><span class="sxs-lookup"><span data-stu-id="61cd8-103">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61cd8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61cd8-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (    [in]  ULONG      celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                    ThreadID ids[],  
    [out] ULONG *   pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61cd8-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="61cd8-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="61cd8-106">[in] Nombre de threads à récupérer.</span><span class="sxs-lookup"><span data-stu-id="61cd8-106">[in] The number of threads to retrieve.</span></span>  
  
 `ids`  
 <span data-ttu-id="61cd8-107">[out] Tableau de valeurs `ThreadID` qui représentent chacune un thread récupéré.</span><span class="sxs-lookup"><span data-stu-id="61cd8-107">[out] An array of `ThreadID` values, each of which represents a retrieved thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="61cd8-108">[out] Pointeur vers le nombre de threads<bpt i="1000001" x="1000001" type="formatting">{b&gt;</bpt><ept i="1000001">&lt;b}</ept>réellement retournés dans le tableau `ids`.</span><span class="sxs-lookup"><span data-stu-id="61cd8-108">[out] A pointer to the number of threads actually returned in the `ids` array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61cd8-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="61cd8-109">Return Value</span></span>  
 <span data-ttu-id="61cd8-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="61cd8-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="61cd8-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="61cd8-111">HRESULT</span></span>|<span data-ttu-id="61cd8-112">Description</span><span class="sxs-lookup"><span data-stu-id="61cd8-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="61cd8-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="61cd8-113">S_OK</span></span>|<span data-ttu-id="61cd8-114">`celt` éléments ont été retournés.</span><span class="sxs-lookup"><span data-stu-id="61cd8-114">`celt` elements were returned.</span></span>|  
|<span data-ttu-id="61cd8-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="61cd8-115">S_FALSE</span></span>|<span data-ttu-id="61cd8-116">Moins de `celt` éléments ont été retournés, ce qui indique que l'énumération est terminée.</span><span class="sxs-lookup"><span data-stu-id="61cd8-116">Fewer than `celt` elements were returned, which indicates that the enumeration is complete.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="61cd8-117">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="61cd8-117">Requirements</span></span>  
 <span data-ttu-id="61cd8-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61cd8-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61cd8-119">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="61cd8-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="61cd8-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61cd8-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61cd8-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61cd8-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61cd8-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61cd8-122">See also</span></span>

- [<span data-ttu-id="61cd8-123">ICorProfilerThreadEnum, interface</span><span class="sxs-lookup"><span data-stu-id="61cd8-123">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="61cd8-124">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="61cd8-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
