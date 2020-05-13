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
ms.openlocfilehash: 841af546cc3586529fe290c69e686438f634b90d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377785"
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="2c6e1-102">ICorDebugThread2::GetTaskID, méthode</span><span class="sxs-lookup"><span data-stu-id="2c6e1-102">ICorDebugThread2::GetTaskID Method</span></span>
<span data-ttu-id="2c6e1-103">Obtient l’identificateur de la tâche en cours d’exécution sur ce thread.</span><span class="sxs-lookup"><span data-stu-id="2c6e1-103">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c6e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c6e1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c6e1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2c6e1-105">Parameters</span></span>  
 `pTaskId`  
 <span data-ttu-id="2c6e1-106">à Pointeur vers l’identificateur de la tâche en cours d’exécution sur le thread représenté par cet objet ICorDebugThread2.</span><span class="sxs-lookup"><span data-stu-id="2c6e1-106">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c6e1-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="2c6e1-107">Remarks</span></span>  
 <span data-ttu-id="2c6e1-108">Une tâche ne peut être exécutée que sur le thread si le thread est associé à une connexion.</span><span class="sxs-lookup"><span data-stu-id="2c6e1-108">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="2c6e1-109">`GetTaskID`retourne la valeur zéro dans `pTaskId` si le thread n’est pas associé à une connexion.</span><span class="sxs-lookup"><span data-stu-id="2c6e1-109">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c6e1-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2c6e1-110">Requirements</span></span>  
 <span data-ttu-id="2c6e1-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c6e1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c6e1-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c6e1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c6e1-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c6e1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c6e1-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c6e1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
