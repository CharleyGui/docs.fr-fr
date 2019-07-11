---
title: IHostMAlloc::Free, méthode
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Free
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Free
helpviewer_keywords:
- IHostMAlloc::Free method [.NET Framework hosting]
- Free method, IHostMAlloc interface [.NET Framework hosting]
ms.assetid: c89abf5b-1120-4437-8b57-4a99fb3ae7f9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6de6d12322e29ddcc854f6b9aed0a4790af089e9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780723"
---
# <a name="ihostmallocfree-method"></a>IHostMAlloc::Free, méthode
Libère la mémoire qui a été alloué à l’aide de la [Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) (fonction).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pMem`  
 [in] Pointeur vers la mémoire à libérer.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`Free` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_INVALIDOPERATION|Une tentative a été effectuée pour libérer la mémoire qui n’était pas alloué via l’hôte.|  
  
## <a name="remarks"></a>Notes  
 Si le `pMem` paramètre fait référence à une région de mémoire qui n’était pas alloué à l’aide d’un appel à `Alloc`, l’hôte doit alors retourner HOST_E_INVALIDOPERATION.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IHostMemoryManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [IHostMalloc, interface](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
