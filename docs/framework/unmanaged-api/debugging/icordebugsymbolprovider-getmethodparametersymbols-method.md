---
title: ICorDebugSymbolProvider::GetMethodParameterSymbols, méthode
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d016007d09a06e923bef78fa8ead99e1e1ce9420
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771372"
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a>ICorDebugSymbolProvider::GetMethodParameterSymbols, méthode
Obtient les symboles de paramètre d'une méthode en fonction de l'adresse virtuelle relative (RVA) de cette méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `nativeRVA`  
 [in] Adresse virtuelle relative native de la méthode.  
  
 `cRequestedSymbols`  
 [in] Nombre de symboles locaux demandés.  
  
 `pcFetchedSymbols`  
 [out] Pointeur vers le nombre de symboles récupérés par la méthode.  
  
 `pcFetchedSymbols`  
 [out] Un pointeur vers un [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) tableau qui contient les symboles locaux de la méthode.  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetMethodLocalSymbols, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)
- [ICorDebugSymbolProvider, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
