---
title: ICorDebugBreakpoint::Activate, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint.Activate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint::Activate
helpviewer_keywords:
- ICorDebugBreakpoint::Activate method [.NET Framework debugging]
- Activate method [.NET Framework debugging]
ms.assetid: e30c29f7-3f19-4081-b572-a731aa14cd44
topic_type:
- apiref
ms.openlocfilehash: 24dc55cc9a49c3602829ca627d584c761b4088ce
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894749"
---
# <a name="icordebugbreakpointactivate-method"></a><span data-ttu-id="16e89-102">ICorDebugBreakpoint::Activate, méthode</span><span class="sxs-lookup"><span data-stu-id="16e89-102">ICorDebugBreakpoint::Activate Method</span></span>
<span data-ttu-id="16e89-103">Définit l’état actif de ce `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="16e89-103">Sets the active state of this `ICorDebugBreakpoint`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16e89-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16e89-104">Syntax</span></span>  
  
```cpp  
HRESULT Activate (  
    [in] BOOL bActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16e89-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="16e89-105">Parameters</span></span>  
 `bActive`  
 <span data-ttu-id="16e89-106">dans Définissez cette valeur sur `true` pour spécifier l’état actif ; Sinon, définissez cette valeur sur `false`.</span><span class="sxs-lookup"><span data-stu-id="16e89-106">[in] Set this value to `true` to specify the state as active; otherwise, set this value to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16e89-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="16e89-107">Requirements</span></span>  
 <span data-ttu-id="16e89-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16e89-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16e89-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16e89-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16e89-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16e89-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16e89-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16e89-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
