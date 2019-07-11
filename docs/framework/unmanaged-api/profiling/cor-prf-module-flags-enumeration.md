---
title: COR_PRF_MODULE_FLAGS, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_MODULE_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MODULE_FLAGS
helpviewer_keywords:
- COR_PRF_MODULE_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 7bc3a938-0df1-4739-9ff1-89cff454b704
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f94867db6908f0999604511d9782b6f5abfb5e77
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752049"
---
# <a name="corprfmoduleflags-enumeration"></a>COR_PRF_MODULE_FLAGS, énumération
Spécifie les propriétés d'un module.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum  
{  
    COR_PRF_MODULE_DISK             = 0x00000001,  
    COR_PRF_MODULE_NGEN             = 0x00000002,  
    COR_PRF_MODULE_DYNAMIC          = 0x00000004,  
    COR_PRF_MODULE_COLLECTIBLE      = 0x00000008,  
    COR_PRF_MODULE_RESOURCE         = 0x00000010,  
    COR_PRF_MODULE_FLAT_LAYOUT      = 0x00000020,  
    COR_PRF_MODULE_WINDOWS_RUNTIME  = 0x00000040  
}   COR_PRF_MODULE_FLAGS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|COR_PRF_MODULE_DISK|Le module a été chargé à partir du disque.|  
|COR_PRF_MODULE_NGEN|Le module a été généré par le Générateur d’images natives (Ngen.exe).|  
|COR_PRF_MODULE_DYNAMIC|Le module a été créé par les méthodes dans le <xref:System.Reflection.Emit?displayProperty=nameWithType> espace de noms.|  
|COR_PRF_MODULE_COLLECTIBLE|Durée de vie du module est gérée par le garbage collector.|  
|COR_PRF_MODULE_RESOURCE|Le module ne contient aucune métadonnée et est utilisé exclusivement en tant que ressource. L’équivalent managé de ce bit est la <xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType> (méthode).|  
|COR_PRF_MODULE_FLAT_LAYOUT|Mise en page du module en mémoire est plat, ne pas mappé. Si un module a ce bit défini, les profileurs qui lisent des informations directement à partir de l’en-tête du fichier exécutable portable (PE) devront être prudent lors de l’interprétation des adresses virtuelles relatives (RVA) dans l’en-tête.|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|L’indicateur de type de contenu de Windows Runtime est défini dans les métadonnées pour l’assembly de ce module. C’est le cas pour tous les modules de métadonnées Windows (.winmd).|  
  
## <a name="remarks"></a>Notes  
 Bits de COR_PRF_MODULE_FLAGS sont retournés au profileur dans le `pdwModuleFlags` paramètre de sortie de la [ICorProfilerInfo3::GetModuleInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md) (méthode). Certaines combinaisons de deux ou plusieurs indicateurs sont possibles, mais pas toutes les combinaisons sont possibles.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
