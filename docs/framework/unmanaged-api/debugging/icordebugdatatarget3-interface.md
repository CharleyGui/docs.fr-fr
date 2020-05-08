---
title: ICorDebugDataTarget3 (interface)
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
ms.openlocfilehash: 57ef9b567d57c77c523ca6daefcf80b1d7de66d1
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976406"
---
# <a name="icordebugdatatarget3-interface"></a>ICorDebugDataTarget3 (interface)
Étend logiquement l’interface [ICorDebugDataTarget](icordebugdatatarget-interface.md) pour fournir des informations sur les modules chargés.  
  
## <a name="method"></a>Méthode  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetLoadedModules, méthode](icordebugdatatarget3-getloadedmodules-method.md)|Obtient la liste des modules qui ont été chargés jusqu'à présent.|  
  
## <a name="remarks"></a>Notes   
  
> [!NOTE]
> Cette interface est uniquement disponible avec .NET Native. Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
