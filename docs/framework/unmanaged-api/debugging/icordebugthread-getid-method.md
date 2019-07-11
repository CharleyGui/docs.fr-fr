---
title: ICorDebugThread::GetID, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetID
helpviewer_keywords:
- ICorDebugThread::GetID method [.NET Framework debugging]
- GetID method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: f1de4584-92df-42f3-9da4-fca03a1c6821
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11e21e913e4749705ba6c7f91016be21b4de1712
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769969"
---
# <a name="icordebugthreadgetid-method"></a><span data-ttu-id="2ae3a-102">ICorDebugThread::GetID, méthode</span><span class="sxs-lookup"><span data-stu-id="2ae3a-102">ICorDebugThread::GetID Method</span></span>
<span data-ttu-id="2ae3a-103">Obtient l’identificateur de système d’exploitation actuel de la partie active du ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="2ae3a-103">Gets the current operating system identifier of the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ae3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ae3a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ae3a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ae3a-105">Parameters</span></span>  
 `pdwThreadId`  
 <span data-ttu-id="2ae3a-106">[out] L’identificateur du thread.</span><span class="sxs-lookup"><span data-stu-id="2ae3a-106">[out] The identifier of the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ae3a-107">Notes</span><span class="sxs-lookup"><span data-stu-id="2ae3a-107">Remarks</span></span>  
 <span data-ttu-id="2ae3a-108">L’identificateur de système d’exploitation peut changer pendant l’exécution d’un processus et peut être une valeur différente pour différentes parties du thread.</span><span class="sxs-lookup"><span data-stu-id="2ae3a-108">The operating system identifier can potentially change during execution of a process, and can be a different value for different parts of the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ae3a-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2ae3a-109">Requirements</span></span>  
 <span data-ttu-id="2ae3a-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ae3a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ae3a-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ae3a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ae3a-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ae3a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ae3a-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ae3a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
