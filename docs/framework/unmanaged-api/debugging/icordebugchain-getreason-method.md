---
title: ICorDebugChain::GetReason, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- GetReason
helpviewer_keywords:
- GetReason method [.NET Framework debugging]
- ICorDebugChain::GetReason method [.NET Framework debugging]
ms.assetid: 9f9f62b9-113a-4a98-8f9b-b593cef27b03
topic_type:
- apiref
ms.openlocfilehash: e51ee2e4d44af547c82a21a782121976d07118c5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124717"
---
# <a name="icordebugchaingetreason-method"></a><span data-ttu-id="7eb5a-102">ICorDebugChain::GetReason, méthode</span><span class="sxs-lookup"><span data-stu-id="7eb5a-102">ICorDebugChain::GetReason Method</span></span>
<span data-ttu-id="7eb5a-103">Gets the reason for the genesis of this calling chain.</span><span class="sxs-lookup"><span data-stu-id="7eb5a-103">Gets the reason for the genesis of this calling chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eb5a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7eb5a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReason (  
    [out] CorDebugChainReason *pReason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7eb5a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7eb5a-105">Parameters</span></span>  
 `pReason`  
 <span data-ttu-id="7eb5a-106">[out] A pointer to a value (a bitwise combination) of the CorDebugChainReason enumeration that indicates the reason for the genesis of this calling chain.</span><span class="sxs-lookup"><span data-stu-id="7eb5a-106">[out] A pointer to a value (a bitwise combination) of the CorDebugChainReason enumeration that indicates the reason for the genesis of this calling chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7eb5a-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="7eb5a-107">Requirements</span></span>  
 <span data-ttu-id="7eb5a-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7eb5a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7eb5a-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7eb5a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7eb5a-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7eb5a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7eb5a-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7eb5a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
