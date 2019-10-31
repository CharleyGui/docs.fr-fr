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
ms.openlocfilehash: 86fa44b609b4b89cfaa28f0bfa7bbdce6217623f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122857"
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="d2754-102">ICorDebugAssemblyEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="d2754-102">ICorDebugAssemblyEnum::Next Method</span></span>
<span data-ttu-id="d2754-103">Obtient le nombre spécifié d’assemblys à partir de la collection, en commençant à la position actuelle du curseur.</span><span class="sxs-lookup"><span data-stu-id="d2754-103">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2754-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2754-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2754-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d2754-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="d2754-106">dans Nombre d’assemblys à récupérer.</span><span class="sxs-lookup"><span data-stu-id="d2754-106">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="d2754-107">à Tableau de pointeurs, chacun pointant vers un objet ICorDebugAssembly qui représente un assembly.</span><span class="sxs-lookup"><span data-stu-id="d2754-107">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="d2754-108">à Pointeur vers le nombre d’assemblys réellement retournés.</span><span class="sxs-lookup"><span data-stu-id="d2754-108">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="d2754-109">Cette valeur peut être null si `celt` est un.</span><span class="sxs-lookup"><span data-stu-id="d2754-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2754-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="d2754-110">Requirements</span></span>  
 <span data-ttu-id="d2754-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2754-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2754-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2754-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2754-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2754-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2754-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2754-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
