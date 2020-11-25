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
ms.openlocfilehash: f7d76c72ed5db95425f5b1fa2db5e4346983daa4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696672"
---
# <a name="cor_prf_suspend_reason-enumeration"></a>COR_PRF_SUSPEND_REASON, énumération

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
|`COR_PRF_FIELD_SUSPEND_OTHER`|Le runtime est suspendu pour une raison non spécifiée.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|Le runtime est suspendu pour traiter une demande de garbage collection.<br /><br /> Les rappels liés à garbage collection se produisent entre les rappels [ICorProfilerCallback :: RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) et [ICorProfilerCallback :: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) .|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|Le runtime est suspendu de sorte qu’un `AppDomain` peut être arrêté.<br /><br /> Pendant que le runtime est suspendu, le runtime détermine les threads qui se trouvent dans le `AppDomain` qui est arrêté et les affecte à la valeur Abort lorsqu’ils reprennent. Il n’existe pas `AppDomain` de rappels spécifiques pendant cette suspension.|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|Le runtime est interrompu afin que la présentation du code puisse se produire.<br /><br /> La mise à l’échelle du code se présente uniquement lorsque le compilateur juste-à-temps (JIT) est actif avec la mise à l’échelle du code activée. Les rappels de présentation de code se produisent entre les `ICorProfilerCallback::RuntimeSuspendFinished` `ICorProfilerCallback::RuntimeResumeStarted` rappels et. **Remarque :**  Le JIT CLR ne met pas en valeur les fonctions dans la version 2,0 de .NET Framework, donc cette valeur n’est pas utilisée dans 2,0.|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|Le runtime est suspendu pour pouvoir être arrêté. Il doit suspendre tous les threads pour terminer l’opération.|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|Le runtime est suspendu pour le débogage en cours de processus.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|Le runtime est suspendu pour préparer un garbage collection.|  
|`COR_PRF_SUSPEND_FOR_REJIT`|Le runtime est suspendu pour la recompilation JIT.|  
  
## <a name="remarks"></a>Remarques  

 Tous les threads d’exécution qui se trouvent dans du code non managé sont autorisés à continuer à s’exécuter jusqu’à ce qu’ils essaient d’entrer à nouveau le Runtime. à partir de là, ils sont également suspendus jusqu’à la reprise du Runtime. Cela s’applique également aux nouveaux threads qui entrent dans le Runtime. Tous les threads au sein du runtime sont suspendus immédiatement s’ils sont dans le code interruptible, ou ils sont invités à s’interrompre lorsqu’ils atteignent du code interruptible.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de profilage](profiling-enumerations.md)
