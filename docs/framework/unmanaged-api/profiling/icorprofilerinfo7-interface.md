---
title: ICorProfilerInfo7, interface
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: 4acafafa284549fe1b078542a88c0818dcde3038
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686057"
---
# <a name="icorprofilerinfo7-interface"></a>ICorProfilerInfo7, interface

[Prise en charge dans le .NET Framework 4.6.1 et versions ultérieures]  
  
 Sous-classe de [ICorProfilerInfo6](icorprofilerinfo6-interface.md) qui fournit une méthode pour appliquer des métadonnées nouvellement définies à un module et qui fournit l’accès à un flux de symboles en mémoire.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ApplyMetaData, méthode](icorprofilerinfo7-applymetadata-method.md)|Applique les métadonnées nouvellement définies par les `IMetadataEmit::Define*` méthodes à un module spécifié.|  
|[GetInMemorySymbolsLength, méthode](icorprofilerinfo7-getinmemorysymbolslength-method.md)|Retourne la longueur d’un flux de symboles en mémoire.|  
|[ReadInMemorySymbols](icorprofilerinfo7-readinmemorysymbols.md)|Lit les octets d’un flux de symboles en mémoire.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](profiling-interfaces.md)
