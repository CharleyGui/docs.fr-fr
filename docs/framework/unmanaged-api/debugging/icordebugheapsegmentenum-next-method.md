---
title: ICorDebugHeapSegmentEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type:
- apiref
ms.openlocfilehash: 8a267ec7123edb73ad51f0781a78344119ec6f21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178893"
---
# <a name="icordebugheapsegmentenumnext-method"></a>ICorDebugHeapSegmentEnum::Next, méthode
Obtient le nombre spécifié de [cas COR_HEAPOBJECT](cor-heapobject-structure.md) qui contiennent des informations sur les régions de mémoire du tas géré.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 celt  
 [dans] Nombre de segments à récupérer.  
  
 segments  
 [out] Un tableau de pointeurs, chacun pointant vers un objet [COR_HEAPOBJECT](cor-heapobject-structure.md) qui fournit des informations sur une région de mémoire dans le tas géré.  
  
 pceltFetched  
 [out] Un pointeur sur [COR_HEAPOBJECT](cor-heapobject-structure.md) le nombre d’objets `segments`COR_HEAPOBJECT effectivement retourné dans . Cette valeur peut être `null` si `celt` est égal à 1.  
  
## <a name="remarks"></a>Notes   
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugHeapSegmentEnum, interface](icordebugheapsegmentenum-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
