---
title: ICorDebugChain::GetCallee, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
ms.openlocfilehash: ba9a4e32216fd6fad285397bfc48fbc54f602b88
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894648"
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="d399c-102">ICorDebugChain::GetCallee, méthode</span><span class="sxs-lookup"><span data-stu-id="d399c-102">ICorDebugChain::GetCallee Method</span></span>
<span data-ttu-id="d399c-103">Obtient la chaîne qui a été appelée par cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="d399c-103">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d399c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d399c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d399c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d399c-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="d399c-106">à Pointeur vers l’adresse d’un objet ICorDebugChain qui représente la chaîne appelée.</span><span class="sxs-lookup"><span data-stu-id="d399c-106">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="d399c-107">Si cette chaîne est en cours d’exécution (autrement dit, si cette chaîne n’attend pas une chaîne appelée à retourner), `ppChain` aura la valeur null.</span><span class="sxs-lookup"><span data-stu-id="d399c-107">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d399c-108">Notes </span><span class="sxs-lookup"><span data-stu-id="d399c-108">Remarks</span></span>  
 <span data-ttu-id="d399c-109">Cette chaîne attend que la chaîne appelée retourne avant de reprendre l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d399c-109">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="d399c-110">La chaîne appelée peut se trouver sur un autre thread dans le cas d’appels marshalés inter-threads.</span><span class="sxs-lookup"><span data-stu-id="d399c-110">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d399c-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d399c-111">Requirements</span></span>  
 <span data-ttu-id="d399c-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d399c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d399c-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d399c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d399c-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d399c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d399c-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d399c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
