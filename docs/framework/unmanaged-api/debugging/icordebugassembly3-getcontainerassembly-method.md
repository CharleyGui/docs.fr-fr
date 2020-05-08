---
title: ICorDebugAssembly3::GetContainerAssembly, méthode
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 068a08d70f2443edfe0970ec1ffb8cba9953c6b9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894853"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a>ICorDebugAssembly3::GetContainerAssembly, méthode
Retourne l'assembly conteneur de cet objet `ICorDebugAssembly3`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppAssembly`  
 Pointeur vers l’adresse d’un objet ICorDebugAssembly qui représente l’assembly de conteneur, ou **null** si l’appel de méthode échoue.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK`Si l’appel de la méthode a échoué ; Sinon, `S_FALSE`et `ppAssembly` a la **valeur null**.  
  
## <a name="remarks"></a>Notes   
 Si cet assembly a été fusionné avec d’autres assemblys dans un seul assembly conteneur, cette méthode retourne l’assembly conteneur. Pour plus d’informations et de terminologie, consultez la rubrique [ICorDebugProcess6 :: enablevirtualmodulesplitting,](icordebugprocess6-enablevirtualmodulesplitting-method.md) .  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugAssembly3, interface](icordebugassembly3-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
