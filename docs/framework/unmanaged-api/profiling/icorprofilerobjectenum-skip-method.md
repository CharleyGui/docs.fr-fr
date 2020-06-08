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
ms.openlocfilehash: 2248f99b76aaabff4bd3dc78b6e777a95692bb9c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494518"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="c4250-102">ICorProfilerObjectEnum::Skip, méthode</span><span class="sxs-lookup"><span data-stu-id="c4250-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="c4250-103">Avance le curseur de cet énumérateur de sa position actuelle afin que le nombre d’éléments spécifié soit ignoré.</span><span class="sxs-lookup"><span data-stu-id="c4250-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4250-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4250-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4250-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c4250-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c4250-106">dans Nombre d’éléments à ignorer.</span><span class="sxs-lookup"><span data-stu-id="c4250-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4250-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="c4250-107">Remarks</span></span>  
 <span data-ttu-id="c4250-108">La nouvelle position du curseur de cet énumérateur est : (position actuelle) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="c4250-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4250-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c4250-109">Requirements</span></span>  
 <span data-ttu-id="c4250-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4250-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4250-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c4250-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c4250-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4250-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4250-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4250-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4250-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4250-114">See also</span></span>

- [<span data-ttu-id="c4250-115">ICorProfilerObjectEnum, interface</span><span class="sxs-lookup"><span data-stu-id="c4250-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
