---
title: ICorProfilerInfo::GetClassFromObject, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromObject
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromObject
helpviewer_keywords:
- GetClassFromObject method [.NET Framework profiling]
- ICorProfilerInfo::GetClassFromObject method [.NET Framework profiling]
ms.assetid: b97493fb-713e-49d5-a73e-5688b2ad0700
topic_type:
- apiref
ms.openlocfilehash: 460162f0fbc9993635d1bce0c5b130358ced4fa7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448151"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="45e7c-102">ICorProfilerInfo::GetClassFromObject, méthode</span><span class="sxs-lookup"><span data-stu-id="45e7c-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="45e7c-103">Gets the `ClassID` of an object, given its `ObjectID`.</span><span class="sxs-lookup"><span data-stu-id="45e7c-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45e7c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45e7c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45e7c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="45e7c-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="45e7c-106">[in] The ID of the object for which to get the `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="45e7c-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="45e7c-107">[out] A pointer to the returned `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="45e7c-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45e7c-108">Notes</span><span class="sxs-lookup"><span data-stu-id="45e7c-108">Remarks</span></span>  
 <span data-ttu-id="45e7c-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span><span class="sxs-lookup"><span data-stu-id="45e7c-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45e7c-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="45e7c-110">Requirements</span></span>  
 <span data-ttu-id="45e7c-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45e7c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45e7c-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="45e7c-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="45e7c-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45e7c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45e7c-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45e7c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45e7c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45e7c-115">See also</span></span>

- [<span data-ttu-id="45e7c-116">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="45e7c-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
