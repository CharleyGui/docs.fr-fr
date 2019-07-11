---
title: IHostMemoryManager::VirtualFree, méthode
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualFree
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualFree
helpviewer_keywords:
- IHostMemoryManager::VirtualFree method [.NET Framework hosting]
- VirtualFree method [.NET Framework hosting]
ms.assetid: 1a436e89-eb28-4d15-bcf1-a072f86dbd99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a60d954cf4331d46a4667afba1e9dee0d214f0a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767680"
---
# <a name="ihostmemorymanagervirtualfree-method"></a>IHostMemoryManager::VirtualFree, méthode
Sert de wrapper logique pour la fonction Win32 correspondante. L’implémentation Win32 de `VirtualFree` libère, annule la validation, ou bien libère et annule la validation d’une région de pages au sein de l’espace d’adressage virtuel du processus appelant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `lpAddress`  
 [in] Pointeur vers l’adresse de base des pages de mémoire virtuelle à libérer.  
  
 `dwSize`  
 [in] La taille, en octets, de la région à libérer.  
  
 `dwFreeType`  
 [in] Le type d’opération de libération.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`VirtualFree` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_INVALIDOPERATION|Une tentative a été effectuée pour libérer la mémoire qui n’était pas alloué via l’hôte.|  
  
## <a name="remarks"></a>Notes  
 `VirtualFree` Libère des pages de mémoire virtuelle associées à la `lpAddress` paramètre via un appel antérieur à la [IHostMemoryManager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) (fonction). Tente de libérer de la mémoire qui n’était pas alloué via l’hôte doit retourner HOST_E_INVALIDOPERATION.  
  
 La sémantique est identique à ceux de l’implémentation Win32 de `VirtualFree`. Pour plus d’informations, consultez la documentation de la plateforme de Windows.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IHostMemoryManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [IHostMalloc, interface](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
