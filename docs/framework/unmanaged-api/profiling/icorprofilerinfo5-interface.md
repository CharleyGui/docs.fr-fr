---
title: ICorProfilerInfo5, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo5
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 7bd48c34-37ed-4230-9eec-39a17280f05d
topic_type:
- apiref
ms.openlocfilehash: a6206e35280e073df2abfb7ae46aa84d34b30208
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733800"
---
# <a name="icorprofilerinfo5-interface"></a>ICorProfilerInfo5, interface

[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
 Une sous-classe de [ICorProfilerInfo4](icorprofilerinfo4-interface.md) qui fournit des méthodes à utiliser par les profileurs de code pour communiquer avec le Common Language Runtime (CLR) afin de contrôler la surveillance des événements.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetEventMask2, méthode](icorprofilerinfo5-geteventmask2-method.md)|Obtient les catégories des événements actifs pour lesquelles le profileur veut recevoir des notifications du CLR.|  
|[SetEventMask2, méthode](icorprofilerinfo5-seteventmask2-method.md)|Définit une valeur qui spécifie les types d'événements pour lesquels le profileur veut recevoir des notifications d'événements du CLR.|  
  
## <a name="remarks"></a>Remarques  

 Les méthodes disponibles sur cette interface sont destinées à remplacer les méthodes [ICorProfilerInfo :: GetEventMask](icorprofilerinfo-geteventmask-method.md) et [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](profiling-interfaces.md)
