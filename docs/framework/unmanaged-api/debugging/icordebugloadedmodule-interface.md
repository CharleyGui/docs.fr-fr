---
title: ICorDebugLoadedModule (interface)
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
ms.openlocfilehash: 6087411e8d23a9c3c97cb97ac8159d436e24759b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731826"
---
# <a name="icordebugloadedmodule-interface"></a>ICorDebugLoadedModule (interface)

Fournit des informations sur un module chargé.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetBaseAddress, méthode](icordebugloadedmodule-getbaseaddress-method.md)|Obtient l'adresse de base du module chargé.|  
|[GetName, méthode](icordebugloadedmodule-getname-method.md)|Obtient le nom du module chargé.|  
|[GetSize, méthode](icordebugloadedmodule-getsize-method.md)|Obtient la taille en octets du module chargé.|  
  
## <a name="remarks"></a>Remarques  

 L'interface `ICorDebugLoadedModule` est implémentée par un débogueur et est utilisée par les interfaces de débogage du CLR pour obtenir des informations sur le module chargé à partir du débogueur.  
  
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
