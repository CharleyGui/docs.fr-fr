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
ms.openlocfilehash: f6e2cfe47bdd212e39549544b06bf5b11033a956
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429885"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="3733a-102">Méthode ICorProfilerFunctionControl::SetILFunctionBody</span><span class="sxs-lookup"><span data-stu-id="3733a-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="3733a-103">Remplace le corps Common Intermediate Language (CIL) de la méthode.</span><span class="sxs-lookup"><span data-stu-id="3733a-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3733a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3733a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3733a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3733a-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="3733a-106">[in] La taille totale du nouveau CIL, y compris l'en-tête et toutes structures intervenant après le corps.</span><span class="sxs-lookup"><span data-stu-id="3733a-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="3733a-107">[in] Un pointeur vers le nouvel en-tête de CIL.</span><span class="sxs-lookup"><span data-stu-id="3733a-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3733a-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3733a-108">Return Value</span></span>  
 <span data-ttu-id="3733a-109">Cette méthode retourne les HRESULT spécifiques suivants.</span><span class="sxs-lookup"><span data-stu-id="3733a-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="3733a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3733a-110">HRESULT</span></span>|<span data-ttu-id="3733a-111">Description</span><span class="sxs-lookup"><span data-stu-id="3733a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3733a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="3733a-112">S_OK</span></span>|<span data-ttu-id="3733a-113">Le remplacement a été correctement effectué.</span><span class="sxs-lookup"><span data-stu-id="3733a-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3733a-114">Notes</span><span class="sxs-lookup"><span data-stu-id="3733a-114">Remarks</span></span>  
 <span data-ttu-id="3733a-115">Contrairement à la méthode [ICorProfilerInfo :: SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) , la méthode `SetILFunctionBody` gère la mémoire requise pour le nouveau corps cil.</span><span class="sxs-lookup"><span data-stu-id="3733a-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="3733a-116">Cela signifie que le corps CIL fourni par le profileur ne doit pas être alloué à l’aide de l’interface [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) ou alloué dans une plage particulière.</span><span class="sxs-lookup"><span data-stu-id="3733a-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="3733a-117">Il peut être alloué sur n'importe quel segment de mémoire.</span><span class="sxs-lookup"><span data-stu-id="3733a-117">It can be allocated on any heap.</span></span> <span data-ttu-id="3733a-118">Le profileur peut libérer la mémoire utilisée pour son corps CIL après le retour de `SetILFunctionBody`.</span><span class="sxs-lookup"><span data-stu-id="3733a-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3733a-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3733a-119">Requirements</span></span>  
 <span data-ttu-id="3733a-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3733a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3733a-121">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3733a-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3733a-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3733a-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3733a-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3733a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3733a-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3733a-124">See also</span></span>

- [<span data-ttu-id="3733a-125">ICorProfilerFunctionControl, interface</span><span class="sxs-lookup"><span data-stu-id="3733a-125">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
