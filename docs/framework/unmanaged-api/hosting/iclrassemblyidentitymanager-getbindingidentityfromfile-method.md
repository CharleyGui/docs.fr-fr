---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromFile, méthode
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
helpviewer_keywords:
- GetBindingIdentityFromFile method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentifyFromFile method [.NET Framework hosting]
ms.assetid: 7797562d-7b4c-4bd9-8b93-f35e0e2869e4
topic_type:
- apiref
ms.openlocfilehash: 5b537d59014afa783d3f8c5046cc02dad7ea7740
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615993"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a>ICLRAssemblyIdentityManager::GetBindingIdentityFromFile, méthode
Obtient les données de liaison de l’identité de l’assembly pour l’assembly dans le chemin d’accès au fichier spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwzFilePath`  
 dans Chemin d’accès au fichier à évaluer.  
  
 `dwFlags`  
 dans Valeur de l’énumération [ECLRAssemblyIdentityFlags,](eclrassemblyidentityflags-enumeration.md) qui indique le type d’identité d’un assembly. Fourni pour une extensibilité future. CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT est la seule valeur prise en charge par la version 2,0 du common language runtime (CLR).  
  
 `pwzBuffer`  
 à Mémoire tampon contenant les données d’identité de l’assembly opaque.  
  
 `pcchBufferSize`  
 [in, out] Pointeur vers la taille de `pwzBuffer` .  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Retour réussi de la méthode.|  
|E_INVALIDARG|Le fourni `pwzFilePath` a la valeur null.|  
|ERROR_INSUFFICIENT_BUFFER|La taille de `pwzBuffer` est trop petite.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Notes  
 `GetBindingIdentityFromFile`est généralement appelée deux fois. Le premier appel fournit une valeur null pour `pwzBuffer` , et la méthode retourne la taille appropriée dans `pcchBufferSize` . Le deuxième appel fournit une mémoire tampon allouée de manière appropriée, et la méthode retourne avec les données de mémoire tampon en cours à l’achèvement.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRAssemblyIdentityManager, interface](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList, interface](iclrassemblyreferencelist-interface.md)
- [ICLRHostBindingPolicyManager, interface](iclrhostbindingpolicymanager-interface.md)
