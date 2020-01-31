---
title: ICorProfilerInfo4::GetObjectSize2, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetObjectSize2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetObjectSize2
helpviewer_keywords:
- GetObjectSize2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetObjectSize2 method [.NET Framework profiling]
ms.assetid: 4a3e43ed-3ee3-4395-ab14-f78b903be13e
topic_type:
- apiref
ms.openlocfilehash: 441f7743ba01884592393ce9382348fbecaeaa9d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861877"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="8c6a4-102">ICorProfilerInfo4::GetObjectSize2, méthode</span><span class="sxs-lookup"><span data-stu-id="8c6a4-102">ICorProfilerInfo4::GetObjectSize2 Method</span></span>
<span data-ttu-id="8c6a4-103">Retourne la taille d’un objet spécifié.</span><span class="sxs-lookup"><span data-stu-id="8c6a4-103">Returns the size of a specified object.</span></span> <span data-ttu-id="8c6a4-104">Remplace la méthode [ICorProfilerInfo :: GetObjectSize,](icorprofilerinfo-getobjectsize-method.md) par la création de rapports sur la taille des objets qui sont plus grands que ce qui peut être exprimé dans un `ULONG`.</span><span class="sxs-lookup"><span data-stu-id="8c6a4-104">Replaces the [ICorProfilerInfo::GetObjectSize](icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c6a4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c6a4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c6a4-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="8c6a4-106">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="8c6a4-107">dans ID de l’objet.</span><span class="sxs-lookup"><span data-stu-id="8c6a4-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="8c6a4-108">à Pointeur vers la taille de l’objet, en octets.</span><span class="sxs-lookup"><span data-stu-id="8c6a4-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c6a4-109">Notes</span><span class="sxs-lookup"><span data-stu-id="8c6a4-109">Remarks</span></span>  
 <span data-ttu-id="8c6a4-110">Les différents objets des mêmes types ont souvent la même taille.</span><span class="sxs-lookup"><span data-stu-id="8c6a4-110">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="8c6a4-111">Toutefois, certains types, tels que les tableaux ou les chaînes, peuvent avoir une taille différente pour chaque objet.</span><span class="sxs-lookup"><span data-stu-id="8c6a4-111">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c6a4-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="8c6a4-112">Requirements</span></span>  
 <span data-ttu-id="8c6a4-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c6a4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c6a4-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8c6a4-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8c6a4-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c6a4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c6a4-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c6a4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c6a4-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c6a4-117">See also</span></span>

- [<span data-ttu-id="8c6a4-118">ICorProfilerInfo4, interface</span><span class="sxs-lookup"><span data-stu-id="8c6a4-118">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
