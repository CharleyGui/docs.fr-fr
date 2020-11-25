---
title: ICorProfilerObjectEnum::GetCount, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::GetCount
helpviewer_keywords:
- ICorProfilerObjectEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 166b0761-ed80-4ccd-9973-dc20e61bf8fa
topic_type:
- apiref
ms.openlocfilehash: a0777797870a707c0d0f00bc0b4c986448118231
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702392"
---
# <a name="icorprofilerobjectenumgetcount-method"></a><span data-ttu-id="27b96-102">ICorProfilerObjectEnum::GetCount, méthode</span><span class="sxs-lookup"><span data-stu-id="27b96-102">ICorProfilerObjectEnum::GetCount Method</span></span>

<span data-ttu-id="27b96-103">Obtient le nombre total d’objets figés dans la collection.</span><span class="sxs-lookup"><span data-stu-id="27b96-103">Gets the total number of frozen objects in the collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27b96-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27b96-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27b96-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="27b96-105">Parameters</span></span>  

 `pcelt`  
 <span data-ttu-id="27b96-106">à Pointeur vers le nombre d’objets figés dans la collection.</span><span class="sxs-lookup"><span data-stu-id="27b96-106">[out] A pointer to the number of frozen objects in the collection.</span></span>  
  
 <span data-ttu-id="27b96-107">Cette méthode retournera toujours zéro dans le .NET Framework version 3,5 Service Pack 1 (SP1) et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="27b96-107">This method will always return zero in the .NET Framework version 3.5 Service Pack 1 (SP1) and later versions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27b96-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="27b96-108">Requirements</span></span>  

 <span data-ttu-id="27b96-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27b96-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27b96-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="27b96-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="27b96-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27b96-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27b96-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27b96-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27b96-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27b96-113">See also</span></span>

- [<span data-ttu-id="27b96-114">ICorProfilerObjectEnum, interface</span><span class="sxs-lookup"><span data-stu-id="27b96-114">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
