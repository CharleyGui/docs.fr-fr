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
ms.openlocfilehash: 88acd50c83eb1ff4d59aa50d677db2383912659a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176277"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a>IHostMemoryManager::GetMemoryLoad, méthode
Obtient la quantité de mémoire physique qui est actuellement en usage, et donc indisponible, tel que rapporté par l’hôte.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pMemoryLoad`  
 [out] Un pointeur sur le pourcentage approximatif de la mémoire physique totale qui est actuellement utilisé.  
  
 `pAvailableBytes`  
 [out] Un pointeur sur le nombre d’octets disponibles à l’heure courante (CLR).  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`GetMemoryLoad`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un état dans lequel il ne peut pas exécuter le code géré ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel s’est fait chronométrer.|  
|HOST_E_NOT_OWNER|L’appelant n’est pas propriétaire de la serrure.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un fil bloqué ou une fibre l’attendait.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Lorsqu’une méthode revient E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels ultérieurs aux méthodes d’hébergement reviennent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Notes   
 `GetMemoryLoad`enveloppe la fonction `GlobalMemoryStatus` Win32. La valeur `pMemoryLoad` de est `dwMemoryLoad` l’équivalent `MEMORYSTATUS` du `GlobalMemoryStatus`champ dans la structure restitué de .  
  
 Le temps d’exécution utilise la valeur de retour comme un heuristique pour le collecteur d’ordures. Par exemple, si l’hôte signale que la majorité de la mémoire est utilisée, le collecteur d’ordures peut choisir de recueillir de plusieurs générations pour augmenter la quantité de mémoire qui peut potentiellement devenir disponible.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor  
  
 **Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.GC?displayProperty=nameWithType>
- [IHostMemoryManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
