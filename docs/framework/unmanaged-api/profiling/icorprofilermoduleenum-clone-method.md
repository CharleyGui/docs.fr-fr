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
ms.openlocfilehash: ccbb051ac30fb25199ce12c16fff74bb0b9944fa
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495084"
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="41b26-102">ICorProfilerModuleEnum::Clone, méthode</span><span class="sxs-lookup"><span data-stu-id="41b26-102">ICorProfilerModuleEnum::Clone Method</span></span>
<span data-ttu-id="41b26-103">Obtient un pointeur d’interface vers une copie de cette interface [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="41b26-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41b26-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41b26-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41b26-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="41b26-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="41b26-106">à Pointeur vers le pointeur d’interface qui pointe à son tour vers la copie de cette interface [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="41b26-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="41b26-107">La copie de l’énumérateur conserve son propre état d’énumération séparément de cet énumérateur.</span><span class="sxs-lookup"><span data-stu-id="41b26-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="41b26-108">Toutefois, la position initiale du curseur de la copie est la même que la position actuelle du curseur de cet énumérateur.</span><span class="sxs-lookup"><span data-stu-id="41b26-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41b26-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="41b26-109">Requirements</span></span>  
 <span data-ttu-id="41b26-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41b26-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41b26-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="41b26-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="41b26-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41b26-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41b26-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41b26-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41b26-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41b26-114">See also</span></span>

- [<span data-ttu-id="41b26-115">ICorProfilerModuleEnum, interface</span><span class="sxs-lookup"><span data-stu-id="41b26-115">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="41b26-116">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="41b26-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
