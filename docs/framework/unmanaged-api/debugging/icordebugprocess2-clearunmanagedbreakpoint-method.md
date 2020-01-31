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
ms.openlocfilehash: e2aaf902afd71a4a81f7d64ef3fec046aacc91fc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792529"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="9776b-102">ICorDebugProcess2::ClearUnmanagedBreakpoint, méthode</span><span class="sxs-lookup"><span data-stu-id="9776b-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="9776b-103">Supprime un point d’arrêt défini précédemment à l’adresse donnée.</span><span class="sxs-lookup"><span data-stu-id="9776b-103">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9776b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9776b-104">Syntax</span></span>  
  
```cpp  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9776b-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="9776b-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="9776b-106">dans Valeur `CORDB_ADDRESS` qui spécifie l’adresse à laquelle le point d’arrêt a été défini.</span><span class="sxs-lookup"><span data-stu-id="9776b-106">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9776b-107">Notes</span><span class="sxs-lookup"><span data-stu-id="9776b-107">Remarks</span></span>  
 <span data-ttu-id="9776b-108">Le point d’arrêt spécifié aurait été précédemment défini par un appel antérieur à [ICorDebugProcess2 :: SetUnmanagedBreakpoint,](icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="9776b-108">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="9776b-109">La méthode `ClearUnmanagedBreakpoint` peut être appelée pendant l’exécution du processus en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="9776b-109">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="9776b-110">La méthode `ClearUnmanagedBreakpoint` retourne un code d’échec si le débogueur est attaché en mode managé uniquement ou si aucun point d’arrêt n’existe à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9776b-110">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9776b-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="9776b-111">Requirements</span></span>  
 <span data-ttu-id="9776b-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9776b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9776b-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9776b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9776b-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9776b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9776b-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9776b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
