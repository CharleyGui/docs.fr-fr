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
ms.openlocfilehash: 604ecb2122cce6e24f0e5168fa286a523d8bb4f7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495071"
---
# <a name="icorprofilermoduleenumgetcount-method"></a><span data-ttu-id="d4da5-102">ICorProfilerModuleEnum::GetCount, méthode</span><span class="sxs-lookup"><span data-stu-id="d4da5-102">ICorProfilerModuleEnum::GetCount Method</span></span>
<span data-ttu-id="d4da5-103">Obtient le nombre de modules managés chargés dans l'application.</span><span class="sxs-lookup"><span data-stu-id="d4da5-103">Gets the number of managed modules that were loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4da5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4da5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4da5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d4da5-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="d4da5-106">à Nombre de modules Runtime dans la collection.</span><span class="sxs-lookup"><span data-stu-id="d4da5-106">[out] The number of runtime modules in the collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4da5-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d4da5-107">Requirements</span></span>  
 <span data-ttu-id="d4da5-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4da5-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4da5-109">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d4da5-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d4da5-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4da5-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4da5-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4da5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4da5-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4da5-112">See also</span></span>

- [<span data-ttu-id="d4da5-113">ICorProfilerModuleEnum, interface</span><span class="sxs-lookup"><span data-stu-id="d4da5-113">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="d4da5-114">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="d4da5-114">Profiling Interfaces</span></span>](profiling-interfaces.md)
