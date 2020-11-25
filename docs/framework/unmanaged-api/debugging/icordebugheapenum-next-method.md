---
title: ICorDebugHeapEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type:
- apiref
ms.openlocfilehash: 320b3ca55a60ec7751c88a246ab6ee90b6b6c4cc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724349"
---
# <a name="icordebugheapenumnext-method"></a>ICorDebugHeapEnum::Next, méthode

Obtient le nombre spécifié d’instances [COR_HEAPOBJECT](cor-heapobject-structure.md) qui contiennent des informations sur les objets sur le tas managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 celt  
 [in] Nombre d'objets à récupérer.  
  
 objets  
 à Tableau de pointeurs, chacun pointant vers un objet [COR_HEAPOBJECT](cor-heapobject-structure.md) qui fournit des informations sur un objet sur le tas managé.  
  
 pceltFetched  
 à Pointeur vers le nombre d’objets [COR_HEAPOBJECT](cor-heapobject-structure.md) réellement retournés dans `objects` . Cette valeur peut être `null` si `celt` est égal à 1.  
  
## <a name="remarks"></a>Remarques  

 Le champ `COR_HEAPOBJECT.type` est l'identificateur d'une interface COM imbriquée avec comptage des références. Cette référence doit être libérée par l'appelant d'`ICorDebugHeapEnum::Next`.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugHeapEnum, interface](icordebugheapenum-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
