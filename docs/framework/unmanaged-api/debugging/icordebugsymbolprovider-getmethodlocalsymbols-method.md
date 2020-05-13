---
title: ICorDebugSymbolProvider::GetMethodLocalSymbols, méthode
ms.date: 03/30/2017
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
ms.openlocfilehash: 7e9aa01a3fa1c90b0ab4f85970c4eb294b9a4904
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379611"
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a>ICorDebugSymbolProvider::GetMethodLocalSymbols, méthode
Obtient les symboles locaux d'une méthode selon l'adresse virtuelle relative (RVA) de cette méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMethodLocalSymbols(  
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
 à Pointeur vers un tableau [méthode icordebugvariablesymbol](icordebugvariablesymbol-interface.md) qui contient les symboles locaux de la méthode.  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetMethodParameterSymbols, méthode](icordebugsymbolprovider-getmethodparametersymbols-method.md)
- [ICorDebugSymbolProvider, interface](icordebugsymbolprovider-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
