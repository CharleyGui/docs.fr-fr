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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c79f3b3b976b83eb99f8aa26d38a1fe316de471a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745000"
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="68469-102">ICorDebugChain::GetActiveFrame, méthode</span><span class="sxs-lookup"><span data-stu-id="68469-102">ICorDebugChain::GetActiveFrame Method</span></span>
<span data-ttu-id="68469-103">Obtient l’actif (autrement dit, plus récente) frame sur la chaîne.</span><span class="sxs-lookup"><span data-stu-id="68469-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68469-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68469-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68469-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="68469-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="68469-106">[out] Un pointeur vers l’adresse d’un objet ICorDebugFrame qui représente l’actif (autrement dit, plus récente) frame sur la chaîne.</span><span class="sxs-lookup"><span data-stu-id="68469-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68469-107">Notes</span><span class="sxs-lookup"><span data-stu-id="68469-107">Remarks</span></span>  
 <span data-ttu-id="68469-108">Si aucun frame de pile managée est disponible, `ppFrame` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="68469-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="68469-109">Si le frame actif n’est pas disponible, l’appel réussira et `ppFrame` sera null.</span><span class="sxs-lookup"><span data-stu-id="68469-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="68469-110">Cadres active ne sera pas disponibles pour les chaînes lancées en raison de CHAIN_ENTER_UNMANAGED et pour certaines chaînes lancées en raison de CHAIN_CLASS_INIT.</span><span class="sxs-lookup"><span data-stu-id="68469-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="68469-111">Consultez l’énumération CorDebugChainReason.</span><span class="sxs-lookup"><span data-stu-id="68469-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68469-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="68469-112">Requirements</span></span>  
 <span data-ttu-id="68469-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68469-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68469-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68469-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68469-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68469-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68469-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68469-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
