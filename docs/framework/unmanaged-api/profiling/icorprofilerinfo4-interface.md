---
title: ICorProfilerInfo4, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4
helpviewer_keywords:
- ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 34c358a3405262787ed495bf9d8d75462d97a71f
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380332"
---
# <a name="icorprofilerinfo4-interface"></a>ICorProfilerInfo4, interface
Fournit des méthodes que les profileurs de code utilisent pour communiquer avec le common language runtime (CLR) pour contrôler la surveillance d’événements et les informations de demande. . Le `ICorProfilerInfo4` interface est une extension de l’autre `ICorProfilerInfo` interfaces. Il fournit de nouvelles méthodes pour prendre en charge de la recompilation du juste-à-temps (JIT), ajoutée dans le .NET Framework 4.5.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumJITedFunctions2, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|Retourne un énumérateur pour toutes les fonctions qui ont été précédemment compilé par JIT et recompilées JIT.|  
|[EnumThreads, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|Obtient un énumérateur qui fournit des méthodes pour boucler séquentiellement dans la collection de tous les threads managés dans le processus profilé.|  
|[GetCodeInfo3, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|Obtient les étendues de code natif associées à la version recompilée juste-à-temps de la fonction spécifiée.|  
|[GetFunctionFromIP2, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|Mappe un pointeur d’instruction de code managé vers la version recompilée au juste d’une fonction spécifiée.|  
|[GetILToNativeMapping2, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|Obtient un mappage à partir de Microsoft intermediate language (MSIL) aux offsets natifs pour le code contenu dans la version recompilée au juste de la fonction spécifiée.|  
|[GetObjectSize2, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|Retourne la taille d’un objet spécifié.|  
|[GetReJITIDs, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|Retourne un tableau d’ID qui identifient tous les-recompilée juste les versions de la fonction spécifiée qui sont toujours allouées.|  
|[InitializeCurrentThread, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|Initialise le thread actuel avant les appels d’API sur le même thread, donc ce blocage peut être évité de profileur suivant.|  
|[RequestReJIT, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|Demande une recompilation juste-à-temps de toutes les instances des fonctions spécifiées.|  
|[RequestRevert, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|Rétablit les versions d'origine de toutes les instances des fonctions spécifiées.|  
  
## <a name="remarks"></a>Notes  
 Le CLR implémente les méthodes de l'interface `ICorProfilerInfo4` à l'aide du modèle libre de threads. Chaque méthode retourne un HRESULT pour indiquer la réussite ou l'échec. Pour obtenir la liste des codes de retour possibles, consultez le fichier CorError.h.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
