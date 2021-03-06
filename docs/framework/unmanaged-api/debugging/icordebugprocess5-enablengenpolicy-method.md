---
title: ICorDebugProcess5::EnableNGENPolicy, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
ms.openlocfilehash: e3dfd3cae83c7891d246ff3a81427c161cc0e2d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731386"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a>ICorDebugProcess5::EnableNGENPolicy, méthode

Définit une valeur qui détermine la façon dont une application charge les images natives lors de l’exécution sous un débogueur managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `ePolicy`  
 dans Constante [cordebugngenpolicy,](cordebugngenpolicy-enumeration.md) qui détermine la façon dont une application charge des images natives lors de l’exécution sous un débogueur managé.  
  
## <a name="remarks"></a>Remarques  

 Si la stratégie est définie avec succès, la méthode retourne `S_OK` . Si `ePolicy` est en dehors de la plage des valeurs énumérées définies par [cordebugngenpolicy,](cordebugngenpolicy-enumeration.md), la méthode retourne `E_INVALIDARG` et l’appel de la méthode n’a aucun effet. Si la stratégie du générateur d’images natives (Ngen.exe) ne peut pas être mise à jour, la méthode retourne `E_FAIL` .  
  
 La `ICorDebugProcess5::EnableNGenPolicy` méthode peut être appelée à tout moment pendant la durée de vie du processus. La stratégie est appliquée pour tous les modules qui sont chargés après la définition de la stratégie.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugProcess5, interface](icordebugprocess5-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
