---
title: ICorDebugChain::GetThread, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugChain interface [.NET Framework debugging]
- ICorDebugChain::GetThread method [.NET Framework debugging]
ms.assetid: b3390319-6366-418c-ba80-b552ac4dfc1e
topic_type:
- apiref
ms.openlocfilehash: ad220289b45078130a0a41e67373fd3384ae9682
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724414"
---
# <a name="icordebugchaingetthread-method"></a><span data-ttu-id="0f960-102">ICorDebugChain::GetThread, méthode</span><span class="sxs-lookup"><span data-stu-id="0f960-102">ICorDebugChain::GetThread Method</span></span>

<span data-ttu-id="0f960-103">Obtient le thread physique dont fait partie cette chaîne d’appel.</span><span class="sxs-lookup"><span data-stu-id="0f960-103">Gets the physical thread this call chain is part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f960-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f960-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread    **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f960-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0f960-105">Parameters</span></span>  

 `ppThread`  
 <span data-ttu-id="0f960-106">à Pointeur vers un objet ICorDebugThread qui représente le thread physique dont fait partie cette chaîne d’appel.</span><span class="sxs-lookup"><span data-stu-id="0f960-106">[out] A pointer to an ICorDebugThread object that represents the physical thread this call chain is part of.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f960-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0f960-107">Requirements</span></span>  

 <span data-ttu-id="0f960-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f960-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f960-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0f960-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f960-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f960-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f960-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f960-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
