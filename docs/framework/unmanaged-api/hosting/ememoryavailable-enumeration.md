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
ms.openlocfilehash: aec3c5f140df7eab10ea2bfa33634a4d853adcb0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134289"
---
# <a name="ememoryavailable-enumeration"></a>EMemoryAvailable, énumération
Contient des valeurs qui indiquent la quantité de mémoire physique disponible sur l’ordinateur. Ces valeurs correspondent logiquement aux événements pour la mémoire haute et la mémoire insuffisante retournés par la fonction `CreateMemoryResourceNotification` dans l’API Windows.  
  
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
|`eMemoryAvailableHigh`|Une grande quantité de mémoire physique est disponible.|  
|`eMemoryAvailableLow`|Très peu de mémoire physique est disponible.|  
|`eMemoryAvailableNeutral`|La mémoire physique disponible est neutre.|  
  
## <a name="remarks"></a>Notes  
 Cette valeur est passée par l’hôte au common language runtime (CLR) à l’aide d’un appel à la méthode [ICLRMemoryNotificationCallback :: OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) .  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
