---
title: ICorProfilerInfo3::GetAppDomainsContainingModule, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetAppDomainsContainingModule Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetAppDomainsContainingModule
helpviewer_keywords:
- GetAppDomainsContainingModule method [.NET Framework profiling]
- ICorProfilerInfo3::GetAppDomainsContainingModule method [.NET Framework profiling]
ms.assetid: 603b3881-ea94-4dca-95cd-91eebac873a0
topic_type:
- apiref
ms.openlocfilehash: 56221c6b3ac40595e999f2a2a3739f023441c46d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862408"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="2a5f2-102">ICorProfilerInfo3::GetAppDomainsContainingModule, méthode</span><span class="sxs-lookup"><span data-stu-id="2a5f2-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="2a5f2-103">Obtient les identificateurs des domaines d'application dans lesquels le module donné a été chargé.</span><span class="sxs-lookup"><span data-stu-id="2a5f2-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a5f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a5f2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a5f2-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="2a5f2-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="2a5f2-106">[in] ID du module chargé.</span><span class="sxs-lookup"><span data-stu-id="2a5f2-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="2a5f2-107">[in] Taille du tableau `appDomainIds`.</span><span class="sxs-lookup"><span data-stu-id="2a5f2-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="2a5f2-108">[out] Pointeur vers le nombre total d'éléments retournés.</span><span class="sxs-lookup"><span data-stu-id="2a5f2-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="2a5f2-109">[out] Tableau de valeurs d'ID de domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="2a5f2-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a5f2-110">Notes</span><span class="sxs-lookup"><span data-stu-id="2a5f2-110">Remarks</span></span>  
 <span data-ttu-id="2a5f2-111">Cette méthode utilise des mémoires tampons allouées par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="2a5f2-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a5f2-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="2a5f2-112">Requirements</span></span>  
 <span data-ttu-id="2a5f2-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a5f2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a5f2-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2a5f2-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2a5f2-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a5f2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a5f2-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a5f2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a5f2-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a5f2-117">See also</span></span>

- [<span data-ttu-id="2a5f2-118">ICorProfilerFunctionEnum, interface</span><span class="sxs-lookup"><span data-stu-id="2a5f2-118">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="2a5f2-119">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="2a5f2-119">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="2a5f2-120">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="2a5f2-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="2a5f2-121">Profilage</span><span class="sxs-lookup"><span data-stu-id="2a5f2-121">Profiling</span></span>](index.md)
