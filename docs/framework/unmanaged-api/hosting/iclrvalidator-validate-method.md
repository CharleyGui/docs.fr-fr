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
ms.openlocfilehash: 427895ffea94e6c657d775ebdeb8571070a61c6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178060"
---
# <a name="iclrvalidatorvalidate-method"></a>ICLRValidator::Validate, méthode
Valide la langue intermédiaire portable exécutable (PE) ou Microsoft (MSIL) dans le fichier spécifié.  
  
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
 [dans] Un pointeur `IVEHandler` à une instance qui gère les erreurs de validation.  
  
 `ulAppDomainId`  
 [dans] L’identifiant pour <xref:System.AppDomain>le courant .  
  
 `ulFlags`  
 [dans] Une combinaison de valeurs [ValidatorFlags,](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) indiquant le type de validation qui doit être effectuée.  
  
 `ulMaxError`  
 [dans] Le nombre maximum d’erreurs à autoriser avant de sortir de la validation.  
  
 `token`  
 [in] Inutilisé.  
  
 `fileName`  
 [dans] Le nom du fichier à valider.  
  
 `pe`  
 [dans] Un pointeur vers le tampon de fichier.  
  
 `ulSize`  
 [dans] La taille, dans les octets, du fichier à valider.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`Validate`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|L’heure courante de l’exécution de la langue (CLR) n’a pas été chargée dans un processus, ou le CLR est dans un état où il ne peut pas exécuter le code géré ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel s’est fait chronométrer.|  
|HOST_E_NOT_OWNER|L’appelant n’est pas propriétaire de la serrure.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un fil bloqué ou une fibre l’attendait.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Lorsqu’une méthode revient E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels ultérieurs aux méthodes d’hébergement reviennent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** IValidator.idl, IValidator.h  
  
 **Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRValidator, interface](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
