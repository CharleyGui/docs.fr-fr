---
title: COR_PRF_TRANSITION_REASON, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_TRANSITION_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_TRANSITION_REASON
helpviewer_keywords:
- COR_PRF_TRANSITION_REASON enumeration [.NET Framework profiling]
ms.assetid: da941118-01b7-4197-ae5b-9f2f8adcd623
topic_type:
- apiref
ms.openlocfilehash: 1c3c311fd431b6c0b18af3d6516973b2471cfabd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867044"
---
# <a name="cor_prf_transition_reason-enumeration"></a>COR_PRF_TRANSITION_REASON, énumération
Indique la raison d'une transition de code managé en code non managé, ou l'inverse.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a>Members  
  
|Member|Description|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|La transition est due à un appel dans une fonction.|  
|`COR_PRF_TRANSITION_RETURN`|La transition est due à un retour d’une fonction.|  
  
## <a name="remarks"></a>Notes  
 Quand une transition se produit, le profileur reçoit un rappel [ICorProfilerCallback :: ManagedToUnmanagedTransition,](icorprofilercallback-managedtounmanagedtransition-method.md) ou [ICorProfilerCallback :: UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) , qui fournit une valeur de l’énumération `COR_PRF_TRANSITION_REASON` pour indiquer la raison de la transition.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
