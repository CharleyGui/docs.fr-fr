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
ms.openlocfilehash: 5a7edc6045969861679d1b80c0563e99f48932cf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680246"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="629b1-102">ICorProfilerInfo::GetClassFromObject, méthode</span><span class="sxs-lookup"><span data-stu-id="629b1-102">ICorProfilerInfo::GetClassFromObject Method</span></span>

<span data-ttu-id="629b1-103">Obtient le `ClassID` d’un objet, en fonction de son `ObjectID` .</span><span class="sxs-lookup"><span data-stu-id="629b1-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="629b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="629b1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="629b1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="629b1-105">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="629b1-106">dans ID de l’objet pour lequel obtenir le `ClassID` .</span><span class="sxs-lookup"><span data-stu-id="629b1-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="629b1-107">à Pointeur vers le retourné `ClassID` .</span><span class="sxs-lookup"><span data-stu-id="629b1-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="629b1-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="629b1-108">Remarks</span></span>  

 <span data-ttu-id="629b1-109">Une valeur null `pClassId` indique que `objectId` a un type qui décharge.</span><span class="sxs-lookup"><span data-stu-id="629b1-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="629b1-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="629b1-110">Requirements</span></span>  

 <span data-ttu-id="629b1-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="629b1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="629b1-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="629b1-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="629b1-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="629b1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="629b1-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="629b1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="629b1-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="629b1-115">See also</span></span>

- [<span data-ttu-id="629b1-116">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="629b1-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
