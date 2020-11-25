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
ms.openlocfilehash: 960f8f1fe2315e068d599aa5a31e03f521b235a8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733865"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="7ae3f-102">ICorProfilerInfo4::GetObjectSize2, méthode</span><span class="sxs-lookup"><span data-stu-id="7ae3f-102">ICorProfilerInfo4::GetObjectSize2 Method</span></span>

<span data-ttu-id="7ae3f-103">Retourne la taille d’un objet spécifié.</span><span class="sxs-lookup"><span data-stu-id="7ae3f-103">Returns the size of a specified object.</span></span> <span data-ttu-id="7ae3f-104">Remplace la méthode [ICorProfilerInfo :: GetObjectSize,](icorprofilerinfo-getobjectsize-method.md) par la création de rapports de tailles d’objets plus grands que ce qui peut être exprimé dans un `ULONG` .</span><span class="sxs-lookup"><span data-stu-id="7ae3f-104">Replaces the [ICorProfilerInfo::GetObjectSize](icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ae3f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ae3f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ae3f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7ae3f-106">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="7ae3f-107">dans ID de l’objet.</span><span class="sxs-lookup"><span data-stu-id="7ae3f-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="7ae3f-108">à Pointeur vers la taille de l’objet, en octets.</span><span class="sxs-lookup"><span data-stu-id="7ae3f-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ae3f-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="7ae3f-109">Remarks</span></span>  

 <span data-ttu-id="7ae3f-110">Les différents objets des mêmes types ont souvent la même taille.</span><span class="sxs-lookup"><span data-stu-id="7ae3f-110">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="7ae3f-111">Toutefois, certains types, tels que les tableaux ou les chaînes, peuvent avoir une taille différente pour chaque objet.</span><span class="sxs-lookup"><span data-stu-id="7ae3f-111">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ae3f-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7ae3f-112">Requirements</span></span>  

 <span data-ttu-id="7ae3f-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ae3f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ae3f-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7ae3f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7ae3f-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ae3f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ae3f-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ae3f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ae3f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ae3f-117">See also</span></span>

- [<span data-ttu-id="7ae3f-118">ICorProfilerInfo4, interface</span><span class="sxs-lookup"><span data-stu-id="7ae3f-118">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
