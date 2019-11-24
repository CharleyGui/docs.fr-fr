---
title: AssemblyFlags, énumération
ms.date: 03/30/2017
api_name:
- AssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyFlags
helpviewer_keywords:
- AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type:
- apiref
ms.openlocfilehash: ffb5953c843a338b4548253457a0c3b1ca0c20f5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444301"
---
# <a name="assemblyflags-enumeration"></a>AssemblyFlags, énumération
Contains values that describe run-time features of an assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`afImplicitExportedTypes`|Specifies that exported type definitions are implicit within the files that comprise the assembly. In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.|  
|`afImplicitResources`|Specifies that resource definitions are implicit within the files that comprise the assembly. In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.|  
|`afNonSideBySideAppDomain`|Specifies that the assembly cannot execute with other versions if they are running in the same application domain.|  
|`afNonSideBySideProcess`|Specifies that the assembly cannot execute with other versions if they are running in the same process.|  
|`afNonSideBySideMachine`|Specifies that the assembly cannot execute with other versions if they are running on the same computer.|  
  
## <a name="remarks"></a>Notes  
 The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly. If none of these values are set, the assembly is assumed to be side-by-side compatible.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** MsCorEE.h  
  
 **Library:** Included as a resource in MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
