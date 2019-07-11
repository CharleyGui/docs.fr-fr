---
title: ICorProfilerObjectEnum::Skip, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Skip
helpviewer_keywords:
- ICorProfilerObjectEnum::Skip method [.NET Framework profiling]
- Skip method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: f8e498f8-f93a-4b82-bd22-55bdbf5e8d45
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5818cb8d7da7415feb61532799df5fa5a16fd3b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781218"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="78d13-102">ICorProfilerObjectEnum::Skip, méthode</span><span class="sxs-lookup"><span data-stu-id="78d13-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="78d13-103">Avance le curseur de cet énumérateur depuis sa position actuelle afin que le nombre spécifié d’éléments soit ignoré.</span><span class="sxs-lookup"><span data-stu-id="78d13-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78d13-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78d13-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78d13-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="78d13-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="78d13-106">[in] Le nombre d’éléments à ignorer.</span><span class="sxs-lookup"><span data-stu-id="78d13-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78d13-107">Notes</span><span class="sxs-lookup"><span data-stu-id="78d13-107">Remarks</span></span>  
 <span data-ttu-id="78d13-108">La nouvelle position du curseur de cet énumérateur est : (position actuelle) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="78d13-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78d13-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="78d13-109">Requirements</span></span>  
 <span data-ttu-id="78d13-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78d13-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78d13-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="78d13-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="78d13-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78d13-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78d13-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78d13-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78d13-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78d13-114">See also</span></span>

- [<span data-ttu-id="78d13-115">ICorProfilerObjectEnum, interface</span><span class="sxs-lookup"><span data-stu-id="78d13-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
