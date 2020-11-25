---
title: ICorDebugProcess2::GetThreadForTaskID, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetThreadForTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetThreadForTaskID
helpviewer_keywords:
- ICorDebugProcess2::GetThreadForTaskId method [.NET Framework debugging]
- GetThreadForTaskID method [.NET Framework debugging]
ms.assetid: 32d54a5b-8ad3-405b-a1b9-0936a3b49d1e
topic_type:
- apiref
ms.openlocfilehash: 2b18289af460f64085fedd7b32387ebcb8c51715
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713546"
---
# <a name="icordebugprocess2getthreadfortaskid-method"></a><span data-ttu-id="fada3-102">ICorDebugProcess2::GetThreadForTaskID, méthode</span><span class="sxs-lookup"><span data-stu-id="fada3-102">ICorDebugProcess2::GetThreadForTaskID Method</span></span>

<span data-ttu-id="fada3-103">Obtient le thread sur lequel s’exécute la tâche avec l’identificateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="fada3-103">Gets the thread on which the task with the specified identifier is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fada3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fada3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadForTaskID (  
    [in]  TASKID            taskid,  
    [out] ICorDebugThread2  **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fada3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fada3-105">Parameters</span></span>  

 `taskid`  
 <span data-ttu-id="fada3-106">dans Identificateur de la tâche.</span><span class="sxs-lookup"><span data-stu-id="fada3-106">[in] The identifier of the task.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="fada3-107">à Pointeur vers l’adresse d’un objet ICorDebugThread2 qui représente le thread à récupérer.</span><span class="sxs-lookup"><span data-stu-id="fada3-107">[out] A pointer to the address of an ICorDebugThread2 object that represents the thread to be retrieved.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fada3-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="fada3-108">Remarks</span></span>  

 <span data-ttu-id="fada3-109">L’hôte peut définir l’identificateur de tâche à l’aide de la méthode [ICLRTask :: SetTaskIdentifier,](../hosting/iclrtask-settaskidentifier-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fada3-109">The host can set the task identifier by using the [ICLRTask::SetTaskIdentifier](../hosting/iclrtask-settaskidentifier-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fada3-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fada3-110">Requirements</span></span>  

 <span data-ttu-id="fada3-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fada3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fada3-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fada3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fada3-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fada3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fada3-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fada3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
