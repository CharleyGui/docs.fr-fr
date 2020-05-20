---
title: ICLRAssemblyIdentityManager::IsStronglyNamed, méthode
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.IsStronglyNamed
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::IsStronglyNamed
helpviewer_keywords:
- IsStronglyNamed method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::IsStronglyNamed method [.NET Framework hosting]
ms.assetid: 954bd386-2076-4d00-9d46-38c728aa9cab
topic_type:
- apiref
ms.openlocfilehash: d388f366671f50c3dcb3bd9d387300dd1bbb168f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615902"
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a>ICLRAssemblyIdentityManager::IsStronglyNamed, méthode
Obtient une valeur qui indique si l’assembly spécifié porte un nom fort.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwzAssemblyIdentity`  
 dans Données d’identité de l’assembly canonique opaque de l’assembly à évaluer.  
  
 `pbIsStronglyNamed`  
 [out] `true` , si l’assembly référencé par le `pwzAssemblyIdentity` paramètre porte un nom fort ; sinon, `false` .  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Retour réussi de la méthode.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRAssemblyIdentityManager, interface](iclrassemblyidentitymanager-interface.md)
