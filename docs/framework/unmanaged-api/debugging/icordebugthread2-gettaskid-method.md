---
title: ICorDebugThread2::GetTaskID, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type:
- apiref
ms.openlocfilehash: d5f2838007504e56ad44614a6778083be046629f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140071"
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="b6171-102">ICorDebugThread2::GetTaskID, méthode</span><span class="sxs-lookup"><span data-stu-id="b6171-102">ICorDebugThread2::GetTaskID Method</span></span>
<span data-ttu-id="b6171-103">Obtient l’identificateur de la tâche en cours d’exécution sur ce thread.</span><span class="sxs-lookup"><span data-stu-id="b6171-103">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6171-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6171-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6171-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b6171-105">Parameters</span></span>  
 `pTaskId`  
 <span data-ttu-id="b6171-106">à Pointeur vers l’identificateur de la tâche en cours d’exécution sur le thread représenté par cet objet ICorDebugThread2.</span><span class="sxs-lookup"><span data-stu-id="b6171-106">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6171-107">Notes</span><span class="sxs-lookup"><span data-stu-id="b6171-107">Remarks</span></span>  
 <span data-ttu-id="b6171-108">Une tâche ne peut être exécutée que sur le thread si le thread est associé à une connexion.</span><span class="sxs-lookup"><span data-stu-id="b6171-108">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="b6171-109">`GetTaskID` retourne la valeur zéro dans `pTaskId` si le thread n’est pas associé à une connexion.</span><span class="sxs-lookup"><span data-stu-id="b6171-109">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6171-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="b6171-110">Requirements</span></span>  
 <span data-ttu-id="b6171-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6171-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6171-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6171-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6171-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6171-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6171-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6171-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
