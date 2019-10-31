---
title: ICorDebugChain::IsManaged, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugChain.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::IsManaged
helpviewer_keywords:
- ICorDebugChain::IsManaged method [.NET Framework debugging]
- IsManaged method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 17b389a0-1a4d-4e8a-8613-9bc1769930f9
topic_type:
- apiref
ms.openlocfilehash: 481f6d08e11a5f315c64b3d58df4ab291fa42e78
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123846"
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="95664-102">ICorDebugChain::IsManaged, méthode</span><span class="sxs-lookup"><span data-stu-id="95664-102">ICorDebugChain::IsManaged Method</span></span>
<span data-ttu-id="95664-103">Obtient une valeur qui indique si cette chaîne exécute du code managé.</span><span class="sxs-lookup"><span data-stu-id="95664-103">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95664-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95664-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95664-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="95664-105">Parameters</span></span>  
 `pManaged`  
 <span data-ttu-id="95664-106">[out] `true` si cette chaîne exécute du code managé ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="95664-106">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95664-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="95664-107">Requirements</span></span>  
 <span data-ttu-id="95664-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95664-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95664-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95664-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95664-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95664-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95664-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95664-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
