---
title: IHostIoCompletionManager::GetHostOverlappedSize, méthode
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetHostOverlappedSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize
helpviewer_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize method [.NET Framework hosting]
- GetHostOverlappedSize method [.NET Framework hosting]
ms.assetid: 2902578b-d5e2-4f8d-a103-0c7b6dceda9e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54e72205f8f976498df3b1fe1e055fb7df12d68e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780679"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a>IHostIoCompletionManager::GetHostOverlappedSize, méthode
Obtient la taille des données personnalisées que l’hôte projette d’ajouter aux demandes d’e/s.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pcbSize`  
 [out] Un pointeur vers le nombre d’octets que le common language runtime (CLR) doit allouer en plus de la taille de Win32 `OVERLAPPED` objet.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`GetHostOverlappedSize` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Notes  
 Tous les appels d’e/s asynchrones aux API de plateforme Windows prennent un Win32 `OVERLAPPED` objet, qui fournit des informations telles que la position du pointeur de fichier. Pour conserver l’état, les applications qui effectuent des appels d’e/s asynchrones généralement ajouter des données personnalisées à la structure. `GetHostOverlappedSize` et [IHostIoCompletionManager::InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) offrent la possibilité de l’hôte d’inclure ces données personnalisées.  
  
 Le CLR appelle le `GetHostOverlappedSize` méthode pour déterminer la taille des données personnalisées qui a l’intention de l’hôte à ajouter à la `OVERLAPPED` objet.  
  
> [!NOTE]
>  `GetHostOverlappedSize` est appelé une seule fois. Données personnalisées de l’hôte doivent être la même taille pour chaque demande d’e/s.  
  
> [!IMPORTANT]
>  La taille de la `OVERLAPPED` objet lui-même n’est pas inclus dans la valeur de `pcbSize`.  
  
 Pour plus d’informations sur la `OVERLAPPED` structure, consultez la documentation de la plateforme de Windows.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.NativeOverlapped>
- [ICLRIoCompletionManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
