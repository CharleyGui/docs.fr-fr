---
title: Énumération COR_PRF_REJIT_FLAGS
ms.date: 08/06/2019
api_name:
- COR_PRF_REJIT_FLAGS Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_REJIT_FLAGS
helpviewer_keywords:
- COR_PRF_REJIT_FLAGS enumeration [.NET Framework profiling]
topic_type:
- apiref
author: davmason
ms.author: davmason
ms.openlocfilehash: 1b1d6ad5d465d746f4c1a9400c43613591373322
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546944"
---
# <a name="cor_prf_rejit_flags-enumeration"></a>Énumération COR_PRF_REJIT_FLAGS
Contient des valeurs qui indiquent comment l’API [ICorProfilerInfo10 :: RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) doit se comporter.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum  
{
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| Les méthodes ReJITted ne peuvent pas être inline dans d’autres méthodes. |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| Reçoit `GetFunctionParameters` des rappels pour toutes les méthodes qui Inline sont demandées par ReJITted. |  

## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/windows.md?pivots=os-windows).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de profilage](profiling-enumerations.md)
