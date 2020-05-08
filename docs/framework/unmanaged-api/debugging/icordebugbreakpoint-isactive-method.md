---
title: ICorDebugBreakpoint::IsActive, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint::IsActive
helpviewer_keywords:
- ICorDebugBreakpoint::IsActive method [.NET Framework debugging]
- IsActive method, ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: 06e583d6-d88a-4ff5-bb95-5c48618a461c
topic_type:
- apiref
ms.openlocfilehash: 64a30ca85a75ebd11918ff630daffbb85c97f6dc
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894722"
---
# <a name="icordebugbreakpointisactive-method"></a><span data-ttu-id="81b30-102">ICorDebugBreakpoint::IsActive, méthode</span><span class="sxs-lookup"><span data-stu-id="81b30-102">ICorDebugBreakpoint::IsActive Method</span></span>
<span data-ttu-id="81b30-103">Obtient une valeur qui indique si ce `ICorDebugBreakpoint` est actif.</span><span class="sxs-lookup"><span data-stu-id="81b30-103">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81b30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81b30-104">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81b30-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="81b30-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="81b30-106">à `true` si ce point d’arrêt est actif ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="81b30-106">[out] `true` if this breakpoint is active; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81b30-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="81b30-107">Requirements</span></span>  
 <span data-ttu-id="81b30-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81b30-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81b30-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81b30-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81b30-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81b30-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81b30-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81b30-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
