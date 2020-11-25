---
title: ICorDebugModuleDebugEvent::GetModule, méthode
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: ec23cda02ff689a3365fe96fb5280054a9795caa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709503"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a>ICorDebugModuleDebugEvent::GetModule, méthode

Obtient le module fusionné qui vient d’être chargé ou déchargé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `ppModule`  
 [out] Pointeur vers l'adresse d'un objet ICorDebugModule représentant le module fusionné qui vient d'être chargé ou déchargé.  
  
## <a name="remarks"></a>Remarques  

 Vous pouvez appeler la méthode [GetEventKind](icordebugdebugevent-geteventkind-method.md) pour déterminer si le module a été chargé ou déchargé.  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugModuleDebugEvent, interface](icordebugmoduledebugevent-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
