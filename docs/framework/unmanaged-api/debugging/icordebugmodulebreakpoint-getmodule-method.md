---
title: ICorDebugModuleBreakpoint::GetModule, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint::GetModule
helpviewer_keywords:
- ICorDebugModuleBreakpoint::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: ffd5d9ec-4564-4200-b625-b306eec0ebd7
topic_type:
- apiref
ms.openlocfilehash: 6f9d8cd79ac4107817d19fc0632aeaee287d253a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097010"
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="d019b-102">ICorDebugModuleBreakpoint::GetModule, méthode</span><span class="sxs-lookup"><span data-stu-id="d019b-102">ICorDebugModuleBreakpoint::GetModule Method</span></span>
<span data-ttu-id="d019b-103">Obtient un pointeur d’interface vers un « ICorDebugModule » qui référence le module dans lequel ce point d’arrêt est défini.</span><span class="sxs-lookup"><span data-stu-id="d019b-103">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d019b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d019b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d019b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d019b-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="d019b-106">à Pointeur vers l’adresse d’une interface `ICorDebugModule` qui référence le module dans lequel le point d’arrêt est défini.</span><span class="sxs-lookup"><span data-stu-id="d019b-106">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d019b-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="d019b-107">Requirements</span></span>  
 <span data-ttu-id="d019b-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d019b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d019b-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d019b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d019b-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d019b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d019b-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d019b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d019b-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d019b-112">See also</span></span>
