---
title: ICorDebugAssembly2::IsFullyTrusted, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2.IsFullyTrusted
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2::IsFullyTrusted
helpviewer_keywords:
- ICorDebugAssembly2::IsFullyTrusted method [.NET Framework debugging]
- IsFullyTrusted method [.NET Framework debugging]
ms.assetid: 26cbd27d-12bf-444a-8197-ccd14d37dda3
topic_type:
- apiref
ms.openlocfilehash: 8a2a6be0db76f5ee2c7fa67c2038e0a5c845bd0f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719708"
---
# <a name="icordebugassembly2isfullytrusted-method"></a>ICorDebugAssembly2::IsFullyTrusted, méthode

Obtient une valeur qui indique si le système de sécurité du runtime a accordé un niveau de confiance totale à l’assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pbFullyTrusted`  
 [out] `true` Si le système de sécurité du runtime a accordé une confiance totale à l’assembly ; Sinon, `false` .  
  
## <a name="remarks"></a>Remarques  

 Cette méthode retourne un HRESULT de CORDBG_E_NOTREADY si la stratégie de sécurité de l’assembly n’a pas encore été résolue, autrement dit, si aucun code de l’assembly n’a encore été exécuté.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
