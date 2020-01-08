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
ms.openlocfilehash: d66e9bc3a027610d917e15dc9769b92ea1c5fb71
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345601"
---
# <a name="osinfo-structure"></a>OSINFO, structure
Contient des détails sur le système d’exploitation d’un assembly ou d’un module.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a>Members  
  
|Member|Description|  
|------------|-----------------|  
|`dwOSPlatformId`|L’une des valeurs d’identificateur définie par la fonction de la plate-forme Microsoft Windows `GetVersionEx`. Les valeurs suivantes sont admises :<br /><br /> -VER_PLATFORM_WIN32s, ou 0x0000, pour spécifier Microsoft Windows 3,1.<br />-VER_PLATFORM_WIN32_WINDOWS, ou 0x0001, pour spécifier les systèmes d’exploitation Windows 95, Windows 98 ou décroissants.<br />-VER_PLATFORM_WIN32_NT, ou 0x0002, pour spécifier les systèmes d’exploitation Windows NT ou décroissants.|  
|`dwOSMajorVersion`|La version principale du système d’exploitation, ou une valeur NULL pour indiquer n’importe quelle version.|  
|`dwOSMinorVersion`|La version mineure du système d’exploitation, ou une valeur NULL pour indiquer n’importe quelle version.|  
  
## <a name="remarks"></a>Notes  
 `OSINFO` est basé sur la structure de `OSVERSIONINFOEX` utilisée dans les appels à la fonction de la plate-forme Microsoft Windows `GetVersionEx`. Cette structure est utilisée par la structure ASSEMBLYMETADATA pour indiquer sa prise en charge par le système d’exploitation.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
