---
title: IHostSyncManager::CreateSemaphore, méthode
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateSemaphore
helpviewer_keywords:
- CreateSemaphore method [.NET Framework hosting]
- IHostSyncManager::CreateSemaphore method [.NET Framework hosting]
ms.assetid: 37679e94-5ff9-4173-8fa5-457febeb89bf
topic_type:
- apiref
ms.openlocfilehash: 680280e959d523356b95a5a4d9390c80720c0330
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803142"
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a>IHostSyncManager::CreateSemaphore, méthode
Crée un objet [IHostSemaphore](ihostsemaphore-interface.md) pour le Common Language Runtime (CLR) à utiliser comme sémaphore pour les événements d’attente.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `dwInitial`  
 dans Nombre initial de `ppSemaphore` .  
  
 `dwMax`  
 dans Nombre maximal pour `ppSemaphore` .  
  
 `ppSemaphore`  
 à Pointeur vers l’adresse d’une `IHostSemaphore` instance, ou null si le sémaphore n’a pas pu être créé.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`CreateSemaphore`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Mémoire disponible insuffisante pour créer l’objet d’événement demandé.|  
  
## <a name="remarks"></a>Notes  
 `CreateSemaphore`reflète la fonction Win32 qui porte le même nom. Les `dwInitial` `dwMax` paramètres et utilisent la même sémantique pour le nombre de sémaphores que les `lInitialCount` paramètres Win32 et `lMaximumCount` , respectivement. `dwInitial`doit être compris entre zéro et `dwMax` , inclus. `dwMax`doit être supérieur à zéro.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRSyncManager, interface](iclrsyncmanager-interface.md)
- [IHostSemaphore, interface](ihostsemaphore-interface.md)
- [IHostSyncManager, interface](ihostsyncmanager-interface.md)
