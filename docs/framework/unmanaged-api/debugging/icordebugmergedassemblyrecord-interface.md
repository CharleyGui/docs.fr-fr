---
title: ICorDebugMergedAssemblyRecord, interface
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
ms.openlocfilehash: a26702c6b21e4bfe352d861387a80b976a8dc556
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710491"
---
# <a name="icordebugmergedassemblyrecord-interface"></a>ICorDebugMergedAssemblyRecord, interface

Fournit des informations sur un assembly fusionné.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetCulture, méthode](icordebugmergedassemblyrecord-getculture-method.md)|Obtient la chaîne de nom de culture de l'assembly.|  
|[GetIndex, méthode](icordebugmergedassemblyrecord-getindex-method.md)|Obtient l'index de préfixe de l'assembly.|  
|[GetPublicKey, méthode](icordebugmergedassemblyrecord-getpublickey-method.md)|Obtient la clé publique de l'assembly.|  
|[GetPublicKeyToken, méthode](icordebugmergedassemblyrecord-getpublickeytoken-method.md)|Obtient le jeton de clé publique de l'assembly.|  
|[GetSimpleName, méthode](icordebugmergedassemblyrecord-getsimplename-method.md)|Obtient le nom simple de l'assembly.|  
|[GetVersion, méthode](icordebugmergedassemblyrecord-getversion-method.md)|Obtient les informations de version de l'assembly.|  
  
## <a name="remarks"></a>Remarques  
  
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
