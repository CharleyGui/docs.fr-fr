---
title: ICorDebugBlockingObjectEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum::Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 3328a2c0-1e48-4a54-802a-9b474cf82c21
topic_type:
- apiref
ms.openlocfilehash: 17d5367564ec1ec98efc264ad9a5794c0d04a947
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672134"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a>ICorDebugBlockingObjectEnum::Next, méthode

Obtient le nombre spécifié d’instances [cordebugexceptionobjectstackframe,](cordebugexceptionobjectstackframe-structure.md) qui contiennent des informations à partir de la pile des appels d’un objet exception.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `celt`  
 dans Nombre d’instances de [cordebugexceptionobjectstackframe,](cordebugexceptionobjectstackframe-structure.md) à récupérer.  
  
 `values`  
 à Tableau de pointeurs, chacun pointant vers un objet [cordebugexceptionobjectstackframe,](cordebugexceptionobjectstackframe-structure.md) .  
  
 `pceltFetched`  
 à Pointeur vers le nombre d’instances [cordebugexceptionobjectstackframe,](cordebugexceptionobjectstackframe-structure.md) réellement retournées.  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Spécifications  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugExceptionObjectCallStackEnum, interface](icordebugexceptionobjectcallstackenum-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
