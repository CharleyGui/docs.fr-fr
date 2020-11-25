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
ms.openlocfilehash: 326e170fa98c9e365f9b68bedb585f547ca207ed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727703"
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="6a4ba-102">ICorDebugChain::GetPrevious, méthode</span><span class="sxs-lookup"><span data-stu-id="6a4ba-102">ICorDebugChain::GetPrevious Method</span></span>

<span data-ttu-id="6a4ba-103">Obtient la chaîne précédente des frames pour le thread.</span><span class="sxs-lookup"><span data-stu-id="6a4ba-103">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a4ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a4ba-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a4ba-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6a4ba-105">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="6a4ba-106">à Pointeur vers l’adresse d’un objet ICorDebugChain qui représente la chaîne précédente des frames pour ce thread.</span><span class="sxs-lookup"><span data-stu-id="6a4ba-106">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="6a4ba-107">Si cette chaîne est la première chaîne, `ppChain` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="6a4ba-107">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a4ba-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6a4ba-108">Requirements</span></span>  

 <span data-ttu-id="6a4ba-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a4ba-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a4ba-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a4ba-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a4ba-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a4ba-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a4ba-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a4ba-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
