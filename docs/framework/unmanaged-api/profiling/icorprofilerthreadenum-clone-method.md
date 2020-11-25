---
title: ICorProfilerThreadEnum::Clone, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Clone method [.NET Framework profiling]
ms.assetid: 5a278bc9-88e2-4c69-b035-9d550dd77081
topic_type:
- apiref
ms.openlocfilehash: de2584b56701f4cffb6a108a5872641ec40e5762
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702522"
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="a9e18-102">ICorProfilerThreadEnum::Clone, méthode</span><span class="sxs-lookup"><span data-stu-id="a9e18-102">ICorProfilerThreadEnum::Clone Method</span></span>

<span data-ttu-id="a9e18-103">Obtient un pointeur d’interface vers une copie de cette interface [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a9e18-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9e18-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9e18-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9e18-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a9e18-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="a9e18-106">à Pointeur vers le pointeur d’interface qui, à son tour, pointe vers la copie de cette interface [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a9e18-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="a9e18-107">La copie de l’énumérateur conserve son propre état d’énumération séparément de cet énumérateur.</span><span class="sxs-lookup"><span data-stu-id="a9e18-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="a9e18-108">Toutefois, la position initiale du curseur de la copie est identique à celle de la position actuelle du curseur de l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="a9e18-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9e18-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a9e18-109">Requirements</span></span>  

 <span data-ttu-id="a9e18-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9e18-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9e18-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a9e18-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a9e18-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9e18-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9e18-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9e18-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9e18-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9e18-114">See also</span></span>

- [<span data-ttu-id="a9e18-115">ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="a9e18-115">ICorProfilerThreadEnum</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="a9e18-116">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="a9e18-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
