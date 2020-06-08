---
title: ICorProfilerInfo3, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3
helpviewer_keywords:
- ICorProfilerInfo3 interface [.NET Framework profiling]
ms.assetid: 044a262f-0fa7-485d-b0c1-64cdc359c654
topic_type:
- apiref
ms.openlocfilehash: 0a474719935ba763cbd15dc6e18fe5ba99c14ebc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496306"
---
# <a name="icorprofilerinfo3-interface"></a>ICorProfilerInfo3, interface
Fournit des méthodes utilisées par les profileurs de code pour communiquer avec le Common Language Runtime (CLR) pour contrôler la surveillance des événements et demander des informations. L' `ICorProfilerInfo3` interface est une extension de l’interface [ICorProfilerInfo2](icorprofilerinfo2-interface.md) . Il fournit de nouvelles méthodes prises en charge dans le .NET Framework 4 et versions ultérieures.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumJITedFunctions, méthode](icorprofilerinfo3-enumjitedfunctions-method.md)|Retourne un énumérateur pour toutes les fonctions précédemment compilées juste-à-temps.|  
|[EnumModules, méthode](icorprofilerinfo3-enummodules-method.md)|Retourne un énumérateur qui fournit des méthodes pour itérer séquentiellement au sein d’une collection de modules managés chargés dans l’application.|  
|[GetAppDomainsContainingModule, méthode](icorprofilerinfo3-getappdomainscontainingmodule-method.md)|Obtient les identificateurs des domaines d'application dans lesquels le module donné a été chargé.|  
|[GetFunctionEnter3Info, méthode](icorprofilerinfo3-getfunctionenter3info-method.md)|Fournit les informations sur le frame de pile et l’argument de la fonction qui est signalée au profileur par la fonction [FunctionEnter3WithInfo](functionenter3withinfo-function.md) ; peut être appelé uniquement pendant le `FunctionEnter3WithInfo` rappel.|  
|[GetFunctionLeave3Info, méthode](icorprofilerinfo3-getfunctionleave3info-method.md)|Fournit le frame de pile et la valeur de retour de la fonction qui est signalée au profileur par la fonction [FunctionLeave3WithInfo](functionleave3withinfo-function.md) ; peut être appelé uniquement pendant le `FunctionLeave3WithInfo` rappel.|  
|[GetFunctionTailcall3Info, méthode](icorprofilerinfo3-getfunctiontailcall3info-method.md)|Fournit le frame de pile de la fonction qui est signalée au profileur par la fonction [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) . peut être appelé uniquement pendant le `FunctionTailcall3WithInfo` rappel.|  
|[GetModuleInfo2, méthode](icorprofilerinfo3-getmoduleinfo2-method.md)|Étant donné un ID de module, retourne le nom de fichier du module, l'ID de l'assembly parent du module et un masque de bits qui décrit les propriétés du module.|  
|[GetRuntimeInformation, méthode](icorprofilerinfo3-getruntimeinformation-method.md)|Fournit des informations de version sur le runtime en cours de profilage.|  
|[GetStringLayout2, méthode](icorprofilerinfo3-getstringlayout2-method.md)|Obtient des informations sur la disposition d'un objet string.|  
|[GetThreadStaticAddress2, méthode](icorprofilerinfo3-getthreadstaticaddress2-method.md)|Obtient l'adresse du champ statique de thread spécifié qui est dans l'étendue du thread et du domaine d'application spécifiés.|  
|[RequestProfilerDetach, méthode](icorprofilerinfo3-requestprofilerdetach-method.md)|Indique au runtime de détacher le profileur.|  
|[SetEnterLeaveFunctionHooks3, méthode](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)|Spécifie les fonctions implémentées par le profileur qui seront appelées sur les fonctions [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)et [FunctionTailcall3](functiontailcall3-function.md) .|  
|[SetEnterLeaveFunctionHooks3WithInfo, méthode](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)|Spécifie les fonctions implémentées par le profileur qui seront appelées sur les raccordements [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)et [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) des fonctions managées.|  
|[SetFunctionIDMapper2, méthode](icorprofilerinfo3-setfunctionidmapper2-method.md)|Spécifie la fonction implémentée par le profileur qui sera appelée pour mapper des valeurs `FunctionID` sur d'autres valeurs, qui sont passées aux raccordements d'entrée/sortie de fonction du profileur. Cette méthode étend [ICorProfilerInfo :: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) avec un paramètre que les profileurs peuvent utiliser pour lever l’ambiguïté entre les runtimes.|  
  
## <a name="remarks"></a>Remarques  
 Le CLR implémente les méthodes de l'interface `ICorProfilerInfo3` à l'aide du modèle libre de threads. Chaque méthode retourne un HRESULT pour indiquer la réussite ou l'échec. Pour obtenir la liste des codes de retour possibles, consultez le fichier CorError.h.  
  
 Le CLR passe une `ICorProfilerInfo3` interface à chaque profileur de code pendant l’initialisation, à l’aide de l’implémentation de la méthode [ICorProfilerCallback :: Initialize](icorprofilercallback-initialize-method.md) ou [ICorProfilerCallback3 :: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) du profileur. Un profileur de code peut ensuite appeler les méthodes `ICorProfilerInfo3` pour obtenir des informations sur le code managé qui est en cours d'exécution sous le contrôle du CLR.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](profiling-interfaces.md)
- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
