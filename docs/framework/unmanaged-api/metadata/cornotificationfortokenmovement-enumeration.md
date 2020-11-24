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
ms.openlocfilehash: 0f9cb8db35a1669cead6f9f26c9a89e063628dd8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687669"
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
|`MDNotifyDefault`|Notifier quand les jetons,, `mdTypeRef` `mdMethodDef` `mdMemberRef` ou `mdFieldDef` se déplacent.|  
|`MDNotifyAll`|Notifier quand un jeton est déplacé.|  
|`MDNotifyNone`|Ne pas avertir quand les jetons sont déplacés.|  
|`MDNotifyMethodDef`|Notifier en cas de déplacement d’un `mdMethodDef` jeton.|  
|`MDNotifyMemberRef`|Notifier en cas de déplacement d’un `mdMemberRef` jeton.|  
|`MDNotifyFieldDef`|Notifier en cas de déplacement d’un `mdFieldDef` jeton.|  
|`MDNotifyTypeRef`|Notifier en cas de déplacement d’un `mdTypeRef` jeton.|  
|`MDNotifyTypeDef`|Notifier en cas de déplacement d’un `mdTypeDef` jeton.|  
|`MDNotifyParamDef`|Notifier en cas de déplacement d’un `mdParamDef` jeton.|  
|`MDNotifyInterfaceImpl`|Notifier en cas de déplacement d’un `mdInterfaceImpl` jeton.|  
|`MDNotifyProperty`|Notifier en cas de déplacement d’un `mdProperty` jeton.|  
|`MDNotifyEvent`|Notifier en cas de déplacement d’un `mdEvent` jeton.|  
|`MDNotifySignature`|Notifier en cas de déplacement d’un `mdSignature` jeton.|  
|`MDNotifyTypeSpec`|Notifier en cas de déplacement d’un `mdTypeSpec` jeton.|  
|`MDNotifyCustomAttribute`|Notifier en cas de déplacement d’un `mdCustomAttribute` jeton.|  
|`MDNotifySecurityValue`|Notifier en cas de déplacement d’un `mdSecurityValue` jeton.|  
|`MDNotifyPermission`|Notifier en cas de déplacement d’un `mdPermission` jeton.|  
|`MDNotifyModuleRef`|Notifier en cas de déplacement d’un `mdModuleRef` jeton.|  
|`MDNotifyNameSpace`|Notifier en cas de déplacement d’un `mdNameSpace` jeton.|  
|`MDNotifyAssemblyRef`|Notifier en cas de déplacement d’un `mdAssemblyRef` jeton.|  
|`MDNotifyFile`|Notifier en cas de déplacement d’un `mdFile` jeton.|  
|`MDNotifyExportedType`|Notifier en cas de déplacement d’un `mdExportedType` jeton.|  
|`MDNotifyResource`|Notifier en cas de déplacement d’un `mdManifestResource` jeton.|  
  
## <a name="remarks"></a>Remarques  

 Un jeton peut être remappé (c’est-à-dire déplacé) au cours d’une fusion de métadonnées.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](metadata-enumerations.md)
