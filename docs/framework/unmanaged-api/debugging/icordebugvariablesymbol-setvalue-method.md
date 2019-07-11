---
title: Méthode ICorDebugVariableSymbol::SetValue
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5c1c77b92d94062206cf9eb38981f38ff2a1cad
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775453"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a>Méthode ICorDebugVariableSymbol::SetValue
Affecte la valeur d'un tableau d'octets à une variable.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `offset`  
 [in] Offset de démarrage dans la variable au niveau duquel définir la valeur. Ce paramètre est utilisé lors de l'écriture dans des champs membres d'un objet.  
  
 `threadID`  
 [in] Identificateur du thread dont le contexte doit être mis à jour pour refléter la nouvelle valeur.  
  
 `cbContext`  
 [in] Taille en octets du contexte de thread.  
  
 `context`  
 [in] Contexte de thread utilisé pour écrire la valeur.  
  
 `cbValue`  
 [in] Taille en octets de la mémoire tampon `pValue`.  
  
 `pValue`  
 [in] Mémoire tampon contenant la valeur à définir.  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugVariableSymbol, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
