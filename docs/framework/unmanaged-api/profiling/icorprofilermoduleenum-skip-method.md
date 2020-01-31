---
title: ICorProfilerModuleEnum::Skip, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Skip method [.NET Framework profiling]
ms.assetid: 8dc29c6a-e2ba-41d8-a1e0-0fdd21421e0b
topic_type:
- apiref
ms.openlocfilehash: fb7a2a6d8bac7e9a67a5275694fc07e0f1d469e1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861331"
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="de50d-102">ICorProfilerModuleEnum::Skip, méthode</span><span class="sxs-lookup"><span data-stu-id="de50d-102">ICorProfilerModuleEnum::Skip Method</span></span>
<span data-ttu-id="de50d-103">Fait avancer le curseur de l'énumérateur depuis sa position actuelle de manière à ignorer le nombre spécifié d'éléments.</span><span class="sxs-lookup"><span data-stu-id="de50d-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de50d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de50d-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de50d-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="de50d-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="de50d-106">dans Nombre d’éléments à ignorer.</span><span class="sxs-lookup"><span data-stu-id="de50d-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de50d-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="de50d-107">Return Value</span></span>  
 <span data-ttu-id="de50d-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="de50d-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="de50d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="de50d-109">HRESULT</span></span>|<span data-ttu-id="de50d-110">Description</span><span class="sxs-lookup"><span data-stu-id="de50d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="de50d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="de50d-111">S_OK</span></span>|<span data-ttu-id="de50d-112">`celt` éléments ont été ignorés.</span><span class="sxs-lookup"><span data-stu-id="de50d-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="de50d-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="de50d-113">S_FALSE</span></span>|<span data-ttu-id="de50d-114">Moins de `celt` éléments ont été ignorés, ce qui indique qu’il n’y a plus d’éléments.</span><span class="sxs-lookup"><span data-stu-id="de50d-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de50d-115">Notes</span><span class="sxs-lookup"><span data-stu-id="de50d-115">Remarks</span></span>  
 <span data-ttu-id="de50d-116">La nouvelle position du curseur de cet énumérateur est (position actuelle) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="de50d-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de50d-117">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="de50d-117">Requirements</span></span>  
 <span data-ttu-id="de50d-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de50d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de50d-119">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="de50d-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="de50d-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de50d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de50d-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de50d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de50d-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de50d-122">See also</span></span>

- [<span data-ttu-id="de50d-123">ICorProfilerModuleEnum, interface</span><span class="sxs-lookup"><span data-stu-id="de50d-123">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="de50d-124">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="de50d-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
