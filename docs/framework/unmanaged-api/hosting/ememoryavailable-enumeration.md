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
ms.openlocfilehash: 822396e28d000a5309738680fec502e1aeacd67c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616214"
---
# <a name="ememoryavailable-enumeration"></a>EMemoryAvailable, énumération
Contient des valeurs qui indiquent la quantité de mémoire physique disponible sur l’ordinateur. Ces valeurs correspondent logiquement aux événements pour la mémoire haute et la mémoire insuffisante retournés par la `CreateMemoryResourceNotification` fonction dans l’API Windows.  
  
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
 Cette valeur est passée par l’hôte au common language runtime (CLR) à l’aide d’un appel à la méthode [ICLRMemoryNotificationCallback :: OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md) .  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations d'hébergement](hosting-enumerations.md)
