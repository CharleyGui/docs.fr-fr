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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a0764cb212a95412a4dcf9455b7648ee863951e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767668"
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
 [in] Pointeur vers l’adresse de départ de la région à allouer.  
  
 `dwSize`  
 [in] La taille, en octets, de la région.  
  
 `flAllocationType`  
 [in] Le type d’allocation de mémoire.  
  
 `flProtect`  
 [in] Protection de la mémoire pour la région de pages à allouer.  
  
 `dwCriticalLevel`  
 [in] Un [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) valeur qui indique l’impact d’un échec d’allocation.  
  
 `ppMem`  
 [out] Pointeur vers l’adresse de départ de la mémoire allouée, ou null si la demande n’a pas pu être satisfaite.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`VirtualAlloc` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Mémoire était insuffisante pour terminer la demande d’allocation|  
  
## <a name="remarks"></a>Notes  
 Vous réservez une région dans l’espace d’adressage de votre processus en appelant `VirtualAlloc`. Le `pAddress` paramètre contient l’adresse de début du bloc de mémoire souhaitée. Ce paramètre est généralement défini sur null. Le système d’exploitation conserve un enregistrement des plages d’adresses libres disponibles pour votre processus. Un `pAddress` NULL comme valeur prescrit au système de réserver la région chaque fois qu’il juge. Vous pouvez également fournir une adresse de départ spécifique pour le bloc de mémoire. Dans les deux cas, le paramètre de sortie `ppMem` est retourné comme un pointeur vers la mémoire allouée. La fonction elle-même retourne une valeur HRESULT.  
  
 Win32 `VirtualAlloc` fonction n’a pas un `ppMem` paramètre et retourne le pointeur vers la mémoire allouée à la place. Pour plus d’informations, consultez la documentation de la plateforme de Windows.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IHostMemoryManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
