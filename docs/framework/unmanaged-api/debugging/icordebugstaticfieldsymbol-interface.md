---
title: ICorDebugStaticFieldSymbol, interface
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: f9b82f0f98a668555a8096d7575c049c31cae93a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379437"
---
# <a name="icordebugstaticfieldsymbol-interface"></a>ICorDebugStaticFieldSymbol, interface
Représente les informations sur les symboles de débogage pour un champ static.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetAddress, méthode](icordebugstaticfieldsymbol-getaddress-method.md)|Obtient l'adresse du champ statique.|  
|[GetName, méthode](icordebugstaticfieldsymbol-getname-method.md)|Obtient le nom du champ static.|  
|[GetSize, méthode](icordebugstaticfieldsymbol-getsize-method.md)|Obtient la taille en octets du champ static.|  
  
## <a name="remarks"></a>Remarks  
 L’interface `ICorDebugStaticFieldSymbol` est utilisée pour récupérer les informations sur les symboles de débogage pour un champ statique.  
  
> [!NOTE]
> Cette interface est uniquement disponible avec .NET Native. Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugInstanceFieldSymbol, interface](icordebuginstancefieldsymbol-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
