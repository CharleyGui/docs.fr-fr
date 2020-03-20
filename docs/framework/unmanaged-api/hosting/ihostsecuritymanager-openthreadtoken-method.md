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
ms.openlocfilehash: 11d042ea9eecc8d428761da6eaa15f7c2907ebd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176264"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a>IHostSecurityManager::OpenThreadToken, méthode
Ouvre le jeton d’accès discrétionnaire associé au fil d’exécution actuel.  
  
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
 [dans] Masque de valeurs d’accès qui spécifient les types d’accès demandés au jeton de thread. Ces valeurs sont définies `OpenThreadToken` dans la fonction Win32. Les types d’accès demandés sont conciliés avec la liste discrétionnaire de contrôle d’accès (DACL) du jeton afin de déterminer quels types d’accès à l’octroi ou au refus.  
  
 `bOpenAsSelf`  
 [dans] `true` spécifier que la vérification d’accès doit être effectuée en utilisant le contexte de sécurité du processus pour le thread d’appel; `false` spécifier que la vérification d’accès doit être effectuée en utilisant le contexte de sécurité du fil d’appel lui-même. Si le thread se fait passer pour un client, le contexte de sécurité peut être celui d’un processus client.  
  
 `phThreadToken`  
 [out] Un pointeur sur le jeton d’accès nouvellement ouvert.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`OpenThreadToken`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|L’heure courante de l’exécution de la langue (CLR) n’a pas été chargée dans un processus, ou le CLR est dans un état où il ne peut pas exécuter le code géré ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel s’est fait chronométrer.|  
|HOST_E_NOT_OWNER|L’appelant n’est pas propriétaire de la serrure.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un fil bloqué ou une fibre l’attendait.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Lorsqu’une méthode revient E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels ultérieurs aux méthodes d’hébergement reviennent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Notes   
 `IHostSecurityManager::OpenThreadToken`se comporte de la même manière que la fonction Win32 correspondante du même nom, sauf que la fonction `IHostSecurityManager::OpenThreadToken` Win32 permet à l’appelant de passer dans une poignée à un thread arbitraire, tout en n’ouvrant que le jeton associé au fil d’appel.  
  
 Le `HANDLE` type n’est pas conforme à com, c’est-à-dire que sa taille est spécifique au système d’exploitation, et il nécessite un marshaling personnalisé. Ainsi, ce jeton n’est utilisé que dans le processus, entre le CLR et l’hôte.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor  
  
 **Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IHostSecurityContext, interface](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [IHostSecurityManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
