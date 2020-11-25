---
title: ICorDebugILFrame3, interface
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 15212cb5-93d4-4025-bec9-d4b9919eb1fe
topic_type:
- apiref
ms.openlocfilehash: dab5329086971b9349deaf84535fa251744f3cf0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724986"
---
# <a name="icordebugilframe3-interface"></a>ICorDebugILFrame3, interface

Fournit une méthode qui encapsule la valeur de retour d'une fonction. `ICorDebugILFrame3` est une extension logique des interfaces ICorDebugILFrame et ICorDebugILFrame2.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetReturnValueForILOffset, méthode](icordebugilframe3-getreturnvalueforiloffset-method.md)|Obtient un objet ICorDebugValue qui encapsule la valeur de retour d’une fonction.|  
  
## <a name="remarks"></a>Remarques  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugCode3, interface](icordebugcode3-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
