---
title: ICLRValidator::Validate, méthode
ms.date: 03/30/2017
api_name:
- ICLRValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5fbf83690f616556774e8f279e1077fccdb8baf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779913"
---
# <a name="iclrvalidatorvalidate-method"></a>ICLRValidator::Validate, méthode
Valide le fichier exécutable portable (PE) ou Microsoft intermediate language (MSIL) dans le fichier spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler        *veh,  
    [in] unsigned long      ulAppDomainId,  
    [in] unsigned long      ulFlags,  
    [in] unsigned long      ulMaxError,  
    [in] unsigned long      token,  
    [in] LPWSTR             fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long      ulSize  
);      
```  
  
## <a name="parameters"></a>Paramètres  
 `veh`  
 [in] Un pointeur vers un `IVEHandler` instance qui gère les erreurs de validation.  
  
 `ulAppDomainId`  
 [in] L’identificateur actuel <xref:System.AppDomain>.  
  
 `ulFlags`  
 [in] Une combinaison de [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) valeurs indiquant le genre de validation doit être effectuée.  
  
 `ulMaxError`  
 [in] Le nombre maximal d’erreurs autorisées avant de quitter la validation.  
  
 `token`  
 [in] Inutilisé.  
  
 `fileName`  
 [in] Le nom du fichier à valider.  
  
 `pe`  
 [in] Pointeur vers la mémoire tampon de fichier.  
  
 `ulSize`  
 [in] La taille, en octets, du fichier à valider.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`Validate` retourné avec succès.|  
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

- [ICLRValidator, interface](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
