---
title: ICorDebugDebugEvent::GetEventKind, méthode
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
ms.openlocfilehash: 7876dc6ec5ecee52b64e54e1c42533f8348e4dc4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713676"
---
# <a name="icordebugdebugeventgeteventkind-method"></a>ICorDebugDebugEvent::GetEventKind, méthode

Indique le type d'événement représenté par cet objet `ICorDebugDebugEvent`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 pDebugEventKind  
 Pointeur vers un membre de l’énumération [cordebugdebugeventkind,](cordebugdebugeventkind-enumeration.md) qui indique le type d’événement.  
  
## <a name="remarks"></a>Remarques  

 En fonction de la valeur de `pDebugEventKind`, vous pouvez appeler `QueryInterface` pour obtenir une interface d'événement de débogage plus précise qui fournit des données supplémentaires.  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugDebugEvent, interface](icordebugdebugevent-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
