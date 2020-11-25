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
ms.openlocfilehash: 612a5f08982b1db5c940a7cca93166480b21e612
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724856"
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
 à Pointeur vers le nombre d’octets que le common language runtime (CLR) doit allouer en plus de la taille de l' `OVERLAPPED` objet Win32.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`GetHostOverlappedSize` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Remarques  

 Tous les appels d’e/s asynchrones aux API de la plateforme Windows acceptent un `OVERLAPPED` objet Win32, qui fournit des informations telles que la position du pointeur de fichier. Pour conserver l’État, les applications qui effectuent des appels d’e/s asynchrones ajoutent généralement des données personnalisées à la structure. `GetHostOverlappedSize` et [IHostIoCompletionManager :: InitializeHostOverlapped,](ihostiocompletionmanager-initializehostoverlapped-method.md) offrent une opportunité pour l’hôte d’inclure ces données personnalisées.  
  
 Le CLR appelle la `GetHostOverlappedSize` méthode pour déterminer la taille des données personnalisées que l’hôte envisage d’ajouter à l' `OVERLAPPED` objet.  
  
> [!NOTE]
> `GetHostOverlappedSize` est appelée une seule fois. Les données personnalisées de l’hôte doivent avoir la même taille pour chaque demande d’e/s.  
  
> [!IMPORTANT]
> La taille de l' `OVERLAPPED` objet lui-même n’est pas incluse dans la valeur de `pcbSize` .  
  
 Pour plus d’informations sur la `OVERLAPPED` structure, consultez la documentation de la plateforme Windows.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.NativeOverlapped>
- [ICLRIoCompletionManager, interface](iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager, interface](ihostiocompletionmanager-interface.md)
