---
title: COR_PRF_MISC, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_MISC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MISC
helpviewer_keywords:
- COR_PRF_MISC enumeration [.NET Framework profiling]
ms.assetid: 619bb5de-e309-48b6-a3af-32d935a0ff46
topic_type:
- apiref
ms.openlocfilehash: 5a3c820b52ae9376d769ea9956edc0b8553a1f88
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682170"
---
# <a name="cor_prf_misc-enumeration"></a>COR_PRF_MISC, énumération

Contient des valeurs de constante qui spécifient des identificateurs spéciaux.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|Identificateur par défaut utilisé par [ICorProfilerInfo :: GetModuleInfo](icorprofilerinfo-getmoduleinfo-method.md) pour un module qui n’a pas encore été attaché à un assembly.|  
|`PROFILER_GLOBAL_CLASS`|Identificateur de classe par défaut pour les constantes globales qui n’appartiennent pas à une classe.|  
|`PROFILER_GLOBAL_MODULE`|Identificateur de module par défaut pour les objets globaux qui n’appartiennent pas à un module.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de profilage](profiling-enumerations.md)
