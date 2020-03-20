---
title: OSINFO, structure
ms.date: 03/30/2017
api_name:
- OSINFO
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OSINFO
helpviewer_keywords:
- OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type:
- apiref
ms.openlocfilehash: 048fe687e4d979576896f5310bddc855b40bb695
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175224"
---
# <a name="osinfo-structure"></a>OSINFO, structure
Contient des détails sur le système d’exploitation d’un assemblage ou d’un module.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;
    DWORD   dwOSMinorVersion;
} OSINFO;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`dwOSPlatformId`|L’une des valeurs d’identification `GetVersionEx`définies par la fonction plate-forme Microsoft Windows . Les valeurs suivantes sont admises :<br /><br /> - VER_PLATFORM_WIN32s, ou 0x0000, pour spécifier Microsoft Windows 3.1.<br />- VER_PLATFORM_WIN32_WINDOWS, ou 0x0001, pour spécifier Windows 95, Windows 98, ou les systèmes d’exploitation descendus d’eux.<br />- VER_PLATFORM_WIN32_NT, ou 0x0002, pour spécifier Windows NT ou les systèmes d’exploitation descendus de lui.|  
|`dwOSMajorVersion`|La version majeure du système d’exploitation, ou une valeur NULL pour indiquer n’importe quelle version.|  
|`dwOSMinorVersion`|La version mineure du système d’exploitation, ou une valeur NULL pour indiquer n’importe quelle version.|  
  
## <a name="remarks"></a>Notes   
 `OSINFO`est basé `OSVERSIONINFOEX` sur la structure qui est utilisée `GetVersionEx`dans les appels à la fonction plate-forme Microsoft Windows . Cette structure est utilisée par la structure ASSEMBLYMETADATA pour indiquer son support du système d’exploitation.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
