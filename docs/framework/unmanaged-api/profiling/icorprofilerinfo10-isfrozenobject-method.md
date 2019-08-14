---
title: ICorProfilerInfo10::IsFrozenObject
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.IsFrozenObject
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 05f25d8fb61a16f41a82a987529017db6a687740
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973989"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="00f0a-102">ICorProfilerInfo10:: IsFrozenObject, méthode</span><span class="sxs-lookup"><span data-stu-id="00f0a-102">ICorProfilerInfo10::IsFrozenObject Method</span></span>
  
 <span data-ttu-id="00f0a-103">À partir d’un ObjectID, détermine si l’objet se trouve dans un segment en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="00f0a-103">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>   
  
## <a name="syntax"></a><span data-ttu-id="00f0a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00f0a-104">Syntax</span></span>  
  
```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```  
  
#### <a name="parameters"></a><span data-ttu-id="00f0a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="00f0a-105">Parameters</span></span>  
 
 `objectId` \
 <span data-ttu-id="00f0a-106">dans Objet à examiner.</span><span class="sxs-lookup"><span data-stu-id="00f0a-106">[in] The object to examine.</span></span>

 `pbFrozen` \
 <span data-ttu-id="00f0a-107">à Valeur `BOOL` qui indique si l’objet se trouve dans un segment en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="00f0a-107">[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="00f0a-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="00f0a-108">Requirements</span></span>  
 <span data-ttu-id="00f0a-109">**Plateformes** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="00f0a-109">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="00f0a-110">**En-tête :** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="00f0a-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="00f0a-111">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00f0a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00f0a-112">**Versions de .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00f0a-112">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="00f0a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00f0a-113">See also</span></span>
- [<span data-ttu-id="00f0a-114">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="00f0a-114">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)

