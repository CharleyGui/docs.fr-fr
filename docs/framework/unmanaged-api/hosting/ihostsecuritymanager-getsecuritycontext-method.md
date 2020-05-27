---
title: IHostSecurityManager::GetSecurityContext, méthode
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.GetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::GetSecurityContext
helpviewer_keywords:
- GetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::GetSecurityContext method [.NET Framework hosting]
ms.assetid: 958970d6-f6a2-4b84-b32a-f555cbaf8f61
topic_type:
- apiref
ms.openlocfilehash: e43eb7ebfc367e7d4a7a209a5037fcc4566cd7ec
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803925"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a>IHostSecurityManager::GetSecurityContext, méthode
Obtient le [IHostSecurityContext](ihostsecuritycontext-interface.md) demandé à partir de l’hôte.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `eContextType`  
 dans L’une des valeurs [EContextType,](econtexttype-enumeration.md) , indiquant le type de contexte de sécurité à retourner.  
  
 `ppSecurityContext`  
 à Adresse d’un pointeur d’interface vers le `IHostSecurityContext` de `eContextType` .  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`GetSecurityContext`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Notes  
 Un hôte peut contrôler tout l’accès du code aux jetons de thread à la fois par le CLR et le code utilisateur. Il peut également s’assurer que les informations de contexte de sécurité complètes sont transmises sur des opérations asynchrones ou des points de code avec accès restreint au code. `IHostSecurityContext`encapsule ces informations de contexte de sécurité, qui sont opaques pour le CLR. Le CLR capture ces informations et les déplace dans la répartition des éléments de travail du pool de threads, l’exécution du finaliseur et la construction des modules et des classes.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [EContextType, énumération](econtexttype-enumeration.md)
- [IHostSecurityContext, interface](ihostsecuritycontext-interface.md)
- [IHostSecurityManager, interface](ihostsecuritymanager-interface.md)
