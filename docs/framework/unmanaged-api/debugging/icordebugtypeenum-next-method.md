---
title: ICorDebugTypeEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugTypeEnum::Next
helpviewer_keywords:
- ICorDebugTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugTypeEnum interface [.NET Framework debugging]
ms.assetid: d0fdeba3-c195-4ece-8caf-79b1f40025d2
topic_type:
- apiref
ms.openlocfilehash: fc205e347fc39fd486d9b8a3fb256a5d29a980a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110067"
---
# <a name="icordebugtypeenumnext-method"></a><span data-ttu-id="9db2a-102">ICorDebugTypeEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="9db2a-102">ICorDebugTypeEnum::Next Method</span></span>
<span data-ttu-id="9db2a-103">Obtient le nombre d’instances « ICorDebugType » spécifiées par `celt` à partir de l’énumération, en démarrant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="9db2a-103">Gets the number of "ICorDebugType" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9db2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9db2a-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugType *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9db2a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9db2a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="9db2a-106">dans Nombre d’instances de `ICorDebugType` à récupérer.</span><span class="sxs-lookup"><span data-stu-id="9db2a-106">[in] The number of `ICorDebugType` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="9db2a-107">à Tableau de pointeurs, chacun pointant vers un objet `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="9db2a-107">[out] An array of pointers, each of which points to an `ICorDebugType` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9db2a-108">à Pointeur vers le nombre d’instances `ICorDebugType` réellement retournées.</span><span class="sxs-lookup"><span data-stu-id="9db2a-108">[out] Pointer to the number of `ICorDebugType` instances actually returned.</span></span> <span data-ttu-id="9db2a-109">Cette valeur peut être null si `celt` est un.</span><span class="sxs-lookup"><span data-stu-id="9db2a-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9db2a-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="9db2a-110">Requirements</span></span>  
 <span data-ttu-id="9db2a-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9db2a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9db2a-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9db2a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9db2a-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9db2a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9db2a-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9db2a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9db2a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9db2a-115">See also</span></span>
