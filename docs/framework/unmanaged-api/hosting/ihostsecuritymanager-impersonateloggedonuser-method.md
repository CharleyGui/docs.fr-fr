---
title: IHostSecurityManager::ImpersonateLoggedOnUser, méthode
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.ImpersonateLoggedOnUser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::ImpersonateLoggedOnUser
helpviewer_keywords:
- ImpersonateLoggedOnUser method [.NET Framework hosting]
- IHostSecurityManager::ImpersonateLoggedOnUser method [.NET Framework hosting]
ms.assetid: acc49ba0-f1d9-45ad-871f-9d053a89dcbe
topic_type:
- apiref
ms.openlocfilehash: dd1d1af8072ac11e37bd2eb1a47d76b12685cb31
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724778"
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a>IHostSecurityManager::ImpersonateLoggedOnUser, méthode

Demande que le code soit exécuté à l’aide des informations d’identification de l’identité de l’utilisateur actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `hToken`  
 dans Jeton représentant les informations d’identification de l’utilisateur dont l’identité doit être empruntée.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`ImpersonateLoggedOnUser` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Remarques  

 Appelez `LogonUser` ou une fonction Win32 associée pour obtenir un handle des informations d’identification de l’identité de l’utilisateur actuel.  
  
 Le `HANDLE` type n’est pas conforme à com, autrement dit, sa taille est spécifique à un système d’exploitation et il nécessite un marshaling personnalisé. Ainsi, ce jeton est destiné à être utilisé uniquement dans le processus, entre le CLR et l’hôte.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IHostSecurityContext, interface](ihostsecuritycontext-interface.md)
- [IHostSecurityManager, interface](ihostsecuritymanager-interface.md)
- [RevertToSelf, méthode](ihostsecuritymanager-reverttoself-method.md)
