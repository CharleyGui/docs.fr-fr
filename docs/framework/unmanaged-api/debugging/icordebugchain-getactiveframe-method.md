---
title: ICorDebugChain::GetActiveFrame, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type:
- apiref
ms.openlocfilehash: 2f67188539d5ad5523c255fbc663e990e1b8245f
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894680"
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="726d6-102">ICorDebugChain::GetActiveFrame, méthode</span><span class="sxs-lookup"><span data-stu-id="726d6-102">ICorDebugChain::GetActiveFrame Method</span></span>
<span data-ttu-id="726d6-103">Obtient le frame actif (c’est-à-dire le plus récent) de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="726d6-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="726d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="726d6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="726d6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="726d6-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="726d6-106">à Pointeur vers l’adresse d’un objet ICorDebugFrame qui représente le frame actif (autrement dit, le plus récent) de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="726d6-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="726d6-107">Notes </span><span class="sxs-lookup"><span data-stu-id="726d6-107">Remarks</span></span>  
 <span data-ttu-id="726d6-108">Si aucun frame de pile managé n’est `ppFrame` disponible, a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="726d6-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="726d6-109">Si le frame actif n’est pas disponible, l’appel échoue et `ppFrame` est null.</span><span class="sxs-lookup"><span data-stu-id="726d6-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="726d6-110">Les frames actifs ne sont pas disponibles pour les chaînes lancées en raison de CHAIN_ENTER_UNMANAGED, et pour certaines chaînes lancées en raison de CHAIN_CLASS_INIT.</span><span class="sxs-lookup"><span data-stu-id="726d6-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="726d6-111">Consultez l’énumération CorDebugChainReason,.</span><span class="sxs-lookup"><span data-stu-id="726d6-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="726d6-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="726d6-112">Requirements</span></span>  
 <span data-ttu-id="726d6-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="726d6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="726d6-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="726d6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="726d6-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="726d6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="726d6-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="726d6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
