---
title: COR_PRF_SUSPEND_REASON, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_SUSPEND_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SUSPEND_REASON
helpviewer_keywords:
- COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e084bc957eca9474078ed5ca3aef0276361dbe1b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745529"
---
# <a name="corprfsuspendreason-enumeration"></a>COR_PRF_SUSPEND_REASON, énumération
Indique la raison pour laquelle le runtime est suspendu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    COR_PRF_SUSPEND_OTHER                   = 0x00,  
    COR_PRF_SUSPEND_FOR_GC                  = 0x01,  
    COR_PRF_SUSPEND_FOR_APPDOMAIN_SHUTDOWN  = 0x02,  
    COR_PRF_SUSPEND_FOR_CODE_PITCHING       = 0x03,  
    COR_PRF_SUSPEND_FOR_SHUTDOWN            = 0x04,  
    COR_PRF_SUSPEND_FOR_INPROC_DEBUGGER     = 0x06,  
    COR_PRF_SUSPEND_FOR_GC_PREP             = 0x07,    COR_PRF_SUSPEND_FOR_REJIT               = 8  
} COR_PRF_SUSPEND_REASON;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|Le runtime est suspendu pour une raison non précisée.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|Le runtime est suspendu pour traiter une demande de garbage collection.<br /><br /> Les rappels de liées au regroupement garbage se produisent entre le [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) et [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) rappels.|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|Le runtime est suspendu afin qu’un `AppDomain` peut être arrêté.<br /><br /> Quand l’exécution est suspendue, le runtime détermine les threads se trouvent dans le `AppDomain` qui est en cours d’arrêter et de les définir pour abandonner lors de leur reprise. Il y a aucune `AppDomain`-rappels spécifiques pendant cette interruption.|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|Le runtime est suspendu pour que la suspension de code peut se produire.<br /><br /> Suspension de code s’ensuit uniquement lorsque compilateur juste-à-temps (JIT) est actif avec la suspension de code activée. Code de rappels de suspension se produisent entre le `ICorProfilerCallback::RuntimeSuspendFinished` et `ICorProfilerCallback::RuntimeResumeStarted` rappels. **Remarque :**  Le JIT CLR ne suspend pas les fonctions dans le .NET Framework version 2.0, cette valeur n’est pas utilisé dans 2.0.|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|Le runtime est suspendu afin qu’il s’arrête. Il doit suspendre tous les threads pour terminer l’opération.|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|Le runtime est suspendu dans le processus de débogage.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|Le runtime est suspendu pour préparer un garbage collection.|  
|`COR_PRF_SUSPEND_FOR_REJIT`|Le runtime est suspendu pour recompilation JIT.|  
  
## <a name="remarks"></a>Notes  
 Tous les threads d’exécution qui se trouvent dans le code non managé sont autorisés à continuer à s’exécuter jusqu'à ce qu’ils essaient d’entrer à nouveau le runtime, auquel cas ils seront aussi suspendues jusqu'à ce que le runtime reprend. Cela s’applique également aux nouveaux threads qui entrent dans le runtime. Tous les threads dans le runtime sont immédiatement suspendus s’ils sont dans du code interruptible, soit invités à s’interrompre lorsqu’ils atteignent du code interruptible.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
