---
title: ICorDebugVirtualUnwinder (interface)
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: 67f2234d37165e421874815bdc2ef34f8f50749a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679375"
---
# <a name="icordebugvirtualunwinder-interface"></a>ICorDebugVirtualUnwinder (interface)

Fournit des méthodes pour faciliter le déroulement de la pile.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Nom|  
|------------|----------|  
|[GetContext, méthode](icordebugvirtualunwinder-getcontext-method.md)|Obtient le contexte actuel de ce dérouleur.|  
|[Next, méthode](icordebugvirtualunwinder-next-method.md)|Avance jusqu'au contexte de l'appelant.|  
  
## <a name="remarks"></a>Remarques  

 Les membres de l'interface `ICorDebugVirtualUnwinder` sont implémentés par le débogueur pour faciliter le déroulement de la pile.  
  
> [!NOTE]
> Cette interface est uniquement disponible avec .NET Native. Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
