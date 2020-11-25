---
title: Interface ICorProfilerCallback7
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: a0be019e-aaa1-4036-990f-565f114d4b5c
ms.openlocfilehash: e9c7186b3217c29805327e6c1d6b10f580c3a9e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725454"
---
# <a name="icorprofilercallback7-interface"></a>Interface ICorProfilerCallback7

[Prise en charge dans le .NET Framework 4.6.1 et versions ultérieures]  
  
 Sous-classe de [ICorProfilerCallback6](icorprofilercallback6-interface.md) qui fournit une méthode de rappel que le Common Language Runtime utilise pour informer le profileur de la mise à jour du flux de symbole associé à un module en mémoire.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ModuleInMemorySymbolsUpdated, méthode](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|Notifie le profileur de la mise à jour du flux de symbole associé à un module en mémoire.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](profiling-interfaces.md)
