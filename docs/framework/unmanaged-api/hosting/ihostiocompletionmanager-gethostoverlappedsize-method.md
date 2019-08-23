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
ms.openlocfilehash: c43f906961b9e76d5f0f34ba5a5b2f656f5b1488
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937507"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a>IHostIoCompletionManager::GetHostOverlappedSize, méthode
Obtient la taille des données personnalisées que l’hôte envisage d’ajouter aux demandes d’e/s.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pcbSize`  
 à Pointeur vers le nombre d’octets que le Common Language Runtime (CLR) doit allouer en plus de la taille de l’objet `OVERLAPPED` Win32.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`GetHostOverlappedSize`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Notes  
 Tous les appels d’e/s asynchrones aux API de la `OVERLAPPED` plateforme Windows acceptent un objet Win32, qui fournit des informations telles que la position du pointeur de fichier. Pour conserver l’État, les applications qui effectuent des appels d’e/s asynchrones ajoutent généralement des données personnalisées à la structure. `GetHostOverlappedSize`et [IHostIoCompletionManager:: InitializeHostOverlapped,](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) offrent une opportunité pour l’hôte d’inclure ces données personnalisées.  
  
 Le CLR appelle la `GetHostOverlappedSize` méthode pour déterminer la taille des données personnalisées que l’hôte envisage d’ajouter à l' `OVERLAPPED` objet.  
  
> [!NOTE]
> `GetHostOverlappedSize`est appelée une seule fois. Les données personnalisées de l’hôte doivent avoir la même taille pour chaque demande d’e/s.  
  
> [!IMPORTANT]
> La taille de l' `OVERLAPPED` objet lui-même n’est pas incluse dans `pcbSize`la valeur de.  
  
 Pour plus d’informations sur `OVERLAPPED` la structure, consultez la documentation de la plateforme Windows.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.NativeOverlapped>
- [ICLRIoCompletionManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
