---
title: IValidator::Validate, méthode
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
ms.openlocfilehash: 8ae47eac713fbee30ea543538957b12460b8e1fc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123275"
---
# <a name="ivalidatorvalidate-method"></a>IValidator::Validate, méthode
Valide le fichier exécutable portable (PE) ou le fichier MSIL (Microsoft Intermediate Language) spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `veh`  
 dans Pointeur vers une instance de `IVEHandler` qui gère les erreurs de validation.  
  
 `pAppDomain`  
 dans Pointeur vers le domaine d’application dans lequel le fichier est chargé.  
  
 `ulFlags`  
 dans Combinaison d’opérations de bits de valeurs [ValidatorFlags,](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) , indiquant les validations qui doivent être effectuées.  
  
 `ulMaxError`  
 dans Nombre maximal d’erreurs à autoriser avant de quitter la validation.  
  
 `token`  
 dans Non utilisé.  
  
 `fileName`  
 dans Chaîne qui spécifie le nom du fichier à valider.  
  
 `pe`  
 dans Pointeur vers la mémoire tampon dans laquelle le fichier est stocké.  
  
 `ulSize`  
 dans Taille, en octets, du fichier à valider.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** IValidator. idl, IValidator. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
