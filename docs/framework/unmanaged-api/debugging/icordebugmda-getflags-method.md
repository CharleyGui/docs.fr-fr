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
ms.openlocfilehash: 7c3b0331cc4d987070b2d04beb621c4966a27cb9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129835"
---
# <a name="icordebugmdagetflags-method"></a><span data-ttu-id="0e483-102">ICorDebugMDA::GetFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="0e483-102">ICorDebugMDA::GetFlags Method</span></span>
<span data-ttu-id="0e483-103">Obtient les indicateurs associés à l’Assistant Débogage managé (MDA) représenté par [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="0e483-103">Gets the flags associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e483-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e483-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e483-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0e483-105">Parameters</span></span>  
 `pFlags`  
 <span data-ttu-id="0e483-106">dans Combinaison d’opérations de bits des valeurs d’énumération [CorDebugMDAFlags,](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md) qui spécifient les paramètres des indicateurs pour cet Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="0e483-106">[in] A bitwise combination of the [CorDebugMDAFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md) enumeration values that specify the settings of the flags for this MDA.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e483-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="0e483-107">Requirements</span></span>  
 <span data-ttu-id="0e483-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e483-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e483-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e483-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e483-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e483-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e483-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e483-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e483-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e483-112">See also</span></span>

- [<span data-ttu-id="0e483-113">ICorDebugMDA, interface</span><span class="sxs-lookup"><span data-stu-id="0e483-113">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="0e483-114">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="0e483-114">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
