---
title: ICorDebugProcess5::EnumerateHandles, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHandles
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type:
- apiref
ms.openlocfilehash: 291b384d6f0c8c1404b380c653693ec65fcfc960
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213411"
---
# <a name="icordebugprocess5enumeratehandles-method"></a>ICorDebugProcess5::EnumerateHandles, méthode
Obtient un énumérateur pour les handles d’objet dans un processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a>Paramètres  
 `types`  
 dans Combinaison d’opérations de bits de valeurs [corgcreferencetype,](corgcreferencetype-enumeration.md) qui spécifient le type de handles à inclure dans la collection.  
  
 `ppENum`  
 à Pointeur vers l’adresse d’un [icordebuggcreferenceenum,](icordebuggcreferenceenum-interface.md) qui est un énumérateur pour les objets qui doivent être récupérés par le garbage collector.  
  
## <a name="remarks"></a>Remarks  
 `EnumerateHandles`est une fonction d’assistance qui prend en charge l’inspection de la table de handles. Elle est similaire à la méthode [ICorDebugProcess5 :: enumerategcreferences,](icordebugprocess5-enumerategcreferences-method.md) , à ceci près qu’au lieu de remplir une collection [icordebuggcreferenceenum,](icordebuggcreferenceenum-interface.md) avec tous les objets qui doivent être récupérés par le garbage collector, elle comprend uniquement les objets qui ont des descripteurs de la table de handles.  
  
 Le `types` paramètre spécifie les types de handles à inclure dans la collection. `types`Il peut s’agir de l’un des trois membres suivants de l’énumération [corgcreferencetype,](corgcreferencetype-enumeration.md) :  
  
- `CorHandleStrongOnly`(Handles vers des références fortes uniquement).  
  
- `CorHandleWeakOnly`(Handles vers des références faibles uniquement).  
  
- `CorHandleAll`(tous les descripteurs).  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](debugging-structures.md)
- [Débogage](index.md)
