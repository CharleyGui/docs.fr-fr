---
title: ICLRHostProtectionManager::SetProtectedCategories, méthode
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetProtectedCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetProtectedCategories
helpviewer_keywords:
- SetProtectedCategories method [.NET Framework hosting]
- ICLRHostProtectionManager::SetProtectedCategories method [.NET Framework hosting]
ms.assetid: fa21dc7b-5da7-440b-b59e-9180e5181f9d
topic_type:
- apiref
ms.openlocfilehash: 0557a8f1c7c495950933a44cacd23ada8e84964e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730498"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a>ICLRHostProtectionManager::SetProtectedCategories, méthode

Spécifie les catégories de types et de membres managés dont l’exécution doit être bloquée dans du code de confiance partielle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `categories`  
 dans Combinaison de valeurs [EApiCategories](eapicategories-enumeration.md) indiquant les catégories de types et de membres managés dont l’exécution doit être bloquée dans du code de confiance partielle.  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetProtectedCategories` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Remarques  

 Chaque `EApiCategories` valeur fait référence à une liste de types et de membres managés. L' `EApiCategories` énumération et la `SetProtectedCategories` méthode sont directement liées à la <xref:System.Security.Permissions.HostProtectionAttribute> classe managée, qui est utilisée pour marquer les types et les membres managés qui exposent les fonctionnalités correspondant aux catégories décrites par `EApiCategories` . Pour plus d’informations, consultez <xref:System.Security.Permissions.HostProtectionAttribute> et l' <xref:System.Security.Permissions.HostProtectionResource> énumération, qui correspond directement à `EApiCategories` .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Security.Permissions.HostProtectionAttribute>
- <xref:System.Security.Permissions.HostProtectionResource>
- [EApiCategories, énumération](eapicategories-enumeration.md)
- [ICLRControl, interface](iclrcontrol-interface.md)
- [ICLRHostProtectionManager, interface](iclrhostprotectionmanager-interface.md)
