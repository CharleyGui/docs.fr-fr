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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a82ce9709e008e092c5f31372a89bf9a16e1f88b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767018"
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
|`MDNoDupChecks`|Ne pas vérifier les jetons de métadonnées pour les doublons.|  
|`MDDupTypeDef`|Vérifier les doublons de `mdTypeDef` jetons.|  
|`MDDupInterfaceImpl`|Vérifier les doublons de `mdInterfaceImpl` jetons.|  
|`MDDupMethodDef`|Vérifier les doublons de `mdMethodDef` jetons.|  
|`MDDupTypeRef`|Vérifier les doublons de `mdTypeRef` jetons.|  
|`MDDupMemberRef`|Vérifier les doublons de `mdMemberRef` jetons.|  
|`MDDupCustomAttribute`|Vérifier les doublons de `mdCustomAttribute` jetons.|  
|`MDDupParamDef`|Vérifier les doublons de `mdParamDef` jetons.|  
|`MDDupPermission`|Vérifier les doublons de `mdPermission` jetons.|  
|`MDDupProperty`|Vérifier les doublons de `mdProperty` jetons.|  
|`MDDupEvent`|Vérifier les doublons de `mdEvent` jetons.|  
|`MDDupFieldDef`|Vérifier les doublons de `mdFieldDef` jetons.|  
|`MDDupSignature`|Vérifier les doublons de `mdSignature` jetons.|  
|`MDDupModuleRef`|Vérifier les doublons de `mdModuleRef` jetons.|  
|`MDDupTypeSpec`|Vérifier les doublons de `mdTypeSpec` jetons.|  
|`MDDupImplMap`|Vérifier les doublons de `mdImplMap` jetons.|  
|`MDDupAssemblyRef`|Vérifier les doublons de `mdAssemblyRef` jetons.|  
|`MDDupFile`|Vérifier les doublons de `mdFile` jetons.|  
|`MDDupExportedType`|Vérifier les doublons de `mdExportedType` jetons.|  
|`MDDupManifestResource`|Vérifier les doublons de `mdManifestResource` jetons.|  
|`MDDupGenericParam`|Vérifier les doublons de `mdGenericParam` jetons.|  
|`MDDupMethodSpec`|Vérifier les doublons de `mdMethodSpec` jetons.|  
|`MDDupGenericParamConstraint`|Vérifier les doublons de `mdGenericParamConstraint` jetons.|  
|`MDDupAssembly`|Vérifier les doublons de `mdAssembly` jetons.|  
|`MDDupDefault`|Vérifier les doublons de `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, et `mdMethodSpec` jetons.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr.h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
