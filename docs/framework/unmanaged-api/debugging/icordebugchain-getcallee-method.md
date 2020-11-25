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
ms.openlocfilehash: a28da34cd3080826f346b8957aa6ba38258b924f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730121"
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="88de1-102">ICorDebugChain::GetCallee, méthode</span><span class="sxs-lookup"><span data-stu-id="88de1-102">ICorDebugChain::GetCallee Method</span></span>

<span data-ttu-id="88de1-103">Obtient la chaîne qui a été appelée par cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="88de1-103">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88de1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88de1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88de1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="88de1-105">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="88de1-106">à Pointeur vers l’adresse d’un objet ICorDebugChain qui représente la chaîne appelée.</span><span class="sxs-lookup"><span data-stu-id="88de1-106">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="88de1-107">Si cette chaîne est en cours d’exécution (autrement dit, si cette chaîne n’attend pas une chaîne appelée à retourner), `ppChain` aura la valeur null.</span><span class="sxs-lookup"><span data-stu-id="88de1-107">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88de1-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="88de1-108">Remarks</span></span>  

 <span data-ttu-id="88de1-109">Cette chaîne attend que la chaîne appelée retourne avant de reprendre l’exécution.</span><span class="sxs-lookup"><span data-stu-id="88de1-109">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="88de1-110">La chaîne appelée peut se trouver sur un autre thread dans le cas d’appels marshalés inter-threads.</span><span class="sxs-lookup"><span data-stu-id="88de1-110">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88de1-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="88de1-111">Requirements</span></span>  

 <span data-ttu-id="88de1-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88de1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88de1-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88de1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88de1-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88de1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88de1-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88de1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
