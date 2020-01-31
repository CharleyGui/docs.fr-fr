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
ms.openlocfilehash: c287b630aee58c6795ef405cc1801149e220fd51
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868419"
---
# <a name="icorprofilerinfo4-interface"></a>ICorProfilerInfo4, interface
Fournit des méthodes utilisées par les profileurs de code pour communiquer avec le common language runtime (CLR) afin de contrôler la surveillance des événements et les informations de demande. . L’interface `ICorProfilerInfo4` est une extension des autres interfaces `ICorProfilerInfo`. Il fournit de nouvelles méthodes pour prendre en charge la recompilation juste-à-temps (JIT), ajoutée dans le .NET Framework 4,5.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumJITedFunctions2, méthode](icorprofilerinfo4-enumjitedfunctions2-method.md)|Retourne un énumérateur pour toutes les fonctions qui ont été précédemment compilées juste-à-temps et qui ont été recompilées juste-à-temps.|  
|[EnumThreads, méthode](icorprofilerinfo4-enumthreads-method.md)|Obtient un énumérateur qui fournit des méthodes pour itérer séquentiellement au sein de la collection de tous les threads managés dans le processus profilé.|  
|[GetCodeInfo3, méthode](icorprofilerinfo4-getcodeinfo3-method.md)|Obtient les étendues de code natif associées à la version recompilée juste-à-temps de la fonction spécifiée.|  
|[GetFunctionFromIP2, méthode](icorprofilerinfo4-getfunctionfromip2-method.md)|Mappe un pointeur d’instruction de code managé à la version recompilée juste-à-temps d’une fonction spécifiée.|  
|[GetILToNativeMapping2, méthode](icorprofilerinfo4-getiltonativemapping2-method.md)|Obtient un mappage des offsets MSIL (Microsoft Intermediate Language) aux offsets natifs pour le code contenu dans la version recompilée juste-à-temps de la fonction spécifiée.|  
|[GetObjectSize2, méthode](icorprofilerinfo4-getobjectsize2-method.md)|Retourne la taille d’un objet spécifié.|  
|[GetReJITIDs, méthode](icorprofilerinfo4-getrejitids-method.md)|Retourne un tableau d’ID identifiant toutes les versions recompilées juste-à-temps de la fonction spécifiée qui sont toujours allouées.|  
|[InitializeCurrentThread, méthode](icorprofilerinfo4-initializecurrentthread-method.md)|Initialise le thread actuel avant les appels d’API du profileur suivants sur le même thread, afin que l’interblocage puisse être évité.|  
|[RequestReJIT, méthode](icorprofilerinfo4-requestrejit-method.md)|Demande une recompilation juste-à-temps de toutes les instances des fonctions spécifiées.|  
|[RequestRevert, méthode](icorprofilerinfo4-requestrevert-method.md)|Rétablit les versions d'origine de toutes les instances des fonctions spécifiées.|  
  
## <a name="remarks"></a>Notes  
 Le CLR implémente les méthodes de l'interface `ICorProfilerInfo4` à l'aide du modèle libre de threads. Chaque méthode retourne un HRESULT pour indiquer la réussite ou l'échec. Pour obtenir la liste des codes de retour possibles, consultez le fichier CorError.h.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](profiling-interfaces.md)
- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
