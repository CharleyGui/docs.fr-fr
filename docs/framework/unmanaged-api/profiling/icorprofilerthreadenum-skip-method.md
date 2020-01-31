---
title: ICorProfilerThreadEnum::Skip, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type:
- apiref
ms.openlocfilehash: b08a501f7d55fbb193afd8c297ca7725348dac76
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860924"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="166e4-102">ICorProfilerThreadEnum::Skip, méthode</span><span class="sxs-lookup"><span data-stu-id="166e4-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="166e4-103">Fait avancer le curseur de l'énumérateur depuis sa position actuelle de manière à ignorer le nombre spécifié d'éléments.</span><span class="sxs-lookup"><span data-stu-id="166e4-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="166e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="166e4-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="166e4-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="166e4-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="166e4-106">dans Nombre d’éléments à ignorer.</span><span class="sxs-lookup"><span data-stu-id="166e4-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="166e4-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="166e4-107">Return Value</span></span>  
 <span data-ttu-id="166e4-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="166e4-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="166e4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="166e4-109">HRESULT</span></span>|<span data-ttu-id="166e4-110">Description</span><span class="sxs-lookup"><span data-stu-id="166e4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="166e4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="166e4-111">S_OK</span></span>|<span data-ttu-id="166e4-112">`celt` éléments ont été ignorés.</span><span class="sxs-lookup"><span data-stu-id="166e4-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="166e4-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="166e4-113">S_FALSE</span></span>|<span data-ttu-id="166e4-114">Moins de `celt` éléments ont été ignorés, ce qui indique qu’il n’y a plus d’éléments.</span><span class="sxs-lookup"><span data-stu-id="166e4-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="166e4-115">Notes</span><span class="sxs-lookup"><span data-stu-id="166e4-115">Remarks</span></span>  
 <span data-ttu-id="166e4-116">La nouvelle position du curseur de cet énumérateur est (position actuelle) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="166e4-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="166e4-117">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="166e4-117">Requirements</span></span>  
 <span data-ttu-id="166e4-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="166e4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="166e4-119">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="166e4-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="166e4-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="166e4-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="166e4-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="166e4-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="166e4-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="166e4-122">See also</span></span>

- [<span data-ttu-id="166e4-123">ICorProfilerThreadEnum, interface</span><span class="sxs-lookup"><span data-stu-id="166e4-123">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="166e4-124">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="166e4-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
