---
title: CorTokenType, énumération
ms.date: 03/30/2017
api_name:
- CorTokenType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTokenType
helpviewer_keywords:
- CorTokenType enumeration [.NET Framework metadata]
ms.assetid: 93c9a369-225f-4eff-9b78-3fbee4902cf1
topic_type:
- apiref
ms.openlocfilehash: 629e18b6cd2fd7910804ecc608a45d2406dddea1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007492"
---
# <a name="cortokentype-enumeration"></a>CorTokenType, énumération
Indique le type d’un jeton de métadonnées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorTokenType {  
  
    mdtModule                       = 0x00000000,  
    mdtTypeRef                      = 0x01000000,  
    mdtTypeDef                      = 0x02000000,  
    mdtFieldDef                     = 0x04000000,  
    mdtMethodDef                    = 0x06000000,  
    mdtParamDef                     = 0x08000000,  
    mdtInterfaceImpl                = 0x09000000,  
    mdtMemberRef                    = 0x0a000000,  
    mdtCustomAttribute              = 0x0c000000,  
    mdtPermission                   = 0x0e000000,  
    mdtSignature                    = 0x11000000,  
    mdtEvent                        = 0x14000000,  
    mdtProperty                     = 0x17000000,  
    mdtModuleRef                    = 0x1a000000,  
    mdtTypeSpec                     = 0x1b000000,  
    mdtAssembly                     = 0x20000000,  
    mdtAssemblyRef                  = 0x23000000,  
    mdtFile                         = 0x26000000,  
    mdtExportedType                 = 0x27000000,  
    mdtManifestResource             = 0x28000000,  
    mdtGenericParam                 = 0x2a000000,  
    mdtMethodSpec                   = 0x2b000000,  
    mdtGenericParamConstraint       = 0x2c000000,  
    mdtString                       = 0x70000000,  
    mdtName                         = 0x71000000,  
    mdtBaseType                     = 0x72000000  
  
} CorTokenType;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`mdtModule`|`mdModule`Jeton.|  
|`mdtTypeRef`|`mdTypeRef`Jeton.|  
|`mdtTypeDef`|`mdTypeDef`Jeton.|  
|`mdtFieldDef`|`mdFieldDef`Jeton.|  
|`mdtMethodDef`|`mdMethodDef`Jeton.|  
|`mdtParamDef`|`mdParamDef`Jeton.|  
|`mdtInterfaceImpl`|`mdInterfaceImpl`Jeton.|  
|`mdtMemberRef`|`mdMemberRef`Jeton.|  
|`mdtCustomAttribute`|`mdCustomAttribute`Jeton.|  
|`mdtPermission`|`mdPermission`Jeton.|  
|`mdtSignature`|`mdSignature`Jeton.|  
|`mdtEvent`|`mdEvent`Jeton.|  
|`mdtProperty`|`mdProperty`Jeton.|  
|`mdtModuleRef`|`mdModuleRef`Jeton.|  
|`mdtTypeSpec`|`mdTypeSpec`Jeton.|  
|`mdtAssembly`|`mdAssembly`Jeton.|  
|`mdtAssemblyRef`|`mdAssemblyRef`Jeton.|  
|`mdtFile`|`mdFile`Jeton.|  
|`mdtExportedType`|`mdExportedType`Jeton.|  
|`mdtManifestResource`|`mdManifestResource`Jeton.|  
|`mdtGenericParam`|`mdGenericParam`Jeton.|  
|`mdtMethodSpec`|`mdMethodSpec`Jeton.|  
|`mdtGenericParamConstraint`|`mdGenericParamConstraint`Jeton.|  
|`mdtString`|`mdString`Jeton.|  
|`mdtName`|`mdName`Jeton.|  
|`mdtBaseType`|Non utilisé.|  
  
## <a name="remarks"></a>Remarques  
 Chaque valeur est égale à la valeur de l’octet de poids le plus élevé dans le jeton de métadonnées correspondant.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](metadata-enumerations.md)
