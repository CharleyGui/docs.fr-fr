---
title: ICorProfilerInfo2::GetBoxClassLayout, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetBoxClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetBoxClassLayout
helpviewer_keywords:
- GetBoxClassLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetBoxClassLayout method [.NET Framework profiling]
ms.assetid: 624672b5-1189-488a-85d2-3e12b49617c1
topic_type:
- apiref
ms.openlocfilehash: ff39a688132112e88438bc192d7c1ab61f169400
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727157"
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="5a85b-102">ICorProfilerInfo2::GetBoxClassLayout, méthode</span><span class="sxs-lookup"><span data-stu-id="5a85b-102">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>

<span data-ttu-id="5a85b-103">Obtient des informations sur l’emplacement du type valeur spécifié lorsqu’il est boxed.</span><span class="sxs-lookup"><span data-stu-id="5a85b-103">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a85b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a85b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a85b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5a85b-105">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="5a85b-106">dans ID de la classe qui décrit le type valeur boxed.</span><span class="sxs-lookup"><span data-stu-id="5a85b-106">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="5a85b-107">à Entier qui est le décalage par rapport au pointeur d’ID d’objet boxed du type valeur.</span><span class="sxs-lookup"><span data-stu-id="5a85b-107">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a85b-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="5a85b-108">Remarks</span></span>  

 <span data-ttu-id="5a85b-109">La `pBufferOffset` valeur est l’emplacement du type de valeur dans une zone.</span><span class="sxs-lookup"><span data-stu-id="5a85b-109">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="5a85b-110">Une fois que `pBufferOffset` est appliqué à un objet boxed, la disposition de classe du type valeur peut être utilisée pour interpréter la valeur de l’objet.</span><span class="sxs-lookup"><span data-stu-id="5a85b-110">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a85b-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5a85b-111">Requirements</span></span>  

 <span data-ttu-id="5a85b-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a85b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a85b-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5a85b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5a85b-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a85b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a85b-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a85b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a85b-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a85b-116">See also</span></span>

- [<span data-ttu-id="5a85b-117">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="5a85b-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="5a85b-118">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="5a85b-118">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
