---
title: ICorProfilerCallback4::SurvivingReferences2, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.SurvivingReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::SurvivingReferences2
helpviewer_keywords:
- ICorProfilerCallback4::SurvivingReferences2 method [.NET Framework profiling]
- SurvivingReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 02b51888-5d89-4e50-a915-45b7e329aad9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: beb260030914de211d227342e497daa3db287c9e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758076"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a>ICorProfilerCallback4::SurvivingReferences2, méthode
Signale la disposition d'objets dans le tas suite à un garbage collection de non-compactage. Cette méthode est appelée si le profileur a implémenté le [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface. Ce rappel remplace la [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) (méthode), car il peut indiquer des plages plus larges d’objets dont les longueurs dépassent ce qui peut être exprimé en ULONG.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Paramètres  
 `cSurvivingObjectIDRanges`  
 [in] Nombre de blocs d'objets contigus qui ont survécu à la suite du garbage collection de non-compactage. Autrement dit, la valeur de `cSurvivingObjectIDRanges` est la taille des tableaux `objectIDRangeStart` et `cObjectIDRangeLength` qui stockent un `ObjectID` et une longueur, respectivement, pour chaque bloc d'objets.  
  
 Les deux arguments suivants de `SurvivingReferences2` sont des tableaux parallèles. En d'autres termes, `objectIDRangeStart` et `cObjectIDRangeLength` concernent le même bloc d'objets contigus.  
  
 `objectIDRangeStart`  
 [in] Tableau de valeurs `ObjectID`, chacune d'elles étant l'adresse de début d'un bloc d'objets actifs contigus dans la mémoire.  
  
 `cObjectIDRangeLength`  
 [in] Tableau d'entiers, chacun d'eux correspondant à la taille d'un bloc survivant d'objets contigus dans la mémoire.  
  
 Une taille est spécifiée pour chaque bloc référencé dans le tableau `objectIDRangeStart`.  
  
## <a name="remarks"></a>Notes  
 Les éléments des tableaux `objectIDRangeStart` et `cObjectIDRangeLength` doivent être interprétés comme suit pour déterminer si un objet a survécu au garbage collection. Supposons qu'une valeur `ObjectID` (`ObjectID`) se trouve dans la plage suivante :  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Pour toute valeur de `i` qui se trouve dans la plage suivante, l’objet a survécu au garbage collection :  
  
 0 <= `i` < `cSurvivingObjectIDRanges`  
  
 Un garbage collection de non-compactage libère la mémoire occupée par des objets « morts », mais ne compacte pas cet espace libéré. Par conséquent, la mémoire est retournée au tas, mais aucun objet « actif » n'est déplacé.  
  
 Le Common Language Runtime (CLR) appelle `SurvivingReferences2` pour les garbage collection de non-compactage. Pour le garbage collection de compactage, [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) est appelée à la place. Un garbage collection unique peut être de compactage pour une génération et de non-compactage pour une autre. Pour un garbage collection de n’importe quel génération, le profileur reçoit un `SurvivingReferences2` rappel ou un [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) rappel, mais pas les deux.  
  
 Plusieurs rappels `SurvivingReferences2` peuvent être reçus pendant un garbage collection particulier, en raison de la mise en mémoire tampon interne limitée, de multiples rappels pendant un garbage collection de serveur et pour d’autres raisons. En cas de rappels multiples pendant un garbage collection, les informations se cumulent ; toutes les références qui sont rapportées dans un rappel `SurvivingReferences2` survivent au garbage collection.  
  
 Si le profileur implémente à la fois le [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) et [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, le `SurvivingReferences2` méthode est appelée avant la [ICorProfilerCallback2 :: SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) (méthode), mais uniquement si `SurvivingReferences2` est retournée avec succès. Les profileurs peuvent retourner une valeur HRESULT qui indique un échec de la méthode `SurvivingReferences2` pour éviter d'appeler la seconde méthode.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback4, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
