---
title: ICorProfilerModuleEnum::Clone, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Clone method [.NET Framework profiling]
ms.assetid: 7dec7e36-8d88-416d-b437-abf98b76c1df
topic_type:
- apiref
ms.openlocfilehash: a6b36883ec0914426b4f4c937390c1622faead25
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868289"
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="7d64a-102">ICorProfilerModuleEnum::Clone, méthode</span><span class="sxs-lookup"><span data-stu-id="7d64a-102">ICorProfilerModuleEnum::Clone Method</span></span>
<span data-ttu-id="7d64a-103">Obtient un pointeur d’interface vers une copie de cette interface [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="7d64a-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d64a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d64a-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d64a-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="7d64a-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="7d64a-106">à Pointeur vers le pointeur d’interface qui pointe à son tour vers la copie de cette interface [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="7d64a-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="7d64a-107">La copie de l’énumérateur conserve son propre état d’énumération séparément de cet énumérateur.</span><span class="sxs-lookup"><span data-stu-id="7d64a-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="7d64a-108">Toutefois, la position initiale du curseur de la copie est la même que la position actuelle du curseur de cet énumérateur.</span><span class="sxs-lookup"><span data-stu-id="7d64a-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d64a-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="7d64a-109">Requirements</span></span>  
 <span data-ttu-id="7d64a-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d64a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d64a-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7d64a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7d64a-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d64a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d64a-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d64a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d64a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d64a-114">See also</span></span>

- [<span data-ttu-id="7d64a-115">ICorProfilerModuleEnum, interface</span><span class="sxs-lookup"><span data-stu-id="7d64a-115">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="7d64a-116">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="7d64a-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
