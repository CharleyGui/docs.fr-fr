---
title: IHostAssemblyManager::GetNonHostStoreAssemblies, méthode
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetNonHostStoreAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies
helpviewer_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies method [.NET Framework hosting]
- GetNonHostStoreAssemblies method [.NET Framework hosting]
ms.assetid: d2250b38-c76a-40ce-80c8-ba45149886e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3680721c70ab69776c973913d929f7bdd9db3909
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779443"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a>IHostAssemblyManager::GetNonHostStoreAssemblies, méthode
Obtient un pointeur d’interface vers un [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) qui représente la liste des assemblys que l’hôte attend le common language runtime (CLR) à charger.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppReferenceList`  
 [out] Un pointeur vers l’adresse d’un `ICLRAssemblyReferenceList` qui contient une liste de références aux assemblys que l’hôte attend le CLR à charger.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`GetNonHostStoreAssemblies` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Pas assez de mémoire n’était disponible pour créer la liste de références pour demandé `ICLRAssemblyReferenceList`.|  
  
## <a name="remarks"></a>Notes  
 Le CLR résout les références à l’aide de l’ensemble des instructions suivantes :  
  
- Tout d’abord, il consulte la liste des références d’assembly retourné par `GetNonHostStoreAssemblies`.  
  
- Si l’assembly apparaît dans la liste, le CLR se lie normalement à ce dernier.  
  
- Si l’assembly n’apparaît pas dans la liste et que l’hôte a fourni une implémentation de [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), le CLR appelle [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) pour autoriser l’hôte de fournir le assembly à lier.  
  
- Sinon, le CLR ne peut pas lier à l’assembly.  
  
 Si l’hôte définit `ppReferenceList` sur null, les sondes premier CLR appelle le global assembly cache, `ProvideAssembly`et des sondes puis la base de l’application pour résoudre une référence d’assembly.  
  
> [!NOTE]
>  Lors de l’initialisation, le CLR appelle `GetNonHostStoreAssemblies` qu’une seule fois. La méthode n’est pas appelée à nouveau.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRAssemblyReferenceList, interface](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore, interface](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
