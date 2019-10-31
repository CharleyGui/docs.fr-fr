---
title: IHostMemoryManager::VirtualQuery, méthode
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualQuery
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualQuery
helpviewer_keywords:
- IHostMemoryManager::VirtualQuery method [.NET Framework hosting]
- VirtualQuery method [.NET Framework hosting]
ms.assetid: 757af1e6-b9e8-49e7-b5db-342be3aa205f
topic_type:
- apiref
ms.openlocfilehash: 00ec0b92a9f7151ee9b831c85548c4f61d87af68
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192032"
---
# <a name="ihostmemorymanagervirtualquery-method"></a>IHostMemoryManager::VirtualQuery, méthode
Sert de wrapper logique pour la fonction Win32 correspondante. L’implémentation Win32 de `VirtualQuery` récupère des informations sur une plage de pages dans l’espace d’adressage virtuel du processus appelant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `lpAddress`  
 dans Pointeur vers l’adresse de la mémoire virtuelle à interroger.  
  
 `lpBuffer`  
 à Pointeur vers une structure qui contient des informations sur la région de mémoire spécifiée.  
  
 `dwLength`  
 dans Taille, en octets, de la mémoire tampon vers laquelle `lpBuffer` pointe.  
  
 `pResult`  
 à Pointeur vers le nombre d’octets retournés par la mémoire tampon d’informations.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`VirtualQuery` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Notes  
 `VirtualQuery` fournit des informations sur une plage de pages dans l’espace d’adressage virtuel du processus appelant. Cette implémentation affecte à la valeur du paramètre `pResult` le nombre d’octets retournés dans la mémoire tampon d’informations et retourne une valeur HRESULT. Dans la fonction `VirtualQuery` Win32, la valeur de retour est la taille de la mémoire tampon. Pour plus d’informations, consultez la documentation de la plateforme Windows.  
  
> [!IMPORTANT]
> L’implémentation de `VirtualQuery` du système d’exploitation n’entraîne pas de blocage et peut s’exécuter jusqu’à la fin avec les threads aléatoires suspendus dans le code utilisateur. Soyez très prudent lors de l’implémentation d’une version hébergée de cette méthode.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IHostMemoryManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
