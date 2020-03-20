---
title: ICorDebugDataTarget2::GetSymbolProviderForImage, méthode
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
ms.openlocfilehash: 500d36b414be686071990a6e1b40dd8759d02ae9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178933"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a>ICorDebugDataTarget2::GetSymbolProviderForImage, méthode
Retourne le fournisseur de symboles d'un module à partir de l'adresse de base de ce module.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `imageBaseAddress`  
 [dans] Une [valeur CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) qui représente l’adresse de base d’un module.  
  
 `ppSymProvider`  
 [out] Un pointeur à l’adresse d’un objet [ICorDebugSymbolProvider.](icordebugsymbolprovider-interface.md)  
  
## <a name="remarks"></a>Notes   
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugDataTarget2, interface](icordebugdatatarget2-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
