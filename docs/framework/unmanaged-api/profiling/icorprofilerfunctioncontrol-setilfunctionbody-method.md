---
title: Méthode ICorProfilerFunctionControl::SetILFunctionBody
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type:
- apiref
ms.openlocfilehash: bebc0cf6ac7912ea3a6641e0c729b759e865dac3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864659"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="e2c4d-102">Méthode ICorProfilerFunctionControl::SetILFunctionBody</span><span class="sxs-lookup"><span data-stu-id="e2c4d-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="e2c4d-103">Remplace le corps Common Intermediate Language (CIL) de la méthode.</span><span class="sxs-lookup"><span data-stu-id="e2c4d-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2c4d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2c4d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2c4d-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="e2c4d-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="e2c4d-106">[in] La taille totale du nouveau CIL, y compris l'en-tête et toutes structures intervenant après le corps.</span><span class="sxs-lookup"><span data-stu-id="e2c4d-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="e2c4d-107">[in] Un pointeur vers le nouvel en-tête de CIL.</span><span class="sxs-lookup"><span data-stu-id="e2c4d-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2c4d-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e2c4d-108">Return Value</span></span>  
 <span data-ttu-id="e2c4d-109">Cette méthode retourne les HRESULT spécifiques suivants.</span><span class="sxs-lookup"><span data-stu-id="e2c4d-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="e2c4d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e2c4d-110">HRESULT</span></span>|<span data-ttu-id="e2c4d-111">Description</span><span class="sxs-lookup"><span data-stu-id="e2c4d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e2c4d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e2c4d-112">S_OK</span></span>|<span data-ttu-id="e2c4d-113">Le remplacement a été correctement effectué.</span><span class="sxs-lookup"><span data-stu-id="e2c4d-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2c4d-114">Notes</span><span class="sxs-lookup"><span data-stu-id="e2c4d-114">Remarks</span></span>  
 <span data-ttu-id="e2c4d-115">Contrairement à la méthode [ICorProfilerInfo :: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) , la méthode `SetILFunctionBody` gère la mémoire requise pour le nouveau corps cil.</span><span class="sxs-lookup"><span data-stu-id="e2c4d-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="e2c4d-116">Cela signifie que le corps CIL fourni par le profileur ne doit pas être alloué à l’aide de l’interface [IMethodMalloc](imethodmalloc-interface.md) ou alloué dans une plage particulière.</span><span class="sxs-lookup"><span data-stu-id="e2c4d-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="e2c4d-117">Il peut être alloué sur n'importe quel segment de mémoire.</span><span class="sxs-lookup"><span data-stu-id="e2c4d-117">It can be allocated on any heap.</span></span> <span data-ttu-id="e2c4d-118">Le profileur peut libérer la mémoire utilisée pour son corps CIL après le retour de `SetILFunctionBody`.</span><span class="sxs-lookup"><span data-stu-id="e2c4d-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2c4d-119">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="e2c4d-119">Requirements</span></span>  
 <span data-ttu-id="e2c4d-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2c4d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2c4d-121">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e2c4d-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e2c4d-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2c4d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2c4d-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2c4d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2c4d-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2c4d-124">See also</span></span>

- [<span data-ttu-id="e2c4d-125">ICorProfilerFunctionControl, interface</span><span class="sxs-lookup"><span data-stu-id="e2c4d-125">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)
