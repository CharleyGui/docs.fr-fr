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
ms.openlocfilehash: 096489fcdc9d604e003386501c22967b45ba6d7f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861097"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="f8d79-102">ICorProfilerObjectEnum::Skip, méthode</span><span class="sxs-lookup"><span data-stu-id="f8d79-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="f8d79-103">Avance le curseur de cet énumérateur de sa position actuelle afin que le nombre d’éléments spécifié soit ignoré.</span><span class="sxs-lookup"><span data-stu-id="f8d79-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8d79-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8d79-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8d79-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="f8d79-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f8d79-106">dans Nombre d’éléments à ignorer.</span><span class="sxs-lookup"><span data-stu-id="f8d79-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8d79-107">Notes</span><span class="sxs-lookup"><span data-stu-id="f8d79-107">Remarks</span></span>  
 <span data-ttu-id="f8d79-108">La nouvelle position du curseur de cet énumérateur est : (position actuelle) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="f8d79-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8d79-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="f8d79-109">Requirements</span></span>  
 <span data-ttu-id="f8d79-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8d79-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8d79-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f8d79-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f8d79-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8d79-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8d79-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8d79-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8d79-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8d79-114">See also</span></span>

- [<span data-ttu-id="f8d79-115">ICorProfilerObjectEnum, interface</span><span class="sxs-lookup"><span data-stu-id="f8d79-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
