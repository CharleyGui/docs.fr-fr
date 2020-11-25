---
title: ICorProfilerFunctionEnum::Clone, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Clone
helpviewer_keywords:
- ICorProfilerFunctionEnum::Clone method [.NET Framework profiling]
- Clone method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0c3d4835-e111-4e82-af6d-53f140b8f2c9
topic_type:
- apiref
ms.openlocfilehash: 092c3b328887b7d36ead77c64d31310b614b616a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707527"
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="fe042-102">ICorProfilerFunctionEnum::Clone, méthode</span><span class="sxs-lookup"><span data-stu-id="fe042-102">ICorProfilerFunctionEnum::Clone Method</span></span>

<span data-ttu-id="fe042-103">Obtient un pointeur d’interface vers une copie de cette interface [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="fe042-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe042-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe042-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe042-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fe042-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="fe042-106">à Pointeur vers le pointeur d’interface qui, à son tour, pointe vers la copie de cette interface [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="fe042-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="fe042-107">La copie de l’énumérateur conserve son propre état d’énumération séparément de cet énumérateur.</span><span class="sxs-lookup"><span data-stu-id="fe042-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="fe042-108">Toutefois, la position initiale du curseur de la copie est la même que la position actuelle du curseur de cet énumérateur.</span><span class="sxs-lookup"><span data-stu-id="fe042-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe042-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fe042-109">Requirements</span></span>  

 <span data-ttu-id="fe042-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe042-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe042-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fe042-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fe042-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe042-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe042-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe042-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe042-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe042-114">See also</span></span>

- [<span data-ttu-id="fe042-115">ICorProfilerFunctionEnum, interface</span><span class="sxs-lookup"><span data-stu-id="fe042-115">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="fe042-116">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="fe042-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
