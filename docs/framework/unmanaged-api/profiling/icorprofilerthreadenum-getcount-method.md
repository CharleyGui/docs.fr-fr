---
title: ICorProfilerThreadEnum::GetCount, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::GetCount
helpviewer_keywords:
- ICorProfilerThreadEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: d6dbdc4a-6115-455d-a3f3-704a81d3646b
topic_type:
- apiref
ms.openlocfilehash: 4bc2ea083d5278afc9278d388f57b048f7682ca6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494395"
---
# <a name="icorprofilerthreadenumgetcount-method"></a><span data-ttu-id="50068-102">ICorProfilerThreadEnum::GetCount, méthode</span><span class="sxs-lookup"><span data-stu-id="50068-102">ICorProfilerThreadEnum::GetCount Method</span></span>
<span data-ttu-id="50068-103">Obtient le nombre de threads utilisés par l'application.</span><span class="sxs-lookup"><span data-stu-id="50068-103">Gets the number of threads that are used by the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50068-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50068-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (    [out] ULONG * pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50068-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="50068-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="50068-106">à Nombre de threads utilisés par l’application.</span><span class="sxs-lookup"><span data-stu-id="50068-106">[out] The number of threads used by the application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50068-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="50068-107">Requirements</span></span>  
 <span data-ttu-id="50068-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50068-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50068-109">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="50068-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="50068-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50068-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50068-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50068-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50068-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50068-112">See also</span></span>

- [<span data-ttu-id="50068-113">ICorProfilerThreadEnum, interface</span><span class="sxs-lookup"><span data-stu-id="50068-113">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="50068-114">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="50068-114">Profiling Interfaces</span></span>](profiling-interfaces.md)
