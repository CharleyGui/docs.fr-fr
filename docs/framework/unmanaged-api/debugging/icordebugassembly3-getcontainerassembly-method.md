---
title: Méthode ICorDebugAssembly3::GetContainerAssembly
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 969cca6d5613670fc4b26fc973785b4874c3684c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778072"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a>Méthode ICorDebugAssembly3::GetContainerAssembly
Retourne l'assembly conteneur de cet objet `ICorDebugAssembly3`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `ppAssembly`  
 Pointeur vers l’adresse d’un objet ICorDebugAssembly qui représente l’assembly de conteneur, ou **null** si l’appel de méthode échoue.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK` si l’appel de la méthode a échoué ; Sinon, `S_FALSE`et `ppAssembly` a la **valeur null**.  
  
## <a name="remarks"></a>Notes  
 Si cet assembly a été fusionné avec d’autres assemblys dans un seul assembly conteneur, cette méthode retourne l’assembly conteneur. Pour plus d’informations et de terminologie, consultez la rubrique [ICorDebugProcess6 :: enablevirtualmodulesplitting,](icordebugprocess6-enablevirtualmodulesplitting-method.md) .  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugAssembly3, interface](icordebugassembly3-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
