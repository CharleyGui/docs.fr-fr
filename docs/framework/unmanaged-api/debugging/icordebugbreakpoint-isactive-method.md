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
ms.openlocfilehash: 8df4e1df7836f340bb04fc47d1ca55e0fb7c9f0e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122770"
---
# <a name="icordebugbreakpointisactive-method"></a><span data-ttu-id="cb32b-102">ICorDebugBreakpoint::IsActive, méthode</span><span class="sxs-lookup"><span data-stu-id="cb32b-102">ICorDebugBreakpoint::IsActive Method</span></span>
<span data-ttu-id="cb32b-103">Obtient une valeur qui indique si ce `ICorDebugBreakpoint` est actif.</span><span class="sxs-lookup"><span data-stu-id="cb32b-103">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb32b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb32b-104">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb32b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cb32b-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="cb32b-106">[out] `true` si ce point d’arrêt est actif ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="cb32b-106">[out] `true` if this breakpoint is active; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb32b-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="cb32b-107">Requirements</span></span>  
 <span data-ttu-id="cb32b-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb32b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb32b-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb32b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb32b-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb32b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb32b-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb32b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
