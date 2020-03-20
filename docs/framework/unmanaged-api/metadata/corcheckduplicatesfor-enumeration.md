---
title: CorCheckDuplicatesFor, énumération
ms.date: 03/30/2017
api_name:
- CorCheckDuplicatesFor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCheckDuplicatesFor
helpviewer_keywords:
- CorCheckDuplicatesFor enumeration [.NET Framework metadata]
ms.assetid: d8ec8d3c-70f7-4cc6-9957-68068fd8f49c
topic_type:
- apiref
ms.openlocfilehash: 04dc12ab4d7d178ebf1575a3260f9f4981972782
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176186"
---
# <a name="corcheckduplicatesfor-enumeration"></a>CorCheckDuplicatesFor, énumération
Spécifie les jetons de métadonnées qui seront vérifiés pour les doublons.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorCheckDuplicatesFor {  
  
    MDDupAll                    = 0xffffffff,  
    MDDupENC                    = MDDupAll,  
    MDNoDupChecks               = 0x00000000,  
    MDDupTypeDef                = 0x00000001,  
    MDDupInterfaceImpl          = 0x00000002,  
    MDDupMethodDef              = 0x00000004,  
    MDDupTypeRef                = 0x00000008,  
    MDDupMemberRef              = 0x00000010,  
    MDDupCustomAttribute        = 0x00000020,  
    MDDupParamDef               = 0x00000040,  
    MDDupPermission             = 0x00000080,  
    MDDupProperty               = 0x00000100,  
    MDDupEvent                  = 0x00000200,  
    MDDupFieldDef               = 0x00000400,  
    MDDupSignature              = 0x00000800,  
    MDDupModuleRef              = 0x00001000,  
    MDDupTypeSpec               = 0x00002000,  
    MDDupImplMap                = 0x00004000,  
    MDDupAssemblyRef            = 0x00008000,  
    MDDupFile                   = 0x00010000,  
    MDDupExportedType           = 0x00020000,  
    MDDupManifestResource       = 0x00040000,  
    MDDupGenericParam           = 0x00080000,  
    MDDupMethodSpec             = 0x00100000,  
    MDDupGenericParamConstraint = 0x00200000,  
  
    MDDupAssembly               = 0x10000000,  
  
    MDDupDefault =
        MDNoDupChecks | MDDupTypeRef | MDDupMemberRef |
        MDDupSignature | MDDupTypeSpec | MDDupMethodSpec  
  
} CorCheckDuplicatesFor;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`MDDupAll`|Vérifiez tous les jetons de métadonnées pour les doublons.|  
|`MDDupENC`|Non utilisé.|  
|`MDNoDupChecks`|Ne vérifiez pas les jetons de métadonnées pour les doublons.|  
|`MDDupTypeDef`|Vérifiez s’il `mdTypeDef` y a des doublons de jetons.|  
|`MDDupInterfaceImpl`|Vérifiez s’il `mdInterfaceImpl` y a des doublons de jetons.|  
|`MDDupMethodDef`|Vérifiez s’il `mdMethodDef` y a des doublons de jetons.|  
|`MDDupTypeRef`|Vérifiez s’il `mdTypeRef` y a des doublons de jetons.|  
|`MDDupMemberRef`|Vérifiez s’il `mdMemberRef` y a des doublons de jetons.|  
|`MDDupCustomAttribute`|Vérifiez s’il `mdCustomAttribute` y a des doublons de jetons.|  
|`MDDupParamDef`|Vérifiez s’il `mdParamDef` y a des doublons de jetons.|  
|`MDDupPermission`|Vérifiez s’il `mdPermission` y a des doublons de jetons.|  
|`MDDupProperty`|Vérifiez s’il `mdProperty` y a des doublons de jetons.|  
|`MDDupEvent`|Vérifiez s’il `mdEvent` y a des doublons de jetons.|  
|`MDDupFieldDef`|Vérifiez s’il `mdFieldDef` y a des doublons de jetons.|  
|`MDDupSignature`|Vérifiez s’il `mdSignature` y a des doublons de jetons.|  
|`MDDupModuleRef`|Vérifiez s’il `mdModuleRef` y a des doublons de jetons.|  
|`MDDupTypeSpec`|Vérifiez s’il `mdTypeSpec` y a des doublons de jetons.|  
|`MDDupImplMap`|Vérifiez s’il `mdImplMap` y a des doublons de jetons.|  
|`MDDupAssemblyRef`|Vérifiez s’il `mdAssemblyRef` y a des doublons de jetons.|  
|`MDDupFile`|Vérifiez s’il `mdFile` y a des doublons de jetons.|  
|`MDDupExportedType`|Vérifiez s’il `mdExportedType` y a des doublons de jetons.|  
|`MDDupManifestResource`|Vérifiez s’il `mdManifestResource` y a des doublons de jetons.|  
|`MDDupGenericParam`|Vérifiez s’il `mdGenericParam` y a des doublons de jetons.|  
|`MDDupMethodSpec`|Vérifiez s’il `mdMethodSpec` y a des doublons de jetons.|  
|`MDDupGenericParamConstraint`|Vérifiez s’il `mdGenericParamConstraint` y a des doublons de jetons.|  
|`MDDupAssembly`|Vérifiez s’il `mdAssembly` y a des doublons de jetons.|  
|`MDDupDefault`|Vérifiez les doublons `mdSignature` `mdTypeSpec`de `mdMemberRef`, `mdTypeRef`, , et `mdMethodSpec` les jetons.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** CorHdr.h  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
