---
title: ICorDebugChain::GetCaller, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCaller
helpviewer_keywords:
- ICorDebugChain::GetCaller method [.NET Framework debugging]
- GetCaller method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: d0b8ab4b-d7d2-4fa0-945f-3d2b87e7e991
topic_type:
- apiref
ms.openlocfilehash: 5a07550d44857526e8ab4ded9f1827ef12e3bba4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192137"
---
# <a name="icordebugchaingetcaller-method"></a><span data-ttu-id="cbfb0-102">ICorDebugChain::GetCaller, méthode</span><span class="sxs-lookup"><span data-stu-id="cbfb0-102">ICorDebugChain::GetCaller Method</span></span>
<span data-ttu-id="cbfb0-103">Obtient la chaîne qui a appelé cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="cbfb0-103">Gets the chain that called this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbfb0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cbfb0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbfb0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cbfb0-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="cbfb0-106">à Pointeur vers l’adresse d’un objet ICorDebugChain qui représente la chaîne appelante.</span><span class="sxs-lookup"><span data-stu-id="cbfb0-106">[out] A pointer to the address of an ICorDebugChain object that represents the calling chain.</span></span>  
  
 <span data-ttu-id="cbfb0-107">Si cette chaîne a été appelée spontanément (comme c’est le cas si cette chaîne ou le débogueur a initialisé la pile des appels), `ppChain` aura la valeur null.</span><span class="sxs-lookup"><span data-stu-id="cbfb0-107">If this chain was spontaneously called (as would be the case if this chain or the debugger initialized the call stack), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbfb0-108">Notes</span><span class="sxs-lookup"><span data-stu-id="cbfb0-108">Remarks</span></span>  
 <span data-ttu-id="cbfb0-109">La chaîne appelante peut se trouver sur un thread différent, si l’appel a été marshalé entre les threads.</span><span class="sxs-lookup"><span data-stu-id="cbfb0-109">The calling chain may be on a different thread, if the call was marshaled across threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbfb0-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="cbfb0-110">Requirements</span></span>  
 <span data-ttu-id="cbfb0-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbfb0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbfb0-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cbfb0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cbfb0-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbfb0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbfb0-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbfb0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
