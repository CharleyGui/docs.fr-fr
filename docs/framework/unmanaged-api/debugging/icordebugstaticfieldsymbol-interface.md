---
title: ICorDebugStaticFieldSymbol, interface
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: b50b9c8435f19e1a77229f01dc85514f5f75c9f5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791801"
---
# <a name="icordebugstaticfieldsymbol-interface"></a>ICorDebugStaticFieldSymbol, interface
Représente les informations sur les symboles de débogage pour un champ static.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetAddress, méthode](icordebugstaticfieldsymbol-getaddress-method.md)|Obtient l'adresse du champ statique.|  
|[GetName, méthode](icordebugstaticfieldsymbol-getname-method.md)|Obtient le nom du champ static.|  
|[GetSize, méthode](icordebugstaticfieldsymbol-getsize-method.md)|Obtient la taille en octets du champ static.|  
  
## <a name="remarks"></a>Notes  
 L’interface `ICorDebugStaticFieldSymbol` est utilisée pour récupérer les informations sur les symboles de débogage pour un champ statique.  
  
> [!NOTE]
> Cette interface est uniquement disponible avec .NET Native. Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugInstanceFieldSymbol, interface](icordebuginstancefieldsymbol-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
