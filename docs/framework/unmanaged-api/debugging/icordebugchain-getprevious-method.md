---
title: ICorDebugChain::GetPrevious, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetPrevious
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetPrevious
helpviewer_keywords:
- ICorDebugChain::GetPrevious method [.NET Framework debugging]
- GetPrevious method [.NET Framework debugging]
ms.assetid: 58eed4c8-d80c-4c6a-a875-967a90dd926c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31c795c2fbbfdc45b6e1aac6684f730f55fc106a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746421"
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="c062d-102">ICorDebugChain::GetPrevious, méthode</span><span class="sxs-lookup"><span data-stu-id="c062d-102">ICorDebugChain::GetPrevious Method</span></span>
<span data-ttu-id="c062d-103">Obtient la chaîne précédente de frames pour le thread.</span><span class="sxs-lookup"><span data-stu-id="c062d-103">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c062d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c062d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c062d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c062d-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="c062d-106">[out] Pointeur vers l’adresse d’un objet ICorDebugChain qui représente la chaîne précédente de frames pour ce thread.</span><span class="sxs-lookup"><span data-stu-id="c062d-106">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="c062d-107">Si cette chaîne est la première chaîne, `ppChain` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="c062d-107">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c062d-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c062d-108">Requirements</span></span>  
 <span data-ttu-id="c062d-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c062d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c062d-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c062d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c062d-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c062d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c062d-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c062d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
