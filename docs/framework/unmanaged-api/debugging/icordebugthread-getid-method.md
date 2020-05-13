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
ms.openlocfilehash: d01936481ec139757566d5b96cb95ea887cb8c20
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378055"
---
# <a name="icordebugthreadgetid-method"></a><span data-ttu-id="61842-102">ICorDebugThread::GetID, méthode</span><span class="sxs-lookup"><span data-stu-id="61842-102">ICorDebugThread::GetID Method</span></span>
<span data-ttu-id="61842-103">Obtient l’identificateur de système d’exploitation actuel de la partie active de ce ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="61842-103">Gets the current operating system identifier of the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61842-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61842-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61842-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="61842-105">Parameters</span></span>  
 `pdwThreadId`  
 <span data-ttu-id="61842-106">à Identificateur du thread.</span><span class="sxs-lookup"><span data-stu-id="61842-106">[out] The identifier of the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61842-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="61842-107">Remarks</span></span>  
 <span data-ttu-id="61842-108">L’identificateur de système d’exploitation peut changer potentiellement lors de l’exécution d’un processus et peut être une valeur différente pour différentes parties du thread.</span><span class="sxs-lookup"><span data-stu-id="61842-108">The operating system identifier can potentially change during execution of a process, and can be a different value for different parts of the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61842-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="61842-109">Requirements</span></span>  
 <span data-ttu-id="61842-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61842-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61842-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61842-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61842-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61842-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61842-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61842-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
