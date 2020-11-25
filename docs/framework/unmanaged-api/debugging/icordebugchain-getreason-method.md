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
ms.openlocfilehash: 58e40995012d98c1af6a41eb12d898c6b9b1d47b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719669"
---
# <a name="icordebugchaingetreason-method"></a><span data-ttu-id="0501a-102">ICorDebugChain::GetReason, méthode</span><span class="sxs-lookup"><span data-stu-id="0501a-102">ICorDebugChain::GetReason Method</span></span>

<span data-ttu-id="0501a-103">Obtient la raison pour le Genesis de cette chaîne d’appel.</span><span class="sxs-lookup"><span data-stu-id="0501a-103">Gets the reason for the genesis of this calling chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0501a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0501a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReason (  
    [out] CorDebugChainReason *pReason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0501a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0501a-105">Parameters</span></span>  

 `pReason`  
 <span data-ttu-id="0501a-106">à Pointeur vers une valeur (combinaison d’opérations de bits) de l’énumération CorDebugChainReason, qui indique la raison du Genesis de cette chaîne d’appel.</span><span class="sxs-lookup"><span data-stu-id="0501a-106">[out] A pointer to a value (a bitwise combination) of the CorDebugChainReason enumeration that indicates the reason for the genesis of this calling chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0501a-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0501a-107">Requirements</span></span>  

 <span data-ttu-id="0501a-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0501a-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0501a-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0501a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0501a-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0501a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0501a-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0501a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
