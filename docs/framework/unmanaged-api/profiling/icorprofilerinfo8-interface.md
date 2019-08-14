---
title: Interface ICorProfilerInfo8
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 210029ed1b1c7d780f3895f975f7a72227bbea80
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973819"
---
# <a name="icorprofilerinfo8-interface"></a>Interface ICorProfilerInfo8

Sous-classe de [ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) qui fournit des méthodes pour demander des informations sur les méthodes dynamiques.

## <a name="methods"></a>Méthodes  

| Méthode|Description|  
| ------------|-----------------|  
|[Méthode IsFunctionDynamic](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-isfunctiondynamic-method.md)| Détermine si une fonction n’a pas de métadonnées associées.|
|[Méthode GetFunctionFromIP3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getfunctionfromip3-method.md)| Mappe un pointeur d’instruction de code managé à une FunctionID. Cette méthode fonctionne pour les méthodes dynamiques et non dynamiques. |
|[Méthode GetDynamicFunctionInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getdynamicfunctioninfo-method.md)| Récupère des informations sur les méthodes dynamiques. |

## <a name="requirements"></a>Configuration requise  
**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
**En-tête :** CorProf. idl, CorProf. h  
**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
## <a name="see-also"></a>Voir aussi
- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
