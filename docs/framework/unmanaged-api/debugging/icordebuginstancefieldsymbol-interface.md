---
title: ICorDebugInstanceFieldSymbol, interface
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: 41258b0eeed5fbf8ab86546f74073f8eeaa3085c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777526"
---
# <a name="icordebuginstancefieldsymbol-interface"></a>ICorDebugInstanceFieldSymbol, interface
Représente les informations sur les symboles de débogage pour un champ d’instance.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetName, méthode](icordebuginstancefieldsymbol-getname-method.md)|Obtient le nom du champ d'instance.|  
|[GetOffset, méthode](icordebuginstancefieldsymbol-getoffset-method.md)|Obtient l'offset en octets de ce champ d'instance dans sa classe parente.|  
|[GetSize, méthode](icordebuginstancefieldsymbol-getsize-method.md)|Obtient la taille en octets du champ d'instance.|  
  
## <a name="remarks"></a>Notes  
 L'interface `ICorDebugInstanceFieldSymbol` est utilisée pour récupérer les informations sur les symboles de débogage pour un champ d'instance.  
  
> [!NOTE]
> Cette interface est uniquement disponible avec .NET Native. Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugStaticFieldSymbol, interface](icordebugstaticfieldsymbol-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
