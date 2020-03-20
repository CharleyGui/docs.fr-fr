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
ms.openlocfilehash: 8fc5f1a488826d8adc6aecb8ef122609bebbe813
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177096"
---
# <a name="cor_prf_rejit_flags-enumeration"></a>Énumération COR_PRF_REJIT_FLAGS
Contient des valeurs qui indiquent comment [l’ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API devrait se comporter.  
  
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
|`COR_PRF_REJIT_BLOCK_INLINING`| Les méthodes ReJITted seront empêchées d’être inlinées dans d’autres méthodes. |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| Recevez `GetFunctionParameters` des rappels pour toutes les méthodes qui en ligne les méthodes demandées pour être ReJITted. |  

## <a name="requirements"></a>Spécifications  
 **Plates-formes:** Voir [.NET Core systèmes d’exploitation pris en charge](../../../core/install/dependencies.md?pivots=os-windows).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de profilage](profiling-enumerations.md)
