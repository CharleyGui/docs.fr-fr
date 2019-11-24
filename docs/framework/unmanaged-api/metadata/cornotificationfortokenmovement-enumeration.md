---
title: CorNotificationForTokenMovement, énumération
ms.date: 03/30/2017
api_name:
- CorNotificationForTokenMovement
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNotificationForTokenMovement
helpviewer_keywords:
- CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type:
- apiref
ms.openlocfilehash: 411fad0accb59431f776c5bd66e8bd3027ddd907
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450147"
---
# <a name="cornotificationfortokenmovement-enumeration"></a>CorNotificationForTokenMovement, énumération
Spécifie les notifications qui seront envoyées au client de l’API de métadonnées lorsqu’un remappage de jeton se produit.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorNotificationForTokenMovement {  
  
    MDNotifyDefault             = 0x0000000f,  
    MDNotifyAll                 = 0xffffffff,  
    MDNotifyNone                = 0x00000000,  
    MDNotifyMethodDef           = 0x00000001,  
    MDNotifyMemberRef           = 0x00000002,  
    MDNotifyFieldDef            = 0x00000004,  
    MDNotifyTypeRef             = 0x00000008,  
  
    MDNotifyTypeDef             = 0x00000010,  
    MDNotifyParamDef            = 0x00000020,  
    MDNotifyInterfaceImpl       = 0x00000040,  
    MDNotifyProperty            = 0x00000080,  
    MDNotifyEvent               = 0x00000100,  
    MDNotifySignature           = 0x00000200,  
    MDNotifyTypeSpec            = 0x00000400,  
    MDNotifyCustomAttribute     = 0x00000800,  
    MDNotifySecurityValue       = 0x00001000,  
    MDNotifyPermission          = 0x00002000,  
    MDNotifyModuleRef           = 0x00004000,  
  
    MDNotifyNameSpace           = 0x00008000,  
  
    MDNotifyAssemblyRef         = 0x01000000,  
    MDNotifyFile                = 0x02000000,  
    MDNotifyExportedType        = 0x04000000,  
    MDNotifyResource            = 0x08000000  
  
} CorNotificationForTokenMovement;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`MDNotifyDefault`|Notifier quand des jetons `mdTypeRef`, `mdMethodDef`, `mdMemberRef`ou `mdFieldDef` se déplacent.|  
|`MDNotifyAll`|Notifier quand un jeton est déplacé.|  
|`MDNotifyNone`|Ne pas avertir quand les jetons sont déplacés.|  
|`MDNotifyMethodDef`|Notifier lorsqu’un jeton `mdMethodDef` se déplace.|  
|`MDNotifyMemberRef`|Notifier lorsqu’un jeton `mdMemberRef` se déplace.|  
|`MDNotifyFieldDef`|Notifier lorsqu’un jeton `mdFieldDef` se déplace.|  
|`MDNotifyTypeRef`|Notifier lorsqu’un jeton `mdTypeRef` se déplace.|  
|`MDNotifyTypeDef`|Notifier lorsqu’un jeton `mdTypeDef` se déplace.|  
|`MDNotifyParamDef`|Notifier lorsqu’un jeton `mdParamDef` se déplace.|  
|`MDNotifyInterfaceImpl`|Notifier lorsqu’un jeton `mdInterfaceImpl` se déplace.|  
|`MDNotifyProperty`|Notifier lorsqu’un jeton `mdProperty` se déplace.|  
|`MDNotifyEvent`|Notifier lorsqu’un jeton `mdEvent` se déplace.|  
|`MDNotifySignature`|Notifier lorsqu’un jeton `mdSignature` se déplace.|  
|`MDNotifyTypeSpec`|Notifier lorsqu’un jeton `mdTypeSpec` se déplace.|  
|`MDNotifyCustomAttribute`|Notifier lorsqu’un jeton `mdCustomAttribute` se déplace.|  
|`MDNotifySecurityValue`|Notifier lorsqu’un jeton `mdSecurityValue` se déplace.|  
|`MDNotifyPermission`|Notifier lorsqu’un jeton `mdPermission` se déplace.|  
|`MDNotifyModuleRef`|Notifier lorsqu’un jeton `mdModuleRef` se déplace.|  
|`MDNotifyNameSpace`|Notifier lorsqu’un jeton `mdNameSpace` se déplace.|  
|`MDNotifyAssemblyRef`|Notifier lorsqu’un jeton `mdAssemblyRef` se déplace.|  
|`MDNotifyFile`|Notifier lorsqu’un jeton `mdFile` se déplace.|  
|`MDNotifyExportedType`|Notifier lorsqu’un jeton `mdExportedType` se déplace.|  
|`MDNotifyResource`|Notifier lorsqu’un jeton `mdManifestResource` se déplace.|  
  
## <a name="remarks"></a>Notes  
 Un jeton peut être remappé (c’est-à-dire déplacé) au cours d’une fusion de métadonnées.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
