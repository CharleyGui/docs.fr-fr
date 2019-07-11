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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 120c31b61734cfb4cb0048489632bc0848a9430b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782177"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="779d3-102">ICorProfilerInfo3::GetAppDomainsContainingModule, méthode</span><span class="sxs-lookup"><span data-stu-id="779d3-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="779d3-103">Obtient les identificateurs des domaines d'application dans lesquels le module donné a été chargé.</span><span class="sxs-lookup"><span data-stu-id="779d3-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="779d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="779d3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="779d3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="779d3-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="779d3-106">[in] ID du module chargé.</span><span class="sxs-lookup"><span data-stu-id="779d3-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="779d3-107">[in] Taille du tableau `appDomainIds`.</span><span class="sxs-lookup"><span data-stu-id="779d3-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="779d3-108">[out] Pointeur vers le nombre total d'éléments retournés.</span><span class="sxs-lookup"><span data-stu-id="779d3-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="779d3-109">[out] Tableau de valeurs d'ID de domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="779d3-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="779d3-110">Notes</span><span class="sxs-lookup"><span data-stu-id="779d3-110">Remarks</span></span>  
 <span data-ttu-id="779d3-111">Cette méthode utilise des mémoires tampons allouées par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="779d3-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="779d3-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="779d3-112">Requirements</span></span>  
 <span data-ttu-id="779d3-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="779d3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="779d3-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="779d3-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="779d3-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="779d3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="779d3-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="779d3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="779d3-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="779d3-117">See also</span></span>

- [<span data-ttu-id="779d3-118">ICorProfilerFunctionEnum, interface</span><span class="sxs-lookup"><span data-stu-id="779d3-118">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="779d3-119">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="779d3-119">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="779d3-120">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="779d3-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="779d3-121">Profilage</span><span class="sxs-lookup"><span data-stu-id="779d3-121">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
