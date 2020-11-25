---
title: ICorDebugGuidToTypeEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type:
- apiref
ms.openlocfilehash: 68f548705213da7d715ae569116abae0cd24129d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705655"
---
# <a name="icordebugguidtotypeenumnext-method"></a>ICorDebugGuidToTypeEnum::Next, méthode

Obtient le nombre spécifié d’instances [cordebugguidtotypemapping,](cordebugguidtotypemapping-structure.md) qui mappent les GUID aux informations de type.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `celt`  
 dans Nombre d’objets de mappage GUID-à-type à récupérer.  
  
 `values`  
 à Tableau de pointeurs, chacun pointant vers un objet [cordebugguidtotypemapping,](cordebugguidtotypemapping-structure.md) qui mappe un GUID Windows Runtime à son objet ICorDebugType correspondant.  
  
 `pceltFetched`  
 à Pointeur vers le nombre d’objets [cordebugguidtotypemapping,](cordebugguidtotypemapping-structure.md) réellement retournés dans `values` .  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Spécifications  

 **Plateformes :** Windows Runtime  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugGuidToTypeEnum, interface](icordebugguidtotypeenum-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
