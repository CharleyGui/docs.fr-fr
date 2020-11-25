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
ms.openlocfilehash: 38a5c2da900530b6bf78f24e224714496ceaa62c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710959"
---
# <a name="icordebugmdagetflags-method"></a><span data-ttu-id="0ada2-102">ICorDebugMDA::GetFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="0ada2-102">ICorDebugMDA::GetFlags Method</span></span>

<span data-ttu-id="0ada2-103">Obtient les indicateurs associés à l’Assistant Débogage managé (MDA) représenté par [ICorDebugMDA](icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="0ada2-103">Gets the flags associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ada2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ada2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ada2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0ada2-105">Parameters</span></span>  

 `pFlags`  
 <span data-ttu-id="0ada2-106">dans Combinaison d’opérations de bits des valeurs d’énumération [CorDebugMDAFlags,](cordebugmdaflags-enumeration.md) qui spécifient les paramètres des indicateurs pour cet Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="0ada2-106">[in] A bitwise combination of the [CorDebugMDAFlags](cordebugmdaflags-enumeration.md) enumeration values that specify the settings of the flags for this MDA.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ada2-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0ada2-107">Requirements</span></span>  

 <span data-ttu-id="0ada2-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ada2-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ada2-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ada2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ada2-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ada2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ada2-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ada2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ada2-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ada2-112">See also</span></span>

- [<span data-ttu-id="0ada2-113">ICorDebugMDA, interface</span><span class="sxs-lookup"><span data-stu-id="0ada2-113">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="0ada2-114">Diagnostic d'erreurs avec les Assistants de débogage managés</span><span class="sxs-lookup"><span data-stu-id="0ada2-114">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
