---
title: ICLRGCManager2::SetGCStartupLimitsEx, méthode
ms.date: 03/30/2017
api_name:
- ICLRGCManager2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2::SetCLRGCStartupLimitsEx
helpviewer_keywords:
- ICLRGCManager2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 6c3a08a9-5d65-48d4-8bbf-2a86ed7d356a
topic_type:
- apiref
ms.openlocfilehash: 27d1ce06800075d2690bc508554b70f8d10168af
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715015"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a>ICLRGCManager2::SetGCStartupLimitsEx, méthode

Définit la taille d’un segment de garbage collection et la taille maximale de la génération 0 du système garbage collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,
    [in] SIZE_T MaxGen0Size  
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
|S_OK|`SetGCStartupLimitsEx` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Remarques  

 Les valeurs définies par `SetGCStartupLimitsEx` ne peuvent être spécifiées qu’avant le démarrage de l’hôte. Les appels ultérieurs à `SetGCStartupLimitsEx` sont ignorés.  
  
 Pour définir l’un ou l’autre paramètre sans affecter l’autre, spécifiez 0 (zéro) pour le paramètre que vous ne souhaitez pas modifier.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Gestion automatique de la mémoire](../../../standard/automatic-memory-management.md)
- [Garbage collection](../../../standard/garbage-collection/index.md)
- [ICLRControl, interface](iclrcontrol-interface.md)
- [ICLRGCManager2, interface](iclrgcmanager2-interface.md)
