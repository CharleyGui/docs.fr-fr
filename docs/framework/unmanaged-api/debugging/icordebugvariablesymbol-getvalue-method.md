---
title: Méthode ICorDebugVariableSymbol::GetValue
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
ms.openlocfilehash: 2dc074384d209d0740a1fb0a9a16d96ff355f02b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790877"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a>Méthode ICorDebugVariableSymbol::GetValue
Obtient la valeur d'une variable sous forme d'un tableau d'octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `offset`  
 [in] Offset de démarrage dans la variable au niveau duquel lire la valeur. Ce paramètre est utilisé lors de la lecture de champs membres d'un objet.  
  
 `cbContext`  
 [in] Taille en octets de l'argument `context`.  
  
 `context`  
 [in] Contexte de thread utilisé pour lire la valeur.  
  
 `cbValue`  
 [in] Taille en octets de la mémoire tampon `pValue`.  
  
 `pcbValue`  
 [out] Nombre d'octets réellement écrits dans la mémoire tampon `pValue`.  
  
 `pValue`  
 [out] Tableau d'octets contenant la valeur de la variable.  
  
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
