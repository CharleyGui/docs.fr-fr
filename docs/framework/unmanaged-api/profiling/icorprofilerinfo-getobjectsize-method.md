---
title: ICorProfilerInfo::GetObjectSize, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetObjectSize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type:
- apiref
ms.openlocfilehash: de6d46897f3d3266bf708528efd712ca7db8ea4a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438826"
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="b12ec-102">ICorProfilerInfo::GetObjectSize, méthode</span><span class="sxs-lookup"><span data-stu-id="b12ec-102">ICorProfilerInfo::GetObjectSize Method</span></span>
<span data-ttu-id="b12ec-103">Obtient la taille d’un objet spécifié.</span><span class="sxs-lookup"><span data-stu-id="b12ec-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b12ec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b12ec-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b12ec-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b12ec-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="b12ec-106">dans ID de l’objet.</span><span class="sxs-lookup"><span data-stu-id="b12ec-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="b12ec-107">à Pointeur vers la taille de l’objet, en octets.</span><span class="sxs-lookup"><span data-stu-id="b12ec-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b12ec-108">Notes</span><span class="sxs-lookup"><span data-stu-id="b12ec-108">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b12ec-109">Cette méthode est obsolète.</span><span class="sxs-lookup"><span data-stu-id="b12ec-109">This method is obsolete.</span></span> <span data-ttu-id="b12ec-110">Elle retourne COR_E_OVERFLOW pour les objets supérieurs à 4 Go sur les plateformes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="b12ec-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="b12ec-111">Utilisez la méthode [ICorProfilerInfo4 :: getobjectsize2,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="b12ec-111">Use the  [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="b12ec-112">Les différents objets des mêmes types ont souvent la même taille.</span><span class="sxs-lookup"><span data-stu-id="b12ec-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="b12ec-113">Toutefois, certains types, tels que les tableaux ou les chaînes, peuvent avoir une taille différente pour chaque objet.</span><span class="sxs-lookup"><span data-stu-id="b12ec-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="b12ec-114">La taille retournée par la méthode `GetObjectSize` n’inclut aucun remplissage d’alignement qui peut apparaître après que l’objet se trouve sur le tas garbage collection.</span><span class="sxs-lookup"><span data-stu-id="b12ec-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="b12ec-115">Si vous utilisez la méthode `GetObjectSize` pour passer d’un objet à l’objet sur le tas garbage collection, ajoutez manuellement le remplissage de l’alignement, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="b12ec-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
- <span data-ttu-id="b12ec-116">Sur Windows 32 bits, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 et COR_PRF_GC_GEN_2 utilisent l’alignement sur 4 octets, et COR_PRF_GC_LARGE_OBJECT_HEAP utilise l’alignement sur 8 octets.</span><span class="sxs-lookup"><span data-stu-id="b12ec-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
- <span data-ttu-id="b12ec-117">Sur Windows 64 bits, l’alignement est toujours de 8 octets.</span><span class="sxs-lookup"><span data-stu-id="b12ec-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b12ec-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b12ec-118">Requirements</span></span>  
 <span data-ttu-id="b12ec-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b12ec-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b12ec-120">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b12ec-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b12ec-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b12ec-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b12ec-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b12ec-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b12ec-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b12ec-123">See also</span></span>

- [<span data-ttu-id="b12ec-124">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="b12ec-124">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
