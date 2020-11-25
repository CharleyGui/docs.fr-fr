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
ms.openlocfilehash: 85cfd7ba648f21721f1a9689843eac232489cb42
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728015"
---
# <a name="icordebugthreadgetid-method"></a><span data-ttu-id="3b9cd-102">ICorDebugThread::GetID, méthode</span><span class="sxs-lookup"><span data-stu-id="3b9cd-102">ICorDebugThread::GetID Method</span></span>

<span data-ttu-id="3b9cd-103">Obtient l’identificateur de système d’exploitation actuel de la partie active de ce ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="3b9cd-103">Gets the current operating system identifier of the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b9cd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b9cd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b9cd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3b9cd-105">Parameters</span></span>  

 `pdwThreadId`  
 <span data-ttu-id="3b9cd-106">à Identificateur du thread.</span><span class="sxs-lookup"><span data-stu-id="3b9cd-106">[out] The identifier of the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b9cd-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="3b9cd-107">Remarks</span></span>  

 <span data-ttu-id="3b9cd-108">L’identificateur de système d’exploitation peut changer potentiellement lors de l’exécution d’un processus et peut être une valeur différente pour différentes parties du thread.</span><span class="sxs-lookup"><span data-stu-id="3b9cd-108">The operating system identifier can potentially change during execution of a process, and can be a different value for different parts of the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b9cd-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3b9cd-109">Requirements</span></span>  

 <span data-ttu-id="3b9cd-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b9cd-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b9cd-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3b9cd-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b9cd-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b9cd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b9cd-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b9cd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
