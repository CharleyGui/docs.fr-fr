---
title: ICorProfilerCallback2::SurvivingReferences, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.SurvivingReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::SurvivingReferences
helpviewer_keywords:
- ICorProfilerCallback2::SurvivingReferences method [.NET Framework profiling]
- SurvivingReferences method [.NET Framework profiling]
ms.assetid: f165200e-3a91-47f7-88fc-13ff10c8babc
topic_type:
- apiref
ms.openlocfilehash: 3681106bca94f1fefb2f24a1aa4254eb2b1b0531
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499738"
---
# <a name="icorprofilercallback2survivingreferences-method"></a>ICorProfilerCallback2::SurvivingReferences, méthode
Signale la disposition d'objets dans le tas suite à un garbage collection de non-compactage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Paramètres  
 `cSurvivingObjectIDRanges`  
 [in] Nombre de blocs d'objets contigus qui ont survécu à la suite du garbage collection de non-compactage. Autrement dit, la valeur de `cSurvivingObjectIDRanges` est la taille des tableaux `objectIDRangeStart` et `cObjectIDRangeLength` qui stockent un `ObjectID` et une longueur, respectivement, pour chaque bloc d'objets.  
  
 Les deux arguments suivants de `SurvivingReferences` sont des tableaux parallèles. En d'autres termes, `objectIDRangeStart` et `cObjectIDRangeLength` concernent le même bloc d'objets contigus.  
  
 `objectIDRangeStart`  
 [in] Tableau de valeurs `ObjectID`, chacune d'elles étant l'adresse de début d'un bloc d'objets actifs contigus dans la mémoire.  
  
 `cObjectIDRangeLength`  
 [in] Tableau d'entiers, chacun d'eux correspondant à la taille d'un bloc survivant d'objets contigus dans la mémoire.  
  
 Une taille est spécifiée pour chaque bloc référencé dans le tableau `objectIDRangeStart`.  
  
## <a name="remarks"></a>Remarques  
  
> [!IMPORTANT]
> Cette méthode signale les tailles en tant que `MAX_ULONG` pour les objets qui sont supérieurs à 4 Go sur les plateformes 64 bits. Pour les objets dont la taille est supérieure à 4 Go, utilisez la méthode [ICorProfilerCallback4 :: survivingreferences2,](icorprofilercallback4-survivingreferences2-method.md) à la place.  
  
 Les éléments des tableaux `objectIDRangeStart` et `cObjectIDRangeLength` doivent être interprétés comme suit pour déterminer si un objet a survécu au garbage collection. Supposons qu'une valeur `ObjectID` (`ObjectID`) se trouve dans la plage suivante :  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Pour toute valeur de `i` qui se trouve dans la plage suivante, l’objet a survécu au garbage collection :  
  
 0 <=`i` < `cSurvivingObjectIDRanges`  
  
 Un garbage collection de non-compactage libère la mémoire occupée par des objets « morts », mais ne compacte pas cet espace libéré. Par conséquent, la mémoire est retournée au tas, mais aucun objet « actif » n'est déplacé.  
  
 Le Common Language Runtime (CLR) appelle `SurvivingReferences` pour les garbage collection de non-compactage. Pour compacter les garbage collection, [ICorProfilerCallback :: MovedReferences](icorprofilercallback-movedreferences-method.md) est appelé à la place. Un garbage collection unique peut être de compactage pour une génération et de non-compactage pour une autre. Pour un garbage collection de n'importe quelle génération, le profileur reçoit un rappel `SurvivingReferences` ou un rappel `MovedReferences`, mais pas les deux.  
  
 Plusieurs rappels `SurvivingReferences` peuvent être reçus pendant un garbage collection particulier, en raison de la mise en mémoire tampon interne limitée, du signalement de plusieurs threads lors d’un garbage collection de serveur, etc. En cas de rappels multiples pendant un garbage collection, les informations se cumulent. Ainsi, toutes les références qui sont signalées dans un rappel `SurvivingReferences` survivent au garbage collection.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
- [ICorProfilerCallback2, interface](icorprofilercallback2-interface.md)
- [SurvivingReferences2, méthode](icorprofilercallback4-survivingreferences2-method.md)
