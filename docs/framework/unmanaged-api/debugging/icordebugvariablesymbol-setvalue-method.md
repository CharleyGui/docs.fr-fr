---
title: Méthode ICorDebugVariableSymbol::SetValue
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
ms.openlocfilehash: fe6b63e4c0706dd69478753b3512f606e73bee7c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790855"
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
  
## <a name="parameters"></a>Parameters  
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
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugVariableSymbol, interface](icordebugvariablesymbol-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
