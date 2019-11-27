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
ms.openlocfilehash: 6b551743227dc1c6069796038782a515e6dbe8c4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443776"
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
|`MDDupTypeDef`|Recherchez les doublons de jetons de `mdTypeDef`.|  
|`MDDupInterfaceImpl`|Recherchez les doublons de jetons de `mdInterfaceImpl`.|  
|`MDDupMethodDef`|Recherchez les doublons de jetons de `mdMethodDef`.|  
|`MDDupTypeRef`|Recherchez les doublons de jetons de `mdTypeRef`.|  
|`MDDupMemberRef`|Recherchez les doublons de jetons de `mdMemberRef`.|  
|`MDDupCustomAttribute`|Recherchez les doublons de jetons de `mdCustomAttribute`.|  
|`MDDupParamDef`|Recherchez les doublons de jetons de `mdParamDef`.|  
|`MDDupPermission`|Recherchez les doublons de jetons de `mdPermission`.|  
|`MDDupProperty`|Recherchez les doublons de jetons de `mdProperty`.|  
|`MDDupEvent`|Recherchez les doublons de jetons de `mdEvent`.|  
|`MDDupFieldDef`|Recherchez les doublons de jetons de `mdFieldDef`.|  
|`MDDupSignature`|Recherchez les doublons de jetons de `mdSignature`.|  
|`MDDupModuleRef`|Recherchez les doublons de jetons de `mdModuleRef`.|  
|`MDDupTypeSpec`|Recherchez les doublons de jetons de `mdTypeSpec`.|  
|`MDDupImplMap`|Recherchez les doublons de jetons de `mdImplMap`.|  
|`MDDupAssemblyRef`|Recherchez les doublons de jetons de `mdAssemblyRef`.|  
|`MDDupFile`|Recherchez les doublons de jetons de `mdFile`.|  
|`MDDupExportedType`|Recherchez les doublons de jetons de `mdExportedType`.|  
|`MDDupManifestResource`|Recherchez les doublons de jetons de `mdManifestResource`.|  
|`MDDupGenericParam`|Recherchez les doublons de jetons de `mdGenericParam`.|  
|`MDDupMethodSpec`|Recherchez les doublons de jetons de `mdMethodSpec`.|  
|`MDDupGenericParamConstraint`|Recherchez les doublons de jetons de `mdGenericParamConstraint`.|  
|`MDDupAssembly`|Recherchez les doublons de jetons de `mdAssembly`.|  
|`MDDupDefault`|Vérifiez les doublons des jetons `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`et `mdMethodSpec`.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
