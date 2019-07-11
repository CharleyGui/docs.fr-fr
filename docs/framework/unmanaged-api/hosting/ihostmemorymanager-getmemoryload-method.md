---
title: IHostMemoryManager::GetMemoryLoad, méthode
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.GetMemoryLoad
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::GetMemoryLoad
helpviewer_keywords:
- IHostMemoryManager::GetMemoryLoad method [.NET Framework hosting]
- GetMemoryLoad method [.NET Framework hosting]
ms.assetid: e8138f6e-a0a4-48d4-8dae-9466b4dc6180
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 917ebe3c2001a9bc87978685d7f9a19eb3d98220
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767201"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a>IHostMemoryManager::GetMemoryLoad, méthode
Obtient la quantité de mémoire physique qui est actuellement en cours d’utilisation et par conséquent pas disponible, comme indiqué par l’hôte.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,   
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pMemoryLoad`  
 [out] Pointeur vers le pourcentage approximatif de mémoire physique totale qui est actuellement en cours d’utilisation.  
  
 `pAvailableBytes`  
 [out] Pointeur vers le nombre d’octets disponibles pour le common language runtime (CLR).  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`GetMemoryLoad` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Notes  
 `GetMemoryLoad` encapsule le Win32 `GlobalMemoryStatus` (fonction). La valeur de `pMemoryLoad` est l’équivalent de la `dwMemoryLoad` champ dans le `MEMORYSTATUS` structure retournée à partir de `GlobalMemoryStatus`.  
  
 Le runtime utilise la valeur de retour comme une méthode heuristique pour le garbage collector. Par exemple, si l’hôte signale que la majorité de la mémoire est en cours d’utilisation, le garbage collector peut choisir de collecter à partir de plusieurs générations afin d’augmenter la quantité de mémoire qui peut potentiellement deviennent disponible.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.GC?displayProperty=nameWithType>
- [IHostMemoryManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
