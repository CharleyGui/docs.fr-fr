---
title: ICorProfilerInfo10::EnumerateObjectReferences
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.EnumerateObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 4b13659f7c9909e9795caee1eace8da8092c5b9a
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974029"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="82696-102">ICorProfilerInfo10:: EnumerateObjectReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="82696-102">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>
  
 <span data-ttu-id="82696-103">À partir d’un ObjectID, callback et ClientData:, énumère chaque référence d’objet (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="82696-103">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>   
  
## <a name="syntax"></a><span data-ttu-id="82696-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82696-104">Syntax</span></span>  
  
```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```  
  
#### <a name="parameters"></a><span data-ttu-id="82696-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="82696-105">Parameters</span></span>  

 `objectId` \
 <span data-ttu-id="82696-106">dans Objet sur lequel énumérer les références.</span><span class="sxs-lookup"><span data-stu-id="82696-106">[in] The object to enumerate references on.</span></span>

 `callback` \
 <span data-ttu-id="82696-107">dans Fonction qui sera appelée avec les références pour l’objet.</span><span class="sxs-lookup"><span data-stu-id="82696-107">[in] The function that will be called with the references for the object.</span></span>

 `clientData` \
 <span data-ttu-id="82696-108">dans Données fournies par le profileur à passer `callback` à la fonction.</span><span class="sxs-lookup"><span data-stu-id="82696-108">[in] Profiler-provided data to pass to the `callback` function.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="82696-109">Notes</span><span class="sxs-lookup"><span data-stu-id="82696-109">Remarks</span></span>  
 <span data-ttu-id="82696-110">La `EnumerateObjectReferences` méthode est similaire à [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), à ceci près qu’elle parcourt les références à la demande pour le profileur au lieu de préallouer un tableau pour stocker les références.</span><span class="sxs-lookup"><span data-stu-id="82696-110">The `EnumerateObjectReferences` method is similar to [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>  

## <a name="requirements"></a><span data-ttu-id="82696-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="82696-111">Requirements</span></span>  
 <span data-ttu-id="82696-112">**Plateformes** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="82696-112">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="82696-113">**En-tête :** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="82696-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="82696-114">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82696-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82696-115">**Versions de .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82696-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="82696-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82696-116">See also</span></span>
- [<span data-ttu-id="82696-117">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="82696-117">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)

