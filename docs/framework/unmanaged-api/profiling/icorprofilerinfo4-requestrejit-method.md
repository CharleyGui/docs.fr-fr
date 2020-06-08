---
title: ICorProfilerInfo4::RequestReJIT, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestReJIT
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type:
- apiref
ms.openlocfilehash: 7dd82f2dfab885070df4789fe5efc16a49d50e06
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495799"
---
# <a name="icorprofilerinfo4requestrejit-method"></a>ICorProfilerInfo4::RequestReJIT, méthode
Demande une recompilation juste-à-temps de toutes les instances des fonctions spécifiées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cFunctions`  
 [in] Nombre de fonctions à recompiler.  
  
 `moduleIds`  
 [in] Spécifie la partie `moduleId` des paires (`module`, `methodDef`) qui identifient les fonctions à recompiler.  
  
 `methodIds`  
 [in] Spécifie la partie `methodId` des paires (`module`, `methodDef`) qui identifient les fonctions à recompiler.  
  
## <a name="return-value"></a>Valeur renvoyée  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Une tentative a été effectuée pour marquer toutes les méthodes de recompilation juste-à-temps. Le profileur doit implémenter la méthode [ICorProfilerCallback4 :: rejiterror,](icorprofilercallback4-rejiterror-method.md) pour déterminer les méthodes qui ont été marquées avec succès pour la recompilation JIT.|  
|CORPROF_E_CALLBACK4_REQUIRED|Le profileur doit implémenter l’interface [ICorProfilerCallback4](icorprofilercallback4-interface.md) pour que cet appel soit pris en charge.|  
|CORPROF_E_REJIT_NOT_ENABLED|La recompilation juste-à-temps n'a pas été activée. Vous devez activer la recompilation JIT pendant l’initialisation à l’aide de la méthode [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) pour définir l' `COR_PRF_ENABLE_REJIT` indicateur.|  
|E_INVALIDARG|`cFunctions` est égal à 0, ou `moduleIds` ou `methodIds` a la valeur `NULL`.|  
|||  
|E_OUTOFMEMORY|Le CLR n'a pas pu terminer la demande en raison d'une mémoire insuffisante.|  
  
## <a name="remarks"></a>Remarques  
 Appelez `RequestReJIT` pour que le runtime recompile un jeu spécifié de fonctions. Un profileur de code peut ensuite utiliser l’interface [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) pour ajuster le code qui est généré lorsque les fonctions sont recompilées. Cela n'affecte pas les fonctions en cours d'exécution ; seules les futurs appels de fonction sont concernés. Si aucune des fonctions spécifiées n'a précédemment été recompilée juste-à-temps, le fait de demander une recompilation équivaut à restaurer et à recompiler la fonction. Pour conserver la capacité de restauration, le compilateur juste-à-temps tient uniquement compte des versions originales de ses appelés dans le cadre des décisions d'incorporation quand il compile la version d'origine d'une fonction. Quand le compilateur juste-à-temps recompile une fonction, il tient compte des versions actuelles (recompilées ou d'origine) de ses appelés pour l'incorporation.  
  
 Un profileur appelle généralement `RequestReJIT` en réponse à une entrée utilisateur demandant au profileur d'instrumenter une ou plusieurs méthodes. `RequestReJIT` interrompt généralement le runtime pour effectuer une partie de son travail et peut éventuellement déclencher un garbage collection. Par conséquent, le profileur doit appeler `RequestReJIT` à partir d'un thread créé précédemment et non à partir d'un thread créé par le CLR qui exécute actuellement un rappel de profileur.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo4, interface](icorprofilerinfo4-interface.md)
- [Interfaces de profilage](profiling-interfaces.md)
- [Profilage](index.md)
