---
title: Interface ICorProfilerInfo8
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 476bcbd91188e3ff9eb63f50cfa2118a440b1a69
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868315"
---
# <a name="icorprofilerinfo8-interface"></a>Interface ICorProfilerInfo8

Sous-classe de [ICorProfilerInfo7](icorprofilerinfo7-interface.md) qui fournit des méthodes pour demander des informations sur les méthodes dynamiques.

## <a name="methods"></a>Méthodes  

| Méthode|Description|  
| ------------|-----------------|  
|[Méthode IsFunctionDynamic](icorprofilerinfo8-isfunctiondynamic-method.md)| Détermine si une fonction n’a pas de métadonnées associées.|
|[Méthode GetFunctionFromIP3](icorprofilerinfo8-getfunctionfromip3-method.md)| Mappe un pointeur d’instruction de code managé à une FunctionID. Cette méthode fonctionne pour les méthodes dynamiques et non dynamiques. |
|[Méthode GetDynamicFunctionInfo](icorprofilerinfo8-getdynamicfunctioninfo-method.md)| Récupère des informations sur les méthodes dynamiques. |

## <a name="requirements"></a>Configuration requise pour  
**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
**En-tête :** CorProf.idl, CorProf.h  
**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](profiling-interfaces.md)
