---
title: ICorDebugProcess2::ClearUnmanagedBreakpoint, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.ClearUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::ClearUnmanagedBreakpoint
helpviewer_keywords:
- ClearUnmanagedBreakpoint method [.NET Framework debugging]
- ICorDebugProcess2::ClearUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 12ed0fff-7f0e-4d7a-bb70-b3376371f36c
topic_type:
- apiref
ms.openlocfilehash: 8377ead42c752d8ebe9813d9e00662b94339f8a3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137242"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="adbb6-102">ICorDebugProcess2::ClearUnmanagedBreakpoint, méthode</span><span class="sxs-lookup"><span data-stu-id="adbb6-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="adbb6-103">Supprime un point d’arrêt défini précédemment à l’adresse donnée.</span><span class="sxs-lookup"><span data-stu-id="adbb6-103">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adbb6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="adbb6-104">Syntax</span></span>  
  
```cpp  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="adbb6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="adbb6-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="adbb6-106">dans Valeur `CORDB_ADDRESS` qui spécifie l’adresse à laquelle le point d’arrêt a été défini.</span><span class="sxs-lookup"><span data-stu-id="adbb6-106">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="adbb6-107">Notes</span><span class="sxs-lookup"><span data-stu-id="adbb6-107">Remarks</span></span>  
 <span data-ttu-id="adbb6-108">Le point d’arrêt spécifié aurait été précédemment défini par un appel antérieur à [ICorDebugProcess2 :: SetUnmanagedBreakpoint,](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="adbb6-108">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="adbb6-109">La méthode `ClearUnmanagedBreakpoint` peut être appelée pendant l’exécution du processus en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="adbb6-109">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="adbb6-110">La méthode `ClearUnmanagedBreakpoint` retourne un code d’échec si le débogueur est attaché en mode managé uniquement ou si aucun point d’arrêt n’existe à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="adbb6-110">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adbb6-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="adbb6-111">Requirements</span></span>  
 <span data-ttu-id="adbb6-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adbb6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adbb6-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="adbb6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="adbb6-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="adbb6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="adbb6-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adbb6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
