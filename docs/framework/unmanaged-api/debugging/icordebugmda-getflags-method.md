---
title: ICorDebugMDA::GetFlags, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetFlags
helpviewer_keywords:
- ICorDebugMDA::GetFlags method [.NET Framework debugging]
- GetFlags method [.NET Framework debugging]
ms.assetid: 87ce7c5b-fd82-453e-bf55-c8a32150b183
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 701d578a1d3af941923d68ddc0cb7c97dd0ca8ab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761942"
---
# <a name="icordebugmdagetflags-method"></a><span data-ttu-id="b0ee3-102">ICorDebugMDA::GetFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="b0ee3-102">ICorDebugMDA::GetFlags Method</span></span>
<span data-ttu-id="b0ee3-103">Obtient les indicateurs associés à l’assistant débogage managé (MDA) représenté par [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b0ee3-103">Gets the flags associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0ee3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0ee3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0ee3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b0ee3-105">Parameters</span></span>  
 `pFlags`  
 <span data-ttu-id="b0ee3-106">[in] Une combinaison au niveau du bit de la [CorDebugMDAFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md) des valeurs d’énumération qui spécifient les paramètres des indicateurs pour cet Assistant Débogage MANAGÉ.</span><span class="sxs-lookup"><span data-stu-id="b0ee3-106">[in] A bitwise combination of the [CorDebugMDAFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md) enumeration values that specify the settings of the flags for this MDA.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0ee3-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b0ee3-107">Requirements</span></span>  
 <span data-ttu-id="b0ee3-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0ee3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0ee3-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0ee3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0ee3-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0ee3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0ee3-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0ee3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0ee3-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0ee3-112">See also</span></span>

- [<span data-ttu-id="b0ee3-113">ICorDebugMDA, interface</span><span class="sxs-lookup"><span data-stu-id="b0ee3-113">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="b0ee3-114">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="b0ee3-114">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
