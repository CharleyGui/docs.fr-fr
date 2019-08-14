---
title: ICorProfilerInfo8::GetFunctionFromIP3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetFunctionFromIP3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: f3c0a3525c87fbf39199c15a6619ff4a0d2acc42
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973849"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a><span data-ttu-id="07171-102">ICorProfilerInfo8:: GetFunctionFromIP3, méthode</span><span class="sxs-lookup"><span data-stu-id="07171-102">ICorProfilerInfo8::GetFunctionFromIP3 Method</span></span>
  
  <span data-ttu-id="07171-103">Mappe un pointeur d’instruction de code managé à une FunctionID.</span><span class="sxs-lookup"><span data-stu-id="07171-103">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="07171-104">Cette méthode fonctionne pour les méthodes dynamiques et non dynamiques.</span><span class="sxs-lookup"><span data-stu-id="07171-104">This method works for both dynamic and non-dynamic methods.</span></span>    
  
## <a name="syntax"></a><span data-ttu-id="07171-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07171-105">Syntax</span></span>  
  
```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```  
  
#### <a name="parameters"></a><span data-ttu-id="07171-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="07171-106">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="07171-107">dans Pointeur d’instruction dans du code managé.</span><span class="sxs-lookup"><span data-stu-id="07171-107">[in] The instruction pointer in managed code.</span></span>  

 `pFunctionId`  
 <span data-ttu-id="07171-108">à ID de la fonction.</span><span class="sxs-lookup"><span data-stu-id="07171-108">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="07171-109">à Identité de la version recompilée juste-à-temps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="07171-109">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07171-110">Notes</span><span class="sxs-lookup"><span data-stu-id="07171-110">Remarks</span></span>  
 <span data-ttu-id="07171-111">Cette méthode fonctionne pour les méthodes dynamiques et non dynamiques.</span><span class="sxs-lookup"><span data-stu-id="07171-111">This method works for both dynamic and non-dynamic methods.</span></span> <span data-ttu-id="07171-112">Il s’agit d’un sur-ensemble de [getfunctionfromip2,](icorprofilerinfo4-getfunctionfromip2-method.md), qui fonctionne uniquement pour les fonctions avec métadonnées.</span><span class="sxs-lookup"><span data-stu-id="07171-112">It is a superset of [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md), which only works for functions with metadata.</span></span>
  

## <a name="requirements"></a><span data-ttu-id="07171-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="07171-113">Requirements</span></span>  
 <span data-ttu-id="07171-114">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07171-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07171-115">**En-tête :** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="07171-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="07171-116">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07171-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07171-117">**Versions de .NET Framework:** [! INCLURE[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span><span class="sxs-lookup"><span data-stu-id="07171-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07171-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07171-118">See also</span></span>
- [<span data-ttu-id="07171-119">Interface ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="07171-119">ICorProfilerInfo8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)

