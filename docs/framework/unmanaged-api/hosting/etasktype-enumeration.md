---
title: ETaskType, énumération
ms.date: 03/30/2017
api_name:
- ETaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ETaskType
helpviewer_keywords:
- ETaskType enumeration [.NET Framework hosting]
ms.assetid: aa527b31-89d4-41f2-ad6f-63b76950b7df
topic_type:
- apiref
ms.openlocfilehash: 0fa72568df77c4916a3c6676e1dcca7c0c616c4a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493316"
---
# <a name="etasktype-enumeration"></a>ETaskType, énumération
Contient des valeurs qui indiquent le type de tâche représenté par une interface [ICLRTask](iclrtask-interface.md) ou [IHostTask](ihosttask-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum ETaskType {  
    TT_DEBUGGERHELPER           = 0x1,  
    TT_GC                       = 0x2,  
    TT_FINALIZER                = 0x4,  
    TT_THREADPOOL_TIMER         = 0x8,  
    TT_THREADPOOL_GATE          = 0x10,  
    TT_THREADPOOL_WORKER        = 0x20,  
    TT_THREADPOOL_IOCOMPLETION  = 0x40,  
    TT_ADUNLOAD                 = 0x80,  
    TT_USER                     = 0x100,  
    TT_THREADPOOL_WAIT          = 0x200,  
    TT_UNKNOWN                  = 0x80000000  
} ETaskType;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`TT_ADUNLOAD`|L’interface représente une tâche de déchargement de domaine d’application.|  
|`TT_DEBUGGERHELPER`|L’interface représente une tâche d’assistance du débogueur.|  
|`TT_FINALIZER`|L’interface représente une tâche de finaliseur.|  
|`TT_GC`|L’interface représente une tâche garbage collection.|  
|`TT_THREADPOOL_GATE`|L’interface représente une tâche de thread de la porte.|  
|`TT_THREADPOOL_IOCOMPLETION`|L’interface représente une tâche de thread d’e/s ou une tâche de thread de terminaison de port.|  
|`TT_THREADPOOL_TIMER`|L’interface représente une tâche de thread de minuterie.|  
|`TT_THREADPOOL_WAIT`|L’interface représente une tâche de thread d’attente.|  
|`TT_THREADPOOL_WORKER`|L’interface représente une tâche de thread de travail.|  
|`TT_UNKNOWN`|La tâche est inconnue.|  
|`TT_USER`|L’interface représente une tâche utilisateur.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations d'hébergement](hosting-enumerations.md)
