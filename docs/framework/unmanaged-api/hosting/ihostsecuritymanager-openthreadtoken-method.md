---
title: IHostSecurityManager::OpenThreadToken, méthode
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.OpenThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type:
- apiref
ms.openlocfilehash: 30ec8cc8bbbd6d49f89cd67371c3326c0cb0df9a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680610"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a>IHostSecurityManager::OpenThreadToken, méthode

Ouvre le jeton d’accès discrétionnaire associé au thread en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,
    [in]  BOOL     bOpenAsSelf,
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `dwDesiredAccess`  
 dans Masque des valeurs d’accès qui spécifient les types d’accès demandés au jeton de thread. Ces valeurs sont définies dans la `OpenThreadToken` fonction Win32. Les types d’accès demandés sont conciliés par rapport à la liste de contrôle d’accès discrétionnaire (DACL) du jeton pour déterminer les types d’accès à accorder ou refuser.  
  
 `bOpenAsSelf`  
 [in] `true` pour spécifier que le contrôle d’accès doit être effectué à l’aide du contexte de sécurité du processus pour le thread appelant ; `false` pour spécifier que le contrôle d’accès doit être effectué à l’aide du contexte de sécurité du thread appelant lui-même. Si le thread emprunte l’identité d’un client, le contexte de sécurité peut être celui d’un processus client.  
  
 `phThreadToken`  
 à Pointeur vers le jeton d’accès récemment ouvert.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`OpenThreadToken` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Remarques  

 `IHostSecurityManager::OpenThreadToken` se comporte de la même façon que la fonction Win32 correspondante du même nom, sauf que la fonction Win32 permet à l’appelant de passer un handle à un thread arbitraire, tandis que `IHostSecurityManager::OpenThreadToken` ouvre uniquement le jeton associé au thread appelant.  
  
 Le `HANDLE` type n’est pas conforme à com, autrement dit, sa taille est spécifique au système d’exploitation et il nécessite un marshaling personnalisé. Ainsi, ce jeton est destiné à être utilisé uniquement dans le processus, entre le CLR et l’hôte.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IHostSecurityContext, interface](ihostsecuritycontext-interface.md)
- [IHostSecurityManager, interface](ihostsecuritymanager-interface.md)
