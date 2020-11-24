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
ms.openlocfilehash: 9b17a179745af65bde05527bd0157f3ce06c12c6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678660"
---
# <a name="icordebugthread2gettaskid-method"></a>ICorDebugThread2::GetTaskID, méthode

Obtient l’identificateur de la tâche en cours d’exécution sur ce thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pTaskId`  
 à Pointeur vers l’identificateur de la tâche en cours d’exécution sur le thread représenté par cet objet ICorDebugThread2.  
  
## <a name="remarks"></a>Remarques  

 Une tâche ne peut être exécutée que sur le thread si le thread est associé à une connexion. `GetTaskID` retourne la valeur zéro dans `pTaskId` si le thread n’est pas associé à une connexion.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
