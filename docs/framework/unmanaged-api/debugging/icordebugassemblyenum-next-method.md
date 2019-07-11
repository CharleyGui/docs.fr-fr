---
title: ICorDebugAssemblyEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAssemblyEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssemblyEnum::Next method
helpviewer_keywords:
- ICorDebugAssemblyEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAssemblyEnum interface [.NET Framework debugging]
ms.assetid: b3e7d0c2-3baa-4ef8-8e3f-b865cf252940
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 00adc852a0940766cdd4188ffa5d6be2b472e51f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744879"
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="b8bb0-102">ICorDebugAssemblyEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="b8bb0-102">ICorDebugAssemblyEnum::Next Method</span></span>
<span data-ttu-id="b8bb0-103">Obtient le nombre spécifié d’assemblys à partir de la collection, en commençant à la position actuelle du curseur.</span><span class="sxs-lookup"><span data-stu-id="b8bb0-103">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8bb0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8bb0-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8bb0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b8bb0-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b8bb0-106">[in] Le nombre d’assemblys à récupérer.</span><span class="sxs-lookup"><span data-stu-id="b8bb0-106">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="b8bb0-107">[out] Tableau de pointeurs, chacun pointant vers un objet ICorDebugAssembly qui représente un assembly.</span><span class="sxs-lookup"><span data-stu-id="b8bb0-107">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b8bb0-108">[out] Pointeur vers le nombre d’assemblys réellement retournés.</span><span class="sxs-lookup"><span data-stu-id="b8bb0-108">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="b8bb0-109">Cette valeur peut être null si `celt` fait partie.</span><span class="sxs-lookup"><span data-stu-id="b8bb0-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8bb0-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b8bb0-110">Requirements</span></span>  
 <span data-ttu-id="b8bb0-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8bb0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8bb0-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8bb0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8bb0-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8bb0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8bb0-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8bb0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
