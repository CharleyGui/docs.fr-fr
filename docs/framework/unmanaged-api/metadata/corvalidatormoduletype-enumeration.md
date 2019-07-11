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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 04bed418d96658e29328cf2ce6bba445639b437f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750757"
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
|`ValidatorModuleTypeInvalid`|Le module est un type non valide.|  
|`ValidatorModuleTypeMin`|La valeur minimale de la `CorValidatorModuleType` enum.|  
|`ValidatorModuleTypePE`|Le module est un fichier exécutable portable (PE).|  
|`ValidatorModuleTypeObj`|Le module est un fichier .obj.|  
|`ValidatorModuleTypeEnc`|Le module est une session de débogueur modifier et continuer.|  
|`ValidatorModuleTypeIncr`|Le module est un qui a été générée de façon incrémentielle.|  
|`ValidatorModuleTypeMax`|La valeur maximale de la `CorValidatorModuleType` enum.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
