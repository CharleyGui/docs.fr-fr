---
title: ICorProfilerInfo2, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2
helpviewer_keywords:
- ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: 91bd49b6-4d12-494f-a8f1-2f251e8c65e3
topic_type:
- apiref
ms.openlocfilehash: fdac9eedb0ae442d6dd2646859cab13398020a87
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449776"
---
# <a name="icorprofilerinfo2-interface"></a>ICorProfilerInfo2, interface
Fournit des méthodes utilisées par les profileurs de code pour communiquer avec le common language runtime (CLR) afin de contrôler la surveillance des événements et les informations de demande. L’interface `ICorProfilerInfo2` est une extension de l’interface [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) . Autrement dit, il fournit de nouvelles méthodes prises en charge dans le .NET Framework version 2,0 et les versions ultérieures.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[DoStackSnapshot, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)|Parcourt la pile du thread spécifié pour signaler les frames d’appels managés au profileur.|  
|[EnumModuleFrozenObjects, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)|Obtient un énumérateur qui autorise l’itération sur les objets figés dans le module spécifié.|  
|[GetAppDomainStaticAddress, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getappdomainstaticaddress-method.md)|Obtient l’adresse du champ statique du domaine d’application spécifié qui est dans la portée du domaine d’application spécifié.|  
|[GetArrayObjectInfo, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getarrayobjectinfo-method.md)|Obtient des informations détaillées sur un objet de tableau.|  
|[GetBoxClassLayout, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getboxclasslayout-method.md)|Obtient des informations sur la disposition de la classe pour un type valeur spécifié qui est boxed.|  
|[GetClassFromTokenAndTypeArgs, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)|Obtient le `ClassID` d’un type à l’aide du jeton de métadonnées spécifié et des valeurs de `ClassID` de tous les arguments de type.|  
|[GetClassIDInfo2, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)|Obtient le module parent de la classe générique spécifiée, le jeton de métadonnées pour la classe, le `ClassID` de sa classe parente et le `ClassID` pour chaque argument de type, le cas échéant, de la classe.|  
|[GetClassLayout, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclasslayout-method.md)|Obtient des informations sur la disposition, dans la mémoire, des champs définis par la classe spécifiée. Autrement dit, cette méthode obtient les offsets des champs de la classe.|  
|[GetCodeInfo2, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)|Obtient l'étendue de code natif associée au `FunctionID` spécifié.|  
|[GetContextStaticAddress, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcontextstaticaddress-method.md)|Obtient l’adresse du champ statique de contexte spécifié qui est dans la portée du contexte spécifié.|  
|[GetFunctionFromTokenAndTypeArgs, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)|Obtient la `FunctionID` d’une fonction à l’aide du jeton de métadonnées spécifié, de la classe conteneur et de `ClassID` valeurs de tous les arguments de type.|  
|[GetFunctionInfo2, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)|Obtient la classe parente, le jeton de métadonnées et le `ClassID` de chaque argument de type, le cas échéant, d’une fonction.|  
|[GetGenerationBounds, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md)|Obtient les régions de mémoire (segments du tas) qui composent les générations du tas récupéré par le garbage collector.|  
|[GetNotifiedExceptionClauseInfo, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)|Obtient les informations d’adresse native et de frame pour la clause d’exception (`catch`/`finally`/`filter`) qui est sur le point d’être exécutée ou qui vient d’être exécutée.|  
|[GetObjectGeneration, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md)|Obtient le segment du tas qui contient l’objet spécifié.|  
|[GetRVAStaticAddress, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getrvastaticaddress-method.md)|Obtient l’adresse du champ statique d’adresse virtuelle relative (RVA) spécifié.|  
|[GetStaticFieldInfo, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstaticfieldinfo-method.md)|Obtient la portée dans laquelle le champ spécifié est statique.|  
|[GetStringLayout, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md)|Obtient des informations sur la disposition d'un objet string.|  
|[GetThreadAppDomain, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)|Obtient l’ID du domaine d’application dans lequel le thread spécifié exécute actuellement du code.|  
|[GetThreadStaticAddress, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md)|Obtient l’adresse du champ statique de thread spécifié qui se trouve dans la portée du thread spécifié.|  
|[SetEnterLeaveFunctionHooks2, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)|Spécifie les fonctions implémentées par le profileur à appeler sur les raccordements « Enter », « Leave » et « tailcall » des fonctions managées.|  
  
## <a name="remarks"></a>Notes  
 Un profileur appelle une méthode dans l’interface `ICorProfilerInfo2` pour communiquer avec le CLR afin de contrôler la surveillance des événements et les informations de demande.  
  
 Les méthodes de l’interface `ICorProfilerInfo2` sont implémentées par le CLR à l’aide du modèle à thread libre. Chaque méthode retourne un HRESULT pour indiquer la réussite ou l'échec. Pour obtenir la liste des codes de retour possibles, consultez le fichier CorError.h.  
  
 Le CLR passe une interface `ICorProfilerInfo2` à chaque profileur de code pendant l’initialisation, à l’aide de l’implémentation de [ICorProfilerCallback :: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)du profileur. Un profileur de code peut ensuite appeler les méthodes de l’interface `ICorProfilerInfo2` pour obtenir des informations sur le code managé en cours d’exécution sous le contrôle du CLR.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
