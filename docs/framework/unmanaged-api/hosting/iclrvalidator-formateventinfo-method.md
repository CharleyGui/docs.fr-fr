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
ms.openlocfilehash: 935d8e9fa3ed15be03c6cd05b1bc3c4919d0cc2b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127852"
---
# <a name="iclrvalidatorformateventinfo-method"></a>ICLRValidator::FormatEventInfo, méthode
Obtient un message détaillé sur l’erreur de validation spécifiée.  
  
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
 dans Valeur HRESULT qui a été passée au gestionnaire d’erreurs de validation.  
  
 `Context`  
 dans Instance `VEContext` qui contient des informations de contexte sur les erreurs de validation.  
  
 `msg`  
 [in, out] Message d’erreur convivial.  
  
 `ulMaxLength`  
 dans Longueur maximale du message d’erreur.  
  
 `psa`  
 dans Tableau sécurisé de paramètres supplémentaires à utiliser dans le message.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`FormatEventInfo` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** IValidator. idl, IValidator. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRErrorReportingManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [ICLRValidator, interface](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
