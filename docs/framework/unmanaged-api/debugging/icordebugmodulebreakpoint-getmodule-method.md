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
ms.openlocfilehash: b6363ef901d5297862ca46e685bb783aaaeb4123
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709620"
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="152f2-102">ICorDebugModuleBreakpoint::GetModule, méthode</span><span class="sxs-lookup"><span data-stu-id="152f2-102">ICorDebugModuleBreakpoint::GetModule Method</span></span>

<span data-ttu-id="152f2-103">Obtient un pointeur d’interface vers un « ICorDebugModule » qui référence le module dans lequel ce point d’arrêt est défini.</span><span class="sxs-lookup"><span data-stu-id="152f2-103">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="152f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="152f2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="152f2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="152f2-105">Parameters</span></span>  

 `ppModule`  
 <span data-ttu-id="152f2-106">à Pointeur vers l’adresse d’une `ICorDebugModule` interface qui référence le module dans lequel le point d’arrêt est défini.</span><span class="sxs-lookup"><span data-stu-id="152f2-106">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="152f2-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="152f2-107">Requirements</span></span>  

 <span data-ttu-id="152f2-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="152f2-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="152f2-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="152f2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="152f2-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="152f2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="152f2-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="152f2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="152f2-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="152f2-112">See also</span></span>
