---
title: ICorProfilerFunctionEnum::GetCount, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::GetCount
helpviewer_keywords:
- ICorProfilerFunctionEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 62ec65e3-3e9d-400b-ae61-d24b8963995b
topic_type:
- apiref
ms.openlocfilehash: 137b1da853535985b2fd383d52f0bcfc48f728ed
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503092"
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="3d7b9-102">ICorProfilerFunctionEnum::GetCount, méthode</span><span class="sxs-lookup"><span data-stu-id="3d7b9-102">ICorProfilerFunctionEnum::GetCount Method</span></span>
<span data-ttu-id="3d7b9-103">Obtient le nombre de fonctions qui ont été chargées par l'application ou chargées de force par le profileur.</span><span class="sxs-lookup"><span data-stu-id="3d7b9-103">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d7b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d7b9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d7b9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3d7b9-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="3d7b9-106">à Nombre de fonctions qui ont été chargées.</span><span class="sxs-lookup"><span data-stu-id="3d7b9-106">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d7b9-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3d7b9-107">Requirements</span></span>  
 <span data-ttu-id="3d7b9-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d7b9-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d7b9-109">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3d7b9-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3d7b9-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d7b9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d7b9-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d7b9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d7b9-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d7b9-112">See also</span></span>

- [<span data-ttu-id="3d7b9-113">ICorProfilerFunctionEnum, interface</span><span class="sxs-lookup"><span data-stu-id="3d7b9-113">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="3d7b9-114">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="3d7b9-114">Profiling Interfaces</span></span>](profiling-interfaces.md)
