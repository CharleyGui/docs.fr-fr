---
title: ICorProfilerFunctionControl::SetILFunctionBody, méthode
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
ms.openlocfilehash: a6b24fd59a183a4a59b117663772417d55cc67db
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503136"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="3b48b-102">ICorProfilerFunctionControl::SetILFunctionBody, méthode</span><span class="sxs-lookup"><span data-stu-id="3b48b-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="3b48b-103">Remplace le corps Common Intermediate Language (CIL) de la méthode.</span><span class="sxs-lookup"><span data-stu-id="3b48b-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b48b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b48b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b48b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3b48b-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="3b48b-106">[in] La taille totale du nouveau CIL, y compris l'en-tête et toutes structures intervenant après le corps.</span><span class="sxs-lookup"><span data-stu-id="3b48b-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="3b48b-107">[in] Un pointeur vers le nouvel en-tête de CIL.</span><span class="sxs-lookup"><span data-stu-id="3b48b-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b48b-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="3b48b-108">Return Value</span></span>  
 <span data-ttu-id="3b48b-109">Cette méthode retourne les HRESULT spécifiques suivants.</span><span class="sxs-lookup"><span data-stu-id="3b48b-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="3b48b-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3b48b-110">HRESULT</span></span>|<span data-ttu-id="3b48b-111">Description</span><span class="sxs-lookup"><span data-stu-id="3b48b-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3b48b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="3b48b-112">S_OK</span></span>|<span data-ttu-id="3b48b-113">Le remplacement a été correctement effectué.</span><span class="sxs-lookup"><span data-stu-id="3b48b-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b48b-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="3b48b-114">Remarks</span></span>  
 <span data-ttu-id="3b48b-115">Contrairement à la méthode [ICorProfilerInfo :: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) , la `SetILFunctionBody` méthode gère la mémoire requise pour le nouveau corps cil.</span><span class="sxs-lookup"><span data-stu-id="3b48b-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="3b48b-116">Cela signifie que le corps CIL fourni par le profileur ne doit pas être alloué à l’aide de l’interface [IMethodMalloc](imethodmalloc-interface.md) ou alloué dans une plage particulière.</span><span class="sxs-lookup"><span data-stu-id="3b48b-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="3b48b-117">Il peut être alloué sur n'importe quel segment de mémoire.</span><span class="sxs-lookup"><span data-stu-id="3b48b-117">It can be allocated on any heap.</span></span> <span data-ttu-id="3b48b-118">Le profileur peut libérer la mémoire utilisée pour son corps CIL après `SetILFunctionBody` retourne.</span><span class="sxs-lookup"><span data-stu-id="3b48b-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b48b-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3b48b-119">Requirements</span></span>  
 <span data-ttu-id="3b48b-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b48b-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b48b-121">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3b48b-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3b48b-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b48b-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b48b-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b48b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b48b-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b48b-124">See also</span></span>

- [<span data-ttu-id="3b48b-125">ICorProfilerFunctionControl, interface</span><span class="sxs-lookup"><span data-stu-id="3b48b-125">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)
