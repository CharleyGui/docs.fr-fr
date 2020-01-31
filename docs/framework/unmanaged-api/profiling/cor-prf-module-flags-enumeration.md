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
ms.openlocfilehash: 0f6fb469aa9d6d40b762bfd2feec28c28299732f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867111"
---
# <a name="cor_prf_module_flags-enumeration"></a>COR_PRF_MODULE_FLAGS, énumération
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
  
## <a name="members"></a>Members  
  
|Member|Description|  
|------------|-----------------|  
|COR_PRF_MODULE_DISK|Le module a été chargé à partir du disque.|  
|COR_PRF_MODULE_NGEN|Le module a été généré par le générateur d’images natives (Ngen. exe).|  
|COR_PRF_MODULE_DYNAMIC|Le module a été créé par des méthodes dans l’espace de noms <xref:System.Reflection.Emit?displayProperty=nameWithType>.|  
|COR_PRF_MODULE_COLLECTIBLE|La durée de vie du module est gérée par le garbage collector.|  
|COR_PRF_MODULE_RESOURCE|Le module ne contient pas de métadonnées et est utilisé uniquement comme ressource. L’équivalent managé de ce bit est la méthode <xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType>.|  
|COR_PRF_MODULE_FLAT_LAYOUT|La disposition du module en mémoire est plate et non mappée. Si ce bit est défini pour un module, les profileurs qui lisent directement les informations à partir de l’en-tête de fichier PE (Portable Executable) devront être vigilants lors de l’interprétation des adresses virtuelles relatives dans l’en-tête.|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|L’indicateur de type de contenu Windows Runtime est défini dans les métadonnées de l’assembly de ce module. C’est le cas pour tous les modules de métadonnées Windows (. winmd).|  
  
## <a name="remarks"></a>Notes  
 Les bits de COR_PRF_MODULE_FLAGS sont retournés au profileur dans le paramètre de sortie `pdwModuleFlags` de la méthode [ICorProfilerInfo3 :: GetModuleInfo2,](icorprofilerinfo3-getmoduleinfo2-method.md) . Certaines combinaisons de deux ou plusieurs indicateurs sont possibles, mais toutes les combinaisons ne sont pas possibles.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de profilage](profiling-enumerations.md)
