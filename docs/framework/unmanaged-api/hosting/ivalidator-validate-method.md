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
ms.openlocfilehash: 688abd210cca193bf03c40f000b74ecb66eb8ede
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008545"
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
 dans Pointeur vers une `IVEHandler` instance qui gère les erreurs de validation.  
  
 `pAppDomain`  
 dans Pointeur vers le domaine d’application dans lequel le fichier est chargé.  
  
 `ulFlags`  
 dans Combinaison d’opérations de bits de valeurs [ValidatorFlags,](validatorflags-enumeration.md) , indiquant les validations qui doivent être effectuées.  
  
 `ulMaxError`  
 dans Nombre maximal d’erreurs à autoriser avant de quitter la validation.  
  
 `token`  
 [in] Non utilisé.  
  
 `fileName`  
 dans Chaîne qui spécifie le nom du fichier à valider.  
  
 `pe`  
 dans Pointeur vers la mémoire tampon dans laquelle le fichier est stocké.  
  
 `ulSize`  
 dans Taille, en octets, du fichier à valider.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** IValidator. idl, IValidator. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
