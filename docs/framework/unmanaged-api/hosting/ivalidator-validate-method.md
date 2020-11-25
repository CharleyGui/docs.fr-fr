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
ms.openlocfilehash: 3c59114f78af1aa8705318af093e47d4f03a82ce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699142"
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
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** IValidator. idl, IValidator. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
