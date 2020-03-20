---
title: EMemoryAvailable, énumération
ms.date: 03/30/2017
api_name:
- EMemoryAvailable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryAvailable
helpviewer_keywords:
- EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type:
- apiref
ms.openlocfilehash: 0073a532f680d8764ec9e76ea22326a630457043
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176433"
---
# <a name="ememoryavailable-enumeration"></a>EMemoryAvailable, énumération
Contient des valeurs qui indiquent la quantité de mémoire physique gratuite sur l’ordinateur. Ces valeurs cartographient logiquement les événements de `CreateMemoryResourceNotification` haute et basse mémoire de la fonction dans l’API Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3
} EMemoryAvailable;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|Beaucoup de mémoire physique est disponible.|  
|`eMemoryAvailableLow`|Très peu de mémoire physique est disponible.|  
|`eMemoryAvailableNeutral`|La mémoire physique disponible est neutre.|  
  
## <a name="remarks"></a>Notes   
 Cette valeur est transmise par l’hôte de l’heure courante (CLR) en utilisant un appel à [l’ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) méthode.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor  
  
 **Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations d'hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
