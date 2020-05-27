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
ms.openlocfilehash: 2985c419b25b8bf76df8fee0f0f37ba9ebee3df7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007897"
---
# <a name="corcheckduplicatesfor-enumeration"></a>CorCheckDuplicatesFor, énumération
Spécifie les jetons de métadonnées dont les doublons seront vérifiés.  
  
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
|`MDNoDupChecks`|Ne pas vérifier les jetons de métadonnées pour les doublons.|  
|`MDDupTypeDef`|Vérifiez les doublons de `mdTypeDef` jetons.|  
|`MDDupInterfaceImpl`|Vérifiez les doublons de `mdInterfaceImpl` jetons.|  
|`MDDupMethodDef`|Vérifiez les doublons de `mdMethodDef` jetons.|  
|`MDDupTypeRef`|Vérifiez les doublons de `mdTypeRef` jetons.|  
|`MDDupMemberRef`|Vérifiez les doublons de `mdMemberRef` jetons.|  
|`MDDupCustomAttribute`|Vérifiez les doublons de `mdCustomAttribute` jetons.|  
|`MDDupParamDef`|Vérifiez les doublons de `mdParamDef` jetons.|  
|`MDDupPermission`|Vérifiez les doublons de `mdPermission` jetons.|  
|`MDDupProperty`|Vérifiez les doublons de `mdProperty` jetons.|  
|`MDDupEvent`|Vérifiez les doublons de `mdEvent` jetons.|  
|`MDDupFieldDef`|Vérifiez les doublons de `mdFieldDef` jetons.|  
|`MDDupSignature`|Vérifiez les doublons de `mdSignature` jetons.|  
|`MDDupModuleRef`|Vérifiez les doublons de `mdModuleRef` jetons.|  
|`MDDupTypeSpec`|Vérifiez les doublons de `mdTypeSpec` jetons.|  
|`MDDupImplMap`|Vérifiez les doublons de `mdImplMap` jetons.|  
|`MDDupAssemblyRef`|Vérifiez les doublons de `mdAssemblyRef` jetons.|  
|`MDDupFile`|Vérifiez les doublons de `mdFile` jetons.|  
|`MDDupExportedType`|Vérifiez les doublons de `mdExportedType` jetons.|  
|`MDDupManifestResource`|Vérifiez les doublons de `mdManifestResource` jetons.|  
|`MDDupGenericParam`|Vérifiez les doublons de `mdGenericParam` jetons.|  
|`MDDupMethodSpec`|Vérifiez les doublons de `mdMethodSpec` jetons.|  
|`MDDupGenericParamConstraint`|Vérifiez les doublons de `mdGenericParamConstraint` jetons.|  
|`MDDupAssembly`|Vérifiez les doublons de `mdAssembly` jetons.|  
|`MDDupDefault`|Vérifiez les doublons des `mdMemberRef` jetons,,, `mdTypeRef` `mdSignature` `mdTypeSpec` et `mdMethodSpec` .|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](metadata-enumerations.md)
