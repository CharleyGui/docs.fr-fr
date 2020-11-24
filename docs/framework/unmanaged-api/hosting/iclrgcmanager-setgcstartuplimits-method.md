---
title: ICLRGCManager::SetGCStartupLimits, méthode
ms.date: 03/30/2017
api_name:
- ICLRGCManager.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: 1c8d9959-95b5-4131-be4a-556d97774014
topic_type:
- apiref
ms.openlocfilehash: 169d344975762b97f89e8dc32d72f2b9c95fea11
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678166"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a>ICLRGCManager::SetGCStartupLimits, méthode

Définit la taille d’un segment de garbage collection et la taille maximale de la génération 0 du système garbage collection.  
  
> [!IMPORTANT]
> À partir de la .NET Framework 4,5, vous pouvez définir la taille du segment et la taille maximale de la génération 0 sur des valeurs supérieures à à `DWORD` l’aide de la méthode [ICLRGCManager2 :: setgcstartuplimitsex,](iclrgcmanager2-setgcstartuplimitsex-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `SegmentSize`  
 dans Taille spécifiée d’un segment de garbage collection.  
  
 La taille minimale du segment est de 4 Mo. Les segments peuvent être augmentés par incréments de 1 Mo ou plus.  
  
 `MaxGen0Size`  
 dans Taille maximale spécifiée pour la génération 0.  
  
 La taille minimale de la génération 0 est de 64 Ko.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetGCStartupLimits` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Remarques  

 Les valeurs définies par `SetGCStartupLimits` ne peuvent être spécifiées qu’une seule fois. Les appels ultérieurs à `SetGCStartupLimits` sont ignorés.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Gestion automatique de la mémoire](../../../standard/automatic-memory-management.md)
- [Garbage collection](../../../standard/garbage-collection/index.md)
- [ICLRControl, interface](iclrcontrol-interface.md)
- [ICLRGCManager, interface](iclrgcmanager-interface.md)
