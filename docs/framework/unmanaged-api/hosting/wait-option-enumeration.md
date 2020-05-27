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
ms.openlocfilehash: 4c57a3fde3565a21800c60794b6c2d1c7616ddd8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007999"
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
|`WAIT_ALERTABLE`|Avertit l’hôte que la tâche doit être réutilisée si le CLR appelle la méthode [IHostTask :: Alert](ihosttask-alert-method.md) .|  
|`WAIT_MSGPUMP`|Indique à l’hôte qu’il doit pomper les messages sur le thread de système d’exploitation actuel si le thread est bloqué. Le runtime spécifie cette valeur uniquement sur un <xref:System.Threading.ApartmentState.STA> thread.|  
|`WAIT_NOTINDEADLOCK`|Indique à l’hôte que la demande de synchronisation spécifiée ne peut pas être interrompue par un hôte. Autrement dit, l’hôte ne peut pas retourner `HOST_E_DEADLOCK` .|  
  
## <a name="remarks"></a>Remarques  
 Les méthodes [IHostTaskManager :: Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) et [IHostTaskManager :: SwitchToTask,](ihosttaskmanager-switchtotask-method.md) prennent toutes deux un paramètre de ce type.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations d'hébergement](hosting-enumerations.md)
