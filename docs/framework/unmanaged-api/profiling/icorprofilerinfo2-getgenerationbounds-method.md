---
title: ICorProfilerInfo2::GetGenerationBounds, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetGenerationBounds
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetGenerationBounds
helpviewer_keywords:
- ICorProfilerInfo2::GetGenerationBounds method [.NET Framework profiling]
- GetGenerationBounds method [.NET Framework profiling]
ms.assetid: 9c37185f-d1e0-4a6e-8b99-707f7df61d88
topic_type:
- apiref
ms.openlocfilehash: 2b9bf1a9f40764f6d0544bafb91f967905eb40c7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703910"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a>ICorProfilerInfo2::GetGenerationBounds, méthode

Obtient les régions de la mémoire, qui sont des segments du tas, composant les différentes générations de garbage collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
## <a name="parameters"></a>Paramètres  

 `cObjectRanges`  
 [in] Nombre d'éléments alloués par l'appelant pour le tableau `ranges`.  
  
 `pcObjectRanges`  
 [out] Pointeur vers un entier qui spécifie le nombre total de plages, dont une partie ou la totalité sera retournée dans le tableau `ranges`.  
  
 `ranges`  
 à Tableau de structures [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) , qui décrivent chacune une plage (autrement dit, un bloc) de mémoire dans la génération qui est en cours d’garbage collection.  
  
## <a name="remarks"></a>Remarques  

 La méthode `GetGenerationBounds` peut être appelée à partir de tout rappel de profileur, à condition que le garbage collection ne soit pas en cours d'exécution.

 La plupart des décalages de générations ont lieu pendant les opérations de garbage collection. Les générations peuvent devenir plus volumineuses entre les collections, mais elles ne se déplacent généralement pas. Par conséquent, les endroits les plus intéressants pour appeler `GetGenerationBounds` sont dans `ICorProfilerCallback2::GarbageCollectionStarted` et `ICorProfilerCallback2::GarbageCollectionFinished`.  
  
 Pendant le démarrage du programme, certains objets sont alloués par le Common Language Runtime (CLR) lui-même, en général dans les générations 3 et 0. Ainsi, quand le code managé commence à s'exécuter, ces générations contiennent déjà des objets. Normalement, les générations 1 et 2 sont vides, à l'exception des objets factices qui sont générés par le garbage collector. (La taille des objets factices est de 12 octets dans les implémentations 32 bits du CLR ; la taille est supérieure dans les implémentations de 64 bits.) Vous pouvez également voir les plages de génération 2 qui se trouvent dans les modules générés par le générateur d’images natives (NGen.exe). Dans ce cas, les objets de la génération 2 sont des *objets figés* qui sont alloués lorsque NGen.exe s’exécute plutôt que par le garbage collector.  
  
 Cette fonction utilise des mémoires tampons allouées par l'appelant.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](icorprofilerinfo2-interface.md)
- [Interfaces de profilage](profiling-interfaces.md)
- [Profilage](index.md)
