---
title: WAIT_OPTION, énumération
ms.date: 03/30/2017
api_name:
- WAIT_OPTION
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAIT_OPTION
helpviewer_keywords:
- WAIT_OPTION enumeration [.NET Framework hosting]
ms.assetid: 962fc293-8ded-4b3b-90ce-2c21a4f1b244
topic_type:
- apiref
ms.openlocfilehash: 9ecfb551b55551e5f6cc7e7e9ffb55e5a96259ee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141519"
---
# <a name="wait_option-enumeration"></a>WAIT_OPTION, énumération
Contient des valeurs qui indiquent l’action qu’un hôte doit effectuer si une opération demandée par le common language runtime (CLR) se bloque.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|Avertit l’hôte que la tâche doit être réutilisée si le CLR appelle la méthode [IHostTask :: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) .|  
|`WAIT_MSGPUMP`|Indique à l’hôte qu’il doit pomper les messages sur le thread de système d’exploitation actuel si le thread est bloqué. Le runtime spécifie cette valeur uniquement sur un thread <xref:System.Threading.ApartmentState.STA>.|  
|`WAIT_NOTINDEADLOCK`|Indique à l’hôte que la demande de synchronisation spécifiée ne peut pas être interrompue par un hôte. Autrement dit, l’hôte ne peut pas retourner `HOST_E_DEADLOCK`.|  
  
## <a name="remarks"></a>Notes  
 Les méthodes [IHostTaskManager :: Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) et [IHostTaskManager :: SwitchToTask,](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) prennent toutes deux un paramètre de ce type.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
