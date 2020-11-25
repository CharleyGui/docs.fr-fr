---
title: ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList, méthode
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetCLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList
helpviewer_keywords:
- GetClrAssemblyReferenceList method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList method [.NET Framework hosting]
ms.assetid: cb5ffae5-287b-4a87-9ca8-7ce3ae0601b7
topic_type:
- apiref
ms.openlocfilehash: cfc384a71ac7e91181bdec09f0d385bacbe31753
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716666"
---
# <a name="iclrassemblyidentitymanagergetclrassemblyreferencelist-method"></a>ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList, méthode

Obtient un pointeur d’interface vers une instance [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) à partir de la liste d’identités d’assembly partielle fournie.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT  GetCLRAssemblyReferenceList (  
    [in] LPCWSTR *ppwzAssemblyReferences,  
    [in] DWORD    dwNumOfReferences,  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `ppwzAssemblyReferences`  
 dans Tableau de chaînes terminées par le caractère null sous la forme « name, Property = value... » qui spécifient une liste d’identités d’assembly partielles.  
  
 `dwNumOfReferences`  
 dans Nombre d’éléments dans `ppwzAssemblyReferences` .  
  
 `ppReferenceList`  
 à Pointeur d’interface vers un `ICLRAssemblyReferenceList` objet qui contient les données d’identité de l’assembly pour la liste d’assemblys spécifiée dans `ppwzAssemblyReferences` .  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Retour réussi de la méthode.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRAssemblyIdentityManager, interface](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList, interface](iclrassemblyreferencelist-interface.md)
