---
title: Interface ICorProfilerInfo9
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: f38195b1a7983e23c7f5c20055ea8c2a8bfcb7d8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556848"
---
# <a name="icorprofilerinfo9-interface"></a>Interface ICorProfilerInfo9

Sous-classe de [ICorProfilerInfo8](icorprofilerinfo8-interface.md) qui fournit des méthodes pour demander des informations sur les fonctions avec plusieurs versions de code natif.  

## <a name="methods"></a>Méthodes  

| Méthode|Description|  
| ------------|-----------------|  
|[Méthode GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md)| Étant donné une functionId et rejitId, énumère l’adresse de début du code natif de toutes les versions JIT de ce code qui existent actuellement. |
|[Méthode GetILToNativeMapping3](icorprofilerinfo9-getiltonativemapping3-method.md)| À partir de l’adresse de début du code natif, retourne les informations de mappage natives à IL pour cette version JIT du code. |
|[Méthode GetCodeInfo4](icorprofilerinfo9-getcodeinfo4-method.md)| À partir de l’adresse de début du code natif, retourne les blocs de mémoire virtuelle qui stockent ce code. |

## <a name="requirements"></a>Spécifications  
**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/windows.md?pivots=os-windows).  
**En-tête :** CorProf.idl, CorProf.h  
**Versions de .net :**[!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]  

## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](profiling-interfaces.md)
