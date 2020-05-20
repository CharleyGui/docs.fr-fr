---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromStream, méthode
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream
helpviewer_keywords:
- GetBindingIdentityFromStream method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream method [.NET Framework hosting]
ms.assetid: 40123b30-a589-46b3-95d3-af7b2b0baa05
topic_type:
- apiref
ms.openlocfilehash: abba19600616cad8ba3377ae2ebb23459449d2a0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615980"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a>ICLRAssemblyIdentityManager::GetBindingIdentityFromStream, méthode
Obtient les données d’identité d’assembly canoniques pour l’assembly dans le flux spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pStream`  
 dans Flux d’assembly à évaluer.  
  
 `dwFlags`  
 dans Fourni pour une extensibilité future. CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT est la seule valeur prise en charge par la version actuelle du common language runtime (CLR).  
  
 `pwzBuffer`  
 à Mémoire tampon contenant les données d’identité de l’assembly opaque.  
  
 `pcchBufferSize`  
 [in, out] Taille de `pwzBuffer` .  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Retour réussi de la méthode.|  
|E_INVALIDARG|Le fourni `pStream` a la valeur null.|  
|ERROR_INSUFFICIENT_BUFFER|La taille de `pwzBuffer` est trop petite.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
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
- [ICLRAssemblyReferenceList, interface](iclrassemblyreferencelist-interface.md)
