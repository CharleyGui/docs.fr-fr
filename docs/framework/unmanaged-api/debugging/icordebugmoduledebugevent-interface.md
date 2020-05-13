---
title: ICorDebugModuleDebugEvent, interface
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: ec6bad730d807b9a36ce5bba1c6f5d80da375f6d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213331"
---
# <a name="icordebugmoduledebugevent-interface"></a>ICorDebugModuleDebugEvent, interface
Étend l’interface [ICorDebugDebugEvent](icordebugdebugevent-interface.md) pour prendre en charge les événements au niveau du module.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetModule, méthode](icordebugmoduledebugevent-getmodule-method.md)|Obtient le module fusionné qui vient d’être chargé ou déchargé.|  
  
## <a name="remarks"></a>Remarks  
 Les types d’événements [MODULE_LOADED](cordebugdebugeventkind-enumeration.md) et [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) implémentent cette interface.  
  
> [!NOTE]
> L'interface est uniquement disponible avec .NET Native. Une tentative d'appel à `QueryInterface` pour récupérer un pointeur d'interface retourne `E_NOINTERFACE` pour les scénarios ICorDebug en dehors de .NET Native.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
