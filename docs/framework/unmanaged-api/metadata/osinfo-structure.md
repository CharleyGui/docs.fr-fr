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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a36cd3c5fb638799a735e4b4a1a98959500300b5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761597"
---
# <a name="osinfo-structure"></a>OSINFO, structure
Contient des détails sur le système d’exploitation pour un assembly ou un module.  
  
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
|`dwOSPlatformId`|Une des valeurs d’identificateur définis par la fonction de la plateforme Microsoft Windows `GetVersionEx`. Les valeurs suivantes sont prises en charge :<br /><br /> -VER_PLATFORM_WIN32s, ou 0 x 0000, pour spécifier Microsoft Windows 3.1.<br />-VER_PLATFORM_WIN32_WINDOWS, ou 0 x 0001, pour spécifier Windows 95, Windows 98 ou les systèmes d’exploitation hérités à partir de celles-ci.<br />-VER_PLATFORM_WIN32_NT, ou 0 x 0010, pour spécifier Windows NT ou les systèmes d’exploitation hérités à partir de celui-ci.|  
|`dwOSMajorVersion`|La version principale du système d’exploitation, ou une valeur NULL pour indiquer n’importe quelle version.|  
|`dwOSMinorVersion`|La version secondaire du système d’exploitation, ou une valeur NULL pour indiquer n’importe quelle version.|  
  
## <a name="remarks"></a>Notes  
 `OSINFO` est basé sur le `OSVERSIONINFOEX` structure qui est utilisé dans les appels à la fonction de la plateforme Microsoft Windows `GetVersionEx`. Cette structure est utilisée par la structure ASSEMBLYMETADATA pour indiquer sa prise en charge du système d’exploitation.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
