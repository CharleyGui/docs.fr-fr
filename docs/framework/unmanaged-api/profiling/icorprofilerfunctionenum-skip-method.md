---
title: ICorProfilerFunctionEnum::Skip, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
- ICorProfilerFunctionEnum::Skip method [.NET Framework profiling]
ms.assetid: 051465b9-e479-494a-804b-c880323b4cbe
topic_type:
- apiref
ms.openlocfilehash: d2a0bff0d3d93ab8542699cffd3d0ecc032246ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448199"
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="85a9e-102">ICorProfilerFunctionEnum::Skip, méthode</span><span class="sxs-lookup"><span data-stu-id="85a9e-102">ICorProfilerFunctionEnum::Skip Method</span></span>
<span data-ttu-id="85a9e-103">Fait avancer le curseur de l'énumérateur depuis sa position actuelle de manière à ignorer le nombre spécifié d'éléments.</span><span class="sxs-lookup"><span data-stu-id="85a9e-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85a9e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85a9e-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85a9e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="85a9e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="85a9e-106">dans Nombre d’éléments à ignorer.</span><span class="sxs-lookup"><span data-stu-id="85a9e-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85a9e-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="85a9e-107">Return Value</span></span>  
 <span data-ttu-id="85a9e-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="85a9e-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="85a9e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="85a9e-109">HRESULT</span></span>|<span data-ttu-id="85a9e-110">Description</span><span class="sxs-lookup"><span data-stu-id="85a9e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="85a9e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="85a9e-111">S_OK</span></span>|<span data-ttu-id="85a9e-112">`celt` éléments ont été ignorés.</span><span class="sxs-lookup"><span data-stu-id="85a9e-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="85a9e-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="85a9e-113">S_FALSE</span></span>|<span data-ttu-id="85a9e-114">Moins de `celt` éléments ont été ignorés, ce qui indique qu’il n’y a plus d’éléments.</span><span class="sxs-lookup"><span data-stu-id="85a9e-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85a9e-115">Notes</span><span class="sxs-lookup"><span data-stu-id="85a9e-115">Remarks</span></span>  
 <span data-ttu-id="85a9e-116">La nouvelle position du curseur de cet énumérateur est (position actuelle) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="85a9e-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85a9e-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="85a9e-117">Requirements</span></span>  
 <span data-ttu-id="85a9e-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85a9e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85a9e-119">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="85a9e-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="85a9e-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85a9e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85a9e-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85a9e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85a9e-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85a9e-122">See also</span></span>

- [<span data-ttu-id="85a9e-123">ICorProfilerFunctionEnum, interface</span><span class="sxs-lookup"><span data-stu-id="85a9e-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="85a9e-124">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="85a9e-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
