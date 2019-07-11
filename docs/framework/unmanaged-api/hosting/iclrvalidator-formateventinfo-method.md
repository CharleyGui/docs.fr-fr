---
title: ICLRValidator::FormatEventInfo, méthode
ms.date: 03/30/2017
api_name:
- ICLRValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::FormatEventInfo
helpviewer_keywords:
- FormatEventInfo method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::FormatEventInfo method [.NET Framework hosting]
ms.assetid: 808e1f1d-52f4-47c4-83cc-dcf47d075219
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7354536db483ad93d29fef29745af44a6f90884c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779932"
---
# <a name="iclrvalidatorformateventinfo-method"></a>ICLRValidator::FormatEventInfo, méthode
Obtient un message détaillé sur l’erreur de validation spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `hVECode`  
 [in] La valeur HRESULT qui a été passée au gestionnaire d’erreurs de validation.  
  
 `Context`  
 [in] Un `VEContext` instance qui contient des informations de contexte sur les erreurs de validation.  
  
 `msg`  
 [in, out] Le message d’erreur convivial.  
  
 `ulMaxLength`  
 [in] La longueur maximale du message d’erreur.  
  
 `psa`  
 [in] Un tableau sécurisé de paramètres supplémentaires à utiliser dans le message.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`FormatEventInfo` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** IValidator.idl, IValidator.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRErrorReportingManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [ICLRValidator, interface](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
