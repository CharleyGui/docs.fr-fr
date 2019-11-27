---
title: ICorProfilerModuleEnum::GetCount, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::GetCount
helpviewer_keywords:
- ICorProfilerModuleEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: f0a4a5e0-4689-474b-b0f4-37ca0639c918
topic_type:
- apiref
ms.openlocfilehash: 9aaf1a282435e3f52b2c2d8f3d17254b877e61cc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442769"
---
# <a name="icorprofilermoduleenumgetcount-method"></a><span data-ttu-id="a1b0f-102">ICorProfilerModuleEnum::GetCount, méthode</span><span class="sxs-lookup"><span data-stu-id="a1b0f-102">ICorProfilerModuleEnum::GetCount Method</span></span>
<span data-ttu-id="a1b0f-103">Obtient le nombre de modules managés chargés dans l'application.</span><span class="sxs-lookup"><span data-stu-id="a1b0f-103">Gets the number of managed modules that were loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1b0f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1b0f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1b0f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a1b0f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a1b0f-106">à Nombre de modules Runtime dans la collection.</span><span class="sxs-lookup"><span data-stu-id="a1b0f-106">[out] The number of runtime modules in the collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1b0f-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a1b0f-107">Requirements</span></span>  
 <span data-ttu-id="a1b0f-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1b0f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1b0f-109">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a1b0f-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a1b0f-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1b0f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1b0f-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1b0f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1b0f-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1b0f-112">See also</span></span>

- [<span data-ttu-id="a1b0f-113">ICorProfilerModuleEnum, interface</span><span class="sxs-lookup"><span data-stu-id="a1b0f-113">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="a1b0f-114">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="a1b0f-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
