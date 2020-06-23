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
ms.openlocfilehash: 3d4e44eefaf99a40b9c4f1c45e7dd81192f8b607
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904271"
---
# <a name="icordebugheapsegmentenumnext-method"></a>ICorDebugHeapSegmentEnum::Next, méthode
Obtient le nombre spécifié d’instances de [COR_SEGMENT](cor-segment-structure.md) qui contiennent des informations sur les régions de mémoire du tas managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 celt  
 dans Nombre de segments à récupérer.  
  
 segments  
 à Tableau de pointeurs, chacun pointant vers un objet [COR_SEGMENT](cor-segment-structure.md) qui fournit des informations sur une zone de mémoire dans le tas managé.  
  
 pceltFetched  
 à Pointeur vers le nombre d’objets [COR_SEGMENT](cor-segment-structure.md) réellement retournés dans `segments` . Cette valeur peut être `null` si `celt` est égal à 1.  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugHeapSegmentEnum, interface](icordebugheapsegmentenum-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
