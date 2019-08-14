---
title: ICorProfilerInfo9::GetNativeCodeStartAddresses
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: f5c7f11a322e4cf3ed38608e0f380dd632bc8fb6
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973809"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a><span data-ttu-id="d89c5-102">ICorProfilerInfo9:: GetNativeCodeStartAddresses, méthode</span><span class="sxs-lookup"><span data-stu-id="d89c5-102">ICorProfilerInfo9::GetNativeCodeStartAddresses Method</span></span>
  
 <span data-ttu-id="d89c5-103">Étant donné une functionId et rejitId, énumère l’adresse de début du code natif de toutes les versions JIT de ce code qui existent actuellement.</span><span class="sxs-lookup"><span data-stu-id="d89c5-103">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span>   
  
## <a name="syntax"></a><span data-ttu-id="d89c5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d89c5-104">Syntax</span></span>  
  
```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```  
  
#### <a name="parameters"></a><span data-ttu-id="d89c5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d89c5-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d89c5-106">dans ID de la fonction dont les adresses de début de code natif doivent être retournées.</span><span class="sxs-lookup"><span data-stu-id="d89c5-106">[in] The ID of the function whose native code start addresses should be returned.</span></span>  
  
 `reJitId`  
 <span data-ttu-id="d89c5-107">[in] Identité de la fonction recompilée juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="d89c5-107">[in] The identity of the JIT-recompiled function.</span></span> 
  
 `cCodeStartAddresses` \
 <span data-ttu-id="d89c5-108">[in] Taille maximale du tableau `codeStartAddresses`.</span><span class="sxs-lookup"><span data-stu-id="d89c5-108">[in] The maximum size of the `codeStartAddresses` array.</span></span>

 `pcCodeStartAddresses` \
 <span data-ttu-id="d89c5-109">à Nombre d’adresses disponibles.</span><span class="sxs-lookup"><span data-stu-id="d89c5-109">[out] The number of available addresses.</span></span>

 `codeStartAddresses` \
 <span data-ttu-id="d89c5-110">à Tableau de `UINT_PTR`, chacun d’entre eux étant l’adresse de début d’un corps natif pour la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d89c5-110">[out] An array of `UINT_PTR`, each one of which is the start address for a native body for the specified function.</span></span> 

## <a name="remarks"></a><span data-ttu-id="d89c5-111">Notes</span><span class="sxs-lookup"><span data-stu-id="d89c5-111">Remarks</span></span>  
 <span data-ttu-id="d89c5-112">Lorsque la compilation à plusieurs niveaux est activée, une fonction peut avoir plusieurs corps de code natif.</span><span class="sxs-lookup"><span data-stu-id="d89c5-112">When tiered compilation is enabled, a function may have more than one native code body.</span></span> 

## <a name="requirements"></a><span data-ttu-id="d89c5-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d89c5-113">Requirements</span></span>  
 <span data-ttu-id="d89c5-114">**Plateformes** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="d89c5-114">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="d89c5-115">**En-tête :** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d89c5-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d89c5-116">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d89c5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d89c5-117">**Versions de .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d89c5-117">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="d89c5-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d89c5-118">See also</span></span>
- [<span data-ttu-id="d89c5-119">Interface ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="d89c5-119">ICorProfilerInfo9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)

