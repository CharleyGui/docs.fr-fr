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
ms.openlocfilehash: 155354b335caf83c466c8d9d6711f36c7efc9298
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894814"
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="7c748-102">ICorDebugAssemblyEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="7c748-102">ICorDebugAssemblyEnum::Next Method</span></span>
<span data-ttu-id="7c748-103">Obtient le nombre spécifié d’assemblys à partir de la collection, en commençant à la position actuelle du curseur.</span><span class="sxs-lookup"><span data-stu-id="7c748-103">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c748-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c748-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c748-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7c748-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7c748-106">dans Nombre d’assemblys à récupérer.</span><span class="sxs-lookup"><span data-stu-id="7c748-106">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="7c748-107">à Tableau de pointeurs, chacun pointant vers un objet ICorDebugAssembly qui représente un assembly.</span><span class="sxs-lookup"><span data-stu-id="7c748-107">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="7c748-108">à Pointeur vers le nombre d’assemblys réellement retournés.</span><span class="sxs-lookup"><span data-stu-id="7c748-108">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="7c748-109">Cette valeur peut être null si `celt` est un.</span><span class="sxs-lookup"><span data-stu-id="7c748-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c748-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7c748-110">Requirements</span></span>  
 <span data-ttu-id="7c748-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c748-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c748-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c748-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c748-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c748-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c748-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c748-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
