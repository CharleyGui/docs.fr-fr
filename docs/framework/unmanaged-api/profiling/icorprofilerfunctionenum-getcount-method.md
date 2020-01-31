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
ms.openlocfilehash: 8a21f1c0018e99b94a1b9910b6f266bdca84b7fe
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864555"
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="0d932-102">ICorProfilerFunctionEnum::GetCount, méthode</span><span class="sxs-lookup"><span data-stu-id="0d932-102">ICorProfilerFunctionEnum::GetCount Method</span></span>
<span data-ttu-id="0d932-103">Obtient le nombre de fonctions qui ont été chargées par l'application ou chargées de force par le profileur.</span><span class="sxs-lookup"><span data-stu-id="0d932-103">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d932-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d932-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d932-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="0d932-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="0d932-106">à Nombre de fonctions qui ont été chargées.</span><span class="sxs-lookup"><span data-stu-id="0d932-106">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d932-107">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="0d932-107">Requirements</span></span>  
 <span data-ttu-id="0d932-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d932-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d932-109">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0d932-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0d932-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d932-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d932-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d932-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d932-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d932-112">See also</span></span>

- [<span data-ttu-id="0d932-113">ICorProfilerFunctionEnum, interface</span><span class="sxs-lookup"><span data-stu-id="0d932-113">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="0d932-114">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="0d932-114">Profiling Interfaces</span></span>](profiling-interfaces.md)
