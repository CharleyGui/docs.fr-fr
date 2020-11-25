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
ms.openlocfilehash: 747313f217092652d5a9404fbf81383fa0828ee9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696659"
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
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|La transition est due à un appel dans une fonction.|  
|`COR_PRF_TRANSITION_RETURN`|La transition est due à un retour d’une fonction.|  
  
## <a name="remarks"></a>Remarques  

 Quand une transition se produit, le profileur reçoit un rappel [ICorProfilerCallback :: ManagedToUnmanagedTransition,](icorprofilercallback-managedtounmanagedtransition-method.md) ou [ICorProfilerCallback :: UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) , qui fournit une valeur de l' `COR_PRF_TRANSITION_REASON` énumération pour indiquer la raison de la transition.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
