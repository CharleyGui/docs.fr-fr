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
ms.openlocfilehash: bc956827ad59fc655137e4147e6d98b6d097d470
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138187"
---
# <a name="etasktype-enumeration"></a>ETaskType, énumération
Contient des valeurs qui indiquent le type de tâche représenté par une interface [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) ou [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) .  
  
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
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
