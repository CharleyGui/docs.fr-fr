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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 022d0d9c86e4b3b9924b8a486166d8ce3b71e42c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781188"
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="2e53d-102">ICorProfilerThreadEnum::Clone, méthode</span><span class="sxs-lookup"><span data-stu-id="2e53d-102">ICorProfilerThreadEnum::Clone Method</span></span>
<span data-ttu-id="2e53d-103">Obtient un pointeur d’interface vers une copie de ce [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="2e53d-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e53d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e53d-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e53d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2e53d-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="2e53d-106">[out] Un pointeur vers le pointeur d’interface, qui, à son tour, pointe vers la copie de ce [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="2e53d-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="2e53d-107">La copie de l’énumérateur maintient son propre état d’énumération séparément à partir de cet énumérateur.</span><span class="sxs-lookup"><span data-stu-id="2e53d-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="2e53d-108">Toutefois, la position du curseur initiale de la copie est identique à cette position actuelle du curseur de l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="2e53d-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e53d-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2e53d-109">Requirements</span></span>  
 <span data-ttu-id="2e53d-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e53d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e53d-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2e53d-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2e53d-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e53d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e53d-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e53d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e53d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e53d-114">See also</span></span>

- [<span data-ttu-id="2e53d-115">ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="2e53d-115">ICorProfilerThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="2e53d-116">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="2e53d-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
