---
title: ICorProfilerInfo7, interface
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: f80f310c10bae33583cb7cd2048ede4f5efbe14c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861747"
---
# <a name="icorprofilerinfo7-interface"></a>ICorProfilerInfo7, interface
[Prise en charge dans le .NET Framework 4.6.1 et versions ultérieures]  
  
 Sous-classe de [ICorProfilerInfo6](icorprofilerinfo6-interface.md) qui fournit une méthode pour appliquer des métadonnées nouvellement définies à un module et qui fournit l’accès à un flux de symboles en mémoire.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ApplyMetaData, méthode](icorprofilerinfo7-applymetadata-method.md)|Applique les métadonnées nouvellement définies par les méthodes `IMetadataEmit::Define*` à un module spécifié.|  
|[GetInMemorySymbolsLength, méthode](icorprofilerinfo7-getinmemorysymbolslength-method.md)|Retourne la longueur d’un flux de symboles en mémoire.|  
|[ReadInMemorySymbols](icorprofilerinfo7-readinmemorysymbols.md)|Lit les octets d’un flux de symboles en mémoire.|  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](profiling-interfaces.md)
