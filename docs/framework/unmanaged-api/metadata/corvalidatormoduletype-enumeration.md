---
title: CorValidatorModuleType, énumération
ms.date: 03/30/2017
api_name:
- CorValidatorModuleType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorValidatorModuleType
helpviewer_keywords:
- CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type:
- apiref
ms.openlocfilehash: 2fb7f11677870f7d53439f1867f167fabe70b22a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723842"
---
# <a name="corvalidatormoduletype-enumeration"></a>CorValidatorModuleType, énumération

Spécifie le type d’un module.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum  
{  
    ValidatorModuleTypeInvalid  = 0x0,  
    ValidatorModuleTypeMin      = 0x00000001,  
    ValidatorModuleTypePE       = 0x00000001,  
    ValidatorModuleTypeObj      = 0x00000002,  
    ValidatorModuleTypeEnc      = 0x00000003,  
    ValidatorModuleTypeIncr     = 0x00000004,  
    ValidatorModuleTypeMax      = 0x00000004  
} CorValidatorModuleType;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|Le type du module n’est pas valide.|  
|`ValidatorModuleTypeMin`|Valeur minimale de l' `CorValidatorModuleType` énumération.|  
|`ValidatorModuleTypePE`|Le module est un fichier exécutable portable (PE).|  
|`ValidatorModuleTypeObj`|Le module est un fichier. obj.|  
|`ValidatorModuleTypeEnc`|Le module est une session de débogueur modifier et continuer.|  
|`ValidatorModuleTypeIncr`|Le module est un module qui a été généré de manière incrémentielle.|  
|`ValidatorModuleTypeMax`|Valeur maximale de l' `CorValidatorModuleType` énumération.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](metadata-enumerations.md)
