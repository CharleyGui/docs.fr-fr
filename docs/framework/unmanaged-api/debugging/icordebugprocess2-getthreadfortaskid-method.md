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
# <a name="icordebugprocess2getthreadfortaskid-method"></a>ICorDebugProcess2::GetThreadForTaskID, méthode

Obtient le thread sur lequel s’exécute la tâche avec l’identificateur spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetThreadForTaskID (  
    [in]  TASKID            taskid,  
    [out] ICorDebugThread2  **ppThread  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `taskid`  
 dans Identificateur de la tâche.  
  
 `ppThread`  
 à Pointeur vers l’adresse d’un objet ICorDebugThread2 qui représente le thread à récupérer.  
  
## <a name="remarks"></a>Remarques  

 L’hôte peut définir l’identificateur de tâche à l’aide de la méthode [ICLRTask :: SetTaskIdentifier,](../hosting/iclrtask-settaskidentifier-method.md) .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
