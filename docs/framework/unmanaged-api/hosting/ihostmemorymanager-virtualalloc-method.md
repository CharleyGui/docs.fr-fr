---
title: IHostMemoryManager::VirtualAlloc, méthode
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type:
- apiref
ms.openlocfilehash: a2deabc5f1c7ea0f42b6d8ec3944d984854ae571
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731278"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a>IHostMemoryManager::VirtualAlloc, méthode

Sert de wrapper logique pour la fonction Win32 correspondante. L’implémentation Win32 de `VirtualAlloc` réserve ou valide une région de pages dans l’espace d’adressage virtuel du processus appelant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pAddress`  
 dans Pointeur vers l’adresse de début de la région à allouer.  
  
 `dwSize`  
 dans Taille, en octets, de la région.  
  
 `flAllocationType`  
 dans Type d’allocation de mémoire.  
  
 `flProtect`  
 dans Protection de la mémoire pour la région de pages à allouer.  
  
 `dwCriticalLevel`  
 dans Valeur [EMemoryCriticalLevel,](ememorycriticallevel-enumeration.md) qui indique l’impact d’un échec d’allocation.  
  
 `ppMem`  
 à Pointeur vers l’adresse de départ de la mémoire allouée, ou null si la demande n’a pas pu être satisfaite.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`VirtualAlloc` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Mémoire disponible insuffisante pour terminer la demande d’allocation|  
  
## <a name="remarks"></a>Remarques  

 Vous réservez une région dans l’espace d’adressage de votre processus en appelant `VirtualAlloc` . Le `pAddress` paramètre contient l’adresse de début du bloc de mémoire souhaité. Ce paramètre a généralement la valeur null. Le système d’exploitation conserve un enregistrement des plages d’adresses disponibles pour votre processus. `pAddress`La valeur null indique au système de réserver la région où elle est visible. Vous pouvez également fournir une adresse de départ spécifique pour le bloc de mémoire. Dans les deux cas, le paramètre de sortie `ppMem` est retourné en tant que pointeur vers la mémoire allouée. La fonction elle-même retourne une valeur HRESULT.  
  
 La `VirtualAlloc` fonction Win32 n’a pas de `ppMem` paramètre et retourne le pointeur vers la mémoire allouée à la place. Pour plus d’informations, consultez la documentation de la plateforme Windows.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IHostMemoryManager, interface](ihostmemorymanager-interface.md)
