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
ms.openlocfilehash: cfe884c3d26e7a52618eb9945f0af9a167132f05
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724375"
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="f88d3-102">ICorDebugChain::IsManaged, méthode</span><span class="sxs-lookup"><span data-stu-id="f88d3-102">ICorDebugChain::IsManaged Method</span></span>

<span data-ttu-id="f88d3-103">Obtient une valeur qui indique si cette chaîne exécute du code managé.</span><span class="sxs-lookup"><span data-stu-id="f88d3-103">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f88d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f88d3-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f88d3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f88d3-105">Parameters</span></span>  

 `pManaged`  
 <span data-ttu-id="f88d3-106">[out] `true` Si cette chaîne exécute du code managé ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="f88d3-106">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f88d3-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f88d3-107">Requirements</span></span>  

 <span data-ttu-id="f88d3-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f88d3-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f88d3-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f88d3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f88d3-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f88d3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f88d3-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f88d3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
