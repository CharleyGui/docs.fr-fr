---
title: ICorDebugThread2::GetVolatileOSThreadID, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetVolatileOSThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetVolatileOSThreadID
helpviewer_keywords:
- GetVolatileOSThreadID method [.NET Framework debugging]
- ICorDebugThread2::GetVolatileOSThreadID method [.NET Framework debugging]
ms.assetid: f0922545-c2cf-40c8-9ef6-ca033563e682
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d964a5a77569762ff4fd69e419324a377b820d97
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768948"
---
# <a name="icordebugthread2getvolatileosthreadid-method"></a><span data-ttu-id="0b499-102">ICorDebugThread2::GetVolatileOSThreadID, méthode</span><span class="sxs-lookup"><span data-stu-id="0b499-102">ICorDebugThread2::GetVolatileOSThreadID Method</span></span>
<span data-ttu-id="0b499-103">Obtient l’identificateur de thread de système d’exploitation pour ICorDebugThread2.</span><span class="sxs-lookup"><span data-stu-id="0b499-103">Gets the operating system thread identifier for this ICorDebugThread2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b499-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b499-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVolatileOSThreadID (  
    [out] DWORD    *pdwTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b499-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0b499-105">Parameters</span></span>  
 `pdwTid`  
 <span data-ttu-id="0b499-106">[out] L’identificateur de thread de système d’exploitation pour ce thread.</span><span class="sxs-lookup"><span data-stu-id="0b499-106">[out] The operating system thread identifier for this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b499-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0b499-107">Requirements</span></span>  
 <span data-ttu-id="0b499-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b499-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b499-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b499-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b499-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b499-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b499-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b499-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
