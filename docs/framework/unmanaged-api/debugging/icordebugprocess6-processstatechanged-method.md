---
title: ICorDebugProcess6::ProcessStateChanged, méthode
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: 6be216741e902b15efc3a3ece95cb4a4229960e3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212843"
---
# <a name="icordebugprocess6processstatechanged-method"></a>ICorDebugProcess6::ProcessStateChanged, méthode
Informe [ICorDebug](icordebug-interface.md) que le processus est en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a>Paramètres  
 `change`  
 dans Membre de l’énumération [processstatechanged,](icordebugprocess6-processstatechanged-method.md)  
  
## <a name="remarks"></a>Remarks  
 Le débogueur appelle cette méthode pour notifier [ICorDebug](icordebug-interface.md) que le processus est en cours d’exécution.  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugProcess6, interface](icordebugprocess6-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
