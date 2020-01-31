---
title: Interface ICorProfilerInfo9
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 371e85ce8f5d7b420a30ac842ec658949e47d30e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861643"
---
# <a name="icorprofilerinfo9-interface"></a>Interface ICorProfilerInfo9

Sous-classe de [ICorProfilerInfo8](icorprofilerinfo8-interface.md) qui fournit des méthodes pour demander des informations sur les fonctions avec plusieurs versions de code natif.  

## <a name="methods"></a>Méthodes  

| Méthode|Description|  
| ------------|-----------------|  
|[Méthode GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md)| Étant donné une functionId et rejitId, énumère l’adresse de début du code natif de toutes les versions JIT de ce code qui existent actuellement. |
|[Méthode GetILToNativeMapping3](icorprofilerinfo9-getiltonativemapping3-method.md)| À partir de l’adresse de début du code natif, retourne les informations de mappage natives à IL pour cette version JIT du code. |
|[Méthode GetCodeInfo4](icorprofilerinfo9-getcodeinfo4-method.md)| À partir de l’adresse de début du code natif, retourne les blocs de mémoire virtuelle qui stockent ce code. |

## <a name="requirements"></a>Configuration requise pour  
**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).  
**En-tête :** CorProf.idl, CorProf.h  
**Versions de .net :** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]  

## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](profiling-interfaces.md)
