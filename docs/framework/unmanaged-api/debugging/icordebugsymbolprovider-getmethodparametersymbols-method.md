---
title: ICorDebugSymbolProvider::GetMethodParameterSymbols, méthode
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
ms.openlocfilehash: a940077e50ff251111ca6eedaee49401775644d3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791595"
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
  
## <a name="parameters"></a>Parameters  
 `nativeRVA`  
 [in] Adresse virtuelle relative native de la méthode.  
  
 `cRequestedSymbols`  
 [in] Nombre de symboles locaux demandés.  
  
 `pcFetchedSymbols`  
 [out] Pointeur vers le nombre de symboles récupérés par la méthode.  
  
 `pcFetchedSymbols`  
 à Pointeur vers un tableau [méthode icordebugvariablesymbol](icordebugvariablesymbol-interface.md) qui contient les symboles locaux de la méthode.  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetMethodLocalSymbols, méthode](icordebugsymbolprovider-getmethodlocalsymbols-method.md)
- [ICorDebugSymbolProvider, interface](icordebugsymbolprovider-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
